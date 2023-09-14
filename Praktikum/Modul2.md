# Praktikum 1 : Instalasi Lumen, MongoDB, dan Konfirgurasi App Key

Langkah - langkah dan hasil Screenshot praktikum instalasi Lumen, MongoDB, dan konofigurasi App Key.

* ## Langkah 1 (Instalasi Composer)
> Download dan jalankan Composer-Setup.exe <br /><br />
![Screenshot Instalasi Composer](../Screenshoot/1.png)

* ## Langkah 2 (Instalasi MongoDB)
> Buka halaman https://www.mongodb.com/try/download/community dan klik Download <br /><br />
> Menjalankan mongodb-windows-x86_64-6.0.1-signed.msi
![Screenshot Instalasi MongoDB](../Screenshoot/2.png)
> Instalasi MongoDB telah berhasil
![Screenshot Instalasi MongoDB](../Screenshoot/2i.png)
> Membuka MongoDB yang telah diinstal
![Tampilan Aplikasi MongoDB Compass](../Screenshoot/mongodb.png)

* ## Langkah 3 (Instalasi Lumen)
> Buka cmd dan masuk ke path folder yang telah dibuat untuk instalasi lumen
![](../Screenshoot/3f.png)
> Instalasi lumen di cmd dengan command composer create-project --prefer-dist laravel/lumen lumenapi
![](../Screenshoot/install lumen.png)
> Menjalankan projek lumen
![](../Screenshoot/Screenshot 2023-09-06 144104.png)

* ## Langkah 4 (Konfigurasi App Key)
> Membuka file web.php pada folder routes, kemudian buat endpoint yang akan mengembalikan random string dengan
panjang 32
![](../Screenshoot/web.php.png)
> Melakukan generate dari website https://pinetools.com/random-string-generator
![](../Screenshoot/generated string.png)
> Memasukkan random string tersebut ke file .env kita pada bagian
APP_KEY
![](../Screenshoot/app key .env.png)






