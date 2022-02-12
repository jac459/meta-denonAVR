## DENON DRIVER FOR NEEO-META OVER HTTP
This package is still under development, but has been tested for a number of buttons on AVR-4400H.

# Contents
This package consists of a NEEO-META devicedriver. 
Volume-Slider only implemented for Mai-Zone. If anyone needs more, let me know it.
This driver published some data over mqtt.
Published data are:
MainPower 
MainInput
MainVolume
MainMute
Zone2Power
Zone2Input
Zone2Volume
Zone2Mute
Zone3Power
Zone3Input
Zone3Volume
Zone3Mute

# Connectiviy
This driver uses the http protocol to control your DenonAVR. Denon Standard-Port till 2016 = 80. Newer Models 8080.
 
# POWER ON and OFF
This package can power on your Denon over http if the Denon is keeping the network connection OPEN.
The POWER OFF command will put the Denon in standby mode, so it can be woken up by http-commands.  

# Autodiscovery 
Not supported. IP must registerd at the start of the driver.

# Issues
None this far.
