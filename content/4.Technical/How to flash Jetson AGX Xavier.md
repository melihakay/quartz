You cannot flash older distributions of L4T with newer host distros. Easiest way to overcome this is to use a bootable Ubuntu 20.04 installation disk and hit try. 

Then install sdkmanager using the .deb file downloaded from the NVIDIA website. Be sure that you have put your [[Jetson AGX Xavier]] in flash mode by holding down middle button and then pressing power button. After 2 seconds you should release recovery button. Check `lsusb`.

Open SDKManager, select target as Jetson AGX Xavier. SDKManager should detect automatically if the Xavier is in flash mode. Then select the target components. If you USB disk is smaller than 32 GB you might need to connect external storage for the target components download. Then 