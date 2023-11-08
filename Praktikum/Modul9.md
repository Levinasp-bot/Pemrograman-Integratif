# Praktikum  9 : JSON Web Token (JWT)

Langkah-langkah dan hasil Screenshot praktikum  9 :  JSON Web Token (JWT)
* ## Penyesuaian Database
* ### Langkah 1
Melakukan perubahan pada length kolom token dengan menghapus parameter 72 di belakangnya</br>
![](../Screenshoot/Modul9/1.png)
* ### Langkah 2
Menjalankan perintah ph partisan migrate:refresh untuk memperbaharui migrasi dan menghapus data yang lama
![](../Screenshoot/Modul9/2.png)
* ### Langkah 3
Menjalankan aplikasi pada endpoint /auth/register
![](../Screenshoot/Modul8/3.png)

* ## JWT Manual
* ### Langkah 1
Menambahkan ketiga fungsi berikut pada AuthController.php
![](../Screenshoot/Modul9/4.png)
* ### Langkah 2
Melakukan perubahan pada fungsi login
![](../Screenshoot/Modul9/5.png)
* ### Langkah 3
Menambahkan keempat fungsi berikut pada Middleware/Authorization.php
![](../Screenshoot/Modul9/6.png)
* ### Langkah 4
Melakukan perubahan pada fungsi handle
![](../Screenshoot/Modul9/7.png)
* ### Langkah 5
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul9/8.png)
* ### Langkah 6
Menjalankan aplikasi pada endpoint /home dengan melampirkan nilai token yang didapat setelah login pada header
![](../Screenshoot/Modul9/9.png)

* ## JWT Library
* ### Langkah 1
Melakukan generate jwt key secara online menggunakan website Djecrety ― Django Secret Key Generator
![](../Screenshoot/Modul9/10.1.png)
* ### Langkah 2
Melakukan instalasi package jwt firebase
![](../Screenshoot/Modul9/10.2.png)
* ### Langkah 3
Menambahkan fungsi berikut pada file AuthController
![](../Screenshoot/Modul9/11.png)
* ### Langkah 4
Melakukan perubahan pada fungsi login
![](../Screenshoot/Modul9/12.png)
* ### Langkah 5
Membuat file JwtMiddleware.php
![](../Screenshoot/Modul9/13.png)
* ### Langkah 6
Mendaftarkan middleware yang telah dibuat pada bootstrap/app.php
![](../Screenshoot/Modul9/14.png)
* ### Langkah 7
Menambahkan baris berikut pada file web.php
![](../Screenshoot/Modul9/15.png)
* ### Langkah 8
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul8/16.png)
* ### Langkah 9
Menjalankan aplikasi pada endpoint /home
![](../Screenshoot/Modul8/17.png)
