### CÀI ĐẶT MÁY CHỦ APACHE2

Sau khi mọi người tạo thành công VM và mở SSH thì chúng ta tiến hành cài đặt máy chủ apache2

```js
// tải các gói thông tin
sudo apt-get update

// Cài đặt apache
sudo apt-get install apache2

// Khỏi động apache
sudo systemctl start apache2

// Kiểm tra trạng thái apache
sudo systemctl status apache2
```

### CÀI ĐẶT PHP 7.3

```
// Kiểm tra phiên bản php xem có chưa
php -v

// Tải gói chưa php
sudo add-apt-repository ppa:ondrej/php

// cập nhật lại toàn bộ gói tin
sudo apt-get update

// cài gói php 7.3
sudo apt-get install php7.3

// Cài các gói mở rộng của php 7.3
sudo apt install php7.3-cli php7.3-fpm php7.3-json php7.3-pdo php7.3-mysql php7.3-zip php7.3-gd  php7.3-mbstring php7.3-curl php7.3-xml php7.3-bcmath php7.3-json

// Xác nhận phiên bản đã cài đặt của phần mở rộng PHP
sudo apt policy php7.3-cli

// Khởi động lại apache
sudo systemctl restart apache2
```
