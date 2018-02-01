# 1. Mô hình OSI 

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

- Logical Link Control - LLC (điều khiển liên kết logic): dùng để liên kết dữ liệu với tầng trên chỉ ra giao thức hoạt động ở tầng mạng (IP, IPX, Apple talk) đã đòng gói ra packet trong phần data của Frame.

- Media Access Control - MAC (điều khiển truy nhập môi trường): tham gia trực tiếp việc đóng gói Packet thành Frame thêm vào địa chỉ Mac nguồn và Mac đích trong Frame, thêm vào các nhóm bít bắt đầu và mã kết thúc của một Frame và điều khiển Frame truy cập đường truyền.

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

# 2. Bộ giao thức TCP/IP
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

# 2.1. Cấu trúc gói tin TCP

Các kết nối TCP có ba pha:

1. Thiết lập kết nối
2. Truyền dữ liệu
3. Kết thúc kết nối

### Thiết lập kết nối
TCP sử dụng một quy trình bắt tay 3 bước (3-way handshake).

Trước khi client thử kết nối với một server, server phải đăng ký một cổng và mở cổng đó cho các kết nối: đây được gọi là mở bị động.  

Một khi mở bị động đã được thiết lập thì một client có thể bắt đầu mở chủ động. Để thiết lập một kết nối, quy trình bắt tay 3 bước xảy ra như sau:

1. Client yêu cầu mở cổng dịch vụ bằng cách gửi gói tin SYN (gói tin TCP) tới server, trong gói tin này, tham số sequence number được gán cho một giá trị ngẫu nhiên X.

2. Server hồi đáp bằng cách gửi lại phía client bản tin SYN-ACK, trong gói tin này, tham số acknowledgment number được gán giá trị bằng X + 1, tham số sequence number được gán ngẫu nhiên một giá trị Y

3. Để hoàn tất quá trình bắt tay ba bước, client tiếp tục gửi tới server bản tin ACK, trong bản tin này, tham số sequence number được gán cho giá trị bằng X + 1 còn tham số acknowledgment number được gán giá trị bằng Y + 1

![](https://sites.google.com/a/javainterview.net/question/_/rsrc/1425457816649/misc/tcp-ip/3-way-handshake-Intro-to-transport-layer-The-internetworking-Part2.gif)

Quy trình này có thể bị lợi dụng để thực hiện tấn công SYN attack. Hacker sẽ gửi đến hệ thống đích một loạt SYN packets với địa chỉ IP nguồn ảo. Hệ thống đích khi nhận được các bad SYN packets này sẽ gởi trở lại SYN/ACK packet đến các địa chỉ không có thực này vào chờ nhận được ACK messages từ các địa chỉ IP đó. Vì đây là các địa chỉ IP không có thực, hệ thống đích sẽ chờ đợi vô ích và còn nối đuôi các “request” chờ đợi này nào hàng đợi, gây lãng phí một lượng đáng kể bộ nhớ trên máy chủ mà đúng ra là phải dùng vào việc khác thay cho phải chờ đợi ACK messages.

### Truyền dữ liệu
Trên lý thuyết, mỗi byte gửi đi đều có một số thứ tự và khi nhận được thì máy tính nhận gửi lại tin báo nhận (ACK). 

Trong thực tế thì chỉ có byte dữ liệu đầu tiên được gán số thứ tự trong trường số thứ tự của gói tin và bên nhận sẽ gửi tin báo nhận bằng cách gửi số thứ tự của byte đang chờ.

VD. Máy tính A gửi 4 byte với số thứ tự ban đầu là 100 (theo lý thuyết thì 4 byte sẽ có thứ tự là 100, 101, 102, 103) thì bên nhận sẽ gửi tin báo nhận có nội dung là 104 vì đó là thứ tự của byte tiếp theo nó cần. Bằng cách gửi tin báo nhận là 104, bên nhận đã ngầm thông báo rằng nó đã nhận được các byte 100, 101, 102 và 103. Trong trường hợp 2 byte cuối bị lỗi thì bên nhận sẽ gửi tin báo nhận với nội dung là 102 vì 2 byte 100 và 101 đã được nhận thành công.

### Kết thúc kết nối
Hai bên sử dụng quá trình bắt tay 4 bước và chiều của kết nối kết thúc độc lập với nhau. Khi một bên muốn kết thúc, nó gửi đi một gói tin FIN và bên kia gửi lại tin báo nhận ACK. Vì vậy, một quá trình kết thúc tiêu biểu sẽ có 2 cặp gói tin trao đổi.

Một kết nối có thể tồn tại ở dạng "nửa mở": một bên đã kết thúc gửi dữ liệu nên chỉ nhận thông tin, bên kia vẫn tiếp tục gửi.

***
Gói tin TCP gồm 2 phần:

* header
* data

## Header
![](https://i.imgur.com/Sf1ZZ3A.png)

Header gồm 11 trường, trong đó có 10 trường đầu là bắt buộc.

* **Source port**: số hiệu của cổng máy tính gửi
* **Destination port**: số hiệu của cổng máy tính nhận
* **Sequence number**: có 2 nhiệm vụ. Nếu cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tiên được gửi có số thứ tự này cộng thêm 1. Nếu không có cờ SYN thì đây là số thứ tự của byte đầu tiên.
* **Acknowledgement number**: Nếu cờ ACK bật thì giá trị của trường chính là số thứ tự gói tin tiếp theo mà bên nhận cần.
* **Data offset**: Trường có độ dài 4 bít quy định độ dài của phần header (tính theo đơn vị từ 32 bít). Phần header có độ dài tối thiểu là 5 từ (160 bit) và tối đa là 15 từ (480 bít).
* **Reserved**: dành cho tương lai và có giá trị là 0.
* **Flags** (hay Control bits): bit điều khiển, gồm 6 cờ
  * **URG**: Cờ cho trường Urgent pointer
  * **ACK**: Cờ cho trường Acknowledgement
  * **PSH**: Hàm Push
  * **RST**: Thiết lập lại đường truyền
  * **SYN**: Đồng bộ lại số thứ tự
  * **FIN**: Không gửi thêm số liệu
* **Checksum**: kiểm tra phần header và data
* **Urgent pointer**: Nếu cờ URG bật thì giá trị trường này chính là số từ 16 bít mà số thứ tự gói tin (sequence number) cần dịch trái.
* **Options**: Đây là trường tùy chọn. Nếu có thì độ dài là bội số của 32 bít.

## Data
Giá trị của trường này là thông tin dành cho các tầng trên (trong mô hình 7 lớp OSI). Thông tin về giao thức của tầng trên không được chỉ rõ trong phần header mà phụ thuộc vào cổng được chọn.

# 2.2. Cấu trúc gói tin UDP

UDP (User Datagram Protocol) là một trong những giao thức cốt lõi của giao thức TCP/IP. 

Dùng UDP, chương trình trên mạng máy tính có thể gửi những dữ liệu ngắn được gọi là datagram tới máy khác. 

UDP không cung cấp sự tin cậy và thứ tự truyền nhận mà TCP làm, các gói dữ liệu có thể đến không đúng thứ tự hoặc bị mất mà không có thông báo. 

Tuy nhiên UDP nhanh và hiệu quả hơn đối với các mục tiêu như kích thước nhỏ và yêu cầu khắt khe về thời gian. 

Do bản chất không trạng thái của nó nên nó hữu dụng đối với việc trả lời các truy vấn nhỏ với số lượng lớn người yêu cầu.

UDP thường được sử dụng cho chương trình phát sóng trực tiếp và trò chơi trực tuyến.

***
## Header
![](https://i.imgur.com/TsdSIAT.png)
Chứa thông tin về địa chỉ cổng nguồn, cổng đích, độ dài của gói và checksum.

Header của gói tin UDP chỉ chứa 4 trường dữ liệu, trong đó có 2 trường là tùy chọn (source port và checksum)

* Source port: xác định cổng của người gửi thông tin và có ý nghĩa nếu muốn nhận thông tin phản hồi từ người nhận. Nếu không dùng đến thì đặt nó bằng 0.
* Destination port: xác định cổng nhận thông tin.
* Length: xác định chiều dài của toàn bộ gói tin
* Checksum: kiểm tra lỗi của phần header và dữ liệu. 

# 2.3. Cấu trúc gói tin ICMP

ICMP (Internet Control Message Protocol) là một giao thức của bộ giao thức TCP/IP. Nó được các thiết bị mạng như router dùng để gửi đi các thông báo lỗi chỉ ra một dịch vụ có tồn tại hay không, hoặc một địa chỉ host hay router có tồn tại hay không.

ICMP khác với các giao thức vận chuyển như TCP và UDP ở chỗ nó không thường được sử dụng để trao đổi dữ liệu giữa các hệ thống, cũng không thường xuyên được sử dụng bởi các ứng dụng mạng của người dùng cuối (với ngoại lệ của một số công cụ chẩn đoán như ping và traceroute).

***

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

Một số thông báo đáng chú ý:
![](https://i.imgur.com/vUPRGlc.png)
## Data
Thông thường, data là header của gói tin IP và là 64 bit đầu tiên của nó.

# Cấu trúc gói tin IP
Mục đích của giao thức IP (Internet Protocol) là kết nối các mạng con thành dạng Internet để truyền dữ liệu.

Có lẽ các khía cạnh phức tạp nhất của IP là việc đánh địa chỉ và định tuyến. 

Đánh địa chỉ là công việc cấp địa chỉ IP cho các máy đầu cuối, cùng với việc phân chia và lập nhóm các mạng con của các địa chỉ IP. Việc định tuyến IP được thực hiện bởi tất cả các máy chủ, nhưng đóng vai trò quan trọng nhất là các thiết bị định tuyến liên mạng. Các thiết bị đó thường sử dụng các giao thức cổng trong (interior gateway protocol, viết tắt là IGP) hoặc các giao thức cổng ngoài (external gateway protocol, viết tắt là EGP) để hỗ trợ việc đưa ra các quyết định chuyển tiếp các gói tin IP (IP datagram) qua các mạng kết nối với nhau bằng giao thức IP.
***
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
* Flags: kiểm soát xem một gói tin bị phân mảnh (có 3 bit)
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

# 2.4. So sánh TCP và UDP

TCP hoạt động theo hướng kết nối (connection-oriented). Trước khi truyền dữ liệu giữa 2 máy, nó thiết lập một kết nối giữa 2 máy theo phương thức “bắt tay 3 bước" (3-way handshake) bằng cách gửi gói tin ACK từ máy đích sang máy nhận, trong suốt quá trình truyền gói tin, máy gửi yêu cầu máy đích xác nhận đã nhận đủ các gói tin đã gửi, nếu có gói tin bị mất, máy đích sẽ yêu cầu máy gửi gửi lại, thường xuyên kiểm tra gói tin có bị lỗi hay ko, ngoài ra còn cho phép qui định số lượng gói tin được gửi trong một lần gửi (window-sizing), điều này đảm bảo máy nhận nhận được đầy đủ các gói tin mà máy gửi gửi đi, dẫn tới nó truyền dữ liệu chậm hơn UDP nhưng đáng tin cậy hơn UDP.

UDP hoạt động theo hướng phi kết nối (connectionless), không yêu cầu thiết lập kết nối giữa 2 máy gửi và nhận, không có sự đảm bảo gói tin khi truyền đi cũng như không thông báo về việc mất gói tin, không kiểm tra lỗi của gói tin, dẫn tới nó truyền dữ liệu nhanh hơn TCP do cơ chế hoạt động có phần đơn giản hơn, tuy nhiên lại ko đáng tin cậy bằng TCP.

TCP thường sử dụng cho các ứng mạng cần độ chính xác và tin cậy cao như mail, FTP,... Còn UDP thích hợp cho các dịch vụ hỗ trợ về mặt tốc độ nhanh như VoIP, truyền hình trực tiếp, game online,...

# 3. Wireshark
**Wireshark** là một công cụ kiểm tra, theo dõi và phân tích thông tin mạng được phát triển bởi Gerald Combs.

Phiên bản đầu tiên của Wireshark mang tên Ethereal được phát hành năm 1988. Đến nay, WireShark vượt trội về khả năng hỗ trợ các giao thức (khoảng 850 loại), từ những loại phổ biến như TCP, IP đến những loại đặc biệt như là AppleTalk và Bit Torrent. 

### 1. Bắt gói tin
Giao diện chương trình:
![](https://i.imgur.com/cbiZhsk.png)

Interface List:

* WireLess Network Connection (Mạng WiFi)
* Local Area Connection (Mạng LAN)

Click icon trong hình để chọn Interface cần bắt gói tin
![](https://i.imgur.com/nZdnMAf.png)
Click **Start** để bắt đầu bắt gói tin.

Ngay sau đó, chúng ta sẽ thấy các gói dữ liệu bất đầu xuất hiện, Wireshark sẽ “bắt” từng gói – package ra và vào hệ thống mạng.

Click icon để dừng quá trình bắt gói tin.
![](https://i.imgur.com/BT9GQZK.png)

Chọn File => Save để lưu lại thành file. Sau này có thể mở ra để xem lại.

Click icon để bắt đầu một quá trình khác.
![](https://i.imgur.com/I3oaVex.png)

Chọn **Save** để lưu lại. Chọn **Continue without Saving** nếu không muốn lưu.
![](https://i.imgur.com/zMwxuv5.png)

Giao diện chương trình khi bắt gói tin:
![](https://i.imgur.com/SUohcoL.png)

Chúng ta sẽ thấy có nhiều màu sắc khác nhau. Wireshark dựa vào cơ chế này để giúp người dùng phân biệt được các loại traffic khác nhau.

Các cột: 

* Time: thời gian
* Source: địa chỉ nguồn
* Destination địa chỉ đích
* Protocol: giao thức
* Length: độ dài gói tin
* Info: thông tin

Danh sách gói tin:
![](https://i.imgur.com/IW7lqpf.png)

### 2. Lọc gói tin
Nhập từ khóa vào ô Filter rồi nhấn Enter, Wireshark sẽ tìm những gói tin với thông tin trên.

VD. Nhập "tcp", Wireshark sẽ chỉ ra những gói sử dụng giao thức TCP để truyền và nhận.

![](https://i.imgur.com/mMIlNo8.png)

VD. Tìm những gói tin có địa chỉ nguồn là *192.168.1.3* và địa chỉ đích là *2.17.150.138*.

![](https://i.imgur.com/Y8qlgth.png)

Nhấp chuột phải vào một packet, chúng ta sẽ thấy toàn bộ quãng thời gian giao tiếp giữa server và client.
![](https://i.imgur.com/XaCLNe3.png)

![](https://i.imgur.com/ObjYIDQ.png)

### 3. Kiểm tra gói tin
Thông tin của một gói tin cụ thể:
![](https://i.imgur.com/lTK9vlT.png)

# 4. tcpdump
**tcpdump** là công cụ được phát triển nhằm mục đích phân tích các gói dữ liệu mạng theo dòng lệnh. Nó cho phép người dùng chặn và hiển thị các gói tin được truyền đi hoặc được nhận trên một mạng mà máy tính có tham gia.

### 1. Cài đặt
Ở Ubuntu, dùng lệnh: `sudo apt-get install tcpdump -y`

### 2. Vài lệnh cơ bản
* Xem các interface đang hoạt động: `tcpdump -D`

![](https://i.imgur.com/KqWgQoe.png)

* Bắt gói tin trên 1 interface: `tcpdump -i <INTERFACE>`

VD. Bắt gói tin trên interface enp0s3.

![](https://i.imgur.com/ZGyFelr.png)

Bấm tổ hợp phím Ctrl + C để dừng.

Sau khi dừng, một vài thông số sau sẽ hiện ra:

* **Packet capture**: số lượng gói tin bắt được và xử lý.
* **Packet received by filter**: số lượng gói tin được nhận bởi bộ lọc.
* **Packet dropped by kernel**: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

Định dạng chung của một dòng giao thức tcpdump:

`time-stamp src > dst:  flags  data-seqno  ack  window urgent options`


|Tên trường|Mô tả|
|---|---|
|Time-swamp|hiển thị thời gian gói tin được bắt.|
|Src và dst|hiển thị địa IP của người gửi và người nhận.|
|Cờ Flag|S(SYN): Được sử dụng trong quá trình bắt tay của giao thức TCP.<br>.(ACK): Được sử dụng để thông báo cho bên gửi biết là gói tin đã nhận được dữ liệu thành công.<br>F(FIN): Được sử dụng để đóng kết nối TCP.<br>P(PUSH): Thường được đặt ở cuối để đánh dấu việc truyền dữ liệu.<br>R(RST): Được sử dụng khi muốn thiết lập lại đường truyền.|
|Data-sqeno|Số sequence number của gói dữ liệu hiện tại.|
|ACK|Mô tả số sequence number tiếp theo của gói tin do bên gửi truyền (số sequence number mong muốn nhận được).|
|Window|Vùng nhớ đệm có sẵn theo hướng khác trên kết nối này.|
|Urgent|Cho biết có dữ liệu khẩn cấp trong gói tin.|

* Bắt n gói tin với tùy chọn -c

`tcpdump -c n -i enp0s3`

Mặc định, tcpdump sẽ bắt liên tiếp các gói tin. Để dừng quá trình này, chúng ta phải thao tác tổ hợp phím Ctrl + C. Nhưng với tùy chọn -c, chúng ta có thể chỉ cho tcpdump biết là "Tôi chỉ muốn bắt n gói."

VD. Bắt 3 gói tin.

![](https://i.imgur.com/rgazd0u.png)

* Lưu file .pcap

`tcpdump -i enp0s3 -w <FILENAME>`

* Đọc file .pcap

`tcpdump -r <FILENAME>`

* Bắt các gói tin theo giao thức

`tcpdump -i enp0s3 <PROTOCOL> -c n`

(n: số gói tin cần bắt)

VD. Bắt các gói TCP

![](https://i.imgur.com/3pq95od.png)

* Bắt theo địa chỉ nguồn hoặc đích

`tcpdump -i emp0s3 src <IP_SOURCE>`
