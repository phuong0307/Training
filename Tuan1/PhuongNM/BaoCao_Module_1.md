# Mô hình OSI 

Mô hình OSI (Open Systems Interconnection Reference Model) là một thiết kế dựa vào nguyên lý tầng cấp, lý giải một cách trừu tượng kỹ thuật kết nối truyền thông giữa các máy vi tính và thiết kế giao thức mạng giữa chúng.

Mô hình OSI được chia thành 7 tầng.

![](http://www.9tut.com/images/ccna_self_study/OSI/OSI_Model.jpg)

### Tầng 1: Tầng Vật lý (Physical Layer)
Tầng này ám chỉ đến phần cứng (hardware) của mạng truyền thông, đến hệ thống dây nối cụ thể, hoặc đến sự liên kết viễn thông điện từ. 
Tầng này còn xử lý thiết kế điện, khống chế xung đột (collision control), và những chức năng ở hạ tầng thấp nhất.

Tầng vật lý là hạ tầng cơ sở của mạng truyền thông, cung cấp phương tiện truyền tín hiệu thô sơ ở dạng bit. Hình dáng của các nút cắm điện (electrical connector), tần số để phát sóng là bao nhiêu, và những cái thuộc hạ tầng tương tự, được xác định ở đây. 

Một ví dụ tương tự của tầng này là ví dụ về hạ tầng của một mạng lưới bưu phẩm, bao gồm việc xác định những thứ như giấy thư và mực chẳng hạn.



### Tầng 2: Tầng Liên kết dữ liệu (Data-Link Layer)

Tầng này định dạng các thông điệp vào một *khung dữ liệu (Frame)*, và thêm vào đó một header chứa các địa chỉ phần cứng nơi nhận và địa chỉ nguồn của nó. Tiêu đề này chịu trách nhiệm cho việc tìm kiếm các thiết bị đích tiếp theo trên một mạng nội bộ.

Tầng Mạng chịu trách nhiệm phân phát các gói dữ liệu từ đầu này sang đầu kia (end-to-end, từ nguồn đến đích), trong khi tầng Liên kết dữ liệu lại chịu trách nhiệm phân phát gói dữ liệu từ nút này sang nút khác (hop-to-hop, giữa hai nút mạng trung gian có đường liên kết (link) trực tiếp).

Tầng Liên kết dữ liệu chính là nơi các *thiết bị chuyển mạch (switches)* hoạt động. Kết nối chỉ được cung cấp giữa các nút mạng được nối với nhau trong nội bộ mạng.

Tầng này được chia thành 2 tầng con:

- Logical Link Control - LLC: điều khiển liên kết logic

- Media Access Control - MAC: điều khiển truy nhập môi trường

### Tầng 3: Tầng Mạng (Network Layer)
Tầng Mạng xử lý việc truyền thông dữ liệu trên cả đoạn đường từ nguồn đến đích, và đồng thời truyền bất cứ tin tức gì, từ bất cứ nguồn nào tới bất cứ đích nào mà chúng ta cần. 

Nếu ở tầng Mạng mà chúng ta không liên lạc được với một địa điểm nào đấy, thì chúng ta chẳng còn cách nào để có thể liên lạc được với nó.

### Tầng 4: Tầng Giao vận (Transport Layer)
Tầng Giao vận cung cấp dịch vụ chuyên dụng chuyển dữ liệu giữa các người dùng tại đầu cuối, nhờ đó các tầng trên không phải quan tâm đến việc cung cấp dịch vụ truyền dữ liệu đáng tin cậy và hiệu quả. 

Một ví dụ điển hình của giao thức tầng 4 là TCP.

Tầng Giao vận kiểm soát độ tin cậy của một kết nối được cho trước.

Tầng này chịu trách nhiệm sửa lỗi (error recovery), điều khiển lưu lượng dữ liệu, đảm bảo dữ liệu được chuyển tải một cách trọn vẹn.

### Tầng 5: Tầng phiên (Session Layer)
Tầng này có nhiệm vụ thiết lập, duy trì và kết thúc giao tiếp với các thiết bị nhận.

Tầng này đáp ứng các yêu cầu dịch vụ của tầng trình diễn và gửi các yêu cầu dịch vụ tới tầng giao vận.

Tầng phiên cung cấp một cơ chế để quản lý hội thoại giữa các tiến trình ứng dụng của người dùng cuối. 

Thông thường, tầng phiên hoàn toàn không được sử dụng, song có một vài chỗ nó có tác dụng. Ý tưởng là cho phép thông tin trên các dòng (stream) khác nhau, có thể xuất phát từ các nguồn khác nhau, được hội nhập một cách đúng đắn. Cụ thể, tầng này giải quyết những vấn đề về đồng bộ hóa, đảm bảo rằng không ai thấy các phiên bản không nhất quán của dữ liệu, hoặc những tình trạng tương tự.

### Tầng 6: Tầng Trình diễn (Presentation Layer)
Tầng này đảm bảo việc trình bày dữ liệu, mà các thông tin liên lạc qua lớp này nằm trong các hình thức thích hợp đối với người nhận.

Nói chung, nó hoạt động như một dịch giả của mạng.

Ví dụ, bạn muốn gửi một email và tầng trình diễn sẽ định dạng dữ liệu của bạn sang định dạng email.

Tầng Trình diễn chịu trách nhiệm phân phát và định dạng dữ liệu cho tầng Ứng dụng, để dữ liệu được tiếp tục xử lý hoặc hiển thị. Tầng này giải phóng tầng ứng dụng khỏi gánh nặng của việc giải quyết các khác biệt về cú pháp trong biểu diễn dữ liệu. 

Sự khác biệt này tồn tại là do việc trao đổi thông tin giữa các kiểu máy tính khác nhau.

Ví dụ, một trong những dịch vụ của tầng trình diễn là dịch vụ chuyển đổi tệp văn bản từ mã EBCDIC sang mã ASCII.

### Tầng 7: Tầng Ứng dụng (Application Layer)
Đây là tầng gần gũi với người dùng cuối nhất.

Nó cung cấp phương tiện cho người dùng truy nhập các thông tin và dữ liệu trên mạng thông qua chương trình ứng dụng. 

Tầng này là giao diện chính để người dùng tương tác với chương trình ứng dụng, và qua đó với mạng. 

Một số ví dụ về các ứng dụng trong tầng này bao gồm Telnet, Giao thức truyền tập tin FTP và Giao thức truyền thư điện tử SMTP, HTTP.

Tầng này giao tiếp trực tiếp với các tiến trình ứng dụng và thi hành những dịch vụ thông thường của các tiến trình đó, nó còn gửi các yêu cầu dịch vụ tới tầng trình diễn.

## Các giao thức sử dụng
Tầng | Giao thức
------------ | -------------
Vật lý | USB, Ethernet,...
Liên kết dữ liệu | PPP, ATM, Ethernet,...
Mạng | IP, ARP, ICMP...
Giao vận | TCP, UDP,...
Phiên | PPTP, NetBIOS,...
Trình diễn | TLS, SSL,...
Ứng dụng | HTTP, FTP, SNMP, DNS, Telnet,...

# Bộ giao thức TCP/IP
TCP/IP *(Transmission Control Protocol / Internet Protocol)* là một tập hợp các giao thức (protocol) điều khiển truyền thông giữa tất cả các máy tính trên Internet. 

Cụ thể hơn, TCP/IP chỉ rõ cách thức đóng gói thông tin (hay còn gọi là gói tin ), được gửi và nhận bởi các máy tính có kết nối với nhau. Nó được phát triển vào năm 1978 bởi Bob Kahn và Vint Cerf.

TCP/IP là sự kết hợp của hai giao thức riêng biệt: Giao thức kiểm soát truyền tin (TCP) và Giao thức Internet (IP). 

IP cho phép các gói được gửi qua mạng, nó cho biết các gói tin được gửi đi đâu và làm thế nào để đến đó.


TCP có trách nhiệm đảm bảo việc truyền dữ liệu đáng tin cậy qua các mạng kết nối Internet. TCP kiểm tra các gói dữ liệu xem có lỗi không và gửi yêu cầu truyền lại nếu có lỗi được tìm thấy.

![](http://www.omnisecu.com/images/tcpip/comparison-tcpip-osi.jpg)

Bộ giao thức TCP/IP được chia thành 4 tầng:

* Tầng 1: Tầng Tầng truy cập mạng (Network access Layer)
* Tầng 2: Tầng Mạng (Internet Layer)
* Tầng 3: Tầng Giao vận (Transport Layer)
* Tầng 4: Tầng Ứng dụng (Application Layer)

### Tầng 1: Tầng Truy nhập mạng (Network access Layer)
Tầng Truy nhập mạng bao gồm các giao thức mà nó cung cấp khả năng truy nhập đến một kết nối mạng. 

Tại tầng này, hệ thống giao tiếp với rất nhiều kiểu mạng khác nhau. Nó cung cấp các trình điều khiển để tương tác với các thiết bị phần cứng ví dụ như Token Ring, Ethernet, FDDI… 

### Tầng 2: Tầng Internet (Internet Layer)
Mục đích của tầng Internet là chọn lấy một đường dẫn tốt nhất xuyên qua mạng cho các gói di chuyển tới đích. Giao thức chính hoạt động tại tầng này là Internet Protocol (IP). Sự xác định đường dẫn tốt nhất và chuyển mạch gói diễn ra tại đây.

Giao thức IP là giao thức truyền thông không tin cậy, vì nó không cung cấp chức năng theo dõi và kiểm tra lỗi gói tin mà chỉ cố chuyển gói tin đến đích.

### Tầng 3: Tầng Giao vận (Transport Layer)
Tầng Giao vận có thể được xem như một cơ chế vận chuyển thông thường, nghĩa là trách nhiệm của một phương tiện vận tải là đảm bảo rằng hàng hóa/hành khách của nó đến đích an toàn và đầy đủ.

Tầng Giao vận cung cấp dịch vụ kết nối các ứng dụng với nhau thông qua việc sử dụng các cổng TCP và UDP. Do IP chỉ cung cấp dịch vụ phát chuyển nỗ lực tối đa (best effort delivery), tầng giao vận là tầng đâu tiên giải quyết vấn đề độ tin cậy.

### Tầng 4: Tầng Ứng dụng (Application Layer)
Tầng này bao gồm các giao thức phục vụ cho việc chia sẻ tài nguyên và điều khiển từ xa (remote access).

Nó bao gồm các giao thức cấp cao được sử dụng để cung cấp các giao diện với người sử dụng hoặc các ứng dụng. 

|Tầng|Giao thức   
|---|---|
|Truy nhập mạng|Ethernet, Token Ring,...
|Internet|IP,ICM, ARP, RARP
|Giao vận|TCP, UDP
|Ứng dụng|HTTP, FTP, SMTP, DNS, RIP, SMNP

# Cấu trúc gói tin TCP
Gói tin TCP gồm 2 phần:

* header
* data

## Header
![](https://i.imgur.com/EbHlstL.png)

Header gồm 11 trường, trong đó có 10 trường đầu là bắt buộc.

* **Source port**: số hiệu của cổng máy tính gửi
* **Destination port**: số hiệu của cổng máy tính nhận
* **Sequence number**: có 2 nhiệm vụ. Nếu cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tiên được gửi có số thứ tự này cộng thêm 1. Nếu không có cờ SYN thì đây là số thứ tự của byte đầu tiên.
* **Acknowledgement number**: Nếu cờ ACK bật thì giá trị của trường chính là số thứ tự gói tin tiếp theo mà bên nhận cần.
* **Data offset**: Trường có độ dài 4 bít quy định độ dài của phần header (tính theo đơn vị từ 32 bít). Phần header có độ dài tối thiểu là 5 từ (160 bit) và tối đa là 15 từ (480 bít).
* **Reserved**: dành cho tương lai và có giá trị là 0.
* **Flags** (hay Control bits): bid điều khiển
* **Checksum**:
16 bít kiểm tra cho cả phần header và dữ liệu. 
Phương pháp sử dụng được mô tả trong RFC 793: 16 bít của trường kiểm tra là bổ sung của tổng tất cả các từ 16 bít trong gói tin. Trong trường hợp số octet (khối 8 bít) của header và dữ liệu là lẻ thì octet cuối được bổ sung với các bít 0. Các bít này không được truyền. Khi tính tổng, giá trị của trường kiểm tra được thay thế bằng 0.
* **Urgent pointer**: Nếu cờ URG bật thì giá trị trường này chính là số từ 16 bít mà số thứ tự gói tin (sequence number) cần dịch trái.
* **Options**: Đây là trường tùy chọn. Nếu có thì độ dài là bội số của 32 bít.

## Data
Giá trị của trường này là thông tin dành cho các tầng trên (trong mô hình 7 lớp OSI). Thông tin về giao thức của tầng trên không được chỉ rõ trong phần header mà phụ thuộc vào cổng được chọn.

# Cấu trúc gói tin UDP

## Header
![](https://i.imgur.com/TsdSIAT.png)
Chứa thông tin về địa chỉ cổng nguồn, cổng đích, độ dài của gói và checksum.

Header của gói tin UDP chỉ chứa 4 trường dữ liệu, trong đó có 2 trường là tùy chọn (source port và checksum)

* Source port: xác định cổng của người gửi thông tin và có ý nghĩa nếu muốn nhận thông tin phản hồi từ người nhận. Nếu không dùng đến thì đặt nó bằng 0.
* Destination port: xác định cổng nhận thông tin.
* Length: xác định chiều dài của toàn bộ gói tin
* Checksum: kiểm tra lỗi của phần header và dữ liệu. 

# Cấu trúc gói tin ICMP
Gói tin ICMP gồm 2 phần:

* header
* data

## Header
![](https://i.imgur.com/pQ8xTrQ.png)

32 bit đầu tiên (4 byte đầu) của một gói tin ICMP là giống nhau cho mỗi loại thông điệp, nội dung các byte 
còn lại sẽ lệ thuộc vào trường type và trường code:

* Type (8 bit): là một số nguyên 8bit để xác định thông điệp. 
* Code (8 bit):cung cấp thêm thông tin về kiểu thông điệp. 
* Checksum (16 bit): ICMP sử dụng thuật checksum như IP, nhưng ICMP checksum chỉ tính đến thông điệp ICMP.

## Data
Thông thường, data là header của gói tin IP và là 64 bit đầu tiên của nó.

# Cấu trúc gói tin IP
Gói tin IP được chia thành 2 phần:


* header
* data

## Header
![](https://i.imgur.com/vSal7oW.png)

* Vesion : xác định phiên bản của IP được sử dụng để tạo ra gói tin. Mục đích của nó nhằm đảm bảo khả năng tương thích giữa các thiết bị có thể chạy trên các phiên bản khác nhau của IP.
* IHL (Internet Header Length): xác định độ dài phần header 
* Type Of Service: mang thông tin để cung cấp chất lượng của các dịch vụ (QoS)
* Total Length : tổng chiều dài của gói tin IP
* Identification : định danh gói tin gốc trước khi nó bị phân mảnh
* Flags : kiểm soát xem một gói tin bị phân mảnh (có 3 bit)
  * Bit 0: không dùng
  * Bit 1: cho biết gói có phân mảnh hay không
  * Bit 2: Nếu gói tin IP bị phân mảnh thì cho biết mảnh này có phải là mảnh cuối không
* Fragment Offset: khi xảy ra phân mảnh, nó sẽ xác định bù đắp phần còn lại của các mảnh
* Time To Live : Chỉ định thời gian tồn tại của gói tin trên mạng
* Padding: bổ sung thêm các số 0 để đảm bảo header luôn là bội số của 32 bit
* Protocol: xác định các giao thức được sử dụng trong phần data của gói tin IP
* Header Checksum : được dùng để kiểm tra lỗi của header
* Source IP Address: địa chỉ nguồn
* Destination IP Address: địa chỉ đích

## Data
Nội dung của nó được xác định dựa trên Protocol ở header. 