---
title: Autonomous System Status Indicator
draft: false
description: 
aliases: 
tags: 
date:
---

>[!todo] Rules [[FSG_Tech_Inspection_24.pdf#page=33|FSG24 Tech Inspection Workshop]]
>-  There need to be exactly three ASSIs (T 14.10.1) 
>- At least one ASSI must be visible from any angle (T 14.10.3) 
>- Each ASSI must be visible in bright sunlight (T 11.10.1)

>[!todo] [[FSG25_AS_Beginners_Guide_v1.0.pdf | FSG25 AS Beginner's Guide]]
>The definition of the AS statuses does not require any information on the previous status the AS has shown. Therefore, the implementation for determining the AS status can be done by transforming the flowchart given in the rules **into a simple set of nested if-else statements that is called with its required inputs during every software execution cycle**. The computed result will then be passed to the [[ASSI]], see chapter 6 and the [[Data Logger]], see chapter 15. 
>>[!info] Thus [[ECU]] computes the [[ASSI]] status using the inputs in our scenario.





