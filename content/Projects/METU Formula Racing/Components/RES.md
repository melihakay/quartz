---
title: Remote Emergency System
draft: false
description: 
aliases: 
tags: 
date:
---
>[!todo] RES Bypass [[FSG25_AS_Beginners_Guide_v1.0.pdf#page=3|FSG25 AS Beginner's Guide]]
>As the RES is always required to close the Shutdown Circuit (SDC), it is mandatory to deactivate the RES during manual driving to avoid any other problems of the RES in manual mode. Due to the safety problems which may arise from this bypass the rules only permit one solution, which is shown in Figure 1 according to T 14.3.5. This circuit needs to be implemented thoroughly to avoid a non-functional RES. Due to the safety criticality, only safety certified relays with forcibly guided or a mirrored contacts are permitted. This certification ensures that both contacts are never closed at the same time. Solutions relying on software are not allowed.

>[!todo] Race Mode Selector [[FSG25_Competition_Handbook_v1.0.pdf|FSG25 Competition Handbook]] (DE 8.4.16)
In order to enable the Race E-Key frequencies at the receiver, the input “Race 1” has to be set to high (by bridging the input with supply “+Ub”). That needs to be done upon receival of the E-Key with a flip switch in proximity to the Autonomous Mission Indicator ([[AMI]]), see T 14.10. Race mode position has to be marked with an “R”. Correct mode selection can be traced via the input’s LED as well as in PDO 2007, bit 7. 

