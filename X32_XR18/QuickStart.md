# Quick Start Guide

## Image the Raspberry Pi

[Follow the instructions here](https://www.raspberrypi.com/software/) to image a microSD card for a Raspberry Pi. This guide is based on imager 1.9.6 which is the latest as of this writing. For this project we don't need the desktop GUI so select "Raspberry Pi OS (other) and then select "Raspberry Pi OS Lite (64-bit).

### Enable 'ssh' for remote access

While still in the imager, when prompted to apply OS Customization Settings, click on Edit Settings. Set the hostname and username and password to something you'll remember. Navigate to the "Services" tab and tick the checkbox to "Enable SSH." and select "allow password authentication".  Click "Save" and "Yes" to apply customizations and "Yes" again to start imaging.

## Install Node.js and Node-RED

Use the bash shell script [found here](https://nodered.org/docs/getting-started/raspberrypi) to install Node.js and Node-RED.

Also follow the instructions at the same location to AutoStart Node-RED on boot.

## Install Node-RED Modules

Once Node-RED is running, use "Manage Pallete" to install the following modules:

- [node-red-contrib-osc](https://flows.nodered.org/node/node-red-contrib-osc)
- [node-red-contrib-slip](https://flows.nodered.org/node/node-red-contrib-slip)
- [node-red-contrib-simple-gate](https://flows.nodered.org/node/node-red-contrib-simple-gate)

## Import Node-RED Flows

From the 3-bars menu in the upper-right of Node-RED, select "Import". Click on  
"select a file to import" and select the flows.json file from this repo. The "Import to" option doesn't matter since this file contains entire flows, not just nodes.

## Configuring the nodes to match your setup

### Connections - Loopy Pro TCP In and Out Nodes

Change the IP address of the TCP In and Out nodes to match the IP address of the iPad running Loopy Pro.

### Connections - X32 UDP Out Node

Change the IP address in the UDP Out node to match the IP address of the mixer.

Change the "send to" port in the UDP Out node to be either 10023 for the X32 or 10024 for the XR18.

### Message Handlers - Filter Nodes

No changes unless more than mixbus sends are needed. Open an issue if you need help adding more OSC messages to the filter nodes.

### Message Handlers - /sync Parameter List Node

Modify the 'parms' array to add or change the OSC parameters that need to sync to Loop Pro.
