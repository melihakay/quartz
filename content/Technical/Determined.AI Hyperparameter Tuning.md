# Tutorials

![](https://www.youtube.com/watch?v=WEYu8DI4LOU)
# Hyperparameters

The `hyperparameters` section defines the hyperparameter space for the experiment. The appropriate hyperparameters for a specific model depend on the nature of the model being trained. In [[DeterminedAI]], it is common to specify hyperparameters that influence various aspects of the model’s behavior, such as data augmentation, neural network architecture, and the choice of optimizer, as well as its configuration.

>[!warning] A deep learning model’s objective (e.g., validation loss) as a function of the hyperparameters is non-continuous and noisy, so we can’t apply analytical or continuous optimization techniques to calculate the validation objective given a set of hyperparameters. Thus, hyperparameter tuning is a black box optimization problem in that we must train a model under a set of hyperparameters in order to evaluate the objective.    

> [!info] To access the value of a hyperparameter in a particular trial, use the trial context with `context.get_hparam()`. For example, you can access the current value of a hyperparameter named `learning_rate` by calling `context.get_hparam("learning_rate")`.

>[!info] Every experiment must specify a hyperparameter called `global_batch_size`. This hyperparameter is required for distributed training to calculate the appropriate per-worker batch size. The batch size per slot is computed at runtime, based on the number of slots used to train a single trial of the experiment (see [resources.slots_per_trial](https://docs.determined.ai/latest/reference/experiment-config-reference.html#exp-config-resources-slots-per-trial)). To access the updated values, use the trial context with `context.get_per_slot_batch_size()` and `context.get_global_batch_size()`.

Determined supports the following searchable hyperparameter data types:

- `int`: an integer within a range
- `double`: a floating point number within a range
- `log`: a logarithmically scaled floating point number. Users specify a `base`, and Determined searches the space of `exponents` within a range.
- `categorical`: a variable that can take on a value within a specified set of discrete values. The values themselves can be of any type.

```yaml
hyperparameters:
  global_batch_size: 64
  optimizer_config:
    optimizer:
      type: categorical
      vals:
        - SGD
        - Adam
        - RMSprop
    learning_rate:
      type: log
      minval: -5.0
      maxval: 1.0
      base: 10.0
  num_layers:
    type: int
    minval: 1
    maxval: 3
  layer1_dropout:
    type: double
    minval: 0.2
    maxval: 0.5
```

# Searcher

The `searcher` section defines how the experiment’s hyperparameter space will be explored. To run an experiment that trains a single trial with fixed hyperparameters, specify the `single` searcher and specify constant values for the model’s hyperparameters. Otherwise, Determined supports three different hyperparameter search algorithms: `adaptive_asha`, `random`, and `grid`.

- [Single](https://docs.determined.ai/latest/model-dev-guide/hyperparameter/search-methods/hp-single.html#topic-guides-hp-tuning-det-single) is appropriate for manual hyperparameter tuning, as it trains a single hyperparameter configuration.
- [Grid](https://docs.determined.ai/latest/model-dev-guide/hyperparameter/search-methods/hp-grid.html#topic-guides-hp-tuning-det-grid) evaluates all possible hyperparameter configurations by brute force and returns the best.
- [Random](https://docs.determined.ai/latest/model-dev-guide/hyperparameter/search-methods/hp-random.html#topic-guides-hp-tuning-det-random) evaluates a set of hyperparameter configurations chosen at random and returns the best.

Check [DeterminedAI Searchers](https://docs.determined.ai/latest/reference/experiment-config-reference.html#searcher).

```yaml
searcher:
  name: random
  metric: accuracy
  max_trials: 5
```

```yaml
searcher:
  name: "adaptive_asha"
  metric: "validation_loss"
  max_trials: 16
  time_metric: batches
  max_time: 100000
  max_concurrent_trials: 8
```

## Adaptive Search

Our default recommended search method is [Adaptive (ASHA)](http://arxiv.org/pdf/1810.05934), a state-of-the-art early-stopping based technique that speeds up traditional techniques like random search by periodically abandoning low-performing hyperparameter configurations in a principled fashion.

[[Adaptive ASHA Searcher]] offers asynchronous search functionality more suitable for large-scale HP search experiments in the distributed setting.

# Handle Trial Errors and Early Stopping Requests

When a trial encounters an error or fails unexpectedly, Determined will restart it from the latest checkpoint up to some maximum number of times, which is configured by [max_restarts](https://docs.determined.ai/latest/reference/experiment-config-reference.html#max-restarts) in the experiment configuration. After Determined reaches `max_restarts`, any further trials that fail will be marked as errored and will not be restarted. For the [adaptive (ASHA)](https://docs.determined.ai/latest/model-dev-guide/hyperparameter/search-methods/hp-adaptive-asha.html#topic-guides-hp-tuning-det-adaptive-asha) search method, which adapts to validation metric values, we do not continue training errored trials, even if the search method would typically call for us to continue training. This behavior is useful when some parts of the hyperparameter space result in models that cannot be trained successfully (e.g., the search explores a range of batch sizes and some of those batch sizes cause GPU OOM errors). An experiment can complete successfully as long as at least one of the trials within it completes successfully.

Trial code can also request that training be stopped early, e.g., via a framework callback such as [tf.keras.callbacks.EarlyStopping](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/EarlyStopping) or manually by calling `determined.TrialContext.set_stop_requested()`. When early stopping is requested, Determined will finish the current training or validation workload and checkpoint the trial. Trials that are stopped early are considered to be “completed”, whereas trials that fail are marked as “errored”.

# Hyperparameter Search Constraints

Determined’s Hyperparameter (HP) Search Constraints API enables finer-grained control over the hyperparameter search space through the specification of additional constraints. This functionality is particularly useful for incorporating prior knowledge/domain expertise into a hyperparameter search and constraining the search to models that fit a particular deployment environment.

Using Determined’s HP Search Constraints requires no changes to the configuration files. Rather, users can simply raise a `determined.InvalidHP` exception in their model code when the trial is first created in its constructor or at any subsequent point during training. This user-raised exception is then handled by Determined’s system internally – resulting in the graceful stop of the current trial being trained, logging the InvalidHP exception in the trial logs, and propagating that information to the search method.

>[!warning] It is important to note that each search method has different behavior when a `determined.InvalidHP` is raised by the user in accordance with the internal dynamics of each searcher, as detailed below.

## HP Search Constraints in PyTorch vs. TF Keras

Since the PyTorch and TF Keras APIs have different behavior, the timing/placement of user-raised InvalidHP exceptions are somewhat different.

In the case of PyTorch, this exception can be raised in the trial’s `__init__`, `train_batch`, or `evaluate_batch` methods. In the case of TF Keras, this exception can be raised in the `__init__` method or in an `on_checkpoint_end` callback.

## Searcher-Specific Behavior for HP Search Constraints

|Search Algorithm|HP Search Constraints Behavior|
|---|---|
|Single|Not applicable to HP Search Constraints as only a single hyperparameter configuration will be trained.|
|Grid|Does nothing since grid does not take actions based on search status or progress.|
|Random|Gracefully terminates current trial, creates a new trial with a randomly sampled set of hyperparameters and adds it to the trial queue.|
|Adaptive (ASHA)|Gracefully terminates and removes metrics associated with the current trial and creates a new trial with a randomly sampled set of hyperparameters.|

# Instrument Model Code

Determined injects hyperparameters from the experiment configuration into model code via a context object in the Trial base class. This `TrialContext` object exposes a `get_hparam()` method that takes the hyperparameter name. For example, to inject the value of the `dropout_probability` hyperparameter defined in the experiment configuration into the constructor of a PyTorch [Dropout](https://pytorch.org/docs/stable/generated/torch.nn.Dropout.html) layer:

```python
nn.Dropout(p=self.context.get_hparam("dropout_probability"))
```

To see hyperparameter injection throughout a complete trial implementation, refer to the [Training APIs](https://docs.determined.ai/latest/model-dev-guide/api-guides/apis-howto/_index.html#apis-howto-overview).

