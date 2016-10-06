### 0. Giới thiệu chung

GNS3 (Graphical Network Simulator-3) là một trình giả lập mạng, cho phép bạn thiết kế các mô hình mạng và chạy giả lập trên chúng với bản phân phối đầu tiên năm 2008.

GNS3 sử dụng phần cứng của máy tính để giả lập thiết bị, khác với Packet Tracer, GNS3 có thể phối hợp với các phần mềm máy ảo khác như VMware Workstation, VMware Player, Virtualbox... để thiết lập một hệ thống mạng hoàn chỉnh như trong thực tế.

GNS3 có các phiên bản chạy trên Windows, Linux và OSX. GNS3 sử dụng phần cứng trên máy tính (RAM, CPU...) để giả lập thiết bị. 

GNS3 được sử dụng bởi rất nhiều công ty lớn như Exxon, Walmart, AT&T và NASA, nó cũng phổ biến trong các bài test lấy chứng chỉ mạng chuyên nghiệp.

Nhà phát triển :  	Jeremy Grossman

Được viết bằng Python 

Website :  	(www.gns3.com](https://www.gns3.com)

Github : https://github.com/GNS3/gns3-server

Đạt 11 triệu lượt download năm 2015 

GNS3 sử dụng bộ mô phỏng Dynamips để giả lập Cisco IOS.
Để thiết bị router có thể hoạt động bạn phải cài đặt hệ điều hành của nó tên gọi IOS (Internetwork Operating System) trên GNS3.

Tải IOS tại : 

https://www.mediafire.com/folder/6l2vplfn9kjvz/GNS3

Mọi câu lệnh bạn sử dụng để cấu hình cho Router trong GNS3 đều được sử dụng như Router thật và dùng IOS thật nhưng Switch trong GNS3 là switch trong suốt bạn không thể thực thiện cấu hình Switch.


### 1. Cài đặt
Trên Windows: 

Sử dụng bản cài đặt cho Windows : GNS3-1.5.2-all-in-one.exe

GNS3 hỗ trợ cho cả Linux, Windows, Mac. Khuyến cáo sử dụng Linux vì tăng hiệu năng và tính ổn định của nó.

### 2. Thêm IOS images 

##### Giới thiệu về Dynamips
Dynamips là một trình mô phỏng Router Cisco sử dụng các IOS images chuẩn. 

Các dòng IOS images được khuyến cáo sử dụng là :  c3640, c3660, c3725, c3745, c7200 
Phần mềm mô phỏng loại này có thể được sử dụng cho :
- Như một công cụ để thực tập, với phần mềm sử dụng trong thế giới thực. Nó cho phép mọi người làm quen với các thiết bị của Cisco.
- Thử nghiệm và làm quen với các đặc tính của Cisco IOS 
- Kiểm tra nhanh chóng cấu hình để triển khai trên các router thật.

###### Demo add IOS image

###### Giả lập Switch trong GNS3 bằng IOU image

GNS3 hỗ trợ giả lập Router Cisco từ IOS images nhưng lại không hỗ trợ cho switch.

- Với những lab không liên quan nhiều đến switch, có thể sử dụng :

. Switch layer 2: Switch > Ethernet switch

. Switch layer 3: Add module NM-16ESW vào router, khi đó có thể cấu hình như switch layer 3

- GNS3 không hỗ trợ mô phỏng Switch từ IOS images nhưng cho phép giả lập từ Linux/UNIX IOU images.

. Step 0: Prepare Tools Required 

. Step 1: GNS3 IOU VM.ova setup 

. Step 2: Upload IOU Image to UNIX (GNS3 IOU VM)

. Step 3: GNS3 Server  Configuaration 

. Step 4: Connect  Cisco IOU tp GNS3
END

##### Hub

Hub là thiết bị cấu hình đơn giản nhất bởi vì bạn chỉ cần chọn số port cho mỗi thiết bị. Mặc định là 8 port.


### 3. Tạo 1 topo đơn giản 
##### Giới thiệu các thành phần của giao diện 
Gồm các khu vực chính :
- Thanh thiết bị 
- Topology : Liệt kê các thiết bị đang sử dụng và các kết nối của nó
- Server : Có 3 loại Local server, GNS3 VM server và Remote server 
- Vùng làm việc chính (Workspace)
- Console 

##### Idle-PC
Sử dụng mô phỏng Router có thể làm CPU của hệ thống hoạt động tới 100%. Lý do là Dynamips không biết khi nào router ảo đang rỗi, khi nào đang hoạt động.

Lệnh idle-pc sẽ phân tích images xác định chu kỳ nghỉ của IOS. Một khi được áp dụng, Dynamips chuyển router về chế độ sleep khi đến chu kỳ nghỉ, giúp giảm sự tiêu tốn CPU trên máy chủ mà không giảm khả năng xử lý công việc thực tế của router.
 
Khi right-click và chọn Idle-PC, các giá trị được đưa ra và kết quả tốt nhất được đánh dấu bằng (*). Chọn một trong các giá trị đó. Nếu thấy giảm sự tiêu tốn CPU một cách đáng kể thì bạn đã chọn được một giá trị Idle-PC tốt với IOS image này.

Nếu tỷ lệ sử dụng không giảm xuống thì bạn nên thử lại với một giá trị khác.

Giá trị Idle-PC là riêng với mỗi image. Chúng có thể khác nhau với các bản IOS khác nhau, thậm chí là các tính năng khác nhau của cùng một phiên bản IOS.

Tuy nhiên nó lại không phụ thuộc máy, hệ điều hành hay phiên bản Dynamips.

##### Tạo 1 topo mạng 
- Bật GNS3
- Kéo 3 router (c3725) ra Workspace 
- Thêm cho các Router : NM-4T card 
- Nối dây

##### Cấu hình 
- 3 đường mạng sẽ là 192.168.1.0/24, 192.168.2.0/24 and 192.168.3.0/24
- Sử dụng định tuyến RIP


### 4. GNS3 VM
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





