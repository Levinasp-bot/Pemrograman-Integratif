# Praktikum  6: Model, Controller dan Request-Response Handler

Langkah-langkah dan hasil Screenshot praktikum   6 : Model, Controller dan Request-Response Handler
* ## Model
Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya.
![tabel users](../Screenshoot/Modul6/1.png)

</br>Bersihkan isi User.php yang ada sebelumnya dan isi dengan baris kode berikut
</br><?php
</br>namespace App\Models;
</br>use Illuminate\Database\Eloquent\Model;
</br>class User extends Model
</br>{
</br>/**
</br>* The attributes that are mass assignable.
</br>*
</br>* @var array
</br>*/
</br>protected $fillable = [ 'name', 'email', 'password'];
</br>/**
</br>* The attributes excluded from the model's JSON form.
</br>*
</br>* @var array
</br>*/
</br>protected $hidden = [];
</br>}
![user.php](../Screenshoot/Modul6/2.png)

* ## Controller
</br>Buatlah salinan ExampleController.php pada folder app/Http/Controllers dengan nama HomeController.php dan buatlah fungsi index()
![user.php](../Screenshoot/Modul6/3.png)

</br>Ubah route / pada file routes/web.php menjadi seperti ini
</br>$router->get('/', ['uses' => 'HomeController@index']);
![web.php](../Screenshoot/Modul6/4.png)

</br>Menjalankan Aplikasi
![web.php](../Screenshoot/Modul6/5.png)

* ## Request Handler
</br>Lakukan import library Request dengan menambahkan baris berikut di bagian atas file
</br> use Illuminate\Http\Request;
![web.php](../Screenshoot/Modul6/6.png)

</br>Ubah fungsi index menjadi
</br>public function index (Request $request)
</br>{
</br>return 'Hello, from lumen! We got your request from endpoint: ' . $request->path();
</br>}
![fungsi index](../Screenshoot/Modul6/7.png)

</br>Menjalankan Aplikasi
![web.php](../Screenshoot/Modul6/8.png)

* ## Response Handler
</br>Lakukan import library Response dengan menambahkan baris berikut di bagian atas file
</br> use Illuminate\Http\Response;
![library response](../Screenshoot/Modul6/9.png)

</br>Buatlah fungsi hello() yang berisi
</br>public function hello()
</br>{
</br>$data['status'] = 'Success';
</br>$data['message'] = 'Hello, from lumen!';
</br>return (new Response($data, 201))
</br>->header('Content-Type', 'application/json');
</br>}
![fungsi hello](../Screenshoot/Modul6/10.png)

</br>Tambahkan route /hello pada file routes/web.php
</br>$router->get('/hello', ['uses' => 'HomeController@hello']);
![route hello](../Screenshoot/Modul6/11.png)

</br>Menjalankan aplikasi pada route /hello
![web.php](../Screenshoot/Modul6/12.png)

* ## Penerapan
</br>Lakukan import model User dengan menambahkan baris berikut di bagian atas file
</br>use App\Models\User;
![import model user](../Screenshoot/Modul6/13.png)

</br>Tambahkan ketiga fungsi berikut di HomeController.php
</br>public function defaultUser()
</br>{
</br>$user = User::create([
</br>'name' => 'Nahida',
</br>'email' => 'nahida@akademiya.ac.id',
</br>'password' => 'smol'
</br>]);
</br>return response()->json([
</br>'status' => 'Success',
</br>'message' => 'default user created',
</br>'data' => [
</br>'user' => $user,
</br>]
</br>],200);
</br>}
</br>public function createUser(Request $request)
</br>{
</br>$name = $request->name;
</br>$email = $request->email;
</br>$password = $request->password;
</br>$user = User::create([
</br>'name' => $name,
</br>'email' => $email,
</br>'password' => $password
</br>]);
</br>return response()->json([
</br>'status' => 'Success',
</br>'message' => 'new user created',
</br>'data' => [
</br>'user' => $user,
</br>]
</br>],200);
</br>}
</br>public function getUsers()
</br>{
</br>$users = User::all();
</br>return response()->json([
</br>'status' => 'Success',
</br>'message' => 'all users grabbed',
</br>'data' => [
</br>'users' => $users,
</br>]
</br>],200);
</br>}
</br>// Tiga Fungsi
</br>}
![menambahkan 3 fungsi](../Screenshoot/Modul6/14.png)

</br>Tambahkan ketiga route pada file routes/web.php menggunakan group route
</br>$router->group(['prefix' => 'users'], function () use ($router) {
</br>$router->post('/default', ['uses' => 'HomeController@defaultUser']);
</br>$router->post('/new', ['uses' => 'HomeController@createUser']);
</br>$router->get('/all', ['uses' => 'HomeController@getUsers']);
</br>});
![menambahkan 3 route](../Screenshoot/Modul6/15.png)

</br>Jalankan aplikasi pada route /users/default menggunakan Postman
![menjalankan aplikasi di postman](../Screenshoot/Modul6/16.png)

</br>Jalankan aplikasi pada route /users/new dengan mengisi body
![menjalankan aplikasi di postman](../Screenshoot/Modul6/17.png)

</br>Jalankan aplikasi pada route /users/all
![menjalankan aplikasi di postman](../Screenshoot/Modul6/18.png)
