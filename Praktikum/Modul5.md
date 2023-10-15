# Praktikum  5 : Dynamic Route dan Middleware

Langkah-langkah dan hasil Screenshot praktikum  4 – Basic Routing dan Migration.
* ## Langkah 1 Dynamic Route
>  Dynamic route adalah route yang dapat berubah-ubah, contohnya pada saat kita membuka
suatu halaman web, kadang kita melihat /users/1 atau /users/2 , hal ini yang dinamakan
dynamic routes.
<br>Untuk menambahkan dynamic routes pada aplikasi lumen kita, kita dapat menggunakan
syntax berikut,
<br>$router->get('/user/{id}', function ($id) {
<br>return 'User Id = ' . $id;
<br>});
<br>Saat menambahkan parameter pada routes, kita tidak terbatas pada 1 variable saja, namun
kita dapat menambahkan sebanyak yang diperlukan seperti kode berikut,
<br>$router->get('/post/{postId}/comments/{commentId}', function ($postId, $commentId) {
<br>return 'Post ID = ' . $postId . ' Comments ID = ' . $commentId;
<br>});
<br>Pada dynamic routes kita juga bisa menambahkan optional routes, yang mana optional
routes tidak mengharuskan kita untuk memberi variable pada endpoint kita, namun saat kita
memanggil endpoint, dapat menggunakan parameter variable ataupun tidak, seperti pada
kode dibawah ini
<br>$router->get('/users[/{userId}]', function ($userId = null) {
<br>return $userId === null ? 'Data semua users' : 'Data user dengan id ' . $userId;
<br>});
![Menambahkan route](../Screenshoot/Modul5/1.png)


* ## Langkah 2 Aliases Route
> Aliases Route digunakan untuk memberi nama pada route yang telah kita buat, hal ini dapat
membantu kita, saat kita ingin memanggil route tersebut pada aplikasi kita. Berikut syntax
untuk menambahkan aliases route<br /><br />
$router->get('/auth/login', ['as' => 'route.auth.login', function (...) {...}])
<br />...
<br />$router->get('/profile', function (Request $request) {
<br />if ($request->isLoggedIn) {
<br />return redirect()->route('route.auth.login');
<br />}
<br />});
![](../Screenshoot/Modul5/2.png)
![](../Screenshoot/Modul5/2.1.png)
![](../Screenshoot/Modul5/2.2.png)


* ## Langkah 3 Group Route
> Pada lumen, kita juga dapat memberikan grouping pada routes kita agar lebih mudah pada
saat penulisan route pada web.php kita. Kita dapat melakukan grouping dengan
menggunakan syntax berikut,
<br />$router->group(['prefix' => 'users'], function () use ($router) {
<br />$router->get('/', function () { // menjadi /users/, /users => prefix, / => path
<br />return "GET /users";
<br />});
<br />});
![](../Screenshoot/Modul5/3.png)
![](../Screenshoot/Modul5/3.1.png)

* ## Langkah 4 Middleware
>  Middleware adalah penengah antara komunikasi aplikasi dan client. Middleware biasanya digunakan untuk membatasi siapa yang dapat berinteraksi dengan aplikasi kita dan semacamnya, kita dapat menambahkan middleware dengan menambahkan file pada folder app/Http/Middleware . Pada folder tersebut terdapat file ExampleMiddleware , kita dapat men-copy file tersebut untuk membuat middleware baru.
> Kemudian, setelah menambahkan filter pada AgeMiddleware , kita harus mendaftarkan
AgeMiddleware pada aplikasi kita, pada file bootstrap/app.php
> Lalu, kita dapat menambahkan middleware pada routes kita dengan menambahkan opsi
middleware pada salah satu route
![](../Screenshoot/Modul5/4.png)
![](../Screenshoot/Modul5/4.1.png)
![](../Screenshoot/Modul5/4.2.png)
![](../Screenshoot/Modul5/4.3.png)
