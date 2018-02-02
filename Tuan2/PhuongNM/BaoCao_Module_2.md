# Mục lục
## 1. Firewall
## 2. Router
## 3. Switch
## 4. VPN
## 5. Hệ thống IDS/IPS
## 6. Lệnh ping, tracert, arp
## 7. Công cụ Netcut
## 8. Load Balancing
## 9. Proxy


***



# 1. Firewall

![](https://s.hswstatic.com/gif/firewall.gif)

## 1.1. Firewall là gì?
Firewall là một kỹ thuật được tích hợp vào hệ thống mạng để chống sự truy cập trái phép, nhằm bảo vệ các nguồn thông tin nội bộ và hạn chế sự xâm nhâp không mong muốn vào hệ thống. 

Firewall được miêu tả như là hệ phòng thủ bao quanh với các “chốt” để kiểm soát tất cả các luồng lưu thông nhập
xuất, có thể theo dõi và khóa truy cập tại các chốt này.

Các mạng riêng nối với Internet thường bị đe dọa bởi những kẻ tấn công. Để bảo vệ dữ liệu bên trong người ta thường dùng Firewall. Firewall có cách để cho phép người dùng hợp lệ đi qua và chặn lại những người dùng không hợp lệ.

Firewall có thể là thiết bị phần cứng hoặc chương trình phần mềm chạy trên host bảo đảm hoặc kết hợp cả hai. Trong mọi trường hợp, nó phải có ít nhất hai giao tiếp mạng, một cho mạng mà nó bảo vệ, một cho mạng bên ngoài. 
Firewall có thể là *gateway* hoặc điểm nối liền giữa hai mạng, thường là một mạng riêng và một mạng công cộng như là Internet.

*Gateway là thiết bị cho phép nối ghép hai loại giao thức với nhau. Ví dụ: mạng của bạn sử dụng giao thức IP và mạng của ai đó sử dụng giao thức IPX, Novell, DECnet, SNA,… hoặc một giao thức nào đó thì Gateway sẽ chuyển đổi từ loại giao thức này sang loại khác. Qua Gateway, các máy tính trong các mạng sử dụng các giao thức khác nhau có thể dễ dàng “nói chuyện” được với nhau.*

Nói ngắn gọn và dễ hiểu, Firewall chính là ranh giới bảo mật giữa bên trong và bên ngoài của một hệ thống mạng máy tính.

## 1.2. Chức năng của Firewall
* **Điều khiển truy nhập**: chỉ cho phép những người dùng hợp lệ có quyền truy cập đến tài nguyên của mạng mà người dùng đó cần; xác định là người dùng được phép và các tài nguyên nào cho họ được phép truy nhập và truy nhập như thế nào.
* **Theo dõi truy nhập**: Firewall có thể theo dõi, hiển thị, lập báo cáo và cảnh báo về những lưu thông
mạng mà nó điều khiển.
* **Ghi lại nhật ký làm việc**: Các Firewall có thể tính toán về các thông tin truy nhập và các thông tin của mọi kết nối một cách chi tiết và lập báo cáo phân tích.
* **Cảnh báo an ninh**: Các Firewall có thể đưa ra nhiều tuỳ chọn để cảnh báo như dùng email để thông báo, sử dụng giao thức SNMP để gửi các cảnh báo an
ninh tới các hệ thống quản trị mạng.
* **Ngăn chặn các kiểu tấn công**:
 * Giả mạo địa chỉ IP (IP Spoofing)
 * Tấn công phong toả dịch vụ (DoS - Denial of Service)
 * Tấn công mạng LAN (LAN attack): với kỹ thuật này, nếu một kẻ tấn công gửi các gói SYN giả tạo chứa địa chỉ IP nguồn và đích cho nạn nhân, nạn nhân đó gửi các gói tin SYN-ACK cho chính bản thân mình, từ đó tạo ra các kết nối không được sử dụng chiếm giữ khoảng trống bảng đến khi hết thời gian. Firewall có thể chống lại các cuộc tấn công mạng LAN bằng
cách kết hợp sự bảo vệ chống lại SYN Flood và IP Spoofing.

## 1.3. Firewall hoạt động như thế nào?
Firewall sử dụng các quy định (*rule*) hoặc ngoại lệ (*exception*) để làm việc với những kết nối tốt và loại bỏ những kết nối xấu. Nhìn chung, quá trình này được thực hiện ẩn, người dùng không thấy được hoặc không cần tương tác gì cả.

Firewall hoạt động chặt chẽ với giao thức TCP/IP vì nó chia nhỏ các dữ liệu nhận được thành các gói
dữ liệu (data packets) rồi gán cho các packet này những địa chỉ có thể nhận dạng, tái lập
lại ở đích cần gửi đến, do đó các loại Firewall cũng liên quan rất nhiều đến các packet và những con số địa chỉ của chúng.

Bộ lọc packet cho phép hay từ chối mỗi packet mà nó nhận được. Nó kiểm tra toàn bộ đoạn dữ liệu để quyết định xem đoạn dữ liệu đó có thỏa mãn một trong số các luật lệ của lọc packet hay không. Các *rule* lọc packet này là dựa trên các thông tin ở phần header của mỗi packet. Nó bao gồm:

* Địa chỉ IP nguồn
* Địa chỉ IP đích 
* Giao thức
* Cổng TCP/UDP nơi xuất phát
* Cổng TCP/UDP nơi nhận
* Dạng thông báo ICMP

## 1.4. Ưu điểm và nhược điểm của Firewall

### 1.4.1. Ưu điểm
* Firewall do con người cấu hình có thể che giấu mạng nội bộ bên trong, lọc dữ liệu và nội dung của dữ liệu để ngăn chặn được các ý đồ xấu từ bên ngoài.
* Firewall có thể ngăn chặn các cuộc tấn công vào các server gây tổn thất lớn cho các doanh nghiệp.

### 1.4.2. Nhược điểm
 * Firewall không thể ngăn chặn các cuộc tấn công nếu như cuộc tấn công đó không “đi qua” nó. VD như nó không thể chống lại một cuộc tấn công từ một đường dial-up (chỉ việc kết nối Internet hoặc các mạng nội bộ thông qua giao thức kết nối sử dụng đường truyền điện thoại), hoặc là sự dò rỉ thông tin do dữ liệu bị sao chép bất hợp pháp ra đĩa mềm.
 * Firewall cũng không thể chống lại các cuộc tấn công bằng dữ liệu (data-driven attack). Khi có một số ứng dụng hay phần mềm được chuyển qua thư điện tử, nó có thể vượt qua Firewall vào trong mạng được bảo vệ.
 * Firewall không thể làm nhiệm vụ rà quét virus trên các dữ liệu được chuyển qua nó, do tốc độ làm việc, sự xuất hiện liên tục của các virus mới và do có rất nhiều cách để mã hóa dữ liệu để có thể thoát khỏi khả năng kiểm soát của firewall. 

## 1.5. Phân loại Firewall
* Firewall lọc gói (Packet Filtering Firewall)
* Firewall mức kết nối (Circuit Level Firewall)
* Firewall mức ứng dụng (Application Layer Firewall)
* Firewall lọc gói động (Dynamic packet filter Firewall)

### 1.5.1. Firewall lọc gói (Packet Filtering Firewall)
Firewall lọc gói là Firewall thế hệ thứ nhất.

Nó phân tích các thông tin về tầng Giao vận trong các gói tin IP của mạng. Mỗi gói tin IP được kiểm tra xem nó có phù hợp với một trong các rule đã được thiết lập trước hay không, xác định gói tin đó là được phép hay không dựa vào thông tin được chứa trong phần header tầng Giao vận của gói tin và hướng được ghi trong phần header của gói tin (từ mạng trong ra mạng ngoài hoặc ngược lại).

Việc kiểm tra gói tin trên mạng một cách đầy đủ gắn với thuật toán thông thường sau:

* Nếu không tìm thấy một rule nào thích hợp thì bỏ gói tin đó.
* Nếu tìm thấy một rule thích hợp cho phép truyền thông tin thì cho phép truyền thông tin ngang hàng.
* Nếu tìm thấy một rule từ chối thông tin thì bỏ gói tin đó.

### 1.5.2. Firewall mức kết nối (Circuit Level Firewall)
Firewall mức kết nối là một công nghệ Firewall thế hệ thứ hai. 

Nó xác nhận tính hợp lệ của một gói tin là yêu cầu kết nối hoặc gói tin dữ liệu thuộc về một kết nối (hoặc kết nối ảo) giữa hai tầng giao vận tương đương.

Để phê chuẩn một phiên làm việc, Firewall mức kết nối kiểm tra thiết lập kết nối để đảm bảo rằng kết nối này tạo ra một thủ tục bắt tay hợp lệ cho giao thức mà tầng Giao vận đang sử dụng (điển hình là TCP). Các gói tin dữ liệu sẽ không được gửi cho đến khi thủ tục bắt tay được hoàn thành. 

Loại Firewall này luôn duy trì một bảng thông tin của các kết nối hợp lệ (bao gồm trạng thái của phiên bản làm việc đầy đủ và thông tin về thứ tự gói tin) và cho phép các gói tin dữ liệu đi qua khi thông tin của gói này phù hợp với một mục trong bảng kết nối ảo. Mỗi lần một kết nối kết thúc thì mục chứa thông tin về kết nối này trong bảng kết nối ảo sẽ bị xoá và kết nối ảo giữa hai tầng giao vận tương đương cũng bị đóng. 

### 1.5.3. Firewall mức ứng dụng (Application layer Firewall)

Firewall mức ứng dụng là công nghệ Firewall thế hệ thứ ba, cung cấp điều khiển tại tầng Ứng dụng nên hoạt động giống như mức ứng dụng. 

Với khả năng kiểm tra chi tiết sự lưu thông, độ an toàn của Firewall mức ứng dụng cao hơn so với Firewall lọc gói nhưng đồng thời cũng làm cho Firewall loại này chậm hơn so với Firewall lọc gói.

Nó kiểm tra tính hợp lệ của các gói dữ liệu tại
tầng Ứng dụng trước khi cho phép thực hiện một kết nối. Nó kiểm tra tất cả các gói tin tại tầng ứng dụng và duy trì thông tin về trạng thái kết nối đầy đủ và
thông tin về thứ tự. 

Ngoài ra, một Firewall mức ứng dụng còn có thể phê chuẩn các mục bảo vệ an ninh khác mà nó chỉ xuất hiện trong tầng ứng dụng, chẳng hạn như: mật khẩu người dùng và các yêu cầu dịch vụ.

### 1.5.4. Firewall lọc gói động (Dynamic packet filter Firewall)
Firewall lọc gói động là công nghệ Firewall thế hệ thứ tư. 

Nó cho phép sửa đổi các chính sách đảm bảo an ninh dựa trên tình huống. Loại công nghệ này rất có ích trong việc cung cấp sự hỗ trợ nào đó đối với giao thức tầng giao vận UDP. Giao thức tầng giao vận UDP thường được sử dụng đối với các yêu cầu thông tin hạn chế và các truy vấn trong trao đổi giao thức tầng ứng dụng.

Các Firewall này thực hiện những yêu cầu chức năng của nó bằng cách liên kết tất cả các gói UDP đi qua vành đai bảo vệ an ninh bằng một kết nối ảo đã được thay đổi và gói tin này được đi qua server Firewall. Thông tin kết hợp với kết nối ảo được lưu giữ trong một thời gian ngắn, và nếu không nhận được gói tin đáp ứng nào trong khoảng thời gian này, kết nối ảo là không hợp lệ.

***

# 2. Router
## 2.1. Router là gì?
Router, hay còn gọi là *thiết bị định tuyến* hoặc *bộ định tuyến*, là thiết bị mạng máy tính dùng để chuyển các gói dữ liệu qua một liên mạng để đến các đầu cuối, thông qua một tiến trình được gọi là định tuyến.

Quá trình định tuyến xảy ra ở tầng 3 (Network) của mô hình OSI 7 tầng.


## 2.2. Chức năng của Router
* Phân cách các mạng máy tính thành các segment riêng biệt để giảm hiện tượng
đụng độ, giảm broadcast hay thực hiện chức năng bảo mật.
* Kết nối các mạng máy tính hay kết nối các user với mạng máy tính ở các
khoảng cách xa với nhau thông qua các đường truyền thông: điện thoại, ISDN,
T1, X.25…

Cùng với sự phát triển của switch, chức năng đầu tiên của router ngày nay đã được
switch đảm nhận một cách hiệu quả. Router chỉ còn phải đảm nhận việc thực hiện các
kết nối truy cập từ xa (remote access) hay các kết nối WAN cho hệ thống mạng LAN.
Do hoạt động ở tầng thứ 3 của mô hình OSI, router sẽ hiểu được các protocol quyết định
phương thức truyền dữ liệu.

## 2.3. Router hoạt động như thế nào?
Một cách tổng quát router sẽ chuyển
packet theo các bước sau:
* Đọc packet.
* Gỡ bỏ dạng format quy định bởi protocol của nơi gửi.
* Thay thế phần gỡ bỏ đó bằng dạng format của protocol của đích đến.
* Cập nhật thông tin về việc chuyển dữ liệu: địa chỉ, trạng thái của nơi gửi, nơi
nhận.
* Gứi packet đến nơi nhận qua đường truyền tối ưu nhất.


***

# 3. Switch
## 3.1. Switch là gì?
Switch, hay còn gọi là thiết bị chuyển mạch, là một thiết bị dùng để kết nối các đoạn mạng với nhau theo mô hình mạng hình sao (star). Theo mô hình này, switch đóng vai trò là thiết bị trung tâm, tất cả các máy tính đều được nối về đây.

Switch làm việc như một Bridge nhiều cổng. Khác với Hub nhận tín hiệu từ một cổng rồi chuyển tiếp tới tất cả các cổng còn lại, switch nhận tín hiệu vật lý, chuyển đổi thành dữ liệu, từ một cổng, kiểm tra địa chỉ đích rồi gửi tới một cổng tương ứng.

Switch làm việc như một Bridge nhiều cổng. Khác với HUB nhận tín hiệu từ một cổng rồi chuyển tiếp tới tất cả các cổng còn lại, switch nhận tín hiệu vật lý, chuyển đổi thành dữ liệu, từ một cổng, kiểm tra địa chỉ đích rồi gửi tới một cổng tương ứng.

![](https://networklessons.com/wp-content/uploads/2016/12/switch-star-topology-hosts.png)

Trong mô hình tham chiếu OSI, switch hoạt động ở tầng Liên kết dữ liệu, ngoài ra có một số loại switch cao cấp hoạt động ở tầng Mạng.

## 3.2. Chức năng của Switch
* Switch quyết định chuyển frame dựa trên địa chỉ MAC, do đó nó được xếp vào thiết bị Lớp 2. Chính nhờ Switch có khả năng lựa chọn đường dẫn để quyết định chuyển frame nên mạng LAN có thể hoạt động hiệu quả hơn.
* Switch nhận biết máy nào kết nối với cổng của nó bằng cách học địa chỉ MAC nguồn trong frame mà nó nhận được. Khi hai máy thực hiện liên lạc với nhau.
* Switch chỉ thiết lập một mạch ảo giữa hai cổng tương ứng mà không làm ảnh hưởng đến lưu thông trên các cổng khác. Do đó, mạng LAN có hiệu suất hoạt động cao thường sử dụng chuyển mạch toàn bộ.
* Switch tập trung các kết nối và quyết định chọn đường dẫn để truyền dữ liệu hiệu quả. Frame được chuyển mạch từ cổng nhận vào đến cổng phát ra. Mỗi cổng là một kết nối cung cấp chọn băng thông cho host.
* Trong Ethernet Hub, tất cả các cổng kết nối vào một mạng chính, hay nói cách khác, tất cả các thiết bị kết nối Hub sẽ cùng chia sẻ băng thông mạng. Nếu có hai máy trạm được thiết lập phiên kết nối thì chúng sẽ sử dụng một lượng băng thông đáng kể và hoạt động của các thiết bị còn lại kết nối vào Hub sẽ bị giảm xuống. Để giải quyết tình trạng trên, Switch xử lý mỗi cổng là một đoạn mạng (segment) riêng biệt. Khi các máy ở các cổng khác nhau cần liên lạc với nhau, Switch sẽ chuyển frame từ cổng này sang cổng kia và đảm bảo cung cấp chọn băng thông cho mỗi phiên kết nối.

## 3.3. Phân loại Switch

* **Workgroup switch**: là loại switch được thiết kế nhằm để nối trực tiếp các máy tính lại với nhau hình thành một mạng ngang hàng. Như vậy, tương ứng với một cổng của switch chỉ có một địa chỉ máy tính trong bảng dịa chỉ. Giá thành thấp hơn các loại khác. Vì thế, loại này không cần thiết phải có bộ nhớ lớn cũng như tốc độ xử lý cao. 
* **Segment switch**: nối các Hub hay workgroup switch lại với nhau, hình thành một liên mạng ở tầng hai. Tương ứng với mỗi cổng trong trường hợp này sẽ có nhiều địa chỉ máy tính, vì thế bộ nhớ cần thiết phải đủ lớn. Tốc độ xử lý đòi hỏi phải cao vì lượng thông tin càn xử lý tại switch là lớn.
* **Backbone switch**: kết nối các segment switch lại với nhau. Bộ nhớ và tốc độ xử lý của switch phải rất lớn để đủ chứa địa chỉ cho tất cả các máy tính trong toàn liên mạng và hoán chuyện kịp thời dữ liệu giữa các nhánh mạng.

***

# 4. VPN

## 4.1 VPN là gì?
![](https://f9official.com/wp-content/uploads/2017/10/VPN-Featured-Image.png)

VPN (Virtual Private Network) là phương pháp làm cho
một mạng công cộng (ví dụ như Internet) hoạt động giống như mạng nội bộ, có cùng các đặc tính như bảo mật và ưu tiên.

VPN cho phép thành lập các kết nối riêng với những người dùng ở xa, các văn phòng chi nhánh và đối tác đang sử dụng một mạng công cộng. Mạng WAN truyền thống yêu cầu công ty phải trả chi phí và duy trì nhiều loại đường dây riêng, song song với đầu tư thiết bị và đội ngũ cán bộ. Rào cản về chi phí cũng là nguyên nhân làm cho doanh nghiệp tuy muốn hưởng lợi ích của việc mở rộng mạng nhưng nhiều lúc lại không thể thực hiện nổi. Trong khi đó, VPN lại không bị rào cản này vì được thực hiện qua mạng công cộng.

VPN dùng việc mã hoá dữ liệu để ngăn ngừa các người dùng không được phép truy cập đến dữ liệu và bảo đảm dữ liệu không bị sửa đổi. Định hướng đường hầm (tunneling) là một cơ chế dùng cho việc đóng gói một giao thức vào trong một giao thức khác. Trong ngữ cảnh Internet, tunneling cho phép những giao thức như IPX, Apple Talk và IP được mã hoá. Trong ngữ cảnh VPN, tunneling che giấu giao thức lớp mạng nguyên thuỷ bằng cách mã hoá gói dữ liệu bằng cách mã hoá gói dữ liệu và chứa gói đã mã hoá và trong một vỏ bọc IP. 

VPN còn cung cấp các thoả thuận về chất lượng dịch vụ (QoS). 

Ta có thể định nghĩa VPN qua công thức:

**VPN = Tunneling + Bảo mật + Các thoả thuận về QoS**

Hiểu trên cơ bản, VPN như là một đường hầm mà dữ liệu được mã hóa của bạn đi qua, giúp bạn an toàn hơn và ẩn danh khi trực tuyến.

## 4.2. Các mô hình kết nối VPN thông dụng
Mục tiêu của công nghệ VPN là quan tâm đến ba yêu cầu cơ bản sau:

* Các nhân viên liên lạc từ xa, người dùng di động, người dùng từ xa của
một công ty có thể truy cập vào tài nguyên mạng của công ty họ bất cứ lúc
nào.
* Có khả năng kết nối từ xa giữa các nhánh văn phòng.
* Kiểm soát được truy cập của các khách hàng, nhà cung cấp là đối tác quan trọng đối với giao dịch thương mại của công ty.

Với các yêu cầu cơ bản như trên, ngày nay, VPN được phát triển và phân thành ba loại như sau: 

* VPN Truy cập từ xa (Remote Access VPN): cung cấp kết nối cho người dùng làm việc từ xa và di động. Nó là một sự thay thế cho các kết nối dial chuyên dụng hoặc ISDN. 
* VPN Cục bộ (Intranet VPN): kết nối trụ sở công ty, văn phòng từ xa và văn phòng chi nhánh qua một cơ sở hạ tầng chia sẻ sử dụng các kết nối chuyên dụng. 
* VPN Mở rộng (Extranet VPN): kết nối khách hàng, nhà cung cấp, đối tác, hoặc cộng đồng người sử dụng thông qua một cơ sở hạ tầng chia sẻ sử dụng kết nối chuyên dụng. 

## 4.3. Các giao thức sử dụng trong VPN
* **Point-to-Point Tunneling Protocol (PPTP)**
* **Internet Protocol Security (IPSec)**
* **Layer2 Tunneling Protocol (L2TP)**
* **Secure Socket Layer (SSL)**

### 4.3.1. Point-to-Point Tunneling Protocol (PPTP)

PPTP là sự mở rộng của giao thức Internet chuẩn Point-to-Point (PPP) và sử dụng cùng kiểu xác thực như PPP (PAP, SPAP, CHAP, MS-CHAP, EAP). Là phương pháp VPN được hỗ trợ rộng rãi nhất giữa các máy trạm chạy Windows. 

PPTP thiết lập đường hầm (tunnel) nhưng không mã hóa. Ưu điểm khi sử dụng PPTP là nó không yêu cầu hạ tầng mã khóa công cộng (Public Key Infrastructure).

### 4.3.2. Internet Protocol Security (IPSec)

IPsec được tích hợp trong rất nhiều giải pháp VPN "tiêu chuẩn", đặc biệt trong các giải pháp VPN gateway-to-gateway (site-to-site) để nối 2 mạng LAN với nhau. IPsec hoạt động tại tầng Mạng (tầng 3) trong mô hình OSI.

IPSec trong chế độ đường hầm bảo mật các gói tin trao đổi giữa hai gateway hoặc giữa máy tính trạm và gateway. Như tên của nó, IPsec chỉ hoạt động với các mạng và ứng dụng dựa trên nền tảng IP (IP-based network). Giống như PPTP và L2TP, IPsec yêu cầu các máy tính trạm VPN phải được cài đặt sẵn phần mềm VPN client.

Việc xác thực được thực hiện thông qua giao thức Internet Key Exchange (IKE) hoặc với chứng chỉ số (digital certificates) đây là phương thức bảo mật hơn hoặc thông qua khóa mã chia sẻ (preshared key). IPSec VPN có thể bảo vệ chống lại hầu hết các phương pháp tấn công thông dụng bao gồm Denial of Service (DoS - tấn công từ chối dịch vụ), replay, và "man-in-the-middle".

### 4.3.3. Layer2 Tunneling Protocol (L2TP)
Giao thức Layer 2 Tunneling Protocol (L2TP) là sự kết hợp các đặc điểm của cả PPTP và giao thức Layer 2 Forwarding (L2F).

Giống như PPTP, L2TP hoạt động tại tầng Liên kết dữ liệu (data link layer) của mô hình mạng OSI.

L2TP yêu cầu sử dụng chứng chỉ số (digital certificates). Xác thực người dùng có thể được thực hiện thông qua cùng cơ chế xác thực PPP tương tự như PPTP. L2TP có một vài ưu điểm so với PPTP. PPTP cho người dùng khả năng bảo mật dữ liệu, nhưng L2TP còn tiến xa hơn khi cung cấp thêm khả năng đảm bảo tính toàn vẹn dữ liệu, khả năng xác thực nguồn gốc (xác định người dùng đã gửi dữ liệu có thực sự đúng người), và khả năng bảo vệ chống gửi lại – replay protection (chống lại việc hacker chặn dữ liệu đã được gửi, ví dụ thông tin quyền đăng nhập (credentials), rồi sau đó gửi lại (replay) chính thông tin đó để bẫy máy chủ. 

Mặt khác, do liên quan đến cung cấp các khả năng bảo mật mở rộng làm cho L2TP chạy chậm hơn chút ít so với PPTP.

### 4.3.4. Secure Socket Layer (SSL)
SSL còn được gọi là giải pháp "clientless". Điều này cũng có nghĩa là các giao thức có thể được xử lý bởi SSL sẽ bị hạn chế nhiều hơn. Dù sao, điều này cũng đem lại một lợi thế về bảo mật. 

Với SSL, thay vì cho phép VPN client truy xuất vào toàn bộ mạng hoặc một mạng con (subnet) như với IPsec, có thể hạn chế chỉ cho phép truy xuất tới một số ứng dụng cụ thể. Nếu một ứng dụng mà người dùng muốn họ truy cập không phải là là loại ứng dụng dựa trên trình duyệt (browser-based), thì cần phải tạo ra một plug-ins Java hoặc Active-X để làm cho ứng dụng đó có thể truy xuất được qua trình duyệt.

SSL hoạt động ở tầng Phiên – cao hơn IPsec trong mô hình OSI. Điều này cho nó khả năng điều khiển truy cập theo khối tốt hơn. SSL sử dụng chứng chỉ số (digital certificates) để xác thực server. Mặc dù các phương pháp khác cũng có thể áp dụng, nhưng sử dụng chứng chỉ số được ưa chuộng vì khả năng bảo mật cao nhất.

## 4.4. Ưu điểm và nhược điểm của VPN
Để xây dựng 1 hệ thống mạng riêng, mạng cá nhân ảo thì dùng VPN là 1 giải pháp không hề tốn kém. Môi trường Internet là cầu nối, giao tiếp chính để truyền tải dữ liệu, xét về mặt chi phí thì nó hoàn toàn hợp lý so với việc trả tiền để thiết lập 1 đường kết nối riêng với giá thành cao. Bên cạnh đó, việc phải sử dụng hệ thống phần mềm và phần cứng nhằm hỗ trợ cho quá trình xác thực tài khoản cũng không phải là rẻ. Việc so sánh sự tiện lợi mà VPN mang lại cùng với chi phí bỏ ra để bạn tự thiết lập 1 hệ thống như ý muốn, rõ ràng VPN chiếm ưu thế hơn hẳn.

Nhưng bên cạnh đó, nó có nhược điểm rất dễ nhận thấy. VPN không có khả năng quản lý Quality of Service (QoS) qua môi trường Internet, do vậy các gói dữ liệu – Data Package vẫn có nguy cơ bị thất lạc, rủi ro. Khả năng quản lý của các đơn vị cung cấp VPN là có hạn, không ai có thể ngờ trước được những gì có thể xảy ra với khách hàng của họ.

***

# 5. IDS/IPS
## 5.1. IDS/IPS là gì?

IDS (Intrusion Detection System) là một hệ thống phát hiện các hành động tấn công vào một mạng. Một tính năng chính của hệ thống này là cung cấp thông tin nhận biết về những hành động không bình thường và đưa ra các báo cảnh thông báo cho quản trị viên mạng khóa các kết nối đang tấn công này. Thêm vào đó công cụ IDS cũng có thể phân biệt giữa những tấn công bên trong từ bên trong tổ chức (nhân viên hoặc khách hàng) và tấn công bên ngoài (hacker).

IPS (Intrusion Prevention Systems) là hệ thống theo dõi, ngăn ngừa kịp thời các hoạt động xâm nhập không mong muốn. Chức năng chính của IPS là xác định các hoạt động nguy hại, lưu giữ các thông tin này. Sau đó nó kết hợp với firewall để dừng ngay các hoạt động này, và cuối cùng đưa ra các báo cáo chi tiết về các hoạt động xâm nhập trái phép trên.

IDS và IPS có rất nhiều điểm chung, do đó hệ thống IDS và IPS có thể được gọi chung là IDP- Intrusion Detection and Prevention. 

Hiện nay, công nghệ của IDS đã được thay thế bằng các giải pháp IPS. 

## 5.2. Chức năng cơ bản
* Nhận diện các nguy cơ có thể xảy ra.
* Ghi nhận thông tin, log để phục vụ cho việc kiểm soát nguy cơ.
* Nhận diện các hoạt động thăm dò hệ thống.
* Nhận diện các yếu khuyết của chính sách bảo mật.
* Ngăn chặn vi phạm chính sách bảo mật.
* Lưu giữ thông tin liên quan đến các đối tượng quan sát
* Cảnh báo những sự kiện quan trọng liên quan đến đối tượng quan sát
* Ngăn chặn các tấn công (IPS)
* Xuất báo cáo

## 5.3. Phân loại IDS/IPS
Dựa trên phạm vi giám sát, IDS được chia thành 2 loại:
* Network-based IDS (NIDS): Là những IDS giám sát trên toàn bộ mạng. Nguồn thông tin chủ yếu của NIDS là các gói dữ liệu đang lưu thông trên mạng. NIDS thường được lắp đặt tại ngõ vào của mạng, có thể đứng trước hoặc sau tường lửa. Hình 1 mô tả một NIDS điển hình.
* Host-based IDS (HIDS): Là những IDS giám sát hoạt động của từng máy tính riêng biệt. Do vậy, nguồn thông tin chủ yếu của HIDS ngòai lưu lượng dữ liệu đến và đi từ máy chủ còn có hệ thống dữ liệu nhật ký hệ thống (system log) và kiểm tra hệ thống (system audit).

Dựa trên kỹ thuật thực hiện, IDS cũng được chia thành 2 loại:
 
* Signature-based IDS: phát hiện xâm nhập dựa trên dấu hiệu của hành vi xâm nhập, thông qua phân tích lưu lượng mạng và nhật ký hệ thống. Kỹ thuật này đòi hỏi phải duy trì một cơ sở dữ liệu về các dấu hiệu xâm nhập (signature database), và cơ sở dữ liệu này phải được cập nhật thường xuyên mỗi khi có một hình thức hoặc kỹ thuật xâm nhập mới. 
* Anomaly-based IDS: phát hiện xâm nhập bằng cách so sánh (mang tính thống kê) các hành vi hiện tại với hoạt động bình thường của hệ thống để phát hiện các bất thường (anomaly) có thể là dấu hiệu của xâm nhập. Ví dụ, trong điều kiện bình thường, lưu lượng trên một giao tiếp mạng của server là vào khỏang 25% băng thông cực đại của giao tiếp. Nếu tại một thời điểm nào đó, lưu lượng này đột ngột tăng lên đến 50% hoặc hơn nữa, thì có thể giả định rằng server đang bị tấn công DoS. Để hoạt động chính xác, các IDS loại này phải thực hiện một quá trình “học”, tức là giám sát hoạt động của hệ thống trong điều kiện bình thường để ghi nhận các thông số hoạt động, đây là cơ sở để phát hiện các bất thường về sau.

## 5.4. So sánh IDS và IPS
Nếu như hiểu đơn giản, có thể xem như IDS chỉ là một cái chuông để cảnh báo cho người quản trị biết những nguy cơ có thể xảy ra tấn công. Dĩ nhiên có thể thấy rằng, nó chỉ là một giải pháp giám sát thụ động, tức là chỉ có thể cảnh báo mà thôi, việc thực hiện ngăn chặn các cuộc tấn công vào hệ thống lại hoàn toàn phụ thuộc vào người quản trị. Vì vậy yêu cầu rất cao đối với nhà quản trị trong việc xác định các lưu lượng cần và các lưu lượng có nghi vấn là dấu hiệu của một cuộc tấn công. Và dĩ nhiên công việc này thì lại hết sức khó khăn. 

Với IPS, người quản trị không nhũng có thể xác định được các lưu lượng khả nghi khi có dấu hiệu tấn công mà còn giảm thiểu được khả năng xác định sai các lưu lượng. Với IPS, các cuộc tấn công sẽ bị loại bỏ ngay khi mới có dấu hiệu và nó hoạt động tuân theo một quy luật do nhà Quản trị định sẵn.

***

# 6. Lệnh ping, tracert, arp

## 1. ping
Ping, viết tắt của **P**acket **I**nter**n**et **G**rouper (Groper), là một công cụ cho mạng máy tính sử dụng trên các mạng TCP/IP (chẳng hạn như Internet) để kiểm tra xem có thể kết nối tới một máy chủ cụ thể nào đó hay không và ước lượng khoảng thời gian trễ trọn vòng để gửi gói dữ liệu cũng như tỉ lệ các gói dữ liệu có thể bị mất giữa hai máy. 

Công cụ này thực hiện nhiệm vụ trên bằng cách gửi một số gói tin ICMP đến máy kia và lắng nghe trả lời.

Cú pháp: `ping <địa chỉ đích> <tham số (nếu có)>`

Các tham số của lệnh **ping**:

![](https://i.imgur.com/e0vgllh.png)

Một số thông điệp trả về khi PING:

* **Request time out**: thực hiện gửi gói thành công nhưng không nhận được gói phản hồi (Lỗi ở phía kia)
* **Destination host unreachable**: đích đến không tồn tại hoặc đang cô lập (lỗi ở phía mình)
* **Reply from 2.17.50.138: bytes=32 time=52ms TTL=58**: Gửi gói đến địa chỉ IP 2.17.50.138 với độ dài gói 32 byte, thời gian phản hồi là 52 mili giây, TTL (time to live - thời gian tồn tại của gói, chỉ số hop mà gói tin truyền thông không phải qua khi truyền từ bên gửi sang bên nhận) là 58.
* **Unknown host / Ping Request Could Not Find Host**: cho biết hostname bạn ping đến không có trên bất cứ hệ thống phân giải tên miền nào hay lý do đơn giản là bạn viết sai chính tả.

VD. `ping fox.com`

![](https://i.imgur.com/IU2rCMa.png)

## 2. tracert
Tracert là công cụ kiểm tra đường đi của gói dữ liệu, xem nó đi qua các trạm nào, mất bao lâu, trạm nào bị nghẽn, không kết nối được không? trạm đó bị nghẽn thì có con đường nào khác để đến đích hay không? Thực tế càng qua nhiều trạm thì càng chậm và càng có rủi ro bị time out (mất kết nối).

Tracert tìm đường tới đích bằng cách gửi các thông báo Echo Request (yêu cầu báo hiệu lại) Internet Control Message Protocol (ICMP) tới từng đích. Sau mỗi lần gặp một đích, giá trị Time to Live (TTL), tức thời gian cần để gửi đi sẽ được tăng lên cho tới khi gặp đúng đích cần đến.

Tracert cho phép xác định đường đi của các gói tin truyền qua mạng tới host cụ thể bạn chỉ định. Khi một gói tin đi qua một host, host sẽ giảm giá trị TTL của gói tin đi một giá trị và gửi tới host tiếp theo. Khi quá thời gian mà chưa đến đúng địa chỉ cần tìm, host nhận được gói tin sẽ loại bỏ và gửi lại thông báo thời gian quá hạn ICMP. 

Cú pháp: `tracert <tên miền>`

VD. `tracert fox.com`
![](https://i.imgur.com/KXVofz3.png)

![](http://www.mygreatname.com/how-traceroute-works/traceroute-e7.gif)

Cách đọc kết quả: `Hop RTT1 RTT2 RTT3 <name/IP address>`

* Hop: số thứ tự của hop (1 hop được tính khi gói tin đi qua 1 router)
* RTT1, RTT2, RTT3: viết tắt của *Round Trip Time* (là khoảng thời gian tính từ lúc client bắt đầu gửi request tới lúc nó nhận gói dữ liệu đầu tiên trả về, không bao gồm thời gian nhận đầy đủ dữ liệu). Có 3 RTT vì tracert gửi đi 3 goisn tin khác nhau.
* Name/IP Address: Nếu như router đó có tên miền tiên thì nó sẽ được hiển thị, thông qua tên miền của router, biết được vị trí của router ở mạng trên. Nếu router không có tên miền thì sẽ hiển thị *địa chỉ IP*.  

## 3. arp

ARP (Address Resolution Protocol) là giao thức được sử dụng để phân giải địa chỉ IP sang địa chỉ máy (MAC).

Nguyên tắc hoạt động của ARP trong mạng LAN:

* Khi một thiết bị mạng muốn biết địa chỉ MAC của một thiết bị mạng nào đó mà nó đã biết địa chỉ ở tầng Mạng, nó sẽ gửi một ARP request bao gồm địa chỉ MAC address của nó và địa chỉ IP của thiết bị mà nó cần biết MAC address trên toàn bộ một miền broadcast. 
* Mỗi một thiết bị nhận được request này sẽ so sánh địa chỉ IP trong request với địa chỉ tầng Mạng của mình. Nếu trùng địa chỉ thì thiết bị đó phải gửi ngược lại cho thiết bị gửi ARP request một gói tin (trong đó có chứa địa chỉ MAC của mình).

Cú pháp: 
`arp`: xem thông tin lệnh arp

`arp -a [inet_addr]`: hiện giá trị tại bảng ARP của giao thức ARP trong máy tính. Nếu có địa chỉ *inet_addr* thì chỉ có máy có địa chỉ tương ứng thể hiện. 

`arp -s inet_addr eth_addr`: thêm vào bảng ARP một địa chỉ IP và MAC.

`arp -d inet_addr`: xóa địa chỉ IP **inet_addr**


***

# 7. Công cụ Netcut

NetCut là một công cụ trông có chức năng như kiểm tra tốc độ mạng, băng thông, thay đổi địa chỉ MAC, hay cắt truy cập mạng đối với bất kỳ thành viên mạng LAN nào.

Việc cắt truy cập mạng chính là chức năng hữu ích nhất dành cho người quản trị mạng LAN, vì đôi khi có những thành viên trong mạng dùng đến mức chiếm hết băng thông của người khác. Nhất là với người quản trị mạng Wi-Fi, đặc tính không dây khiến việc kiểm soát các thành viên truy cập là không dễ (ngay cả khi đặt mật khẩu).

![](https://i.imgur.com/JDW0z9c.png)

* Để xem danh sách truy cập riêng một mạng LAN cụ thể, click **Choice NetCard** và chọn card mạng mong muốn.
* Để cắt mạng truy cập của một thành viên, chọn máy tính của thành viên đó trong danh sách rồi click **Cut off**.
* Để tìm địa chỉ IP, click **Find IP** rồi nhập địa chỉ vào.
* Để xem thông tin về thiết bị đang kết nối, click **Find Type**. Lúc này, một cửa sổ của trình duyệt web sẽ hiện ra với thông tin về thiết bị.

![](https://i.imgur.com/nWDMg7g.png)

* Để thay đổi địa chỉ MAC của một thiết bị, click **Change MAC**.

* Nếu dùng NetCut bản 2.1.0 trở lên thì sẽ có lựa chọn **Protect My Computer** để chống lại lệnh cắt mạng bởi NetCut trên máy khác. Nếu chỉ đơn giản muốn không bị cắt mạng bởi NetCut thì có thể dùng công cụ chuyên biệt NetCut Defender.

![](https://i.imgur.com/T9vROsZ.png)

* Để thay đổi địa chỉ MAC, click **Change MAC**.
* Ngoài ra, ta có thể ngăn việc liên lạc giữa máy tính A với riêng máy tính B bất kỳ. Chọn máy B và bấm nút **>>** để NetCut coi máy B là cổng GateWay, sau đó chọn máy A và bấm **Cut off**. Lý do vì nguyên lý cắt mạng của NetCut là cắt liên lạc với GateWay.

![](https://i.imgur.com/eXUg1nw.png)

## 8. Load Balancing - Cân bằng tải

Load Balancing – Cân Bằng Tải là việc phân bố đồng đều lưu lượng truy cập giữa hai hay nhiều các máy chủ có cùng chức năng trong cùng một hệ thống. Bằng cách đó, sẽ giúp cho hệ thống giảm thiểu tối đa tình trạng một máy chủ bị quá tải và ngưng hoạt động. Hoặc khi một máy chủ gặp sự cố, Cân Bằng Tải sẽ chỉ đạo phân phối công việc của máy chủ đó cho các máy chủ còn lại, đẩy thời gian uptime của hệ thống lên cao nhất và cải thiện năng suất hoạt động tổng thể.

Cân Bằng Tải cũng là cơ chế rất quan trọng trong việc mở rộng quy mô của mạng máy tính. Khi lắp đặt một máy chủ mới vào hệ thống, Cân Bằng Tải sẽ tự động cắt giảm khối lượng công việc từ các máy chủ cũ và chuyển sang máy chủ mới.

Các thuật toán cân bằng tải:

* **Round Robin**: phương thức này lựa chọn server theo tuần tự. Bộ cân bằng tải sẽ chọn server đầu tiên trong danh sách của mình cho yêu cầu đầu tiên, sau đó di chuyển xuống server tiếp theo trong danh sách theo thứ tự và bắt đầu lại từ đầu khi hết danh sách.

* **Least Connections**: hệ thống cân bằng tải sẽ chọn server có ít kết nối nhất và cách này được khuyên dùng khi tốc độ truy cập bị chậm.

* **Source**: bộ cân bằng tải sẽ chọn server dựa trên một chuỗi các IP gốc của yêu cầu, chẳng hạn như IP của người truy cập. Phương thức này đảm bảo một người dùng cụ thể sẽ luôn kết nối với cùng một server.

## 9. Proxy
### 9.1. Proxy là gì?
Proxy là một Internet server làm nhiệm vụ chuyển tiếp thông tin và kiểm soát tạo sự an toàn cho việc truy cập Internet của các máy khách, còn gọi là khách hàng sử dụng dịch vụ Internet. Trạm cài đặt proxy gọi là proxy server. Proxy hay trạm cài đặt proxy có địa chỉ IP và một cổng truy cập cố định. Ví dụ: 123.234.111.222:80. Địa chỉ IP của proxy trong ví dụ là 123.234.111.222 và cổng truy cập là 80.

### 9.2. Chức năng của Proxy

Một số hãng và công ty sử dụng proxy với mục đích: Giúp nhiều máy tính truy cập Internet thông qua một máy tính với tài khoản truy cập nhất định, máy tính này được gọi là Proxy server. Chỉ duy nhất máy Proxy này cần modem và account truy cập Internet, các máy client (các máy trực thuộc) muốn truy cập Internet qua máy này chỉ cần nối mạng LAN tới máy Proxy và truy cập địa chỉ yêu cầu. Những yêu cầu của người sử dụng sẽ qua trung gian proxy server thay thế cho server thật sự mà người sử dụng cần giao tiếp, tại điểm trung gian này công ty kiểm soát được mọi giao tiếp từ trong công ty ra ngoài Internet và từ Internet vào máy của công ty. Sử dụng Proxy, công ty có thể cấm nhân viên truy cập những địa chỉ web không cho phép, cải thiện tốc độ truy cập nhờ sự lưu trữ cục bộ các trang web trong bộ nhớ của proxy server và giấu định danh địa chỉ của mạng nội bộ gây khó khăn cho việc thâm nhập từ bên ngoài vào các máy của công ty.

Đối với các nhà cung cấp dịch vụ đường truyền Internet: Do Internet có nhiều lượng thông tin mà theo quan điểm của từng quốc gia, từng chủng tộc hay địa phương mà các nhà cung cấp dịch vụ Internet khu vực đó sẽ phối hợp sử dụng proxy với kỹ thuật tường lửa để tạo ra một bộ lọc gọi là firewall proxy nhằm ngăn chặn các thông tin độc hại hoặc trái thuần phong mỹ tục đối với quốc gia, chủng tộc hay địa phương đó. Địa chỉ các website mà khách hàng yêu cầu truy cập sẽ được lọc tại bộ lọc này, nếu địa chỉ không bị cấm thì yêu cầu của khách hàng tiếp tục được gửi đi, tới các DNS server của các nhà cung cấp dịch vụ. Firewall proxy sẽ lọc tất cả các thông tin từ Internet gửi vào máy của khách hàng và ngược lại.

