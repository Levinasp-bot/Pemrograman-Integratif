# Praktikum 2 : CRUD MongoDB Compass dan Shell

Langkah - langkah dan hasil Screenshot praktikum CRUD MongoDB Compass dan Shell.
## MongoDB Compass
* ## Langkah 1 
> Melakukan koneksi ke MongoDB menggunakan connection string <br /><br />
![Screenshot koneksi ke MongoDB](../Screenshoot/Modul2/1.png)

* ## Langkah 2 
> Membuat database dengan melakukan klik “Create Database” <br /><br />
![Screenshot membuat database](../Screenshoot/Modul2/2.png)

* ## Langkah 3 
> Melakuakan insert buku pertama dengan melakukan klik “Add Data”, pilih “Insert
Document”, isi dengan data yang diinginkan dan klik “Insert”
![Screenshot insert buku pertama](../Screenshoot/Modul2/3.png)

* ## Langkah 4 
> insert buku kedua dengan cara yang sama.
![Screenshot insert buku kedua](../Screenshoot/Modul2/4.png)

* ## Langkah 5
> Melakukan pencarian buku dengan author “Osamu Dazai” dengan mengisi filter yang
diinginkan dan klik “Find”
![Screenshot pencarian buku](../Screenshoot/Modul2/5.png)

* ## Langkah 6
> Melakukan perubahan summary pada buku “No Longer Human” menjadi “Buku yang
bagus (<NAMA>,<NIM>) dengan melakukan klik “Edit Document” (berlambang
pensil), mengisi nilai summary yang baru, dan melakukan klik “Update”
![Screenshot update buku](../Screenshoot/Modul2/6.png)

* ## Langkah 7
> Melakukan penghapusan pada buku “I Am a Cat” dengan melakukan klik “Remove
Document” (berlambang tong sampah) dan melakukan klik “Delete”
![Screenshot delete buku](../Screenshoot/Modul2/7.png)

## MongoDB Shell
* ## Langkah 1
> Melakukan koneksi ke MongoDB Server dengan menjalankan command mongosh bagi
yang menggunakan terminal build in OS sehingga tampilan terminal kalian akan
menjadi seperti berikut
![Screenshot koneksi MongoDB](../Screenshoot/Modul2/8.png)

* ## Langkah 2
> Melihat list database yang ada di server dengan menjalankan command
show dbs
> Untuk berpindah ke database “bookstore” gunakan command use bookstore , kalian
dapat memastikan telah berpindah ke database yang benar dengan melihat tulisan
sebelum tanda “>”
> Melihat collection yang ada pada database tersebut dengan
menggunakan command show collections
![Screenshot melihat list database](../Screenshoot/Modul2/9.png)

* ## Langkah 3
> Melakukan insert buku “Overlord I” dengan menggunakan command
db.books.insertOne(<data kalian>) , setelah insert buku berhasil maka MongoDB akan
mengembalikan pesan sebagai berikut.
![Screenshot insert buku Overlord I](../Screenshoot/Modul2/10.png)

* ## Langkah 4
> Melakukan insert buku “The Setting Sun” dan “Hujan” dengan insert many dengan
menggunakan command db.books.insertMany(<data kalian>) , dan akan mengembalikan pesan sebagai berikut.
![Screenshot insert buku many](../Screenshoot/Modul2/11.png)

* ## Langkah 5
> Melakukan pencarian buku dengan menggunakan command db.books.find() untuk
melakukan pencarian semua buku.
![Screenshot pencarian buku](../Screenshoot/Modul2/12.png)

* ## Langkah 6
> Menampilkan seluruh buku dengan author “Osamu Dazai” dengan mengisi argument
pada find() dengan menggunakan command db.books.find({<filter yang ingin
diisi>})
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul2/13.png)

* ## Langkah 7
> Melakukan perubahan summary pada buku “Hujan” menjadi “Buku yang bagus
(<NAMA>,<NIM>) dengan mengunakan command db.books.updateOne({<filter>},
{$set: {<data yang akan di update>}}) sehingga output yang dihasilkan oleh MongoDB
akan menjadi seperti berikut
![Screenshot update buku](../Screenshoot/Modul2/14.png)

* ## Langkah 8
> Melakukan perubahan publisher menjadi “Yen Press” pada semua buku “Osamu
Dazai” dengan menggunakan command db.books.updateMany({<filter>}, {$set: {<data
yang akan di update>}})
![Screenshot update buku](../Screenshoot/Modul2/15.png)

* ## Langkah 9
> Melakukan penghapusan pada buku “Overlord I” dengan menggunakan command
db.books.deleteOne({<argument>})
![Screenshot delete buku](../Screenshoot/Modul2/16.png)

* ## Langkah 9
> Melakukan penghapusan pada semua buku “Osamu Dazai dengan menggunakan
command db.books.deleteMany({<argument>})
![Screenshot delete buku](../Screenshoot/Modul2/17.png)












