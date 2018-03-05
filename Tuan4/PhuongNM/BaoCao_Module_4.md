# MỤC LỤC


## 1. Web Server
### 1.1. Cài đặt, cấu hình Apache
### 1.2. Cài đặt, cấu hình nginx
### 1.3. Các module cơ bản trong Apache, nginx

## 2. Dịch vụ DNS
### 2.1. DNS là gì?
### 2.2. Triển khai DNS sử dụng Bind
### / 2.3. Xây dựng mô hình DNS master-slave

## 3. Dịch vụ MySQL, PHP
### / 3.1. Cài đặt, cấu hình MySQL
### / 3.2. Cài đặt, câu hình PHP
### / 3.3. Các câu lệnh T-SQL
### / 3.4. Cấu hình MySQL Replication

## 4. Dựng website sử dụng Wordpress


***

# 1. Web Server

Web Server là máy chủ cài đặt các chương trình (phần mềm) phục vụ các ứng dụng web. Web Server có khả năng tiếp nhận yêu cầu từ các trình duyệt web và gửi phản hồi đến máy khách những trang web thông qua môi trường mạng Internet qua giao thức HTTP hoặc các giao thức khác.

Mỗi loại Web server chỉ hỗ trợ một số loại tập tin riêng biệt, ví dụ như IIS hỗ trợ một số tập tin như .asp, .aspx, .html, .php,… còn Apache hỗ trợ .php Có nhiều phần mềm Web Server khác nhau như: Apache, Nginx, LiteSpeed, IIS,…

## 1.1. Cài đặt, cấu hình Apache

Apache là phần mềm web server được sử dụng rộng rãi nhất thế giới. Apache được phát triển và duy trì bởi một cộng đồng mã nguồn mở dưới sự bảo trợ của Apache Software Foundation. Apache được phát hành với giấy phép Apache License, là một phần mềm tự do, miễn phí.

Cài đặt: `sudo apt-get install apache2`

Khởi động trình duyệt và gõ địa chỉ http://localhost. Nếu kết quả hiển thị "It Works!" nghĩa là chúng ta đã cài đặt Apache thành công.

![](https://archive.cnx.org/resources/f91d58526c6b7da9f25bfb5c9c87464e488ac641/Ubuntu_Apache2_successful_installation_%202015-04-18.png)

**Chạy Apache**: `sudo /etc/init.d/apache2 start` 

**Dừng Apache**: `sudo /etc/init.d/apache2 stop`

**Khởi động lại Apache**: `sudo /etc/init.d/apache2 restart` 

Nếu không muốn Apache tự khởi động cùng hệ thống, dùng lệnh: `sudo update-rc.d -f apache2 remove`

Nếu muốn làm ngược lại quá trình trên thì dùng lệnh: `sudo update-rc.d apache2 defaults`

**Thay đổi thư mục localhost mặc định**:

Ở chế độ default, Apache sẽ chỉ hoạt động dựa trên thư mục /var/www. Tức là bất cứ file nào được đặt tại đây cũng sẽ hiển thị và truy cập từ đường dẫn http://localhost. 

**VD**: Bạn muốn đường dẫn này sẽ trỏ trực tiếp đến 1 thư mục khác (trong trường hợp này là /home/user/public_html) thì hãy làm theo các bước sau. Đầu tiên, đảm bảo thư mục `/home/user/public_html` tồn tại, tạo 1 trang HTML đơn giản và đặt tên là index.html, đặt ở trong thư mục public_html. 

Gõ lệnh: `sudo gedit /etc/apache2/sites-enabled/000-default.conf`. Thay đổi `DocumentRoot /var/www` thành `DocumentRoot /home/user/public_html`, 

Gõ lệnh: `sudo gedit /etc/apache2/apache2.conf`. Thay đổi `<Directory /var/www/>` thành `<Directory /home/user/public_html/>`.

Lưu thay đổi của 2 file này, rồi khởi động lại Apache: `sudo /etc/init.d/apache2 restart`

**Cài đặt Virtual Host trên Apache**

Virtual Host là một định nghĩa chỉ chức năng nhúng nhiều tên miền vào một địa chỉ IP của một Server. Và bằng cách cài đặt riêng, Server sẽ nhận biết được tên miền nào sẽ hoạt động ở một folder nào. Điều này mang ý nghĩa rất lớn vì chúng ta không cần mỗi tên miền một địa chỉ IP mà chỉ cần một server là có thể nhúng hàng trăm tên miền cùng hoạt động.

VD. Tên miền hello911.com

Bước 1. Thiết lập Virtual Directories

Tạo thư mục trong /var/www

`sudo mkdir -p /var/www/hello911.com/public_html`

Bước 2. Tạo một trang sample cho Virtual Host

Tạo file index.html và chỉnh sửa rồi copy vào thư mục vừa tạo.

Bước 3. Tạo file của Virtual Host

`sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/hello911.com.conf`

Mở file .conf vừa được tạo và thay đổi thông tin như sau:

`<VirtualHost *:80>`

	ServerName hello911.com
	ServerAlias www.hello911.com

	ServerAdmin admin@hello911.com
	DocumentRoot /var/www/hello911.com/public_html

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

`</VirtualHost>`

Sau khi modify file .conf, tiến hành disable cấu hình default và enable cấu hình mới:

`sudo a2dissite 000-default.conf`

`sudo a2ensite hello911.com.conf`

Restart Apache: `sudo service apache2 restart`

Bước 4. Sửa đổi file hosts: `sudo gedit /etc/hosts`

Thêm vào domain: `127.0.1.2	hello911.com`

![](https://i.imgur.com/M7SlU2s.png)

Mở trình duyệt và gõ hello911.com 

![](https://i.imgur.com/Rnjv9G8.png)

## 1.2. Cài đặt, cấu hình nginx

**Cài đặt**: `sudo apt-get install nginx`

**Chạy nginx**: `sudo /etc/init.d/nginx start` 

Khởi động trình duyệt và gõ địa chỉ http://localhost.

![](http://linuxhint.com/wp-content/uploads/2016/04/nginx-img1.jpg)

**Dừng nginx**: `sudo /etc/init.d/nginx stop`

**Khởi động lại nginx**: `sudo /etc/init.d/nginx restart` 


## 1.3. Các module cơ bản trong Apache, nginx
### 1.3.1. Các module trong Apache

Mặc định, sau khi cài đặt, trong Apache có đi kèm sẵn một số module để thực thi nhiệm vụ của một Web Server. Các module này xếp theo thứ tự từng giai đoạn xử lý bao gồm:

*Chuyển đổi giữa URL thành filename trên Server*

mod_userdir: chuyển thư mục home cho từng user

mod_rewrite: điều chỉnh lại đường dẫn URL

*Giai đoạn xác thực/phân quyền*

mod_auth, mod_auth_anon,mod_auth_db, mod_auth_dbm: các kiểu xác thực người dùng

mod_access: kiểm soát truy nhập theo từng host

*Xác định MIME của đối tượng được truy vấn*

mod_mime: xác định loại file bằng cách dựa vào phần mở rộng

mod_mime_magic: xác định loại file bằng cách sử dụng “magic number”

*Chỉnh sửa đường dẫn*

mod_alias: thay thế alias bằng đường dẫn thực trên server

mod_env: thay đổi các tham số hệ thống dựa trên thông tin trong file cấu hình

mod_spelling: tự động sửa lỗi trong URL

*Gửi trả lại dữ liệu cho client*

mod_actions: các script cho từng loại file sẽ được thực thi

mod_asis: gửi file nguyên dạng

mod_autoindex:

mod_cgi: gọi script CGI và trả lại kết quả

mod_include:

mod_dir: xử lý về thư mục

mod_imap: xử lý image-map files

*Ghi log*

mod_log_*: các module log khác nhau

### 1.3.2. Các module trong nginx

***

# 2. Dịch vụ DNS
## 2.1. DNS là gì?

DNS (Domain Name System) là Hệ thống phân giải tên miền, được phát minh vào năm 1984 cho Internet, chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền. Hệ thống tên miền (DNS) là một hệ thống đặt tên theo thứ tự cho máy vi tính, dịch vụ, hoặc bất kỳ nguồn lực tham gia vào Internet. Nó liên kết nhiều thông tin đa dạng với tên miền được gán cho những người tham gia. Quan trọng nhất là, nó chuyển tên miền có ý nghĩa cho con người vào số định danh (nhị phân), liên kết với các trang thiết bị mạng cho các mục đích định vị và địa chỉ hóa các thiết bị khắp thế giới.

Phép tương thường được sử dụng để giải thích hệ thống tên miềnlà, nó phục vụ như một “Danh bạ điện thoại” để tìm trên Internet bằng cách dịch tên máy chủ máy tính thành địa chỉ IP 

Ví dụ, www.example.com dịch thành 208.77.188.166.

Hệ thống tên miền giúp cho nó có thể chỉ định tên miền cho các nhóm người sử dụng Internet trong một cách có ý nghĩa, độc lập với mỗi địa điểm của người sử dụng. Bởi vì điều này, World-Wide Web (WWW) siêu liên kết và trao đổi thông tin trên Internet có thể duy trì ổn định và cố định ngay cả khi định tuyến dòng Internet thay đổi hoặc những người tham gia sử dụng một thiết bị di động. Tên miền internet dễ nhớ hơn các địa chỉ IP như là 208.77.188.166 (IPv4) hoặc 2001: db8: 1f70:: 999: de8: 7648:6 e8 (IPv6).

**Hiện nay hệ thống tên miền được phân thành nhiêu cấp**:

* Gốc (Domain root) : Nó là đỉnh của nhánh cây của tên miền. Nó có thể biểu diễn đơn giản chỉ là dấu chấm “.”
* Tên miền cấp một (Top-level-domain) : gồm vài kí tự xác định một nước, khu vưc hoặc tổ chức. Nó được thể hiện là “.com” , “.edu”,...
* Tên miền cấp hai (Second-level-domain): Nó rất đa dạng rất đa dạng có thể là tên một công ty, một tổ chức hay một cá nhân.
* Tên miền cấp nhỏ hơn (Subdomain): Chia thêm ra của tên miền cấp hai trở xuống thường được sử dụng như chi nhánh, phòng ban của một cơ quan hay chủ đề nào đó.

**Phân loại tên miền:**

* Com: dùng cho các tổ chức thương mại
* Edu: dùng cho các cơ quan giáo dục, trường học
* Net: dùng cho các tổ chức mạng lớn
* Gov: dùng cho các tổ chức chính phủ
* Org: dùng cho các tổ chức khác
* Int: dùng cho các tổ chức quốc tế
* Info: dùng cho việc phục vụ thông tin
* Arpa: tên miền ngược
* Mil: dành cho các tổ chức quân sự, quốc phòng
* Mã các nước trên thế giới tham gia vào mạng internet, các quốc gia này được qui định bằng hai chữ cái theo tiêu chuẩn ISO-3166. (Ví dụ: Việt Nam là .vn, Singapore là sg, Anh là uk,…)

DNS Server
* Là một máy tính có nhiệm vụ là DNS Server, chạy dịch vụ DNS.
* DNS Server là một cơ sở dữ liệu chứa các thông tin về vị trí của các DNS domain và phân giải các truy vấn xuất phát từ các Client.
* DNS Server có thể cung cấp các thông tin do Client yêu cầu, và chuyển đến một DNS Server khác để nhờ phân giải hộ trong trường hợp nó không thể trả lời được các truy vấn về những tên miền không thuộc quyền quản lý và cũng luôn sẵn sàng trả lời các máy chủ khác về các tên miền mà nó quản lý. DNS Server lưu thông tin của Zone, truy vấn và trả kết quả cho DNS Client.

**Các kiểu tên miền**

Một tên miền được chia ra thành nhiều cấp bậc:

* gTLD (Generic Top Level Domain) – tên miền kết thúc bằng .com, .net, .org, .gov, .edu và .name.
* ccTLD (Country Code Top Level Domain) – tên miền riêng của mỗi quốc gia (ví dụ .il, .ru, .uk, ,us, .cn, .vn).
* Infrastructure TLD – Xử lý và điều hướng chuyển đổi từ địa chỉ IP sang tên miền, Ví dụ IPv4 48.199.81.in-addr.arpa. Sử dụng trong bản ghi PTR (được giải thích bên dưới).
* Cấp 2ld, 3ld, 4ld – Ví dụ www.somedomain.co.uk, uk là ccTLD, co là 2ld, somedomain là 3ld và www là 4ld.

**Cách thức hoạt động của DNS Server**

![](http://cloudvpsgiare.com/wp-content/uploads/2015/07/dnswhite.png)

VD. Bạn muốn truy cập `google.com` trên trình duyệt web.

Nếu hệ điều hành hoặc trình duyệt web của bạn không tìm được địa chỉ IP trong bộ nhớ đệm, nó sẽ gửi câu truy vấn đến Resolver Server (ISP của bạn).

Resolver Server sẽ tìm trong bộ nhớ đệm của nó xem có địa chỉ IP bạn cần hay không. Nếu không thấy, nó sẽ gửi câu truy vấn đến cấp tiếp theo, Root Server.

Root Server là phân cấp cao nhất trong DNS. Root Server không biết địa chỉ IP là gì, nhưng nó biết nơi mà Resolver có thể đến để tìm địa chỉ IP. Nó chỉ Resolver đến TLD Server (Top-Level Domain Server), nơi quản lý tên miền ".com".

Resolver sẽ hỏi TLD Server: "Địa chỉ IP của `google.com` là gì?". TLD Server sẽ không biết IP của `google.com` là gì. Nó sẽ chỉ Resolver tới Name Server.

Giờ Resolver sẽ hỏi Name Server. Name Server chịu trách nhiệm về tên miền, bao gồm IP. Khi nhận được câu truy vấn, Name Server sẽ trả về cho Resolver địa chỉ IP của `google.com`.

Resolver sẽ nói cho máy tính của bạn biết điều đó, giờ bạn có thể truy cập trang web.

## 2.2. Triển khai DNS sử dụng Bind

Cài đặt: `sudo apt-get install bind9`

**Cấu hình**:

* *Thiết lập IP tĩnh cho máy:*

(VD. IP tĩnh cho máy là `192.168.10.2`)

`sudo ifconfig enp0s3 192.168.10.2 netmask 255.255.255.0`

`sudo route add default gw 192.168.10.1`

* *Khởi động lại dịch vụ mạng*:

`sudo /etc/init.d/network restart`

* *Cấu hình file named.conf.options:*

`sudo gedit /etc/bin/named.conf.options`

Thêm `forwarders` (dùng để trỏ DNS Server ra bên ngoài để phân giải tên miền):

`	forwarders {
		8.8.8.8;
		8.8.4.4;
	}	`

* *Cấu hình file named.conf.local:*

`sudo gedit /etc/bin/named.conf.local`

Thêm zone phân giải thuận (tên miền => địa chỉ) và zone phân giải nghịch (địa chỉ => tên miền):

(VD tên miền là `goodday.com`)

![](https://i.imgur.com/q7yDKtF.png)

File của zone thuận là `/etc/bin/db.forward.com`, file của zone nghịch là `/etc/bin/db.reverse.com`.

* *Tạo file `db.forward.com` bằng cách copy file `db.local` từ `/etc/bind/`, chỉnh sửa hostname, thêm các tên miền mới và địa chỉ*

![](https://i.imgur.com/hNa5RkW.png)

* *Tạo file `db.reserve.com` bằng cách copy file `db.127` từ `/etc/bind/`, chỉnh sửa hostname, thêm các tên miền mới và địa chỉ*

![](https://i.imgur.com/KAudkJn.png)

* *Sửa file `/etc/resolv.conf`*

` nameserver 192.68.10.2`

` search goodday.com`

* *Khởi động lại bind*: `sudo /etc/init.d/bind restart`

* *Dùng lệnh `nslookup` để kiểm tra hoạt động của DNS*

![](https://i.imgur.com/2DnsOvS.png)

* *Cấu hình IP tĩnh cho máy Client và nhập địa chỉ của DNS Server*

![](https://i.imgur.com/hlh5nfP.png)

![](https://i.imgur.com/D02TORx.png)

* *Trên máy Client, dùng lệnh `nslookup` để kiểm tra hoạt động của DNS*

![](https://i.imgur.com/tSECgec.png)

## / 2.3. Xây dựng mô hình DNS master-slave


## 3. Dịch vụ MySQL, PHP
### 3.1. Cài đặt, cấu hình MySQL

**Cài đặt**: `sudo apt-get install mysql-server5.7`

**Khởi động MySQL bằng tài khoản root**: `/usr/bin/mysql -u root -p`

### 3.2. Cài đặt, câu hình PHP

**Cài đặt**: `sudo apt-get install php libapache2-mod-php php-mcrypt`


### 3.3. Các câu lệnh T-SQL

Các câu lệnh luôn kết thúc bằng dấu ";".

**Nhóm lệnh thao tác dữ liệu – DML**

Đây là nhóm lệnh phổ biến được dùng nhiều trong các phần mềm để thao tác đến các dữ liệu. Nhóm này bao gồm 4 lệnh: 

![](https://tuandc.com/wp-content/uploads/2017/06/DML-SQL.png)

*Lệnh SELECT trong SQL Server*

* Lệnh được sử dụng để truy xuất các tập kết quả của các cột hay các hàng trong CSDL.
* Cú pháp: `SELECT tên_cột FROM Tên_bảng`
* Trong lệnh select bạn có thể tạo ra các trường tính toán hoặc nối các bảng dữ liệu lại với nhau để truy vấn. ví dụ mình có 2 bảng sinh_vien và diem mình sẽ nối như sau: SELECT * FROM sinh_vien join diem ON sinh_vien.id = diem.id_sinhvien.
* Trong SELECT còn có 2 phép Join là Inner join (chỉ hiển thị các dòng có các trường bằng nhau) và outer join (hiển thị cả những dòng không có trường bằng nhau).
* Trong phần tên_cột bạn có thể thêm AS để đặt trên cho cột đó ví dụ SELECT (toan+ly) AS diemtoanly FROM sinh_vien join diem ON sinh_vien.id = diem.id_sinhvien.

*Lệnh INSERT trong SQL Server* 

* Để thêm dữ liệu vào CSDL bạn cần một câu lệnh để làm việc này và đó là lệnh INSERT.
* Cú pháp: `INSERT INTO Tên_bảng (tên_các_trường) VALUES (giá_trị_thêm)`
* Trong lệnh này nếu muốn thêm vào dữ liệu có hỗ trợ chữ tiếng việt có đấu bạn phải thêm chữ N phía trước. Ví dụ: `INSERT INTO sinh_vien (ten_sinh_vien, tuoi) VALUES (N"Tuấn",18)`


*Lệnh UPDATE trong SQL Server*

* Để cập nhật, thay đổi dữ liệu cần sử dụng một câu lệnh có tên UPDATE.
* Cú pháp: UPDATE Tên_bảng SET tên_trường = giá_trị WHERE điều kiện.
* Với lệnh này bạn thường phải đưa ra điều kiện để xác định, thông thường là trường ID, ví dụ: `UPDATE sinh_vien SET ten = N"Tuấn ĐC" WHERE id=1`

*Lệnh DELETE trong SQL Server*

* Mặc dù lệnh DELETE rất ít được sử dụng trong các vấn đề yêu cầu sự toàn vẹn và không để mất mát dữ liệu, nhưng lệnh này cũng được đưa ra như một vấn đề tất yếu.
* Cú pháp: `DELETE FROM tên_bảng WHERE điều_kiện`
* Trong lệnh này bạn không cần đưa vào trường nhưng bạn cần đưa vào điều kiện để xóa. Nếu không có điều kiện dữ liệu trong bảng có thể bị xóa hết.

*Tạo Procedure trong SQL Server*

* Procedure là thủ tục được lưu trữ sẵn trong csdl. Nó được sử dụng để hạng chế phần mềm truy vấn thẳng để các bảng hay trường của csdl, thay vào đó chỉ cần truyền đến các thông số hoặc gửi yêu cầu.
* Cú pháp: `CREATE PROCEDURE tên_thủ_tục @Tham_số [kiểu_dữ_liệu] AS Lệnh_DML`
* Cú pháp thực thi: EXEC tên_thủ_tục 'Tham số'.
* VD: `CREATE PROCEDURE lay_du_lieu_sv @so_luong int AS SELECT TOP @so_luong FROM ten_sinh_vien`

**Nhóm lệnh định nghĩa dữ liệu – DDL**

![](https://tuandc.com/wp-content/uploads/2017/06/DDL-SQL.png)

Nhóm lệnh này rất ít được sử dụng bởi các phần mềm, tuy nhiên chúng là những lệnh rất quan trọng có thể làm thay đổi csdl ở mức lớn nhất. Nhóm lệnh này thường chỉ được sử dụng bởi các Database Admin (DBA).

*Lệnh CREATE DATABASE trong SQL Server*

* Trong một hệ quản trị csdl có chứa rất nhiều csdl. các hệ hỗ trợ những đoạn lệnh khác nhau để tạo ra một database. Trong SQL Server cũng có câu lệnh để làm việc này.
* Cú pháp: `CREATE DATABASE tên_csdl`

*Lệnh CREATE TABLE trong SQL Server*

* Chúng ta đã biết trong một database sẽ có nhiều bảng (table), để tạo ra các bảng ta có câu lệnh để tạo bảng.
* Cú pháp: `CREATE TABLE tên_bảng (tên_cột_1 [kiểu_dữ_liệu],  tên_cột_2 [kiểu_dữ_liệu],....)`

*Lệnh ALTER TABLE trong SQL Server*

* SQL hỗ trợ các lệnh thay đổi bảng sau khi đã tạo như thêm (ADD) các trường (cột), Xóa (DROP) các trường, Sửa (ALTER) các trường.
* Cú pháp thêm cột vào bảng: `ALTER TABLE Tên_bảng ADD Tên_cột [kiểu_dữ_liệu]`
* Cú pháp xóa một cột trong bảng: `ALTER TABLE Tên_bảng DROP COLUMN Tên_cột`
* Cú pháp sửa một cột trong bảng: `ALTER TABLE Tên_bảng ALTER COLUMN Tên_cột [kiểu_dữ_liệu]`

*Lệnh DROP TABLE trong SQL Server*

* Mặc dù không khuyến khích nhưng nó vẫn thường xuyên được sử dụng để loại bỏ đi các bảng thừa. Mặc dù có thể dùng Management studio (SSMS) để thực hiện việc này nhanh hơn nhưng với lệnh bạn có thể thao tác nhanh hơn.
* Cú pháp: `DROP TABLE Tên_bảng`

## / 3.4. Cấu hình MySQL Replication

# 4. Dựng website sử dụng Wordpress

## 4.1. Cài đặt Wordpress

**Bước 1 — Tạo MySQL Database và User cho WordPress**

Login vào mysql với lệnh: `mysql -u root -p`

Tạo cơ sở dữ liệu cho Wordpress:

`CREATE DATABASE wordpress;`

Tạo user để quản lí riêng cơ sở dữ liệu này (để cho an toàn, bạn không nên dùng cùng user của CSDL khác như Koha, đặc biệt không nên dùng root user):

`CREATE USER wordpressuser@localhost IDENTIFIED BY 'password';`

Gán quyền quản lí cơ sở dữ liệu "wordpress" cho user này:

`GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;`

Thêm câu lệnh sau đảm bảo các thay đổi có hiệu lực:

`FLUSH PRIVILEGES;`

Thoát khỏi mysql, về Ubuntu: `exit`

**Bước 2: Tải Wordpress**

`cd /var/www/`

`sudo wget http://wordpress.org/latest.tar.gz`

`sudo tar xzvf latest.tar.gz`

**Bước 3: Config Wordpress**

Tiến vào thư mục gốc của Wordpress.

Tạo ra file wp-config.php dành cho wordpress (chứa user, password của cơ sở dữ liệu mà bạn tạo ở bước 1):

`sudo cp wp-config-sample.php wp-config.php`

Mở file wp-config.php và chỉnh sửa:

`define('DB_PASSWORD', 'password');`
`define('DB_USER', 'wordpressuser');`
`define('DB_PASSWORD', 'password');`

**Bước 4: Cài đặt Wordpress**

Truy cập `<tên website>/wordpress`

![](https://assets.digitalocean.com/articles/wordpress_1404/initial_config.png)

![](https://assets.digitalocean.com/articles/wordpress_1404/confirm_install.png)

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-6-nguyenhuuhoang.com_.jpg)

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-7-nguyenhuuhoang.com_.jpg)

