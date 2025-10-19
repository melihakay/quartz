
# Structs

## CanMsg

```cpp
struct devrimCanMsg {
	uint32_t id
	uint8_t length
	bool is_extended
	int8_t[] data
};
```

## ControlCommand

```cpp
struct ControlCommand{
	float torque; // -1 to 1
	float brake; // -1 to 1
	float wheel_angle; // rad
	float wheel_angle_rate // rad/s
}
```

## AS State

# Classes

- DevrimCan
	- has-a canHandler
	- has-a Bamocar is-a BaseCanDevice

## DevrimCan

Member:

- CanHandler canHandler
- Bamocar bamocar

Methods:

Examples:

```cpp
// Send Bamocar Torque
devrimCan.bamocar.setTorqueCommandNormalized(float torqueCommand);
devrimCan.bamocar.sendTorqueCommand();
```

```cpp
class DevrimCan {
	private:
		CanHandler* can;
		
		Bamocar bamocar;
		Imecar imecar;
		RemoteEmergencySystem res;
		Ena36ilBrakeSensor brakeSensor;
		
	public:
		DevrimCan(CanHandler* canHandler) :
			can(canHandler)
		{
			bamocar(&can);
			imecar(&can);
			res(&can);
			brakeSensor(&can);
		}
		
		void digest(CanMsg msg) {
			switch (msg.id) {
				case ...
			}
		}
}



// Main

SN65CanHandler canHandler(pin, min);
DevrimCan devrimCan(&canHandler);

CanMsg canReceivedMsg;
void canListenTask() {
	while true {
		bool rxSuccess = canHandler.rx(&canReceivedMsg);
		if (rxSuccess) {
			devrimCan.digest(msg);
		}
	}
}
```
## CanHandler (Abstract)

All CanHandler classes should be able to handle both extended and normal methods.

Methods: 

- rx([[#CanMsg]] msg) -> bool
- tx([[#CanMsg]]) -> bool

### Sn65TwaiCanHandler: CanHandler

###  Ros2CanHandler: CanHandler

Ros2CanHandler(canHandler*)


## BaseCanDevice (Abstract)

Methods:

- void processCanMsg([[#CanMsg]])

Members:

- CanHandler canHandler

### Bamocar

```cpp
public void setTorqueCommandNormalized(float torqueCommand) {
	torqueCommandNormalized = torqueCommand;
}

public bool sendTorqueCommand() {
	can->tx
}
```

# CAN Listen

## ECU

```cpp
devrimCan
```