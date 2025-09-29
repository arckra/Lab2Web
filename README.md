<b>Praktikum 2 Lab2Web Output</b>

<img width="782" height="829" alt="image" src="https://github.com/user-attachments/assets/d6d25c91-3509-474d-bca2-40c860003b7e" />

Pertanyaan
1. Lakukan eksperimen dengan mengubah dan menambah properti dan nilai pada kode CSS
dengan mengacu pada CSS Cheat Sheet yang diberikan pada file terpisah dari modul ini.

Saya melakukan perubahan pada html
```html
<div class="container">
        <h1>Biodata Mahasiswa</h1>
        
        <div class="info-item">
            <span class="label">Nama:</span>
            <span class="value">Ari Cakra Kurniawan</span>
        </div>
        
        <div class="info-item">
            <span class="label">NIM:</span>
            <span class="value">312410248</span>
        </div>
        
        <div class="info-item">
            <span class="label">Kelas:</span>
            <span class="value">TI.24.A2</span>
        </div>
        
        <div class="info-item">
            <span class="label">Mata Kuliah:</span>
            <span class="value">Pemrograman Web 1</span>
</div>
```
dan css
```css
body {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background-color: #f5f5f5;
}

.container {
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

h1 {
    color: #2c3e50;
    text-align: center;
    margin-bottom: 30px;
}

.info-item {
    margin-bottom: 15px;
    padding: 10px;
    border-left: 4px solid #3498db;
    background-color: #f8f9fa;
}

.label {
    font-weight: bold;
    color: #2c3e50;
}

.value {
    color: #3498db;
}

.footer {
    text-align: center;
    margin-top: 30px;
    color: #7f8c8d;
    font-size: 14px;
}
```

2. Apa perbedaan pendeklarasian CSS elemen h1 {...} dengan #intro h1 {...}? berikan
penjelasannya!

h1 {...}

- Merupakan selector type / element
- Akan menerapkan style ke SEMUA elemen 
```<h1>```
 di halaman
- Spesifisitas: 0,0,1 (rendah)

contoh :
```html
<h1>CSS Internal dan <i>Inline CSS</i></h1>
```
```css
h1 {
    font-size: 24px;
    color: #0f189f;
    text-align: center;
    padding: 20px 10px;
}
```

#intro h1 {...}

- Merupakan selector descendant yang menggabungkan ID dan element
- Hanya menerapkan style ke elemen 
```<h1>```
 yang berada di dalam elemen dengan ```id="intro" ```
- Spesifisitas: 1,0,1 (lebih tinggi)

contoh :
```html
<div id="intro">
        <h1>Hello World</h1>
        <p>Kami sedang belajar HTML dan CSS dasar, pada mata kuliah <b>Pemrograman
Web</b> di <i>Universitas Pelita Bangsa</i>. Pelajaran pertama yang kami dapat
adalah membuat tampilan web sederhana dalam rangka mengenal tag-tag dasar HTML
dan CSS.</p>
        <a class="button btn-primary" href="#intro">Informasi selengkapnya.</a>
    </div>
```
```css
#intro h1 {
    text-align: center;
    border: 0;
    color: #fff;
}
```

3. Apabila ada deklarasi CSS secara internal, lalu ditambahkan CSS eksternal dan inline CSS pada
elemen yang sama. Deklarasi manakah yang akan ditampilkan pada browser? Berikan
penjelasan dan contohnya!

Urutan beberapa deklarasi CSS yang ditampilkan terlebih dahulu bila ketiga tersebut dalam 1 folder yang sama
- Inline CSS (dalam atribut style elemen HTML) - Prioritas tertinggi
- Internal CSS (dalam tag ```<style>``` di head atau body) - Prioritas menengah
- Eksternal CSS (bila file .css terpisah) - Prioritas terendah

- Alasannya yaitu karena browser mengikuti sistem yang disebut "Cascade" dalam CSS, yang menentukan bagaimana konflik antara deklarasi CSS yang berbeda diselesaikan.

contoh :
```html
<!-- CSS Eksternal -->
    <link rel="stylesheet" href="style.css">
```
```html    
<!-- CSS Internal -->
<head>
    <style>
        .contoh-paragraf {
            color: green;
            font-size: 18px;
            background-color: #e0ffe0;
            padding: 15px;
            border: 2px solid darkgreen;
            margin: 10px 0;
        }
        
        #header-prioritas {
            color: purple;
            text-align: center;
            background-color: #f0e6ff;
            padding: 20px;
            border: 3px dashed purple;
        }
    </style>
</head>
```
```css
/* CSS Eksternal - Prioritas Terendah */
nav {
    background: #20a759;
    color: #fff;
    text-align: center;
    padding: 10px;
}
nav a {
    color: #fff;
    text-decoration: none;
    padding: 10px 20px;
}
nav .active,
nav a:hover {
    background: #0b6b3a;
}
```

4. Pada sebuah elemen HTML terdapat ID dan Class, apabila masing-masing selector tersebut
terdapat deklarasi CSS, maka deklarasi manakah yang akan ditampilkan pada browser?
Berikan penjelasan dan contohnya!
```( <p id="paragraf-1" class="text-paragraf"> )```

Selector ID akan menang atas selector Class ketika ada konflik.
```html
<!DOCTYPE html>
<html>
<head>
<style>
    .text-paragraf {
        color: blue;
        background: lightblue;
    }
    #paragraf-1 {
        color: red;
        background: pink;
    }
</style>
</head>
<body>

<p id="paragraf-1" class="text-paragraf">
    Teks ini akan berwarna MERAH dan background PINK
    karena ID lebih kuat daripada Class
</p>

</body>
</html>
```

Analogi Sederhana
Bayangkan ini seperti sistem peringkat:

ID = ⭐⭐⭐⭐⭐ (Bintang 5 - Paling kuat)

Class = ⭐⭐⭐ (Bintang 3 - Kuat)

Element = ⭐ (Bintang 1 - Lemah)

Mengapa ID Lebih Kuat?
1. ID itu UNIK (seperti KTP)
- Setiap ID hanya boleh dipakai oleh 1 elemen
- Class bisa dipakai oleh banyak elemen

2. Aturan Nilai Kekuatan CSS

contoh :
```html
<!DOCTYPE html>
<html>
<head>
    <title>Prioritas ID vs Class</title>
    <style>
        /* CLASS selector */
        .text-paragraf {
            color: blue;
            background: lightblue;
        }
        
        /* ID selector - INI YANG MENANG */
        #paragraf-1 {
            color: red;
            background: pink;
        }
    </style>
</head>
<body>
    <p id="paragraf-1" class="text-paragraf">
        Teks ini berwarna MERAH (dari ID), bukan biru (dari Class)
    </p>
</body>
</html>
```

Terimakasih Banyak sudah membaca hingga akhir.

Saya Ari, pamit undur diri

Wassalamualaikum wr. wb.
