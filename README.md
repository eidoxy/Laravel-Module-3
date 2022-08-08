###### Nama     : Adrian Sondang I.
###### Kelas    : XII RPL-1
###### No Absen : 08

# Modul 4
## View Blade Template

**Pada Modul 4 ini, kita akan belajar tentang view blade template dan cara membuatnya.**

>View merupakan bagian yang menampilkan informasi untuk disampaikan kepada users. View
terdiri dari script HTML dengan bantuan CSS dan javascript. Sesuai dengan aturan konsep MVC, di
dalam view tidak boleh ada script logika maupun script untuk mengakses database. Di dalam laravel
view diletekan di dalam folder resources/views/.

>Sedangkan blade template merupakan engine yang disediakan laravel untuk memudahkan
developer dalam menampilkan data pada view. Dengan blade tempalte ini kita tidak perlu lagi
menggunakan `<? php echo $data ?>` untuk menampilkan variabel data pada view. Untuk
menggunakan blade tempalete, file view harus disimpan dengan akhiran .blade.php dan disimpan pada
folder resourcess/views.

**Membuat View Blade Template**
  Sebelum membuat template pada laravel, pertama kalian menuju ke folder **resources/view** dan buat folder beserta filenya pada masing masing folder berikut:
1.Barang
  -`dataBarang.blade.php`
2.Kategori
  -`dataKategori.blade.php`
Dan kalian buat file `home.blade.php` pada folder view. Kegunaan file `dataBarang.blade.php` adalah untuk membuat tampilan data barang dan file `dataKategori.blade.php` adalah untuk membuat tampilan kategori serta file `home.blade.php` adalah untuk membuat tampilan awal website atau tampilan utama.

Setelah kalian membuat folder dan file diatas, kalian buat file lagi di folder *layout* yaitu:
1.`master.blade.php`
2.`sidebar.blade.php`
Fungsi dari file diatas adalah untuk membuat template website yang akan kita buat. Berikut file yang telah kita buat:

![image](https://user-images.githubusercontent.com/79520394/183362328-ccf14a75-db85-4a2d-9b0f-6ab26279eb93.png)

Pada file `master.blade.php` kalian ketik code berikut:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>
        @yield('title')
    </title>
</head>
<body>
    <div class="header">
        @include('layout.sidebar')
    </div>

    <div class="container">
        @yield('content')
    </div>
</body>
</html>
```

Untuk membuat tampilan layout kali ini kita akan menggunakan bootstrap. Apa itu bootstrap?
>Bootstrap adalah framework HTML, CSS, dan JavaScript yang berfungsi untuk mendesain website responsive dengan cepat dan mudah. Framework open source ini diciptakan pada tahun 2011 oleh Mark Otto dan Jacob Thornton dari Twitter. Itulah kenapa dulunya Bootstrap dinamakan Twitter Blueprint. Bootstrap dengan cepat meraih popularitas digunakan oleh 27% website di seluruh dunia. Hal itu karena kesederhanaan dan konsistensi yang ditawarkan Bootstrap dibanding framework lainnya saat itu.

Untuk menggunakan bootstrap, kalian harus salin link berikut
*Letakkan pada bagian head*
```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx" crossorigin="anonymous">
```
*Letakkan pada bagian body*
```
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-A3rJD856KowSb7dwlZdYEkO39Gagi7vIsF0jrRAoQmDKKtQBHUuLZ9AsSv4jD4Xa" crossorigin="anonymous"></script>
```

Kalian bisa menemukan code berikut pada website resmi bootstrap atau kalian bisa klik link [di sini](https://getbootstrap.com/docs/5.2/getting-started/introduction/) pada bagian Introduction no 3.

Setelah itu pada file `sidebar.blade.php` kalian ketik code berikut:

```
<nav class="navbar navbar-expand-lg bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="/">Aplikasi Toko</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Home</a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              List
            </a>
            <ul class="dropdown-menu">
              <li><a class="dropdown-item" href="/barang">Barang</a></li>
              <li><a class="dropdown-item" href="/kategori">Kategori</a></li>
              <li><hr class="dropdown-divider"></li>
              <li><a class="dropdown-item" href="#">Lainnya</a></li>
            </ul>
          </li>
        </ul>
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success" type="submit">Cari</button>
        </form>
      </div>
    </div>
  </nav>
```

Code di atas adalah template untuk membuat tampilan search atau navbar, untuk melihat source code aslinya kalian bisa mengunjungi bootstrap atau klik link [di sini](https://getbootstrap.com/docs/5.2/components/navbar/#containers).

Setelah template telah kita buat, maka kita akan membuat data pada file `dataBarang.blade.php` untuk membuat data barang dan `dataKategori.blade.php` untuk membuat data kategori. Pada file `dataBarang.blade.php` ketikan code berikut:

```
@extends('layout.master')

@section('title')
    Data Barang
@endsection

@section('content')
    <button class="btn btn-success mt-5 mb-3">
        Tambah Barang
    </button>
    <table class="table table-striped table-bordered table-responsive">
        <thead>
            <th width="20px">No</th>
            <th>Nama</th>
            <th>Kategori</th>
            <th>Qty</th>
            <th>Harga Jual</th>
            <th>Harga Beli</th>
            <th width="125px">Action</th>
        </thead>

        <tbody>
            <tr>
                <td>1</td>
                <td>Monitor</td>
                <td>Elektronik</td>
                <td>10</td>
                <td>Rp. 1.200.000</td>
                <td>Rp. 1.000.000</td>
                <td>
                    <a href="#" class="btn btn-warning btn-sm">Edit</a>
                    <a href="#" class="btn btn-danger btn-sm">Delete</a>
                </td>
            </tr>
        </tbody>
    </table>
@endsection
```

Dan pada file `dataKategori.blade.php` kalian ketikan code berikut:

```
@extends('layout.master')

@section('title')
    Data Kategori
@endsection

@section('content')
        <table class="table table-striped table-bordered table-responsive mt-5">
        <thead>
            <th width="20px">No</th>
            <th>Nama Katgori</th>
            <th width="125px">Action</th>
        </thead>

        <tbody>
            <tr>
                <td>1</td>
                <td>Elektronik</td>
                <td>
                    <a href="#" class="btn btn-warning btn-sm">Edit</a>
                    <a href="#" class="btn btn-danger btn-sm">Delete</a>
                </td>
            </tr>
        </tbody>
    </table>
@endsection
```

Jika kita menggunakan view blade, kita akan mudah untuk mengubah, menambah, atau menghapus data. Jadi saat kita ingin menambah data, kita tidak perlu mengubah semua isi file, kita tinggal mengubah data filenya dari satu file saja
Misalkan saya ingin menambahkan barang lagi pada data barang, kita hanya perlu menambah data pada file `dataBarang.blade.ohp`. Sangat efisien bukan?

Setelah membuat data barang dan data kategori, selanjutnya kita akan membuat tampilan homenya pada file `home.blade.php`, pada bagian home ini saya juga menggunakan bootstrap. Jika kalian ingin source code aslinya, kalian bisa ke web resmi bootstrap atau klik link [di sini](https://getbootstrap.com/docs/5.2/examples/) setelah itu download folder zip nya.
Ketikan code berikut pada `home.blade.php`:

```
<!doctype html>
<html lang="en" class="h-100">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="Mark Otto, Jacob Thornton, and Bootstrap contributors">
    <meta name="generator" content="Hugo 0.101.0">
    <title>Aplikasi Toko</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx" crossorigin="anonymous">
    <link rel="canonical" href="https://getbootstrap.com/docs/5.2/examples/cover/">
    <link href="{../assets/dist/css/bootstrap.min.css}" rel="stylesheet">
    {{-- <link href="{{asset('style/style.css')}}" rel="stylesheet"> --}}

    <style>
        /*
        * Globals
        */


        /* Custom default button */
        .btn-secondary,
        .btn-secondary:hover,
        .btn-secondary:focus {
        color: rgb(255, 255, 255);
        text-shadow: none; /* Prevent inheritance from `body` */
        }


        /*
        * Base structure
        */

        /* body {
        text-shadow: 0 .05rem .1rem rgba(0, 0, 0, .5);
        box-shadow: inset 0 0 5rem rgba(0, 0, 0, .5);
        } */

        .cover-container {
        max-width: 42em;
        }


        /*
        * Header
        */

        .nav-masthead .nav-link {
        color: rgba(0, 0, 0, 0.5);
        border-bottom: .25rem solid transparent;
        }

        .nav-masthead .nav-link:hover,
        .nav-masthead .nav-link:focus {
        border-bottom-color: rgba(0, 0, 0, 0.25);
        }

        .nav-masthead .nav-link + .nav-link {
        margin-left: 1rem;
        }

        .nav-masthead .active {
        color: rgb(0, 0, 0);
        border-bottom-color: rgb(0, 0, 0);
        }
    </style>

    <!-- Custom styles for this template -->
    <link href="cover.css" rel="stylesheet">
    </head>
    <body class="d-flex h-100 text-center text-bg-light">
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-A3rJD856KowSb7dwlZdYEkO39Gagi7vIsF0jrRAoQmDKKtQBHUuLZ9AsSv4jD4Xa" crossorigin="anonymous"></script>

        <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">
        <header class="mb-auto">
            <div>
            <h3 class="float-md-start mb-0">Home</h3>
            <nav class="nav nav-masthead justify-content-center float-md-end">
                <a class="nav-link fw-bold py-1 px-0 active" aria-current="page" href="/">Home</a>
                <a class="nav-link fw-bold py-1 px-0" href="/barang">Barang</a>
                <a class="nav-link fw-bold py-1 px-0" href="/kategori">Kategori</a>
            </nav>
            </div>
        </header>

        <main class="px-3">
            <h1>Aplikasi Toko</h1>
            <p class="lead">Aplikasi toko yang telah dipercaya oleh para pedagang UMKM di seluruh Indonesia.</p>
            <p class="lead">
            <a href="#" class="btn btn-lg btn-secondary fw-bold border-black-50 bg-black">Lebih lanjut</a>
            </p>
        </main>

        <footer class="mt-auto text-black-50">
            <p>© 2022 Adrian. All rights reserved.</p>
        </footer>
        </div>    
    </body>
</html>
```

Setelah membuat tampilan home dan semua tampilan data, selanjutnya kita akan membuat routernya agar kita bisa terhubung ke websitenya.
Pergi ke folder routes/web.php lalu ketik code berikut:

```
<?php

use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('home');
});

Route::get('/barang', function () {
    return view('barang.dataBarang');
});

Route::get('/kategori', function () {
    return view('kategori.dataKategori');
});
```

Setelah membuat router, pastikan kalian telah mengaktifkan XAMPP dan server laravelnya.
Untuk website yang telah kita buat akan memiliki tampilan seperti ini.

*Tampilan home*
![image](https://user-images.githubusercontent.com/79520394/183368162-85538fed-6d7d-4d78-a77e-1fcdabc39dec.png)

*Tampilan data barang*
![image](https://user-images.githubusercontent.com/79520394/183368359-068e9339-9df4-4467-b86e-18d671b9ab8b.png)

*Tampilan data kategori*
![image](https://user-images.githubusercontent.com/79520394/183368449-9c2e963c-43c1-4e81-b98a-ceb1f18a66c9.png)
