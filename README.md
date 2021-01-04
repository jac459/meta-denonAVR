
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


Installation.

A) DenonAVR, Custom driver for NEEO
The custom driver DenonAVR, as delivered in this package will already be supplied as a driver in META's own Library.
It only requires activating through the Meta-driver for it to work. See the instructions on Metadriver how to activate the driver.  

If you want to install the custom driver through other ways, you;ll be experienced enough to figure out how to install DenonAVR.json, as delivered in this package.

B) Node-red configuration.
The custom driver DenonAVR sends all of its actions over MQTT (Mosquitto), where a Node-red flow needs to pick them up.
This functionality is included in the flow DenonAVR Flow.json, located in thia package at directory "node-red Flow".

You can import this file by copy&paste its content into a new node-red flow, but also by downloading the flow and importing it by selecting the downloaded file on node-red. 
Following instructions apply to installation of the flow on a pre-configured NEEO eco system on your NEEO-Brain.  
We'll use <ip-address Brain> as the IP-address of your brain (don't type the < and > sign) and we'll be using the copy&paste method to import the flow.

First, open the github repository where you've found this README.MD file (https://github.com/jac459/meta-denonAVR) and open the file Denon AVR Flow.json which will show you the content of the flow.
Important: in the line just above the actual content, you';ll see two icons named RAW and BLAME. Click on RAW...
Copy entire content of the raw-window go the clipboard node-red-contrib-denon

Open your browser and goto <ip-address Brain>:1880
This should open the node-red GUI.
In the top of the browser window, you'll see a black line with left the name Node-RED and the logo, while at the right, you'll have 3 horizontal bars. The 3 bars will show a submenu for Node-RED.
Click on the 3-bars/submenu. 
You'll now see the submenu, with the function "import". Click on import.
In the window you can now paste the content of your clipboard.
Important: do not import yet, first click at "import to" the "New flow" button so you do not overwrite any flow that is already opened in Node-RED.
Now click Import.

Some flows need additional packages (nodes) that deliver specific functionality and are developed by others than the Metadriver-team. 
For DenonAVR, we do need such an external node, called "node-red-contrib-denon". 
This extra node can be installed  through the Node-RED submenu we used to start the import of the flow, but this time choose function "Manage palette". 

A dialog name "User settings" will open with 3 tabs at the left. Click the tab "Palette". Thios part of the dialog shows two Tabs at the top: "Nodes" and "Install". 
The Nodes-tab shows all the nodes that are installed. You can see if there's already a line with the extra node we need ("node-red-contrib-denon"), but normally, it should not be there yet.
Now open the Tab-Install. You'll see the search field (magnifying glass with the text "search module"). Type "node-red-contrib-denon" (without quotes) in there.
Once done, you'll see the node with a button to install it. Click on install, confirm you indeed want to install it and wait for the process to complete successfully.
You now have installed the extra node required for your flow to work. If you check the Tab-Palette, you'll now see the extra node.

Configure the flow
As each network is different and IP-addresses vary, you need to tell Node-RED where to listen and talk to.
The Node-RED flow needs to be told where it will receive the buttons pressed (MQTT on META) and what IP-address you Denon AVR has.
In the flow DenonAVR, you'll see a box (it's in fact a 'node') at the left, called MQTT Brain which represents the product MQTT running on the NEEO-Brain and at the right, a box called Denon in which represents your AVR.
Double click on the node named NEEO which will open the properties of this "node". Mosty of it is already configured, but we need to change the IP-address. Click on the pencil, right to the field named Server.
Change the default IP-address and set it to <ip-address Brain> (without the < and >).
Click "Update" at the right of this dialog and click 'Done".

Now we'll change the IP-address of the node representing your Denon AVR by double clicking the box "Denon in". Change the IP-address in a similar way as done above, but now specifiy the IP-address of your Denon AVR.
Do the same for the other green box, labeled Denon-out

Last, we're going to "Deploy" this flow and the changes we made to it; Node-RED is already telling us that we have not-deployed changes by the bright red Icon labeled "Deploy: at the rioght, just besides the submenu icon (3 bars).
You always need to look at the Deploy-icon to know if the last changes are actually activated...

As soon as you click on Deploy, Node-RED will check flow and parameters and if they are found correct, it will activate the flow with changes. 

Now you are all set to control your Denon AVR through HTTP.... Apart from one function.... power-on.... As the TV shuts down its internal processor, it will not respond to commands send oer the network.
For this, we're still sending an InfraRed-command to  your TV to power on.
