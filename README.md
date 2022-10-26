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

- **Ostania**
    
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

- **SSS**
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.1.2
    	netmask 255.255.255.0
    	gateway 192.178.1.1
    ```

- **Garden**
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.1.3
    	netmask 255.255.255.0
    	gateway 192.178.1.1
    ```

- **WISE**
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.3.2
    	netmask 255.255.255.0
    	gateway 192.178.3.1
    ```

- **Berlint**
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.2.2
    	netmask 255.255.255.0
    	gateway 192.178.2.1
    ```

- **Eden**
    
    ```
    auto eth0
    iface eth0 inet static
    	address 192.178.2.3
    	netmask 255.255.255.0
    	gateway 192.178.2.1
    ```

## Initial Script

Pada initial project, kami mengubah `root/.bashrc` masing-masing node sehingga saat dijalankan akan langsung melakukan command berikut ini

- **Ostania**
    
    ```
    # ~/.bashrc: executed by bash(1) for non-login shells.
    # see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
    # for examples
    ...
    apt-get update
    apt-get install nano
    iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.178.0.0/16
    ```

- **Eden**
    
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

- **Lainnya**
    
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

Setelah berhasil melakukan konfigurasi dan selesai menjalankan start command, kita akan melakukan pengecekan internet untuk semua node dengan melakukan ping terhadap `google.com`.

> Script dibawah ini terdapat pada **root semua node**, untuk menjalankannya bisa langsung dengan melakukan command `bash no1.sh`

- **Semua Node** 
    ```
    echo -e "--------------------------------------------------------------------------------------"
    echo " TES AKSES INTERNET:"
    ping google.com -c 3
    echo -e "--------------------------------------------------------------------------------------"
    ```

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture1.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture2.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal1/Capture3.PNG)


## Question 2

> Untuk mempermudah mendapatkan informasi mengenai misi dari Handler, bantulah Loid membuat website utama dengan akses wise.yyy.com dengan alias www.wise.yyy.com pada folder wise

### Script

Pertama-tama pada node WISE (Master), kita harus konfigurasikan `/etc/bind/named.conf.local` dengan domain wise.B11.com. Setelah itu buatlah direktori `/etc/bind/wise`. Kemudian buatlah file `wise.B11.com` pada direktori yang baru saja dibuat dan isilah file sesuai dengan contoh dibawah ini (setelah command `mkdir /etc/bind/wise`). Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash no2.sh`

- WISE
    ```
    echo -e '
    zone "wise.B11.com" {
            type master;
            file "/etc/bind/wise/wise.B11.com";
    };
     ' > /etc/bind/named.conf.local

    mkdir /etc/bind/wise

    echo -e '
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     wise.B11.com. root.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      wise.B11.com.
    @       IN      A       192.178.3.2     ; IP WISE
    www     IN      CNAME   wise.B11.com.
    @       IN      AAAA    ::1
    ' > /etc/bind/wise/wise.B11.com

    service bind9 restart
    ```

Kemudian pada node client (SSS & Garden), kita harus lakukan setting nameserver yang ada. Kemudian kita akan mengecek dengan melakukan `host -t CNAME www.wise.B11.com` dan `www.wise.B11.com -c 3`.

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no2.sh`

- SSS & Garden
    
    ```
    echo -e '
    nameserver 192.178.3.2          ; IP WISE
    nameserver 192.168.122.1
    ' > /etc/resolv.conf

    echo -e "--------------------------------------------------------------------------------------"
    host -t CNAME www.wise.B11.com
    echo "TEST ALIAS (CNAME) (alias dari wise.B11.com)"
    echo -e "--------------------------------------------------------------------------------------"
    echo "TEST ARAH PING www.wise.B11.com (mengarah ke host IP WISE)"
    ping www.wise.B11.com -c 3
    echo -e "--------------------------------------------------------------------------------------"
    ```

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal2/Capture1.PNG)


## Question 3

> Setelah itu ia juga ingin membuat subdomain eden.wise.yyy.com dengan alias www.eden.wise.yyy.com yang diatur DNS-nya di WISE dan mengarah ke Eden

### Script

Untuk membuat subdomain kita harus menambahkan `eden            IN      A       192.178.2.3             ; IP Eden` pada file `/etc/bind/wise/wise.B11.com`. Kemudian tambahkan juga `www.eden        IN      CNAME   eden.wise.B11.com.` pada file yang sama. Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash no3.sh`

- WISE
    
    ```
    echo -e '
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     wise.B11.com. root.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @               IN      NS      wise.B11.com.
    @               IN      A       192.178.3.2             ; IP WISE
    www             IN      CNAME   wise.B11.com.
    eden            IN      A       192.178.2.3             ; IP Eden
    www.eden        IN      CNAME   eden.wise.B11.com.
    @               IN      AAAA    ::1
    ' > /etc/bind/wise/wise.B11.com

    service bind9 restart
    ```

Kemudian kita akan mengecek dengan melakukan test ping `ping eden.wise.B11.com -c 3` dan test cname `host -t CNAME www.eden.wise.B11.com`.

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no3.sh`

- SSS & Garden
    
    ```
    echo -e "--------------------------------------------------------------------------------------"
    echo "TEST PING SUBDOMAIN (mengarah ke host IP Eden)"
    ping eden.wise.B11.com -c 3
    echo -e "--------------------------------------------------------------------------------------"
    echo "TEST ALIAS (CNAME) (alias dari  eden.wise.B11.com)"
    host -t CNAME www.eden.wise.B11.com
    echo -e "--------------------------------------------------------------------------------------"
    ``` 

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal3/Capture1.PNG)


## Question 4

> Buat juga reverse domain untuk domain utama

### Script

Untuk membuat reverse domain kita memerlukan tambahan Zone Baru, tambahkan zone tersebut pada file `/etc/bind/named.conf.local` sesuai dengan ip kita.  Kemudian buatlah sebuah file pada direktori `/etc/bind/wise/` dengan nama file `"3 byte reverse ip kita".in-addr.arpa`. Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash no4.sh`

- WISE
    
    ```
    echo -e '
    zone "wise.B11.com" {
            type master;
            file "/etc/bind/wise/wise.B11.com";
    };

    zone "3.178.192.in-addr.arpa" {
        type master;
        file "/etc/bind/wise/3.178.192.in-addr.arpa";
    };

     ' > /etc/bind/named.conf.local

    echo -e '
    $TTL    604800
    @       IN      SOA     wise.B11.com. root.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    3.178.192.in-addr.arpa.    IN     NS      wise.B11.com.
    2                          IN     PTR     wise.B11.com.
    ' > /etc/bind/wise/3.178.192.in-addr.arpa

    service bind9 restart
    ```

Kemudian kita akan mengecek reverse domain dengan melakukan `host -t PTR 192.178.3.2`.

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no4.sh`

- SSS & Garden
    
    ```
    echo -e "--------------------------------------------------------------------------------------"
    echo "TES REVERSE DOMAIN (point to wise.b11.com.)"
    host -t PTR 192.178.3.2
    echo -e "--------------------------------------------------------------------------------------"
    ``` 

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal4/Capture1.PNG)


## Question 5

> Agar dapat tetap dihubungi jika server WISE bermasalah, buatlah juga Berlint sebagai DNS Slave untuk domain utama

### Script

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash no5.sh`

- WISE
    
    ```
    echo -e '
    zone "wise.B11.com" {
            type master;
            notify yes;
            also-notify { 192.178.2.2; }; // Masukan IP Berlint tanpa tanda petik
            allow-transfer { 192.178.2.2; }; // Masukan IP Berlint tanpa tanda petik
            file "/etc/bind/wise/wise.B11.com";
    };

    zone "3.178.192.in-addr.arpa" {
        type master;
        file "/etc/bind/wise/3.178.192.in-addr.arpa";
    };

     ' > /etc/bind/named.conf.local

    service bind9 restart
    ```

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node Berlint**, untuk menjalankannya bisa langsung dengan melakukan command `bash no5.sh`

- Berlint
    
    ```
    echo -e '
    zone "wise.B11.com" {
        type slave;
        masters { 192.178.3.2; }; // Masukan IP WISE tanpa tanda petik
        file "/var/lib/bind/wise.B11.com";
    };
     ' > /etc/bind/named.conf.local
    
    service bind9 restart
    ```

Pada server WISE kita akan mematikan service bind9 dengan command `service bind9 stop`

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no5test.sh`

- WISE
    
    ```
    echo -e "--------------------------------------------------------------------------------------"
    echo "DNS MASTER STOP"
    service bind9 stop
    echo -e "--------------------------------------------------------------------------------------"
    ```

Kemudian pada node client (SSS & Garden), kita harus menambahkan nameserver Berlint. Kemudian setelah mematikan server WISE, kita akan mengecek dengan melakukan `ping wise.B11.com -c 3`

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no5.sh`

- SSS & Garden
    
    ```
    echo -e '
    nameserver 192.178.3.2          ; IP WISE
    nameserver 192.178.2.2          ; IP Berlint
    nameserver 192.168.122.1
    ' > /etc/resolv.conf

    echo -e "--------------------------------------------------------------------------------------"
    echo "TES SLAVE DNS, DNS MASTER DI STOP"
    ping wise.B11.com -c 3
    echo -e "--------------------------------------------------------------------------------------"
    ``` 

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal5/Capture1.PNG)

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal5/Capture2.PNG)


## Question 6

> Karena banyak informasi dari Handler, buatlah subdomain yang khusus untuk operation yaitu operation.wise.yyy.com dengan alias www.operation.wise.yyy.com yang didelegasikan dari WISE ke Berlint dengan IP menuju ke Eden dalam folder operation 

### Script

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node WISE**, untuk menjalankannya bisa langsung dengan melakukan command `bash no6.sh`

- WISE
    
    ```
    echo -e '
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     wise.B11.com. root.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @                       IN      NS      wise.B11.com.
    @                       IN      A       192.178.3.2             ; IP WISE
    www                     IN      CNAME   wise.B11.com.
    eden                    IN      A       192.178.2.3             ; IP Eden
    www.eden                IN      CNAME   eden.wise.B11.com.      ; IP Eden
    ns1                     IN      A       192.178.2.2             ; IP Berlint
    operation               IN      NS      ns1
    @                       IN      AAAA    ::1
    ' > /etc/bind/wise/wise.B11.com

    echo -e '
    zone "wise.B11.com" {
            type master;
            notify yes;
            also-notify { 192.178.2.2; }; // Masukan IP Berlint tanpa tanda petik
            allow-transfer { 192.178.2.2; }; // Masukan IP Berlint tanpa tanda petik
            file "/etc/bind/wise/wise.B11.com";
    };

    zone "3.178.192.in-addr.arpa" {
        type master;
        file "/etc/bind/wise/3.178.192.in-addr.arpa";
    };
    ' > /etc/bind/named.conf.local

    echo -e '
    options {
            directory "/var/cache/bind";

            // If there is a firewall between you and nameservers you want
            // to talk to, you may need to fix the firewall to allow multiple
            // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
               forwarders {
                    192.168.122.1;
               };

            //========================================================================
            // If BIND logs error messages about the root key being expired,
            // you will need to update your keys.  See https://www.isc.org/bind-keys
            //========================================================================
            //dnssec-validation auto;
            allow-query{any;};
            auth-nxdomain no;    # conform to RFC1035
            listen-on-v6 { any; };
    };
    ' > /etc/bind/named.conf.options

    service bind9 restart    
    ```

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node Berlint**, untuk menjalankannya bisa langsung dengan melakukan command `bash no6.sh`

- Berlint
    
    ```
    echo -e '
    options {
            directory "/var/cache/bind";

            // If there is a firewall between you and nameservers you want
            // to talk to, you may need to fix the firewall to allow multiple
            // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
            // forwarders {
            //      0.0.0.0;
            // };

            //========================================================================
            // If BIND logs error messages about the root key being expired,
            // you will need to update your keys.  See https://www.isc.org/bind-keys
            //========================================================================
            //dnssec-validation auto;
            allow-query{any;};
            auth-nxdomain no;    # conform to RFC1035
            listen-on-v6 { any; };
    };
    ' > /etc/bind/named.conf.options

    echo -e '
    zone "wise.B11.com" {
        type slave;
        masters { 192.178.3.2; }; // Masukan IP WISE tanpa tanda petik
        file "/var/lib/bind/wise.B11.com";
    };
    zone "operation.wise.B11.com" {
            type master;
            file "/etc/bind/operation/operation.wise.B11.com";
    };
    ' > /etc/bind/named.conf.local

    mkdir /etc/bind/operation

    echo -e '
    $TTL    604800
    @       IN      SOA     operation.wise.B11.com. root.operation.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @               IN      NS          operation.wise.B11.com.
    @               IN      A           192.178.2.3                 ; IP Eden
    www             IN      CNAME       operation.wise.B11.com.
    ' > /etc/bind/operation/operation.wise.B11.com

    service bind9 restart
    ```

Kemudian kita akan mengecek dengan melakukan test ping `ping operation.wise.B11.com -c 3` dan test cname `host -t CNAME www.operation.wise.B11.com`.

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no6.sh`

- SSS & Garden
    
    ```
    echo "----------------------------------------------------------------"
    echo "TEST PING DELEGASI SUBDOMAIN (mengarah ke host IP Eden)"
    ping operation.wise.B11.com -c 3
    echo "----------------------------------------------------------------"
    echo "TEST ALIAS (CNAME) (alias dari operation.wise.B11.com)"
    host -t CNAME www.operation.wise.B11.com
    echo "----------------------------------------------------------------"
    ``` 

### Test

![image](https://raw.githubusercontent.com/Chroax/Jarkom-Modul-2-B11-2022/main/image/Soal6/Capture1.PNG)


## Question 7

> Untuk informasi yang lebih spesifik mengenai Operation Strix, buatlah subdomain melalui Berlint dengan akses strix.operation.wise.yyy.com dengan alias www.strix.operation.wise.yyy.com yang mengarah ke Eden

### Script

Setelah selesai maka kita harus merestart bind9 dengan command `service bind9 restart`.

> Script dibawah ini terdapat pada **root node Berlint**, untuk menjalankannya bisa langsung dengan melakukan command `bash no7.sh`

- Berlint
    
    ```
    echo -e '
    $TTL    604800
    @       IN      SOA     operation.wise.B11.com. root.operation.wise.B11.com. (
                                  2         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @               IN      NS              operation.wise.B11.com.
    @               IN      A               192.178.2.3                     ; IP Eden
    www             IN      CNAME           operation.wise.B11.com.
    strix           IN      A               192.178.2.3                     ; IP Eden
    www.strix       IN      CNAME           strix.operation.wise.B11.com.
    ' > /etc/bind/operation/operation.wise.B11.com

    service bind9 restart
    ```

Kemudian kita akan mengecek dengan melakukan test ping `ping strix.operation.wise.B11.com. -c 3` dan test cname `ping www.strix.operation.wise.B11.com. -c 1`.

> Script dibawah ini terdapat pada **root node SSS & Garden**, untuk menjalankannya bisa langsung dengan melakukan command `bash no7.sh`

- SSS & Garden
    
    ```
    echo -e "--------------------------------------------------------------------------------------"
    echo "TEST PING SUBDOMAIN (mengarah ke host IP Eden)"
    ping strix.operation.wise.B11.com. -c 3
    echo -e "--------------------------------------------------------------------------------------"
    echo "TEST ALIAS (CNAME) (alias dari  strix.operation.B11.com)"
    ping www.strix.operation.wise.B11.com. -c 1
    echo -e "--------------------------------------------------------------------------------------"
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
 