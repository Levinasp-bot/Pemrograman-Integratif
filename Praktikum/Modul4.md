# Praktikum  4 : Basic Routing dan Migration

Langkah-langkah dan hasil Screenshot praktikum  4 – Basic Routing dan Migration.
## GET
* ## Langkah 1 
</br> Untuk menambahkan endpoint dengan method GET pada aplikasi kita, kita dapat
mengunjungi file web.php pada folder routes. Kemudian tambahkan baris ini pada akhir file
<br> $router->get('/get', function () {<br />
<br>  return 'GET';<br />
<br> }); <br />
![Screenshot Menambahkan enpoint method GET pada file web.php (routes)](../Screenshoot/Modul4/1.png)

* ## Langkah 2 
</br> Setelah itu coba jalankan aplikasi dengan command,
</br> php -S localhost:8000 -t public <br /><br />
![Screenshot jalankan server](../Screenshoot/Modul4/2.png)

* ## Langkah 3 
</br> Setelah aplikasi berhasil dijalankan, kita dapat membuka browser dengan url,
http://localhost:8000/get, path yang akan kita akses akan berbentuk demikian,
http://{BASE_URL}{PATH}, jika BASE_URL kita adalah localhost:8000 dan PATH kita
adalah /get, maka url akan berbentuk seperti diatas.
![Screenshot . Mencoba mengakses url http://localhost:8000/get sesuai endpoint yang telah ditambahkan sebelumnya](../Screenshoot/Modul4/3.png)

## POST, PUT, PATCH, DELETE, dan OPTIONS
* ## Langkah 1
</br>Sama halnya saat menambahkan method GET, kita dapat menambahkan methode POST, PUT, PATCH, DELETE, dan OPTIONS pada file web.php dengan code seperti ini
<br> $router->post('/post', function () { </br>
<br> return 'POST'; </br>
<br> }); </br>
<br> $router->put('/put', function () { </br>
<br> return 'PUT'; </br>
<br> }); </br>
<br> $router->patch('/patch', function () {
 return 'PATCH'; </br>
<br> }); </br>
<br> $router->delete('/delete', function () {
 return 'DELETE'; </br>
<br> }); </br>
<br> $router->options('/options', function () {
 return 'OPTIONS'; </br>
<br> }); </br>
![Screenshot Menambahkan endpoint method POST, PUT, PATCH, DELETE, dan OPTIONS](../Screenshoot/Modul4/4.png)

* ## Langkah 2
</br>Mengakses url http://localhost:8000/get pada Thunder Client
![](../Screenshoot/Modul4/4get.png)

* ## Langkah 3
</br>Mengakses url http://localhost:8000/post pada Thunder Client
![](../Screenshoot/Modul4/4post.png) 

* ## Langkah 4
</br>Mengakses url http://localhost:8000/put pada Thunder Client
![](../Screenshoot/Modul4/4put.ong) 

* ## Langkah 5
</br> Mengakses url http://localhost:8000/patch pada Thunder Client
![](../Screenshoot/Modul4/4patch.png) 

* ## Langkah 6
</br>Mengakses url http://localhost:8000/delete pada Thunder Client
![](../Screenshoot/Modul4/4delete.png) 

## Migrasi Database
* ## Langkah 1 
</br>Sebelum melakukan migrasi database pastikan server database aktif kemudian pastikan sudah membuat database dengan nama lumenapi<br />
![](../Screenshoot/Modul4/5a.png)

* ## Langkah 2 
</br>Kemudian ubah konfigurasi database pada file .env menjadi seperti ini<br /><br> DB_CONNECTION=mysql <br />
<br> DB_HOST=127.0.0.1 <br />
<br> DB_PORT=3306 <br />
<br> DB_DATABASE=lumenapi <br />
<br> DB_USERNAME=root <br />
<br> DB_PASSWORD=<<password masing-masing>> <br />
<br> <br />
![](../Screenshoot/Modul4/5b.png)

* ## Langkah 3 
</br>Setelah mengubah konfigurasi pada file .env, kita juga perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap dan mengubah baris ini,
<br>//$app->withFacades();<br />
<br>//$app->withEloquent(); <br />
<br> Menjadi <br />
<br> $app->withFacades();
$app->withEloquent(); <br />
![](../Screenshoot/Modul4/5c.png)

* ## Langkah 4
</br>Setelah itu jalankan command berikut untuk membuat file migration
<br> php artisan make:migration create_users_table # membuat migrasi
untuk tabel users<br />
<br>php artisan make:migration create_products_table # membuat
migrasi untuk tabel products<br />
<br> Setelah menjalankan 2 syntax diatas akan terbuat 2 file pada folder database/migrations dengan format YYYY_MM_DD_HHmmss_nama_migrasi. Pada file migrasi kita akan menemukan fungsi up() dan fungsi down(), fungsi up() akan digunakan pada saat kita melakukan migrasi, fungsi down() akan digunakan saat kita ingin me-rollback migrasi <br />
![](../Screenshoot/Modul4/5d.png)

* ## Langkah 5
</br>Ubah fungsi up pada file migrasi create_users_table menjadi seperti dibawah ini
<br>public function up()<br />
<br>{<br />
<br>Schema::create('users', function (Blueprint $table) {<br />
<br>$table->id();<br />
<br>$table->timestamps();<br />
<br>$table->string('email');<br />
<br>$table->string('password');<br />
<br>});<br />
<br>}<br />
![](../Screenshoot/Modul4/5e.png)


* ## Langkah 6
</br>Ubah fungsi up pada file migrasi create_products_table menjadi seperti dibawah ini
<br>public function up()<br />
<br>{<br />
<br>Schema::create('products', function (Blueprint $table) {<br />
<br>$table->id();<br />
<br>$table->timestamps();<br />
<br>$table->string('name');<br />
<br>$table->integer('category_id');<br />
<br>$table->string('slug');<br />
<br>$table->integer('price');<br />
<br>$table->integer('weight');<br />
<br>a$table->text('description');<br />
<br>});<br />
<br>}<br />
![](../Screenshoot/Modul4/5f.png)

* ## Langkah 6
</br> Kemudian jalankan command,
  php artisan migrate
![](../Screenshoot/Modul4/5g.png)

* ## Langkah 7
</br>Tampilan tabel yang berhasil dibuat pada database lumenapi di phpmyadmin
![](../Screenshoot/Modul4/5h.png)
