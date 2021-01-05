
This package is still under development and must be seen as Alpha-version.
Currenlty, it's missing the power-on button. This will come thbrough broadlink learn IR-function, but that function isn't available yet.
Will follow once broadlik is running in meta.
Second, we're using a Denon-noide in Node-RED that is developed outside our meta-team, where we donl;t have control over. 
 This "external node" (or my Denon AVR) sometimes just doesn't open the network-connection, or disconnects the den on, showing Inactive on the node. This state probably isn't detected/handled correctly by the external node. Still looking in to this

This package delivers support for Denon AVR's with older protocols (2012 and earlier) to be controlled wit a NEEO-remote through HTTP.

For this, you need to have:

Preferably, a complete NEEO eco system can run on a rooted NEEO-brain, configured by installmeta.sh (see https://github.com/jac459/neeo2021onward/tree/main/Meta%20running%20in%20Brain)
and the files in this package.
 
Alternatively, it can run on:
- the metadriver installed at an arbitrary location of your own choice (see https://github.com/jac459/metadriver)
- an mqtt-installation (tested with mosquitto)
- a node-red installation.

This flow has two types of nodes:
1) MQTT as the default communication-method with the Metadriver running on the NEEO Brain.
2) Target-nodes which represent the equipment; in this case they are called Denon-In and Denon out.

Use these two types that are also used in the generic description found at https://github.com/jac459/neeo2021onward/blob/main/Instructions_for_Flows_Node-RED_FLOW.MD
