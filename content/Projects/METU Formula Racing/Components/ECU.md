Pins:

- Bamocar Hard Enable (for [[R2D]])
- APPS
- AMI (ledli) [+4 pin] +SCS pin
- Brake light
- 

ECU is able to open [[SDC]] via watchdog timer. Note that this is not programmable logic since it cannot close [[SDC]] on request.

>[!warning]
>If the proper vehicle operation cannot be ensured (e.g. loss of envi- ronmental perception) the system shall react by activating the EBS immediately. This sig- nificantly decreases the time between a fail- ure and the brake maneuver compared to a brake maneuver that is manually triggered via the RES. 
# Modes

# Manual

- APPS data for throttle
- Reject Aut. throttle (hardware)

>[!info] We might disconnect PC USB if rules do not permit throttle filtering using only software.

# Autonomous