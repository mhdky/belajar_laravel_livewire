# Belajar Laravel Livewire

### Table of Content

* [Apa Itu Laravel Livewire](https://github.com/mhdky/belajar_laravel_livewire#apa-itu-laravel-livewire)
* [Laravel Liviwire Untuk Fullstack Developer](https://github.com/mhdky/belajar_laravel_livewire#laravel-liviwire-untuk-fullstack-developer)
* [Cara Menggunakan Laravel Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-menggunakan-laravel-livewire)
* [Cara Membuat Componet Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-membuat-componet-livewire)
* [Cara Membuat Properties Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-membuat-properties-livewire)


## Apa Itu Laravel Livewire
Laravel Livewire dibangun untuk dapat membuat suatu website modern, seperti project React dan View.

Sumber Youtube: [Ferry Dermawan](https://youtu.be/ia3QN9ud-yI?list=PL-X81XM3cE187IIB2_RM6eNjnsYkwG8tW&t=7)



## Laravel Livewire Untuk Fullstack Developer
Laravel Livewire diperuntukan untuk seorang Fullstack Developer yang menyentuh Frontend dan Backend hanya dengan satu bahasa pemerogramman.

Sumber Youtube: [Ferry Dermawan](https://youtu.be/ia3QN9ud-yI?list=PL-X81XM3cE187IIB2_RM6eNjnsYkwG8tW&t=23)

Laravel Livewire dicitakan oleh Calep Porzio yang juga merupakan pencipta dari Alpine Js.


## Cara Menggunakan Laravel Livewire
1. Install project laravel
2. Install Livewire
``` 
composer required livewire/livewire 
```

3. Jalankan local server
``` 
php artisan serve 
```
4. Tambahkan pada head ` @livewireStyles `
5. Tambahkan di atas tutup body ` @livewireScripts `


## Cara Membuat Componet Livewire
Syarat penulisan component bisa mengikuti seperti di bawah ini:
```
php artisan make:livewire ShowPosts
```
atau bisa seperti di bawah ini

```
php artisan make:livewire show-posts
```

Bisa juga memasukan ke dalam subfolder seperti di bawah ini

```
php artisan make:livewire Post\\Show
php artisan make:livewire Post/Show
php artisan make:livewire post.show
```

Sumber: [https://laravel-livewire.com/docs/2.x/making-components](https://laravel-livewire.com/docs/2.x/making-components)

1. Buat component 
``` 
php artisan livewire:make NamaComponet
```

2. Panggil componet/template livewire dengan cara ` @livewire('nama-template') `

### Cara Hapus Component
``` 
php artisan livewire:delete NamaComponet
```


## Cara Membuat Properties Livewire
1. Masuk ke dalam folder ` Http/Livewire/NamaComponent `
2. Tambahkan properti misalnya nama
```
public $nama = 'Muhammad Rizki';
```
3. Masuk ke dalam folder ` resorces/views/NamaTemplate ` sesuaikan dengan nama component yang ada di atas
4. Tulis kata-kata dan masukan nilai dari properti $nama
```
Halo nama saya adalah {{ $nama }}
```