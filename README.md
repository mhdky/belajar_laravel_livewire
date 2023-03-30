# Belajar Laravel Livewire

### Table of Content

* [Apa Itu Laravel Livewire](https://github.com/mhdky/belajar_laravel_livewire#apa-itu-laravel-livewire)
* [Laravel Liviwire Untuk Fullstack Developer](https://github.com/mhdky/belajar_laravel_livewire#laravel-liviwire-untuk-fullstack-developer)
* [Cara Menggunakan Laravel Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-menggunakan-laravel-livewire)
* [Cara Membuat Componet Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-membuat-componet-livewire)
* [Cara Membuat Properties Livewire](https://github.com/mhdky/belajar_laravel_livewire#cara-membuat-properties-livewire)
* [Binding Nested Data](https://github.com/mhdky/belajar_laravel_livewire#binding-nested-data)
* [Show dan Hidden Password](https://github.com/mhdky/belajar_laravel_livewire#show-dan-hidden-password)
* [Action Counter Tambah Barang](https://github.com/mhdky/belajar_laravel_livewire#action-counter-tambah-barang)
* [Creat Data](https://github.com/mhdky/belajar_laravel_livewire#creat-data)



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
```javascript
public $nama = 'Muhammad Rizki';
```
3. Masuk ke dalam folder ` resorces/views/NamaTemplate ` sesuaikan dengan nama component yang ada di atas.
4. Tulis kata-kata dan masukan nilai dari properti $nama
```javascript
Halo nama saya adalah {{ $nama }}
```


## Binding Nested Data
1. Buka folder ` Http/Livewire/NamaComponent `
2. Tambahkan method public dan nama properti yang diinginkan, misalnya
```javascript
class PostForm extends Component
{
    public $name = '';

    public function render()
    {
        return view('livewire.post-form');
    }
}
```

3. Masuk ke dalam folder ` resorces/views/NamaTemplate ` sesuaikan dengan nama component yang ada di atas.
4. Buat input type:text dan tambahkan wire:model
```html
<input type="text" wire:model="name">
```
5. Tampung data yang diinputkan
```html
<p>Halo nama saya adalah {{ $name }}</p>
```

Sumber Youtube: [Ferry Dermawan](https://youtu.be/k7xJ_qOuiJE?list=PL-X81XM3cE187IIB2_RM6eNjnsYkwG8tW&t=156)

```
Catatan:
Data yang disimpan di properti publik dapat dilihat oleh JavaScript front-end. Oleh karena itu,  TIDAK HARUS menyimpan data sensitif di dalamnya.
```



## Show dan Hidden Password
1. Buka folder ` Http/Livewire/NamaComponent `
2. Tambahkan method public dan nama properti seperti di bawah ini
```javascript
class PostForm extends Component
{
    public $password = '';
    public $showPass = false;

    public function render()
    {
        return view('livewire.post-form');
    }
}
```
3. Masuk ke dalam folder ` resorces/views/NamaTemplate ` sesuaikan dengan nama component yang ada di atas.
4. Tambahkan kode di bawah ini:
```html
@if ($showPass == 'show')
    <input type="text" wire:model="password">
@else
    <input type="password" wire:model="password">
@endif

<input type="checkbox" wire:model="showPass" value="show">
```

Sumber Youtube: [Ferry Dermawan](https://youtu.be/k7xJ_qOuiJE)



## Action Counter Tambah Barang
### Cara Membuat Counter Tambah Barang
1. Buat sebuah input lalu tambahkan wire model
```html
<input type="number" wire:model="keranjang" class="mx-5">
```
2. Buat sebuah button minus lalu tambahkan wire click
```html
<button type="submit" {{ ($keranjang <=  0 ? 'disabled' : '') }} class="bg-zinc-200 w-9 h-9 flex justify-center items-center rounded-md text-xl leading-none {{ ($keranjang <=  0 ? 'opacity-50' : '') }}" wire:click="kurang">-</button>
```
3. Buat sebuah button plus lalu tambahkan wire click
```html
<button type="submit" {{ ($keranjang >= 5 ? 'disabled' : '') }} class="bg-zinc-200 w-9 h-9 flex justify-center items-center rounded-md text-xl leading-none {{ ($keranjang >= 5 ? 'opacity-50' : '') }}" wire:click="tambah">+</button>
```
4. Buka folder ` Http/Livewire/NamaComponent `
5. Tambahkan code dibawah ini, sesuaikan dengan nama wire model dan wire click yang ada pada template sebelumnya
```javascript
// counter tambah barang
public $keranjang = 0;
// tambah
public function tambah() {
    $this->keranjang++;
}
// kurang
public function kurang() {
    $this->keranjang--;
}
```

Sumber Youtube: [Ferry Dermawan](https://youtu.be/VzlwohCee4M)



## Creat Data
1. Buat file blade post lalu tambahkan ` @livewire('post.table-post') ` dan ` @livewire('post.create-post') `
2. Buat component yang nantinya di dalamnya terdapat form  dan masukan ke dalam folder post
```
php artisan make:livewire post.CreatePost
```
3. Buka file create-post yang ada di ` resorces/view/livewire/post/create-post.blade.php `. Buat kode seperti di bawah ini dan tambahkan wire:submit.prevent pada form dan wire:model pada input 
```html
<form autocomplete="off" wire:submit.prevent="store">
    {{-- title --}}
    <label for="title">Title</label>
    <input type="text" wire:model="title" id="title">
    @error('title')
        <p>{{ $message }}</p>
    @enderror

    {{-- author --}}
    <label for="author" class="mb-1 mt-3">Author</label>
    <input type="text" wire:model="author" id="author">
    @error('author')
        <p>{{ $message }}</p>
    @enderror

    <div><button type="submit">Simpan</button></div>
</form>
```
4. Buat component yang nantinya di dalamnya terdapat table untuk menampung data dari post dan masukan ke dalam folder post
```
php artisan make:livewire post.TablePost
```

5. Buka file table-post yang ada di ` resorces/view/livewire/post/table-post.blade.php `. Buat kode seperti di bawah ini dan tambahkan foreach untuk mengambil seluruh data dari database 
```html
<div>
    <table>
        <tr>
            <th>No</th>
            <th>Title</th=>
            <th>Author</th=>
            <th>Action</th=>
        </tr>
        @foreach ($posts as $post)
            <tr>
                <td>{{ $loop->iteration }}</td=>
                <td>{{ $post->title }}</td=>
                <td>{{ $post->author }}</td=>
                <td>Edit</td=>
                <td>Delete</td=>
            </tr>
        @endforeach
    </table>
</div>
```

6. Masuk ke dalam file CreatePost yang ada di ` app/http/Livewire/Post.CreatePost `
7. Tambahkan code di bawah ini
```javascript
public $title;
public $author;

protected $rules = [
    'title' => 'required|min:3|max:255',
    'author' => 'required|min:3|max:255'
];

public function store() {
    $this->validate();

    Post::create([
        'title' => $this->title,
        'author' => $this->author
    ]);

    $this->title = Null;
    $this->author = Null;

    // no refresh
    // sumber youtube :https://youtu.be/jd-K_z0z3C4?list=LL&t=586
    $this->emit('createPost');

    session()->flash('ok', 'Postingan baru telah ditambahkan');
}
```

8. Masuk ke dalam file TablePost yang ada di ` app/http/Livewire/Post.TablePost `
9. Lalu tambahkan kode di bawah ini
```javascript
// sumber youtube :https://youtu.be/jd-K_z0z3C4?list=LL&t=586
protected $listeners = [
    'createPost' => '$refresh'
];

public function render()
{
    return view('livewire.post.table-post', [
        'posts' => Post::latest()->get()
    ]);
}
```

Sumber Youtube: [Ferry Dermawan](https://youtu.be/2jyLnvbxxEg)