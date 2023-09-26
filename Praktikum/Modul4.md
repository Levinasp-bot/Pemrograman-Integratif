# Praktikum  4 : Basic Routing dan Migration

Langkah-langkah dan hasil Screenshot praktikum  4 – Basic Routing dan Migration.
## GET
* ## Langkah 1 
>  Untuk menambahkan endpoint dengan method GET pada aplikasi kita, kita dapat
mengunjungi file web.php pada folder routes. Kemudian tambahkan baris ini pada akhir file
<br> $router->get('/get', function () {<br />
<br>  return 'GET';<br />
<br> }); <br />
![Screenshot Menambahkan enpoint method GET pada file web.php (routes)](../Screenshoot/Modul4/1.PNG)

* ## Langkah 2 
> Setelah itu coba jalankan aplikasi dengan command,
> php -S localhost:8000 -t public <br /><br />
![Screenshot jalankan server](../Screenshoot/Modul4/2.PNG)

* ## Langkah 3 
> Setelah aplikasi berhasil dijalankan, kita dapat membuka browser dengan url,
http://localhost:8000/get, path yang akan kita akses akan berbentuk demikian,
http://{BASE_URL}{PATH}, jika BASE_URL kita adalah localhost:8000 dan PATH kita
adalah /get, maka url akan berbentuk seperti diatas.
![Screenshot . Mencoba mengakses url http://localhost:8000/get sesuai endpoint yang telah ditambahkan sebelumnya](../Screenshoot/Modul4/3.PNG)

## POST, PUT, PATCH, DELETE, dan OPTIONS
* ## Langkah 1
>  Sama halnya saat menambahkan method GET, kita dapat menambahkan methode POST, PUT, PATCH, DELETE, dan OPTIONS pada file web.php dengan code seperti ini
> <br> $router->post('/post', function () { </br>
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
![Screenshot Menambahkan endpoint method POST, PUT, PATCH, DELETE, dan OPTIONS](../Screenshoot/Modul4/4.PNG)

* ## Langkah 2
> Mengakses url http://localhost:8000/get pada Postman
![Screenshot npm init -](../Screenshoot/Modul4/5.PNG)

* ## Langkah 3
> Mengakses url http://localhost:8000/post pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul4/6.PNG) 

* ## Langkah 4
> Mengakses url http://localhost:8000/put pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul4/7.PNG) 

* ## Langkah 5
> Mengakses url http://localhost:8000/patch pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul4/8.PNG) 

* ## Langkah 6
> Mengakses url http://localhost:8000/delete pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul4/9.PNG) 

* ## Langkah 7
> Mengakses url http://localhost:8000/options pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul4/10.PNG) 

## Migrasi Database
* ## Langkah 1 
>  Sebelum melakukan migrasi database pastikan server database aktif kemudian pastikan sudah membuat database dengan nama lumenapi<br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul4/11.PNG)

* ## Langkah 2 
>  Kemudian ubah konfigurasi database pada file .env menjadi seperti ini<br /><br> DB_CONNECTION=mysql <br />
<br> DB_HOST=127.0.0.1 <br />
<br> DB_PORT=3306 <br />
<br> DB_DATABASE=lumenapi <br />
<br> DB_USERNAME=root <br />
<br> DB_PASSWORD=<<password masing-masing>> <br />
<br> <br />
![Screenshot jalankan node setup](../Screenshoot/Modul4/12.PNG)

* ## Langkah 3 
>Setelah mengubah konfigurasi pada file .env, kita juga perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap dan mengubah baris ini,
> <br>//$app->withFacades();<br />
<br>//$app->withEloquent(); <br />
<br> Menjadi <br />
<br> $app->withFacades();
$app->withEloquent(); <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul4/13.PNG)

* ## Langkah 4
> Setelah itu jalankan command berikut untuk membuat file migration
> <br> php artisan make:migration create_users_table # membuat migrasi
untuk tabel users<br />
<br>php artisan make:migration create_products_table # membuat
migrasi untuk tabel products<br />
<br> Setelah menjalankan 2 syntax diatas akan terbuat 2 file pada folder database/migrations dengan format YYYY_MM_DD_HHmmss_nama_migrasi. Pada file migrasi kita akan menemukan fungsi up() dan fungsi down(), fungsi up() akan digunakan pada saat kita melakukan migrasi, fungsi down() akan digunakan saat kita ingin me-rollback migrasi <br />
![Screenshot insert buku many](../Screenshoot/Modul4/14.PNG)

* ## Langkah 5
> Ubah fungsi up pada file migrasi create_users_table menjadi seperti dibawah ini
<br>public function up()<br />
<br>{<br />
<br>Schema::create('users', function (Blueprint $table) {<br />
<br>$table->id();<br />
<br>$table->timestamps();<br />
<br>$table->string('email');<br />
<br>$table->string('password');<br />
<br>});<br />
<br>}<br />
![Screenshot pencarian buku](../Screenshoot/Modul4/15.PNG)


* ## Langkah 6
> Ubah fungsi up pada file migrasi create_products_table menjadi seperti dibawah ini
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
![Screenshot pencarian buku](../Screenshoot/Modul4/16.PNG)

* ## Langkah 6
>  Kemudian jalankan command,
  php artisan migrate
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul4/17.PNG)

* ## Langkah 7
> Tampilan tabel yang berhasil dibuat pada database lumenapi di phpmyadmin
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul4/18.PNG)
