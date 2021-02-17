## DENON DRIVER FOR NEEO-META OVER HTTP
This package is still under development, but has been tested for a number of buttons on both an older Denon AVBR3808 as well as a DENON AVC-X8500.

# Contents
This package consists of both a NEEO-MEA devicedriver and a Node-0RED exernal node. As the Denon-node in Node-RED is developed outside our meta-team, we don't have control over it. But is seems quite stable during our tests.  

Both files are supplied within this package in Github. The device driver can be found as an "External" installable package in meta-Library, but can be copied, modified and placed in Meta's UserLibrary as well.

The Node-RED flow is populated with the most-used commands for Denon, but not all buttons are actually coded in it. Functions will/can be defined that handle buttons that are not yet in the Node-RED FLOW.   

# Connectiviy
 The "external node" on the Denon AVR3808 will only connect successfully to your Denon if no other connection is running. Multiple connections don;t seem to be supported by the Denon firmware. 
 
# POWER ON and OFF
This package can power on your Denon over HTTP if the Denon is keeping the network connection OPEN. Not all Denon-devices allow this, the ones tha do n eed to have this configured through he menu. 
For devices that do not listen to HTTP when powered-off, we have included an infrared-POWER ON command.
The POWER OFF command will put the Denon in standby mode, so it can be woken up by HTTP-commands.  

# Issues
Currently, two issues exist:
- MUTE Toggle is implemented as 2 buttons: MUTE ON and MUTE OFF as he serial interface of Denon does not support MUTE TOGGLE.
- INPUT DVD doesn't seem to be recognized by the X8500H.... Looks like a bug in the Denon firmware.

For this, you need to have:

Preferably, a complete NEEO eco system can run on a rooted NEEO-brain, configured by installmeta.sh (see https://github.com/jac459/neeo2021onward/tree/main/Meta%20running%20in%20Brain)
and the files in this package.
 
Alternatively, it can run on:
- the metadriver installed at an arbitrary location of your own choice (see https://github.com/jac459/metadriver)
- an mqtt-installation (tested with mosquitto)
- a node-red installation.

This flow has two types of I/O nodes:
1) MQTT as the default communication-method with the Metadriver running on the NEEO Brain.
2) Target-nodes which represent the equipment; in this case they are called Denon-In and Denon out. For this, you need to install the Library called "NODE RED Contrib Denon". 

Use these two types that are also used in the generic description found at https://github.com/jac459/neeo2021onward/blob/main/Instructions_for_Flows_Node-RED_FLOW.MD
