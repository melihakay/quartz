---
title:
draft: false
description: Development road-map for the Wheelie project.
aliases:
tags:
  - wheelie
  - formula-student-driverless
date: 19.10.2025
---
Here lies the development road-map for the [[Wheelie, An End-to-End Autonomous Racing Framework for Formula Student Driverless Competition|Wheelie]] project. 

```timeline-labeled
[line-2, body-2]

date: October 2025
title: Perception Final
content:
- [ ] [[Hungarian Algorithm | Hungarian algorithm]] for LiDAR-Camera fusion.

date: November 2025
title: Vehicle Model & State Estimation
content:
- [ ] Implement [[Dynamic Bicycle Model]]
- [ ] Design and implement [[Extended Kalman Filter | EKF]] for [[Inertial Measurement Unit | IMU]]-Wheel Odometry fusion.

date: December 2025
title: Graph-SLAM
content:
- [ ] Implement [[Graph-SLAM]].

>[!success] Vehicle can map the environment under the manual control

date: January 2026
title: Planning & Control
content:
- [ ] Implement [[Delaunay Triangulation]] on map.
- [ ] Implement [[Model Predictive Controller]].
      
>[!success] Autonomous control
```
