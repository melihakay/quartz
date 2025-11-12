---
title:
draft: false
description:
aliases:
tags:
  - machine-learning
date:
---

# Notes from papers

## Agnostic Active Learning Is Always Better Than Passive Learning

>[!info]
>See the [video](https://www.youtube.com.mcas.ms/watch?v=0TADiY7iPAc&t=3530s) and the [[Agnostic Active Learning Is Always Better Than Passive Learning.pdf|the paper]]


## Active Learning from Scene Embeddings for End-to-End Autonomous Driving

See [[Active Learning from Scene Embeddings for End-to-End Autonomous Driving.pdf|the paper]].

> we propose an active learning framework that relies on these vectorized scene-level features, called SEAD. The framework selects initial data based on driving-environmental information and incremental data based on BEV features. Experiments show that we only need 30% of the nuScenes training data to achieve performance close to what can be achieved with the full dataset.  [[Active Learning from Scene Embeddings for End-to-End Autonomous Driving.pdf#page=1&selection=71,36,86,23|Active Learning from Scene Embeddings for End-to-End Autonomous Driving, page 1]]

> In complex and dynamic driving environments, E2E approaches demonstrate the potential to handle diverse scenarios and better tackle real-world challenges. However, E2E-AD models have higher data requirements [Caesar et al., 2020; Jia et al., 2024]. ... To alleviate these labeling costs, active learning has emerged as a promising solution. By selecting the most informative samples for labeling, active learning aims to achieve high model performance with fewer labeled examples, thus reducing both labeling and training expenses [Ren et al., 2021; Zhan et al., 2022]. [[Active Learning from Scene Embeddings for End-to-End Autonomous Driving.pdf#page=1&selection=134,0,170,55|Active Learning from Scene Embeddings for End-to-End Autonomous Driving, page 1]]

> There is an urgent need to find a data selection strategy that does not depend on manually set selection rules and is more generalizable to different data distributions. [[BEV]] algorithms [Philion and Fidler, 2020; Huang et al., 2021; Liu et al., 2023] shine in AD by virtue of their ability to com- prehensively perceive the environment, efficiently fuse multi-sensor data, and improve system stability and reliability. BEV-Former [Li et al., 2022] achieved state-of-the-art performance in perception tasks using solely visual inputs.
[[Active Learning from Scene Embeddings for End-to-End Autonomous Driving.pdf#page=1&selection=187,0,206,48|Active Learning from Scene Embeddings for End-to-End Autonomous Driving, page 1]]

> We first leverage the abundant dynamic and static information in AD datasets to construct a diverse initial dataset, which is used to train a baseline model. Using this baseline model, we extract BEV features from the remaining data to evaluate scene value based on the predefined rule. The rule can be summarized as extracting key elements from BEV features and calculating the cumulative changes in these elements at the clip level as the selection criterion. For valuable scenes, key consecutive frames are selected and labeled, then combined with the existing data for further rounds of training and refinement. 
[[Active Learning from Scene Embeddings for End-to-End Autonomous Driving.pdf#page=2&selection=7,56,17,58|Active Learning from Scene Embeddings for End-to-End Autonomous Driving, page 2]]