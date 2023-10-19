# Praktikum  7 : Relasi One-to-Many dan Many-to-Many

Langkah-langkah dan hasil Screenshot praktikum  7 : Relasi One-to-Many dan Many-to-Many
* ## Pembuatan Tabel
* ### Langkah 1
Sebelum membuat migrasi database atau membuat tabel pastikan server database aktif kemudian pastikan sudah membuat database dengan nama lumenpost,</br>
![](../Screenshoot/Modul7/1.png)
* ### Langkah 2
Kemudian ubah konfigurasi database pada file .env
![](../Screenshoot/Modul7/2.png)
* ### Langkah 3
Menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap
![](../Screenshoot/Modul7/3.png)
* ### Langkah 4
Menjalankan command berikut untuk membuat file migration
![](../Screenshoot/Modul7/4.png)
* ### Langkah 5
Mengubah fungsi up() pada file migrasi create_posts_table
![](../Screenshoot/Modul7/5.png)
* ### Langkah 6
Mengubah fungsi up() pada file migrasi create_comments_table
![](../Screenshoot/Modul7/6.png)
* ### Langkah 7
Mengubah fungsi up() pada file migrasi create_tags_table
![](../Screenshoot/Modul7/7.png)
* ### Langkah 8
Mengubah fungsi up() pada file migrasi create_post_tag_table
![](../Screenshoot/Modul7/8.png)
* ### Langkah 9
Menjalankan command php artisan migrate
![](../Screenshoot/Modul7/9.png)

* ## Pembuatan Model
* ### Langkah 1
Membuat file dengan nama Post.php
![](../Screenshoot/Modul7/10.png)
* ### Langkah 2
Membuat file dengan nama Comment.php
![](../Screenshoot/Modul7/11.png)
* ### Langkah 3
Membuat file dengan nama Tag.php
![](../Screenshoot/Modul7/12.png)

* ## Relasi One-to-Many
* ### Langkah 1
Menambahkan fungsi comments() pada file Post.php
![](../Screenshoot/Modul7/13.png)
* ### Langkah 2
Menambahkan fungsi post() dan atribut postId pada $fillable pada file Comment.php
![](../Screenshoot/Modul7/14.png)
* ### Langkah 3
Membuat file PostController.php
![](../Screenshoot/Modul7/15.png)
* ### Langkah 4
Membuat file CommentController.php
![](../Screenshoot/Modul7/16.png)
* ### Langkah 5
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul7/17.png)
* ### Langkah 6
Membuat satu post menggunakan Postman
![](../Screenshoot/Modul7/18.png)
* ### Langkah 7
Membuat satu comment menggunakan Postman
![](../Screenshoot/Modul7/19.png)
* ### Langkah 8
Menampilkan post menggunakan Postman
![](../Screenshoot/Modul7/20.png)

* ## Relasi One-to-Many
* ### Langkah 1
Menambahkan fungsi tags() pada file Post.php
![](../Screenshoot/Modul7/21.png)
* ### Langkah 2
Menambahkan fungsi posts() pada file Tag.php
![](../Screenshoot/Modul7/22.png)
* ### Langkah 3
Membuat file TagController.php
![](../Screenshoot/Modul7/23.png)
* ### Langkah 4
Menambahkan fungsi addTag dan response tags pada PostController.php
![](../Screenshoot/Modul7/24.png)
* ### Langkah 5
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul7/25.png)
* ### Langkah 6
Membuat satu tag menggunakan Postman
![](../Screenshoot/Modul7/26.png)
* ### Langkah 7
Menambahkan tag “jadul” pada post “disana engkau berdua”
![](../Screenshoot/Modul7/27.png)
* ### Langkah 8
Menampilkan post “disana engkau berdua” menggunakan Postman
![](../Screenshoot/Modul7/28.png)
* ### Langkah 9
Membuat postingan “tanpamu apa artinya” menggunakan Postman
![](../Screenshoot/Modul7/29.png)
* ### Langkah 10
Menambahkan tag “jadul” pada postingan “tanpamu apa artinya”
![](../Screenshoot/Modul7/30.png)
* ### Langkah 11
Membuat tag “lagu” menggunakan Postman
![](../Screenshoot/Modul7/31.png)
* ### Langkah 12
Menambahkan tag “lagu” pada postingan “tanpamu apa artinya”
![](../Screenshoot/Modul7/32.png)
* ### Langkah 13
Menampilkan post pertama
![](../Screenshoot/Modul7/33.png)
* ### Langkah 14
Menampilkan post kedua
![](../Screenshoot/Modul7/34.png)



























