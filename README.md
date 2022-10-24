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

## Initial Script
Pada initial project, kami mengubah `root/.bashrc` masing-masing node sehingga saat dijalankan akan langsung melakukan command berikut ini
- Ostania
    
    ```
    ```

- Eden
    
    ```
    ```

- Lainnya
    
    ```
    ```


## Question 1
> WISE akan dijadikan sebagai DNS Master, Berlint akan dijadikan DNS Slave, dan Eden akan digunakan sebagai Web Server. Terdapat 2 Client yaitu SSS, dan Garden. Semua node terhubung pada router Ostania, sehingga dapat mengakses internet
### Script
- Semua Node
    
    ```
    ```
### Test
![image]()

![image]()

![image]()


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
![image]()


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
![image]()


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
![image]()


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
![image]()

![image]()


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
![image]()


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
![image]()


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
![image]()


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
![image]()


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
 