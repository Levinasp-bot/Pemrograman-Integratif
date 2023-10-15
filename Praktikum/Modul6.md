# Praktikum  6: Model, Controller dan Request-Response Handler

Langkah-langkah dan hasil Screenshot praktikum   6 : Model, Controller dan Request-Response Handler
* ## Model
>  Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya.
![tabel users](../Screenshoot/Modul6/1.png)

>  Bersihkan isi User.php yang ada sebelumnya dan isi dengan baris kode berikut
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
>  Buatlah salinan ExampleController.php pada folder app/Http/Controllers dengan nama HomeController.php dan buatlah fungsi index()
![user.php](../Screenshoot/Modul6/3.png)

>  Ubah route / pada file routes/web.php menjadi seperti ini
> $router->get('/', ['uses' => 'HomeController@index']);
![web.php](../Screenshoot/Modul6/4.png)

>  Menjalankan Aplikasi
![web.php](../Screenshoot/Modul6/5.png)

* ## Request Handler
>  Lakukan import library Request dengan menambahkan baris berikut di bagian atas file
> use Illuminate\Http\Request;
![web.php](../Screenshoot/Modul6/6.png)
