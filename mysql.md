### CÀI ĐẶT MÁY CHỦ MYSQL

Sau khi mọi người tạo thành công VM và mở SSH thì chúng ta tiến hành cài đặt máy chủ Mysql
- Chạy các lệnh dưới đây
```js
// tải các gói thông tin
sudo apt-get update

// Cài đặt mysql kèm apache
sudo apt-get install apache2 php mysql-server

// Kiểm tra trạng thái
systemctl status mysql
```
- Trạng thái mysql chạy thành công

![Alt text](img/mysql1.png?raw=true)

- Khi chạy nó yêu cầu gì cứ chọn `Y` và `Enter`
- Yêu cầu nhập mật khẩu để đăng nhập thì cứ nhập và nhập lại để xác nhận thôi.
- Chờ nó chạy xong thì đăng nhập thử vào mysql xem sao
```
// Đăng nhập mysql
mysql -uroot -padmin

/*
    root    - là tên đăng nhập
    admin   - là mật khẩu do mình đặt  
*/

// LẤy danh sách database
show databases;

// tạo database
create database demo;

// chọn database
use demo;

// lấy danh sách các bảng trong csdl demo
show tables;

// thoát
exit;
```
- Một số thao tác tạo csdl, xem csdl bằng ssh

![Alt text](img/mysql2.png?raw=true)

### CÀI ĐẶT phpMyAdmin (Đối với chưa cài mysql)

- Chạy các lệnh dưới đây
```js
// tải các gói thông tin
sudo apt-get update

// Cài đặt mysql kèm apache
sudo apt-get install apache2 php mysql-server

// cài đặt phpmyadmin
sudo apt-get install phpmyadmin
```

- Sau khi chạy lệnh cài đặt phpmyadmin nó hỏi `Yes/No` thì chọn `Y` và `Enter`
- Nó yêu cầu bọn web server thì chọn apache2 bằng cách bấm `backspace` rồi `Enter`

![Alt text](img/phpmyadmin1.png?raw=true)

- Bấm `Enter`

![Alt text](img/phpmyadmin2.png?raw=true)

- Nhập mật khẩu `admin`

![Alt text](img/phpmyadmin3.png?raw=true)

- Xác nhận mật khẩu

![Alt text](img/phpmyadmin4.png?raw=true)

```
// không biết làm gì nhưng chúng nó bảo chạy
sudo a2enconf phpmyadmin

// Khởi động lại apache2
sudo service apache2 restart
```

- Sau khi cài xong mở vào trình duyệt mở phpmyadmin bằng cách gõ `ip/phpmyadmin`

![Alt text](img/phpmyadmin5.png?raw=true)

- Fix lỗi kiểu file code như trên thì chạy lệnh này ``sudo apt-get install libapache2-mod-php`` và chọn `Y` , ấn `Enter`
- mở lại `ip/phpmyadmin` và đăng nhập với tài khoản `root`

![Alt text](img/phpmyadmin6.png?raw=true)

### HƯỚNG DẪN MỞ CỔNG MYSQL

- Mở file `mysqld.cnf` bằng lệnh sau: ``sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf``
- Tìm dòng `bind-address = 127.0.0.1` sửa thành `bind-address = 0.0.0.0` bấm `Ctr+X`, `Y`, `Enter` để lưu file
- Khởi động lại `mysql` bằng lệnh: ``sudo systemctl restart mysql``
- Kiểm tra cổng `sudo netstat -plunt | grep mysqld` nếu như dưới là oke

![Alt text](img/phpmyadmin7.png?raw=true)

- Update cổng `sudo ufw allow mysql`

#### Check cổng xem đã mở chưa [Tại đây](https://www.yougetsignal.com/tools/open-ports/)
- Nếu như dưới hình là mở rồi còn nếu là `Closed` thì chưa mở cần tạo một Rule mới

![Alt text](img/port.png?raw=true)

#### Thay đổi tài khoản root để có thể kết nối
- Sau khi đăng nhập vào phpmyadmin

![Alt text](img/root.png?raw=true)

- Check vào check box `check all....` và bấm `Go`
