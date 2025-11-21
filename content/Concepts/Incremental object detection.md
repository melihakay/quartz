---
title:
draft: false
description:
aliases:
  IOD
tags:
  object-detection
date:
---

> Incremental Object Detection (IOD). As a typical extension of incremental learning, IOD aims to handle both old and new task data appearing simultaneously in images. In this task, Knowledge Distillation (KD) [4, 15, 29, 39] has been widely adopted for its ability to leverage prior knowledge from new training samples, thereby minimizing discrepancies between the responses of the previous and current models [3, 13, 31, 45]. A pioneering approach, ILOD [36], applies knowledge distillation to Fast R-CNN [11] to retain responses for old classes, effectively mitigating catastrophic forgetting. 
> 
> Subsequently, knowledge distillation has been extended to various object detection frameworks, including SID [32] on CenterNet [46], RILOD [19] on RetinaNet [24], and ERD [9] on GFLV1 [23]. Further advancements have applied this technique to Faster R-CNN [34], with methods such as CIFRCN [14], Faster ILOD [31], DMC [42], BNC [7], and IOD-ML [17]. More recently, knowledge distillation has been integrated into Transformer-based detectors, leading to methods such as CL-DETR [28], DyQ-DETR [43], and Incremental-DETR [8], leveraging architectures like DETR [2], UP-DETR [6], and Deformable DETR [48]. 
> 
> Exemplar Replay (ER) is another key strategy in incremental object detection [1, 12, 33, 35]. ORE [16] uses an exemplar set for fine-tuning, while AFD [26] introduces adaptive sampling, and CL-DETR [28] applies distributionpreserving calibration. ABR [27] further enhances replay with a mosaic-based approach. However, these methods often rely on exemplars with incomplete annotations, overlooking their informativeness and reliability. In domainincremental object detection, this limitation weakens crossdomain knowledge transfer, making it harder to address data and feature distribution shifts.

[[Dual Domain Control via Active Learning for Remote Sensing Domain.pdf#page=2&selection=83,0,121,32|Dual Domain Control via Active Learning for Remote Sensing Domain, page 2]]

# Domain incremental object detection

> Domain incremental object detection aims to train a model to detect objects across a sequence of $T$ tasks, where each task $D^t = (x^t, y^t$ consists of a set of images xt from the t-th domain. The model should be able to detect objects in new domain images $x^t$ while preserving its ability to detect objects in previously encountered domains , without experiencing catastrophic forgetting. However, domain increment introduces two primary effects: the shift in data distribution and the shift in feature vectors.

[[Dual Domain Control via Active Learning for Remote Sensing Domain.pdf#page=3&selection=215,0,263,1|Dual Domain Control via Active Learning for Remote Sensing Domain, page 3]]