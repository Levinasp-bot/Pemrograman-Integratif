# Praktikum 3 : Integrasi MongoDB dan Express

Langkah Percobaan
## Percobaan instalasi NodeJS
* ### Langkah 1 
</br>Membuka Halaman https://nodejs.org/en/ <br /><br />
![](../Screenshoot/Modul3/1.png)

* ### Langkah 2 
</br>Mengunduh dan menjalankan node setup <br /><br />

* ### Langkah 3 
</br>Setelah instalasi selesai, menjalankan command node -v untuk memeriksa apakah
NodeJS sudah terinstall
![Screenshot insert buku pertama](../Screenshoot/Modul3/3.png)

## Inisiasi project Express dan pemasangan package
* ### Langkah 1 
</br>Membuat folder dengan nama express-mongodb dan masuk ke dalam
folder tersebut lalu buka melalui text editor masing-masing
![](../Screenshoot/Modul3/4.png)

* ### Langkah 2
</br>Melakukan npm init untuk mengenerate file package.json dengan menggunakan
command npm init -y
![](../Screenshoot/Modul3/5.png)

* ### Langkah 3
</br>Melakukan instalasi express, mongoose, dan dotenv dengan menggunakan command
npm i express mongoose dotenv
![](../Screenshoot/Modul3/6.png)

## Koneksi Express ke MongoDB
* ### Langkah 1
</br>Membuat file index.js pada root folder dan masukkan kode di bawah ini
![](../Screenshoot/Modul3/7.png)

* ### Langkah 2
</br>MeLakukan pembuatan file .env dan masukkan baris berikut
<br />PORT=5000
<br />Setelah itu ubahlah kode pada listening port menjadi berikut dan coba jalankan aplikasi
kembali
<br />const PORT = process.env.PORT || 8000;
app.listen(PORT, () => {
console.log(`Running on port ${PORT}`);
})
![](../Screenshoot/Modul3/8.png)

* ### Langkah 3
</br>Copy connection string yang terdapat pada compas atau atlas dan paste kan pada
.env seperti berikut
<br />MONGO_URI=<Connection string masing-masing>
![](../Screenshoot/Modul3/9.png)

* ### Langkah 4
</br>Tambahkan baris kode berikut pada file index.js
<br />require('dotenv').config();
<br />const express = require('express');
<br />const mongoose = require('mongoose');
<br />mongoose.connect(process.env.MONGO_URI);
<br />const db = mongoose.connection;
<br />db.on('error', (error) => {
<br />console.log(error);
<br />});
<br />db.once('connected', () => {
<br />console.log('Mongo connected');
<br />})
![](../Screenshoot/Modul3/10.png)

## Pembuatan Routing
* ### Langkah 1
</br>Lakukan pembuatan direktori routes di tingkat yang sama dengan index.js
![](../Screenshoot/Modul3/11.png)

* ### Langkah 2
</br>Buatlah file book.route.js di dalamnya
![](../Screenshoot/Modul3/12.png)

* ### Langkah 3
</br>Tambahkan baris kode berikut untuk fungsi getAllBooks
<br />const router = require('express').Router();
<br />router.get('/', function getAllBooks(req, res) {
<br />res.status(200).json({
<br />message: 'mendapatkan semua buku'
<br />})
<br />})
<br />module.exports = router;
![](../Screenshoot/Modul3/13.png)

* ### Langkah 4
</br>Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
<br />const router = require('express').Router();
<br />...
<br />router.get('/:id', function getOneBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'mendapatkan satu buku',
<br />id,
<br />})
<br />})
<br />router.post('/', function createBook(req, res) {
<br />res.status(200).json({
<br />message: 'membuat buku baru'
<br />})
<br />})
<br />router.put('/:id', function updateBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'memperbaharui satu buku',
<br />id,
<br />})
<br />})
<br />router.delete('/:id', function deleteBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'menghapus satu buku',
<br />id,
<br />})
<br />})
<br />module.exports = router;
![](../Screenshoot/Modul3/14.png)

* ### Langkah 5
</br>Lakukan import book.route.js pada file index.js dan tambahkan baris kode berikut
<br />require('dotenv').config();
<br />const express = require('express');
<br />const mongoose = require('mongoose');
<br />const bookRoutes = require('./routes/book.route'); //
<br />...
<br />app.get('/', (req, res) => {
<br />res.status(200).json({
<br />message: '<nama>,<nim>'
<br />})
<br />})
<br />app.use('/books', bookRoutes); //
<br />const PORT = process.env.PORT || 8000;
<br />app.listen(PORT, () => {
<br />console.log(`Running on port ${PORT}`);
<br />})
![](../Screenshoot/Modul3/15.png)

* ### Langkah 6
</br>Uji salah satu endpoint dengan Postman
![](../Screenshoot/Modul3/16.png)

## Pembuatan Controller
* ### Langkah 1
</br>Lakukan pembuatan direktori controllers di tingkat yang sama dengan index.js
![](../Screenshoot/Modul3/17.png)

* ### Langkah 2
</br>Buatlah file book.controller.js di dalamnya
![](../Screenshoot/Modul3/18.png)

* ### Langkah 3
</br>Salin baris kode dari routes untuk fungsi getAllBooks
<br />function getAllBooks(req, res) {
<br />res.status(200).json({
<br />message: 'mendapatkan semua buku'
<br />})
<br />};
<br />module.exports = {
<br />getAllBooks,
<br />}
![](../Screenshoot/Modul3/19.png)

* ### Langkah 4
</br>Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
<br />Integrasi MongoDB dan Express 9
<br />...
<br />function getOneBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'mendapatkan satu buku',
<br />id,
<br />})
<br />}
<br />function createBook(req, res) {
<br />res.status(200).json({
<br />message: 'membuat buku baru'
<br />})
<br />}
<br />function updateBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'memperbaharui satu buku',
<br />id,
<br />})
<br />}
<br />function deleteBook(req, res) {
<br />const id = req.params.id;
<br />res.status(200).json({
<br />message: 'menghapus satu buku',
<br />id,
<br />})
<br />}
<br />module.exports = {
<br />getAllBooks,
<br />getOneBook, //
<br />createBook, //
<br />updateBook, //
<br />deleteBook //
}
![](../Screenshoot/Modul3/20.png)

* ### Langkah 5
</br>Lakukan import book.controller.js pada file book.route.js
const router = require('express').Router();
const book = require('../controllers/book.controller'); //
...
module.exports = router;
![](../Screenshoot/Modul3/21.png)

* ### Langkah 6
</br>Lakukan perubahan pada fungsi agar dapat memanggil fungsi dari book.controller.js
const router = require('express').Router();
const book = require('../controllers/book.controller');
router.get('/', book.getAllBooks);
router.get('/:id', book.getOneBook);
router.post('/', book.createBook);
router.put('/:id', book.updateBook);
router.delete('/:id', book.deleteBook);
module.exports = router;
![](../Screenshoot/Modul3/22.png)

## Pembuatan Model
* ### Langkah 1
</br>Lakukan pembuatan direktori models di tingkat yang sama dengan index.js
![](../Screenshoot/Modul3/24.png)

* ### Langkah 2
</br>Buatlah file book.model.js di dalamnya
![](../Screenshoot/Modul3/25.png)

* ### Langkah 3
</br>Tambahkan baris kode berikut sesuai dengan tabel di atas
const mongoose = require('mongoose');
const bookSchema = new mongoose.Schema({
title: {
type: String
},
author: {
type: String
},
year: {
type: Number
},
pages: {
type: Number
},
summary: {
type: String
},
publisher: {
type: String
}
})
module.exports = mongoose.model('book', bookSchema);
![](../Screenshoot/Modul3/26.png)

## Operasi CRUD
* ### Langkah 1
</br>Hapus semua data pada collection books
![](../Screenshoot/Modul3/27.png)

* ### Langkah 2
</br>Lakukan import book.model.js pada file book.controller.js
const Book = require('../models/book.model');
![](../Screenshoot/Modul3/28.png)

* ### Langkah 3
</br>Lakukan perubahan pada fungsi createBook
const Book = require('../models/book.model');
...
async function createBook(req, res) {
const book = new Book({
title: req.body.title,
author: req.body.author,
year: req.body.year,
pages: req.body.pages,
summary: req.body.summary,
publisher: req.body.publisher,
})
try {
const savedBook = await book.save();
res.status(200).json({
message: 'membuat buku baru',
book: savedBook,
})
} catch (error) {
res.status(500).json({
message: 'kesalahan pada server',
error: error.message,
})
}
}
![](../Screenshoot/Modul3/29.png)

* ### Langkah 4
</br>Buatlah dua buah buku dengan data di bawah ini dengan Postman
{
"title": "Dilan 1990",
"author": "Pidi Baiq",
"year": 2014,
"pages": 332,
"summary": "Mirea, anata wa utsukushī",
"publisher": "Pastel Books"
}

{
"title": "Dilan 1991",
"author": "Pidi Baiq",
"year": 2015,
"pages": 344,
"summary": "Watashi ga kare o aishite iru to ittara",
"publisher": "Pastel Books"
}
![](../Screenshoot/Modul3/30.png)

* ### Langkah 5
</br>Lakukan perubahan pada fungsi getAllBooks
const Book = require('../models/book.model');
async function getAllBooks(req, res) {
try {
const books = await Book.find();
res.status(200).json({
message: 'mendapatkan semua buku',
books,
})
} catch (error) {
res.status(500).json({
message: 'kesalahan pada server',
error: error.message,
})
}
}
![](../Screenshoot/Modul3/31.png)

* ### Langkah 6
</br>Lakukan perubahan pada fungsi getOneBook
const Book = require('../models/book.model');
...
async function getOneBook(req, res) {
const id = req.params.id;
try {
const book = await Book.findById(id);
res.status(200).json({
message: 'mendapatkan satu buku',
book,
})
} catch (error) {
res.status(500).json({
message: 'kesalahan pada server',
error: error.message,
})
}
}
![](../Screenshoot/Modul3/32.png)

* ### Langkah 7
</br>Tampilkan semua buku dengan Postman
![](../Screenshoot/Modul3/33.png)

* ### Langkah 8
</br>Tampilkan buku Dilan 1990 dengan Postman
![](../Screenshoot/Modul3/34.png)

* ### Langkah 9
</br>Lakukan perubahan pada fungsi updateBook
</br>const Book = require('../models/book.model');
...
async function updateBook(req, res) {
const id = req.params.id;
try {
const book = await Book.findByIdAndUpdate(
id, req.body, { new: true }
)
res.status(200).json({
message: 'memperbaharui satu buku',
book,
})
} catch (error) {
res.status(500).json({
message: 'kesalahan pada server',
error: error.message,
})
}
}
![](../Screenshoot/Modul3/35.png)

* ### Langkah 10
</br>Ubah judul buku Dilan 1991 menjadi “<NAMAPANGGILAN> 1991” dengan
Postman
![](../Screenshoot/Modul3/36.png)

* ### Langkah 11
</br>Lakukan perubahan pada fungsi deleteBook
</br>const Book = require('../models/book.model');
...
async function deleteBook(req, res) {
const id = req.params.id;
try {
const book = await Book.findByIdAndDelete(id);
res.status(200).json({
message: 'menghapus satu buku',
book,
})
} catch (error) {
res.status(500).json({
message: 'kesalahan pada server',
error: error.message,
})
}
}
![](../Screenshoot/Modul3/37.png)

* ### Langkah 11
</br>Hapus buku Dilan 1990 dengan Postman
![](../Screenshoot/Modul3/38.png)
