# Praktikum  6: Model, Controller dan Request-Response Handler

Langkah-langkah dan hasil Screenshot praktikum   6 : Model, Controller dan Request-Response Handler
* ## Model
>  Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya.
![](../Screenshoot/Modul6/1.png)
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
![](../Screenshoot/Modul6/2.png)
