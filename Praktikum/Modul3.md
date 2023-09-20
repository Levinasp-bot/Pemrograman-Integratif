# Praktikum 3 : Integrasi MongoDB dan Express

Langkah Percobaan
## Percobaan instalasi NodeJS
* ### Langkah 1 
> Buka Halaman https://nodejs.org/en/ <br /><br />
![](../Screenshoot/Modul3/1.png)

* ### Langkah 2 
> Download dan jalankan node setup <br /><br />

* ### Langkah 3 
> Setelah instalasi selesai jalankan command node -v untuk memeriksa apakah
NodeJS sudah terinstall
![Screenshot insert buku pertama](../Screenshoot/Modul3/3.png)

## Inisiasi project Express dan pemasangan package
* ### Langkah 1 
> Lakukan pembuatan folder dengan nama express-mongodb dan masuk ke dalam
folder tersebut lalu buka melalui text editor masing-masing
![](../Screenshoot/Modul3/4.png)

* ### Langkah 2
> Lakukan npm init untuk mengenerate file package.json dengan menggunakan
command npm init -y
![](../Screenshoot/Modul3/5.png)

* ### Langkah 3
> Lakukan instalasi express, mongoose, dan dotenv dengan menggunakan command
npm i express mongoose dotenv
![](../Screenshoot/Modul3/6.png)

## Koneksi Express ke MongoDB
* ### Langkah 1
> Buatlah file index.js pada root folder dan masukkan kode di bawah ini
![](../Screenshoot/Modul3/7.png)

* ### Langkah 2
> Lakukan pembuatan file .env dan masukkan baris berikut
PORT=5000
> Setelah itu ubahlah kode pada listening port menjadi berikut dan coba jalankan aplikasi
kembali
const PORT = process.env.PORT || 8000;
app.listen(PORT, () => {
console.log(`Running on port ${PORT}`);
})
![](../Screenshoot/Modul3/8.png)

* ### Langkah 3
> Copy connection string yang terdapat pada compas atau atlas dan paste kan pada
.env seperti berikut
MONGO_URI=<Connection string masing-masing>
![](../Screenshoot/Modul3/9.png)

* ### Langkah 4
> Tambahkan baris kode berikut pada file index.js
require('dotenv').config();
const express = require('express');
const mongoose = require('mongoose');
mongoose.connect(process.env.MONGO_URI);
const db = mongoose.connection;
db.on('error', (error) => {
console.log(error);
});
db.once('connected', () => {
console.log('Mongo connected');
})
![](../Screenshoot/Modul3/10.png)

## Pembuatan Routing
* ### Langkah 1
> Lakukan pembuatan direktori routes di tingkat yang sama dengan index.js
![](../Screenshoot/Modul3/11.png)

* ### Langkah 2
> Buatlah file book.route.js di dalamnya
![](../Screenshoot/Modul3/12.png)

* ### Langkah 3
> Tambahkan baris kode berikut untuk fungsi getAllBooks
const router = require('express').Router();
router.get('/', function getAllBooks(req, res) {
res.status(200).json({
message: 'mendapatkan semua buku'
})
})
module.exports = router;
![](../Screenshoot/Modul3/13.png)

* ### Langkah 4
> Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
const router = require('express').Router();
...
router.get('/:id', function getOneBook(req, res) {
const id = req.params.id;
res.status(200).json({
message: 'mendapatkan satu buku',
id,
})
})
router.post('/', function createBook(req, res) {
res.status(200).json({
message: 'membuat buku baru'
})
})
router.put('/:id', function updateBook(req, res) {
const id = req.params.id;
res.status(200).json({
message: 'memperbaharui satu buku',
id,
})
})
router.delete('/:id', function deleteBook(req, res) {
const id = req.params.id;
res.status(200).json({
message: 'menghapus satu buku',
id,
})
})
module.exports = router;
![](../Screenshoot/Modul3/14.png)

* ### Langkah 5
> Lakukan import book.route.js pada file index.js dan tambahkan baris kode berikut
require('dotenv').config();
const express = require('express');
const mongoose = require('mongoose');
const bookRoutes = require('./routes/book.route'); //
...
app.get('/', (req, res) => {
res.status(200).json({
message: '<nama>,<nim>'
})
})
app.use('/books', bookRoutes); //
const PORT = process.env.PORT || 8000;
app.listen(PORT, () => {
console.log(`Running on port ${PORT}`);
})
![](../Screenshoot/Modul3/15.png)

* ### Langkah 6
> Uji salah satu endpoint dengan Postman
![](../Screenshoot/Modul3/16.png)

## Pembuatan Controller
* ### Langkah 1
> Lakukan pembuatan direktori controllers di tingkat yang sama dengan index.js
![](../Screenshoot/Modul3/17.png)












