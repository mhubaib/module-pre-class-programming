# Bab 14: Iframe & Ikon Eksternal

## Tujuan Pembelajaran

- Bisa memahami konsep _Embedding_ menyusupkan halaman website utuh orang lain mendarat nyempil di permukaan HTML kita.
- Menguasai teknik instalasi dewa Peta Google Map atau Player YouTube menggunakan senjata canggih `<iframe>`.
- Mengundang ikon visual modern ke kanvas kita tanpa pusing nyari gambar `.png` via pustaka sakti FontAwesome (Teknik Eksternal Icon).

## Materi Utama

Terkadang, mencipatkan fungsional mandiri 100% sendirian adalah kerja bodoh (Reinventing The Wheel). Bayangkan klien yang punya Toko Roti minta dibangunkan fitur Peta Interaktif di navigasi websitenya. Bikin sirkuit Peta GIS memakan ribuan baris kode! Mengapa tidak kita tempel colong saja "Google Maps" masuk bersarang ke web kita?

Di sinilah seninya web modern bermain, pinjam meminjam fungsi antar situs memakai **Iframe** dan perpustakaan eksternal (CDN Ikon).

### 1. Tag Portal Lintas Dimensi: `<iframe>`

Iframe (Inline Frame) adalah semacam jendela bolong portal di dimensi dinding halamanmu. Lewat jendela bingkai tersebut, pengguna bisa mengintip seutuhnya beroperasinya website alam semesta eksternal milik orang lain tanpa pernah beranjak kaki dari pelataran domainmu.

Penulisannya sederhana persis perpaduan gambar `<img src="...">` digabung ukuran pixel murni!

**Analogi Jendela Tembus Pandang:**
Kalau web kamu itu sebuah tembok rumah utuh kamar.. Iframe layaknya sebuah jendela kaca. Melalui jendela kaca itu, kamu membiarkan pemandangan tetangga (misal web Youtube) terpampang berinteraksi lalu lalang nyata.

```html
<!-- Manggil portal cermin nampilin artikel Wikipedia pas di perut Web kita! -->
<iframe
  src="https://id.wikipedia.org/"
  width="500"
  height="400"
  title="Kotak Wiki Ajaib"
></iframe>
```

### 2. Embed Player YouTube tanpa Coding JS (Praktek Iframe #1)

Developer Google/Youtube sangat memanjakan coder pemula. Kita bisa langsung menyedot pemutar videonya untuk dipajang gratis!
Tahap manual copasnya gampang:

1. Buka YouTube di laptop, play video viral incaranmu.
2. Klik tombol Menu **Bagikan / Share**, dan tekan logo bulet gembok bersilang `"< >"` bertuliskan rajutan emas **"Sematkan/Embed"**.
3. _Boom!_ Youtube ngasih script barisan `<iframe ...>` siap hidang yang tinggal dicopas taruh di IDE Visual Studio Code-mu!.

Pola rahasia Youtube pada `src`-nya adalah `youtube.com/embed/ID_Videonya_Disini`.

```html
<h2>Tutorial Membuat Tempe Goreng</h2>
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/dQw4w9WgXcQ"
  title="YouTube video player"
  frameborder="0"
  allowfullscreen
></iframe>
```

_Note penting: atribut bonus `allowfullscreen` mempersilakan penonton menswipe layarnya jadi layar penuhh mode bioskop!_

### 3. Embed Peta Google (Google Maps Canggih)

Sama kasusnya kalau kamu bikin template portofolio Undangan Pernikahan atau alamat PT/Toko kelontong, seribu kali elegan pakai Peta Asli geser _touchscreen_ alih-alih screenshot gambar JPEG mandeg mati.

Tahap copasnya di web aslinya:

1. Cari target lokasi di _maps.google.com_.
2. Tekan menu Share **"Bagikan"** berlogo titik tiga rantai.
3. Sorot tabulasi pilihan atas: Pilih yang klik **"Sematkan Peta" / "Embed a Map"**.
4. Copas kode HTML raksasa `<iframe..>` yang ada `src="https://www.google.com/maps/embed?pb=...."` di sana.

### 4. Menggunakan Perpustakaan Ikon Online Sedunia (Alternatif Favicon / Ikon UI UX)

Mengawali bab Bab 3 dulu, kita bikin logo Favorit Web tab (_Favicon_) pakai metode tradisional cari foto `kucing.png` dan pasang Link manual satu persatu pakai File gambar!
Hal tersebut kuno di masa Front-End masa kini. Jika kamu meletakkan seribu Icon Keranjang/Delete/Trash Can di Web, naruh pakai ratusan file _img_ akan ngabisin _Storage Bandwidth_ hosting server dan Web bakal lelet berjam-jam saat muat foto!.

Kini kita bertransisi memanggil **Icon Font**! Yaitu simbol huruf/teks biasa tapi dimanipulasi otak sihir CSS dari Website Pustaka Ikon Eksternal bernama dewa **FontAwesome** (Font pemersatu web sedunia).

_Langkah 1:_ Taruh tautan URL FontAwesome (_CDN link generator_) ini tepat mengapung nyempil di sarang `HEAD` (Biar sistem HTML mu mengemis minjem rumus gambar CSS-nya dari pangkalan data di luar angkasa server jarak jauh):

```html
<head>
  <!-- Menghubungi Server FontAwesome diam di background -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
  />
</head>
```

_Langkah 2:_ Setelah terhubung, barulah lempar tag kosong inline `<i>` dan modifikasi memakai Atribut "Class / Klasifikasi jenis" rahasia yang tercetak di buku katalog website Font Awesome, misal serdadu simbol `fa-solid`, atau jenis gambar `fa-house`/ `fa-user`:

```html
<body>
  <p>
    Mari kita kemping di <i class="fa-solid fa-tent"></i> (Coba renderingnya ini
    logo Tenda Kemah vector!).
  </p>
  <button><i class="fa-solid fa-download"></i> Unduh File Resumenya</button>
</body>
```

_Pelajaran besar: Ikon vektor ini sungguhan bisa dibesarkan sampai gajah tanpa pecah pecah Blur buram selayaknya penyakit pixel gambar JPG/PNG biasa!_
