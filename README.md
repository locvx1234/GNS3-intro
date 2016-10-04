# GNS3-intro

### 1. Install 
##### Linux, Windows ,Mac OS

https://www.gns3.com/software/download

##### Ubuntu and all distributions based on it 

	sudo add-apt-repository ppa:gns3/ppa
	sudo apt-get update
	sudo apt-get install gns3-gui

### 2. Add IOS images

**Recommend** using c3640, c3660, c3725, c3745 and c7200 IOS images 

Download IOS images: 

https://drive.google.com/file/d/0ByQrVPPzqnowNWpHT2otbXMzZzA/view?usp=sharing

### 3. Creating a simple topology 
#####  Introduction
- Devices Toolbar

- The Workspace

- Topology Summary

- Servers Summary 

##### Configuring a router

##### Idle-PC

##### Creating a simple connection

- Step I: Start GNS3

- Step II: Drag three routers (here we are using Router c3725) running an IOS you have configured into the workspace.

- Step III: Select the 3 routers, right-click and choose Configure.

- Step IV: Choose a NM-4T serial adapter for slot1. This should have configured a NM-4T network module in slot1 for all the routers.

- Step V: Now we’re ready to connect the routers together. Click the Add a link button on the toolbar.

##### Configuring the routers

1. Assign interfaces within the 192.168.1.0/24, 192.168.2.0/24 and 192.168.3.0/24 network.

2. Enable RIP.

Basic Router Configuration Commands:
https://www.dropbox.com/s/ob1achpz4rgt8ai/BasicRouterConfiguration.pdf?dl=0



*Reference: [gns3.com](https://www.gns3.com/support/docs) *





