---
title: System Critical Signal
draft: false
description: 
aliases: 
tags: 
date:
---

>[!info] SCS in Autonomous Systems 
>[[FSG_Tech_Inspection_24.pdf#page=32|FSG24 Tech Inspection Workshop]] 
>If an AS is implemented, all its signals must be monitored accordingly (T 11.9 + T 14.5.1)
>
>[[FSG25_AS_Beginners_Guide_v1.0.pdf|FSG25 AS Beginner's Guide]]
>The ASB signals and other signals of the Autonomous System are considered to be System Critical Signals (SCSs), see T 11.9.1, and therefore require some additional measures to be taken that are also discussed in this document. 

>[!todo] Checking SCS for AS
>USB connection is used between ECU and ACU
>>[!danger] T 11.9.2
>>- (c) Failures of sensor signals used in programmable devices: 
>>	- Implausibility due to out of range signals, e.g. mechanically impossible angle of an angle sensor. 
>>- (d) Failures of digitally transmitted signals by cable or wireless: 
>>	- Data corruption (e.g. checked by a checksum) 
>>	- Loss and delay of messages (e.g. checked by transmission time outs)



