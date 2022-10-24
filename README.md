# Jarkom-Modul-2-B11-2022

### Kelompok B11

| **No** | **Nama**              | **NRP**    |
| ------ | --------------------- | ---------- |
| 1      | Cahyadi Surya Nugraha | 5025201184 |
| 2      | Sarah Alissa Putri    | 5025201272 |
| 3      | Ravin Pradhitya       | 5025201068 |

### List

1. [Soal 1](#Question-1)
2. [Soal 2](#Question-2)
3. [Soal 3](#Question-3)
4. [Soal 4](#Question-4)
5. [Soal 5](#Question-5)
6. [Soal 6](#Question-6)
7. [Soal 7](#Question-7)
8. [Soal 8](#Question-8)
9. [Soal 9](#Question-9)
10. [Soal 10](#Question-10)
11. [Soal 11](#Question-11)
12. [Soal 12](#Question-12)
13. [Soal 13](#Question-13)
14. [Soal 14](#Question-14)
15. [Soal 15](#Question-15)
16. [Soal 16](#Question-16)
17. [Soal 17](#Question-17)


## Topografi
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/topografi.PNG)


## Konfigurasi
- Ostania
    
    ```
    auto eth0
    iface eth0 inet dhcp

    auto eth1
    iface eth1 inet static
    	address 192.178.1.1
    	netmask 255.255.255.0

    auto eth2
    iface eth2 inet static
    	address 192.178.2.1
    	netmask 255.255.255.0

    auto eth3
    iface eth3 inet static
    	address 192.178.3.1
    	netmask 255.255.255.0
    ```

- SSS
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.1.2
    	netmask 255.255.255.0
    	gateway 192.178.1.1
    ```

- Garden
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.1.3
    	netmask 255.255.255.0
    	gateway 192.178.1.1
    ```

- WISE
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.3.2
    	netmask 255.255.255.0
    	gateway 192.178.3.1
    ```

- Berlint
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.2.2
    	netmask 255.255.255.0
    	gateway 192.178.2.1
    ```

- Eden
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.2.3
    	netmask 255.255.255.0
    	gateway 192.178.2.1
    ```

    
## Initial Script
Pada initial project, kami mengubah `root/.bashrc` masing-masing node sehingga saat dijalankan akan langsung melakukan command berikut ini
- Ostania
    
    ```
    # ~/.bashrc: executed by bash(1) for non-login shells.
    # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
    # for examples
    ...
    apt-get update
    apt-get install nano
    iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.178.0.0/16
    ```

- Eden
    
    ```
    # ~/.bashrc: executed by bash(1) for non-login shells.
    # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
    # for examples
    ...
    echo 'nameserver 192.168.122.1' > /etc/resolv.conf
    apt-get update
    apt-get install nano
    apt-get install dnsutils
    apt-get install bind9 -y
    apt-get install lynx
    apt-get install apache2
    apt-get install libapache2-mod-php7.0
    service apache2 start
    apt-get install wget -y
    apt-get install unzip -y
    apt-get install php
    echo -e "\n\nPHP Version:"
    php -v
    cd /var/www
    wget 'https://github.com/Chroax/Jarkom-Modul-2-B11-2022/raw/main/resources/wise.zip'
    unzip wise.zip
    wget 'https://github.com/Chroax/Jarkom-Modul-2-B11-2022/raw/main/resources/strix.operation.wise.zip'
    unzip strix.operation.wise.zip
    wget 'https://github.com/Chroax/Jarkom-Modul-2-B11-2022/raw/main/resources/eden.wise.zip'
    unzip eden.wise.zip
    cd ~
    ```

- Lainnya
    
    ```
    # ~/.bashrc: executed by bash(1) for non-login shells.
    # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
    # for examples
    ...
    echo 'nameserver 192.168.122.1' > /etc/resolv.conf
    apt-get update
    apt-get install nano
    apt-get install dnsutils
    apt-get install bind9 -y
    apt-get install lynx
    apt-get install apache2
    service apache2 start
    apt-get install php
    echo -e "\n\nPHP Version:"
    php -v
    ```

## Question 1
> WISE akan dijadikan sebagai DNS Master, Berlint akan dijadikan DNS Slave, dan Eden akan digunakan sebagai Web Server. Terdapat 2 Client yaitu SSS, dan Garden. Semua node terhubung pada router Ostania, sehingga dapat mengakses internet
### Script
- Semua Node
    
    ```
    ```
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture1.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture2.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture3.PNG)


## Question 2
> Untuk mempermudah mendapatkan informasi mengenai misi dari Handler, bantulah Loid membuat website utama dengan akses wise.yyy.com dengan alias www.wise.yyy.com pada folder wise
### Script
- WISE
    
    ```
    ```

- SSS & Garden
    
    ```
    ```    
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal2/Capture1.PNG)


## Question 3
> Setelah itu ia juga ingin membuat subdomain eden.wise.yyy.com dengan alias www.eden.wise.yyy.com yang diatur DNS-nya di WISE dan mengarah ke Eden
### Script
- WISE
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal3/Capture1.PNG)


## Question 4
> Buat juga reverse domain untuk domain utama
### Script
- WISE
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal4/Capture1.PNG)


## Question 5
> Agar dapat tetap dihubungi jika server WISE bermasalah, buatlah juga Berlint sebagai DNS Slave untuk domain utama
### Script
- WISE
    
    ```
    ```

- Berlint
    
    ```
    ```

- WISE
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal5/Capture1.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal5/Capture2.PNG)


## Question 6
> Karena banyak informasi dari Handler, buatlah subdomain yang khusus untuk operation yaitu operation.wise.yyy.com dengan alias www.operation.wise.yyy.com yang didelegasikan dari WISE ke Berlint dengan IP menuju ke Eden dalam folder operation 
### Script
- WISE
    
    ```
    ```

- Berlint
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal6/Capture1.PNG)


## Question 7
> Untuk informasi yang lebih spesifik mengenai Operation Strix, buatlah subdomain melalui Berlint dengan akses strix.operation.wise.yyy.com dengan alias www.strix.operation.wise.yyy.com yang mengarah ke Eden
### Script
- Berlint
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal7/Capture1.PNG)


## Question 8
> Setelah melakukan konfigurasi server, maka dilakukan konfigurasi Webserver. Pertama dengan webserver www.wise.yyy.com. Pertama, Loid membutuhkan webserver dengan DocumentRoot pada /var/www/wise.yyy.com
### Script
- WISE
    
    ```
    ```

- Eden
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal8/Capture1.PNG)


## Question 9
> Setelah itu, Loid juga membutuhkan agar url www.wise.yyy.com/index.php/home dapat menjadi menjadi www.wise.yyy.com/home
### Script
- Eden
    
    ```
    ```

- SSS & Garden
    
    ```
    ``` 
### Test
![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal9/Capture1.PNG)


## Question 10
>


## Question 11
>


## Question 12
>


## Question 13
>


## Question 14
>


## Question 15
>


## Question 16
>


## Question 17
>
 