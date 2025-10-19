---
title: Emergency Brake System
draft: false
description: 
aliases: 
tags: 
date:
---
>[!warning] ASB & EBS statuses must be published to CAN for [[Data Logger]]. Check [[Data Logger]]
>To do so we need to settle who will read and publish sensor values and statuses.

>[!info] [[FSG25_AS_Beginners_Guide_v1.0.pdf#page=page=14|EBS Startup ]]
>We first close [[LVMS]] in our sequence. Then we open [[TSMS]] but precharge doesn't start despite [[EBS]] coil has power, since activation logic is not complete. [[TSAL]] is still green. EBS valve closes after we close TSMS. In this case [[EBS]] doesn't go off since it has power. If the valve is opened before shutting down the TSMS, the EBS will blow because power is not reaching the EBS coil at the end of the [[SDC]], there is a power interruption in the EBS.


