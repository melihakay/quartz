---
title: Electronical Control Unit
draft: false
description: 
aliases: 
tags: 
date:
---
Pins:

- Bamocar Hard Enable (for [[R2D]])
- APPS
- AMI (with led) [+4 pin] +SCS pin
- Brake light
- [[ASB]] watchdog ready & watchdog reset

>[!info] ECU is able to open [[SDC]] via watchdog timer. Note that this is not programmable logic since it cannot close [[SDC]] on request.

>[!warning] [[FSG25_AS_Beginners_Guide_v1.0.pdf|FSG25 AS Beginner's Guide]]
>If the proper vehicle operation cannot be ensured (e.g. loss of environmental perception) the system shall react by activating the [[EBS]] immediately. This significantly decreases the time between a failure and the brake maneuver compared to a brake maneuver that is manually triggered via the RES. 
# Modes

# Manual

- APPS data for throttle
- Reject Aut. throttle (hardware)

>[!info] We might disconnect PC USB if rules do not permit throttle filtering using only software.

# Autonomous