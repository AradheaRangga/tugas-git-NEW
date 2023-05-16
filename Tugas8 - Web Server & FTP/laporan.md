# Laporan Instalasi Web Server dan FTP
### Aradhea Rangga Maulana / 2D4ITB / 3121600057

#### Melakukan Instalasi Web Server
Web Server yang akan digunakan adalah apache. Sehingga untuk melakukan isntalasi menjalankan perintah 

```bash
sudo apt install apache2
```
![](/Foto/install_webserver.jpeg)

Setelah Web Server berhasil diinstall, diperlukan perintah untuk memodifikasi pengaturan firewall untuk mengizinkan akses dari luar ke port web default. Ini dilakukan menggunakan UFW, apabila belum memiliki UFW kita bisa melakukan instalasi terlebih dahulu menggunakan perintah
```bash
sudo apt install ufw
```

Selanjutnya, kita melihat list dari ufw application menggunakan perintah
```bash
sudo ufw app list
```

![](/Foto/ufw_app_list.jpeg)

Selanjutnya melakukan perintah untuk mengijinkan 'WWW' menggunakan perintah
```bash
sudo ufw allow 'WWW'
```

untuk melihat hasilnya enable ufw tersebut dan lihat statusnya, gunakan perintah
```bash
sudo ufw enable
sudo ufw status
```
![](/Foto/ufw_enable.jpeg)

Proses instalasi terakhir adalah melakukan pengecekan terhadap status apache / web server menggunakan perintah
```bash
sudo systemctl status apache2
```
![](/Foto/status_apache2.jpeg)

Untuk memastikan berjalan, kita membuka server ip kita ke browser seperti chrome, mozilla atau edge. Berikut tampilan ketika web server sudah berjalan

![](/Foto/web_server_loaded.jpeg)

#### Melakukan Instalasi PROFTPD

Melakukan instalasi PROFTPD menggunakan perintah 
```bash
sudo apt install proftpd -y
```
![](/Foto/install_proftpd.jpeg)

Kemudian menjalankan PROFTPD menggunakan perintah start dan status untuk melihatnya
```bash
systemctl start proftpd
systemctl status proftpd
 ```
 ![](/Foto/start_proftpd.jpeg)
 
 #### Melakukan instalasi PHP / cek versi PHP
 
 Menggunakan perintah
 ```bash
 sudo apt install php
 php -v
 ```
 ![](/Foto/cek_php.jpeg)
 
 #### Install mysql
 
 Sebelum melakukan instalasi mysql, menambahkan repository mysql dengan cara
 ```bash
 cd tmp
 wget https://dev.mysql.com/get/mysql-apt-config_0.8.22-1_all.deb
 ```
 ![](/Foto/save_package_mysql.jpeg)
 
 Setelah itu, mysql sudah siap untuk diinstal menggunakan dpkg yang berfungsi untuk install, remove dan inspect software packages.
 
 ```bash
 sudo dpkg -i mysql-apt-config*
 ```
 ![](/Foto/dpkg_mysql.jpeg)
 
 Setelah itu, package siap diinstal menggunakan perintah
 ```bash
 sudo apt install mysql-server
 ```
 Dan melakukan pengecekan menggunakan perintah systemctl status
 ```bash
 sudo systemctl status mysql
 ```
 ![](/Foto/status_mysql.jpeg)
 
 Terakhir, menjalankan perintah 
 ```bash
 mysqladmin -u root -p version
 ```
 Perintah mysqladmin -u root -p version digunakan untuk menampilkan versi MySQL yang sedang berjalan. Penjelasan dari opsi yang digunakan dalam perintah tersebut adalah sebagai berikut:

     mysqladmin: perintah untuk mengelola server MySQL melalui baris perintah.
    -u root: opsi untuk menentukan nama pengguna yang akan digunakan saat mengakses server MySQL, di sini digunakan nama pengguna root.
    -p: opsi untuk menanyakan password pengguna saat perintah dieksekusi.
    version: perintah untuk menampilkan informasi versi MySQL yang sedang berjalan.
