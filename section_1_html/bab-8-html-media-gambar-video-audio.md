# Bab 8: HTML Media (Gambar, Video, Audio)

## Tujuan Pembelajaran

- Mampu memahami cara menyisipkan berbagai konten multimedia (gambar, audio, dan video).
- Menguasai penggunaan tag `<img>` beserta atribut `src` dan `alt`.
- Mengenali tag `<video>` dan `<audio>` fitur canggih dari HTML5.
- Mempraktekkan atribut kontrol untuk memutar media (Play, Pause, Volume).

## Materi Utama

Website yang isinya hanya teks seratus persen akan terlihat seperti koran jadul yang sangat kering dan membosankan. Kekuatan utama web modern terletak pada multimedia: memadukan warna cerah lewat gambar ilustrasi, memberikan lagu latar asyik, hingga memutar video langsung secara mulus.

Di bab ini, kita akan belajar memajang lukisan dan memasang TV di dinding HTML-mu.

### 1. Menampilkan Gambar (Tag `<img>`)

Untuk memajang gambar, kita menggunakan tag **Image** atau disingkat `<img>`.
Sifat unik dari `<img`> adalah: ia merupakan **Self-Closing Tag (Tag Tunggal)**. Ia tidak memiliki tag penutup `</img>` dan _tidak mungkin_ membungkus teks.

Dua sekawan atribut utama yang **WAJIB** menempel pada tag img adalah:

- `src` (Source): Menyimpan alamat (path) letak file gambar berada.
- `alt` (Alternative text): Menyediakan deskripsi rahasia bagi penyandang disabilitas (dan mesin Google) jika gambar gagal termuat akibat koneksi bermasalah.

**Analogi Memajang Bingkai Foto:**
Tag `<img>` ibarat sebuah bingkai pigura kosong transparan di dinding kamarmu. Atribut `src` adalah file lembaran foto aslinya yang kamu masukkan ke dalam bingkai tersebut. Sementara atribut `alt` adalah secarik kertas kecil yang kamu tempel di balik bingkai; jika fotonya luntur atau dicuri orang, kertas kecil itu bisa memberi tahu orang lain foto apa yang dulunya ada di situ.

```html
<!-- Mengambil gambar langsung dari internet (Absolute) -->
<img
  src="https://images.unsplash.com/kucing.jpg"
  alt="Foto Kucing Oren Melompat"
/>

<!-- Mengambil gambar dari folder komputer sendiri (Relative) -->
<img src="foto-keluarga.png" alt="Foto bersama keluarga di pantai" />
```

_Tips Mengatur Ukuran:_ Kamu juga bisa menambahkan atribut `width` (lebar) dan `height` (tinggi) langsung dalam HTML. Nilainya menggunakan rasio _pixel_.

```html
<img src="logo.png" alt="Logo Perusahaan" width="200" height="200" />
```

### 2. Memutar Audio dan Musik (Tag `<audio>`)

Dulu (sebelum era HTML5), memasang lagu Murottal atau musik pop MP3 di website membutuhkan plugin berat seperti _Flash Player_. Kini, bernapaslah lega karena HTML5 menghadirkan tag sakti bernama `<audio>`. File yang didukung biasanya berformat `.mp3` atau `.ogg`.

Untuk memunculkan tampilan "Music Player" (tombol Play, Pause, durasi, volume slider), kita wajib menambahkan atribut sakti: `controls`. Tanpa `controls`, lagumu akan berstatus ghaib (tidak bisa diklik apa-apa).

```html
<audio controls>
  <source src="lagu-santai.mp3" type="audio/mpeg" />
  <source src="lagu-santai.ogg" type="audio/ogg" />
  Browser kamu terlalu jadul, tidak mendukung fitur audio ini Bro!
</audio>
```

**Mengapa ada dua `<source>` di dalamnya?**
Sebagai programmer Web, kamu harus mengantisipasi bahwa tidak semua browser di dunia diciptakan sama (Safari menangani audio berbeda dengan Chrome). Kamu menyediakan alternatif file. Browser akan mencoba memutar file baris pertama (.mp3). Jika gagal dibaca, browser akan mundur memutar file baris kedua (.ogg). Teks paling bawah otomatis tampil jika kedua file gagal total diputar oleh sistem si pengguna.

### 3. Menampilkan Video Langsung (Tag `<video>`)

Sama persis secara konsep dengan `<audio>`, namun kali ini menyajikan tayangan visual dan suara. Format juara bertahan untuk web selalu berada pada ekstensi `.mp4`.

Tag `<video>` luar biasa modifiable! Kamu bisa memberikan ukuran lebar-tinggi yang spesifik (_width/height_), dan lagi-lagi... jangan lupa pasangkan atribut `controls` jika ingin melihat tombol pemutarnya.

```html
<video width="640" height="360" controls>
  <source src="video-kenangan-sekolah.mp4" type="video/mp4" />
  <source src="video-kenangan-sekolah.webm" type="video/webm" />
  Maaf, videonya gagal dimuat di browsermu.
</video>
```

**Bumbu Tambahan Rahasia untuk `<video>` dan `<audio>`:**
Apakah kamu penasaran bagaimana video iklan di website berita sering berjalan otomatis tanpa perlu di-klik? Berikut atribut tambahan rahasianya:

- `autoplay`: Media otomatis diputar (_Play_) segera setelah web terbuka (Catatan: Chrome modern akan memblokir _autoplay_ bersuara keras kecuali digabung dengan _Muted_).
- `muted`: Media diputar dalam kondisi dibisukan (volume 0%).
- `loop`: Media akan terus mengulang pemutarannya ke awal saat mencapai detik terakhir tiada henti.
- `poster` (khusus Video): Mengatur gambar statis (sayup/thumbnail jilid) yang tampil sebelum tayangan video di-Play (seperti _thumbnail_ di Youtube).

Contoh video Autoplay Looping layaknya tayangan papan reklame digital:

```html
<video src="reklame.mp4" autoplay muted loop width="100%"></video>
```
