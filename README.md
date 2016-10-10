# GNS3-intro
Graphical Network Simulator-3

### 0. General introduction


<img src="https://secure.gravatar.com/avatar/4176b714c203e7967af31c857e95ee06.jpg?s=512&r=g&d=mm">


- First released 	in 2008
- Developer(s) 		Jeremy Grossman
- Written in 		Python
- License 			GNU GPL
- Website 			[www.gns3.com](https://www.gns3.com/)
- Repository 		[github.com/GNS3/gns3-server](https://github.com/GNS3/gns3-server)


### 1. Install 
##### Linux, Windows, Mac OS

https://www.gns3.com/software/download

##### Ubuntu and all distributions based on it 

	sudo add-apt-repository ppa:gns3/ppa
	sudo apt-get update
	sudo apt-get install gns3-gui

### 2. Display 

- Tools bar
- Devices bar
- Topology Summary
- Servers Summary
- Workspace
- Console

### 3. GNS3 VM

What is the GNS3 VM?

Why use the GNS3 VM?

Installation

The VM is distributed in three different flavors:

-    VMware Workstation to be used with Workstation Pro/Player and Fusion (Recommended)
-    VMware ESXi (For experts only)
-    VirtualBox (No nested virtualization support)
	
Download : 

https://github.com/GNS3/gns3-gui/releases 

### 4. Dynamips
- Dynamips

- IOS images

**Recommend** using c3640, c3660, c3725, c3745 and c7200 IOS images 

Download IOS images: 

https://drive.google.com/file/d/0ByQrVPPzqnowNWpHT2otbXMzZzA/view?usp=sharing

or

https://mega.nz/#F!nJR3BTjJ!N5wZsncqDkdKyFQLELU1wQ

or

https://www.mediafire.com/folder/6l2vplfn9kjvz/GNS3

- Add IOS image

### 5. Switching Simulation in GNS3 

##### Switch layer 2 : Use Ethernet switching devices 
##### Switch layer 3 : Routers that change into Switches: Add module NM-16ESW to Router 

	# show ip int brief
	(config)# no ip routing (switch layer 2)
	#show vlan-switch
	
#####  Use IOU images to emulate Switch 

+ Cisco IOU License Generator

+ Generate Switch Layer 2 and Switch Layer 3


##### Hub 

### 6. QEMU (Quick Emulator)

<img src="http://wiki.qemu.org/images/0/0c/Qemu-logo.png">

### 7. VMware 

<img src="http://siliconangle.com/files/2011/01/Picture-93.png">

### 8. Docker

<img src="https://d2mw6vgfxwlz2a.cloudfront.net/2016/Feb/docker_logo-1455828502290.png">

- Use: Alpine
- Image name : alpine:3.2 
- Start command : sh 
- Environment : HELLO=WORLD

### 9. Creating a simple topology 

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

3. Ping

4. Capture 

Router 1 Example:

	R1>en
	R1#conf t
	R1(config)#int f0/0
	R1(config-if)#ip add 192.168.1.1 255.255.255.0
	R1(config-if)#no sh
	R1(config-if)#int f0/1
	R1(config-if)#ip add 192.168.3.1 255.255.255.0
	R1(config-if)#no shut
	R1(config-if)#exit
	R1(config)#router rip
	R1(config-router)no auto-summary
	R1(config-router)version 2
	R1(config-router)network 192.168.1.0
	R1(config-router)network 192.168.3.0
	R1(config-router)exit
	R1(config)#exit


Router 2 Example:

	R2>en
	R2#conf t
	R2(config)#int f0/0
	R2(config-if)#ip add 192.168.1.2 255.255.255.0
	R2(config-if)#no sh
	R2(config-if)#int f1/0
	R2(config-if)#ip add 192.168.2.2 255.255.255.0
	R2(config-if)#no sh
	R2(config-if)#exit
	R2(config)#router rip
	R2(config-router)no auto-summary
	R2(config-router)version 2
	R2(config-router)#net 192.168.1.0
	R2(config-router)#net 192.168.2.0
	R2(config-router)#exit
	R2(config t)exit



Router 3 Example:

	R3>en
	R3#conf t
	R3(config)#int f0/1
	R3(config-if)#ip add 192.168.3.2 255.255.255.0
	R3(config-if)#no sh
	R3(config-if)#int f1/0
	R3(config-if)#ip add 192.168.2.1 255.255.255.0
	R3(config-if)#no sh
	R3(config-if)#exit
	R3(config)#router rip
	R2(config-router)no auto-summary
	R2(config-router)version 2
	R3(config-router)#net 192.168.2.0
	R3(config-router)#net 192.168.3.0
	R3(config-router)#exit
	R3(config t)exit



Basic Router Configuration Commands:
https://www.dropbox.com/s/ob1achpz4rgt8ai/BasicRouterConfiguration.pdf?dl=0



*Reference:* 

https://www.gns3.com/support/docs

https://www.gns3.com/software/faq


What is the difference between GNS3 and Packet Tracer / VIRL?
Packet Tracer and VIRL are Cisco's offerings and answers to the advancement of GNS3's advanced EMULATION. 
There are strengths and weaknesses to each product, but GNS3 is first in Emulating real production networks. For more information attached are some recent articles written on the comparison:

- Cisco VIRL vs. GNS3 - How They Compare - GlobalConfig.net

- (Un)Biased review of someone who used VIRL


