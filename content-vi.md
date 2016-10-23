<a name="top"></a>
### Mục lục 

- [0. Giới thiệu chung](#gioi_thieu)
- [1. Cài đặt](#cai_dat)
- [2. Các thành phần của giao diện ](#thanh_phan)
- [3. GNS3 VM](#gns3_vm)
- [4. Thêm IOS images](#IOS_images)
- [5. Mô phỏng Switch trong GNS3](#switch)
- [6. QEMU](#qemu)
- [7. VMware](#VMware)
- [8. Docker](#docker)
- [9. Tạo 1 topo đơn giản](#topo)

<a name="gioi_thieu"></a>
### 0. Giới thiệu chung

GNS3 (Graphical Network Simulator-3) là một trình giả lập mạng, cho phép bạn thiết kế các mô hình mạng và chạy giả lập trên chúng với bản phân phối đầu tiên năm 2008.

GNS3 sử dụng phần cứng của máy tính (RAM, CPU...) để giả lập thiết bị, khác với Packet Tracer, GNS3 có thể phối hợp với các phần mềm máy ảo khác như VMware Workstation, VMware Player, Virtualbox... để thiết lập một hệ thống mạng hoàn chỉnh như trong thực tế.

GNS3 có các phiên bản chạy trên Windows, Linux và OSX. 

GNS3 được sử dụng bởi rất nhiều công ty lớn như Exxon, Walmart, AT&T và NASA, nó cũng phổ biến trong các bài test lấy chứng chỉ mạng chuyên nghiệp.

Nhà phát triển :  	Jeremy Grossman

Được viết bằng Python 

Website :  	[www.gns3.com](https://www.gns3.com)

Github : https://github.com/GNS3/gns3-server

Đạt 11 triệu lượt download năm 2015 

<a name="cai_dat"></a>
### 1. Cài đặt

##### Linux, Windows, Mac OS

https://www.gns3.com/software/download

##### Ubuntu and all distributions based on it 

	sudo add-apt-repository ppa:gns3/ppa
	sudo apt-get update
	sudo apt-get install gns3-gui
	
##### Windows: 

Sử dụng bản cài đặt cho Windows : GNS3-1.5.2-all-in-one.exe

GNS3 hỗ trợ cho cả Linux, Windows, Mac. Khuyến cáo sử dụng Linux vì tăng hiệu năng và tính ổn định của nó.

<a name="thanh_phan"></a>
### 2. Các thành phần của giao diện 

<img src="http://i.imgur.com/AVnsGz4.png">

Gồm các khu vực chính :
- Thanh chức năng
- Thanh thiết bị 
- Topology : Liệt kê các thiết bị đang sử dụng và các kết nối của nó
- Server : Có 3 loại Local server, GNS3 VM server và Remote server 
- Vùng làm việc chính (Workspace)
- Console

<a name="gns3_vm"></a>
### 3. GNS3 VM
GNS3 VM là một máy ảo chạy trên nền Ubuntu được cài sẵn tất cả những thành phần đi kèm để thực hiện các bài lab với GNS3.

Lý do sử dụng GNS3 VM thay vì sử dụng trên Local
- Với người dùng Linux, một vài thành phần đi kèm khó để cài đặt, như là các yêu cầu cho IOU (cần xác định các thư viện và hỗ trợ 32-bits)
- Sử dụng VMware thì có thể sử dụng công nghệ KVM để tăng tốc để chạy trên Qemu với hiệu năng tốt trên Windows và Mac.
- Dynamips và Qemu xu hướng làm việc tốt hơn rất nhiều trên Linux.
- Hỗ trợ đầy đủ IOU.
- Phiên bản sau của VM sẽ bao gồm đầy đủ cho hỗ trợ Docker.
...

##### Cài đặt 

Có nhiều bản phân phối, nhưng khuyến cáo là dùng VMware Workstation

- VMware Workstation to be used with Workstation Pro/Player and Fusion (Recommended)
- VMware ESXi (For experts only)
- VirtualBox (No nested virtualization support)

Download : 

https://github.com/GNS3/gns3-gui/releases 

Mình dùng bản `GNS3.VM.VMware.Workstation.1.5.2.zip`

Sau khi tải GNS3 VM về, unzip ta được file `GNS3 VM.ova`

Chuột phải và `Open with VMWare Workstation`

<img src="http://i.imgur.com/B0Yls3A.png">

Quá trình cài đặt hoàn tất, ta được một máy ảo GNS3 VM như hình :

<img src="http://i.imgur.com/LInGczj.png"> 

<a name="IOS_images"></a>
### 4. Thêm IOS images 

##### Giới thiệu về Dynamips

Để thiết bị router có thể hoạt động bạn phải cài đặt hệ điều hành của nó tên gọi IOS (Internetwork Operating System) trên GNS3.

Dynamips là một trình mô phỏng Router Cisco sử dụng các IOS images chuẩn. 

Tải IOS tại : 

https://drive.google.com/file/d/0ByQrVPPzqnowNWpHT2otbXMzZzA/view?usp=sharing

or

https://mega.nz/#F!nJR3BTjJ!N5wZsncqDkdKyFQLELU1wQ

or

https://www.mediafire.com/folder/6l2vplfn9kjvz/GNS3

Mọi câu lệnh bạn sử dụng để cấu hình cho Router trong GNS3 đều được sử dụng như Router thật và dùng IOS thật nhưng Switch trong GNS3 là switch trong suốt bạn không thể thực thiện cấu hình Switch.

Các dòng IOS images được khuyến cáo sử dụng là :  c3640, c3660, c3725, c3745, c7200 

Phần mềm mô phỏng loại này có thể được sử dụng cho :
- Như một công cụ để thực tập, với phần mềm sử dụng trong thế giới thực. Nó cho phép mọi người làm quen với các thiết bị của Cisco.
- Thử nghiệm và làm quen với các đặc tính của Cisco IOS 
- Kiểm tra nhanh chóng cấu hình để triển khai trên các router thật.

#####Thực hiện add IOS image 

<img src="http://i.imgur.com/vwtWRJE.png">

Sau đó import IOS images đã tải ở hộp thoại kế tiếp .

<a name="switch"></a>
### 5. Mô phỏng Switch trong GNS3

GNS3 hỗ trợ giả lập Router Cisco từ IOS images nhưng lại không hỗ trợ cho switch.

#### Với những bài Lab cấu hình không liên quan nhiều tới Switch thì có thể sử dụng :
+ Switch layer 2 : Ethernet switching devices 

<img src="http://i.imgur.com/Av9aAft.png">

Ethernet switch hỗ trợ công nghệ VLAN với chuẩn 802.1q trunking. Bạn có thể thiết lập đường trunk bằng cách chọn "dot1q" trong configuration Ethernet switch. 

Mặc định Ethernet switch có 8 ports trong VLAN 1 và ở chế độ access. Tuy nhiên trên lý thuyết bạn có thể có tới 10,000 ports và 10,000 VLANs.

+ Switch layer 3 : thêm module NM-16ESW vào router, lúc đó có thể cấu hình như Switch layer 3

<img src="http://i.imgur.com/m32k1o7.png">

Để xem các interface : # show ip int brief

Nếu bạn muốn tắt chức năng routing : (config)# no ip routing (switch layer 2)

Để xem VLAN : #show vlan-switch

#### Sử dụng IOU images giả lập Switch

##### Tạo IOU licence
Chạy file [CiscoKeyGen.py](https://github.com/locvx1234/GNS3-intro/blob/master/CiscoKeyGen.py) trên server đang dùng và lưu 2 dòng kết quả vào 1 file text mà import vào gns3 

Ví dụ một file `IOURC.txt` với nội dung như sau :

	[license]
	gns3vm = 73635fd3b0a13ad0;

<img src="http://i.imgur.com/lK7D6eY.png">

##### Tạo switch L2, L3

Sử dụng IOU images cho L2 và L3 để tạo các switch tương ứng. Cách thực hiện tương tự như tạo router bằng IOS images.

<img src="http://i.imgur.com/uBuqRhf.png">

Link Switch L2, L3

https://drive.google.com/file/d/0ByQrVPPzqnowRl9meGJYbEtfQ2s/view?usp=sharing

Switch sau khi đã tạo xong 

<img src="http://i.imgur.com/a3BW5XA.png">

<img src="http://i.imgur.com/A7vpkHS.png">

- Hub

<img src="http://i.imgur.com/miMDKA8.png">

Hub là thiết bị cấu hình đơn giản nhất bởi vì bạn chỉ cần chọn số port cho mỗi thiết bị. Mặc định là 8 port.

<a name="qemu"></a>
### 6. QEMU (Quick Emulator)

QEMU là một trình ảo hóa để chạy các máy ảo Linux tương tự như VMWare, Virtual PC, Bochs. Qemu có thể chạy tốt trên Linux và Windows. 

Qemu thuần bằng dòng lệnh, nhỏ nhẹ. Qemu hỗ trợ nhiều loại máy ảo (ARM, PowerPC, x86, Sparc, MIPS).

##### Tạo host ASAv

ASA nó là thiết bị bảo mật có nhiều chức năng, ví dụ: chức năng Firewal, IPS, VPN, ngoài ra nó còn có một số tính năng của router.

Tương tự tạo thêm IOS images

<img src="http://i.imgur.com/kIuFFHk.png">

Check vào ô `This is a legacy ASA VM`

<img src="http://i.imgur.com/o4O722k.png">

Link ASA

https://drive.google.com/file/d/0ByQrVPPzqnowQ3p2ZWxtMEZ1aFk/view?usp=sharing

<a name="VMware"></a>
### 7. VMware 
##### Tạo host XP, CenOS đã cài trên VMWare Workstation

<img src="http://i.imgur.com/5i3AkEi.png">

Chọn một VM đã cài trên VMWare Workstation

<img src="http://i.imgur.com/JZgH1Jh.png">

<a name="docker"></a>
### 8. Docker

Docker - đây là một công cụ tạo môi trường được "đóng gói" (còn gọi là Container) trên máy tính mà không làm tác động tới môi trường hiện tại của máy, môi trường trong Docker sẽ chạy độc lập.

Một số developer thường tạo sẵn các môi trường này, và upload lên mạng để mọi người lấy về dùng, và mấy cái này gọi là các Images.


##### Tạo host Alpine  - một distro gọn nhẹ của Linux 

<img src="http://i.imgur.com/SZXGVAq.png">

	Image name : alpine:3.2 
	Start command : sh 
	Environment : HELLO=WORLD

<a name="topo"></a>
### 9. Tạo 1 topo đơn giản

##### Idle-PC
Sử dụng mô phỏng Router có thể làm CPU của hệ thống hoạt động tới 100%. Lý do là Dynamips không biết khi nào router ảo đang rỗi, khi nào đang hoạt động.

Lệnh idle-pc sẽ phân tích images xác định chu kỳ nghỉ của IOS. Một khi được áp dụng, Dynamips chuyển router về chế độ sleep khi đến chu kỳ nghỉ, giúp giảm sự tiêu tốn CPU trên máy chủ mà không giảm khả năng xử lý công việc thực tế của router.
 
Khi right-click và chọn Idle-PC, các giá trị được đưa ra và kết quả tốt nhất được đánh dấu bằng (*). Chọn một trong các giá trị đó. Nếu thấy giảm sự tiêu tốn CPU một cách đáng kể thì bạn đã chọn được một giá trị Idle-PC tốt với IOS image này.

Nếu tỷ lệ sử dụng không giảm xuống thì bạn nên thử lại với một giá trị khác.

Giá trị Idle-PC là riêng với mỗi image. Chúng có thể khác nhau với các bản IOS khác nhau, thậm chí là các tính năng khác nhau của cùng một phiên bản IOS.

Tuy nhiên nó lại không phụ thuộc máy, hệ điều hành hay phiên bản Dynamips.

Cách thực hiện : 

Chuột phải vào `Router` (running) chọn `IDLE PC` và chọn giá trị thích hợp.

##### Tạo 1 topo mạng 
- Bật GNS3
- Kéo 3 router (c3725) ra Workspace 
- Thêm cho các Router : NM-4T card 
- Nối dây

<img src="http://i.imgur.com/nrlOihr.png">

##### Cấu hình 
- 3 đường mạng sẽ là 192.168.1.0/24, 192.168.2.0/24 and 192.168.3.0/24
- Sử dụng định tuyến RIP

Router 1:

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


Router 2:

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

Router 3:

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


##### Capture gói tin 

Chuột phải vào `Router` (running) chọn `IDLE PC` và chọn port cần bắt. Chương trình sẽ khởi động `Wireshark` để bắt gói tin. 





* Bài viết còn nhiều thiếu sót, mong bạn đọc góp ý thêm *



