# Bab 3: Struktur Dasar HTML

## Tujuan Pembelajaran

- Mengenali dan menghafalkan struktur kerangka wajib (_boilerplate_) dari kode HTML.
- Memahami secara mendalam perbedaan fungsi antara bagian `<head>` dan `<body>`.
- Mampu membuat dan menjalankan file HTML riil di komputermu secara mandiri.
- Menguasai cara menambahkan Favicon untuk memberikan kesan profesional pada websitemu.

## Materi Utama

Sama seperti membuat surat resmi yang memiliki aturan baku (ada bagian Tanggal Surat, Alamat Tujuan, Isi Surat, dan Tanda Tangan), HTML juga memiliki kerangka dasar yang mutlak harus ditulis.
Di dunia programming, kerangka/template dasar sebuah file kode yang berulang-ulang kita pakai sering disebut dengan istilah **Boilerplate**.

### 1. Membedah Kerangka Dasar HTML5

Setiap kali kamu membuat file dengan akhiran `.html` (contoh: `profil-saya.html`), kamu HARUS mengetikkan rentetan kode ini di baris paling awal. Ini adalah "Surat Pengantar" untuk Web Browser.

Berikut adalah sintaks standar Boilerplate HTML5:

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Website Pertamaku</title>
  </head>
  <body>
    <!-- Di sinilah semua elemen visual diletakkan -->
    <h1>Halo Dunia!</h1>
    <p>Ini adalah langkah pertamaku menjadi Web Developer.</p>
  </body>
</html>
```

Mari kita pecah dan pahami satu demi satu fungsinya agar kamu tidak sekadar menghafal mati:

- `<!DOCTYPE html>`: Ini adalah Deklarasi (Document Type Declaration). Letaknya wajib ada di baris pertama nomor 1. Fungsinya untuk memberi tahu mesin browser, _"Mulai sekarang, bacalah dokumen di bawah ini dengan standar peraturan HTML5 yang paling baru."_ Jika kode ini ketinggalan, browser kadang akan bingung dan mengacak-acak tampilan websitemu (dikenal dengan istilah _Quirks Mode_).
- `<html lang="id">`: Ini adalah **Akar Element (Root)** yang "memeluk" seluruh dokumen web. Layaknya kardus besar yang membungkus semua tag lain. Atribut `lang="id"` memberi info ke Google Search bahwa konten website ini berbahasa Indonesia (`en` untuk Inggris).
- **`<head>`**: Bagian "Kepala".
- **`<body>`**: Bagian "Badan".

**Analogi Gedung Teater untuk `<head>` vs `<body>`**

Bagi pemula, seringkali ada kebingungan di mana harus menaruh kode kita (Apakah di head? Atau body?). Bayangkan file HTML sebagai sebuah Gedung Teater pementasan drama.

- **`<head>` adalah Ruang Kendali/Backstage (Ruang Rahasia di belakang panggung).**
  Segala sesuatu yang kamu tulis di dalam `<head>` ... `</head>` **TIDAK AKAN** terlihat di panggung (di layar putih browser milik pengunjung internet). Ruangan ini murni berisi "Sistem Pengaturan" (_meta data_) yang mengatur lalu lintas website.
  - `<meta charset="UTF-8">`: Instruksi teknis yang mengatur agar browser mampu merender dan membaca huruf rumit (Jepang, Arab, sampai emoji 🚀) tanpa mengubahnya menjadi simbol kotak-kotak error ``.
  - `<meta name="viewport"...>`: Senjata rahasia untuk membuat website-mu ramah di layar gawai pintar (Responsive).
  - `<title>`: Satu-satunya bagian `<head>` yang terlihat oleh pengunjung. Teks "Website Pertamaku" ini akan nongol di Tab Bar atas browsermu, bukan di layarnya.

- **`<body>` adalah Panggung Utama (Stage).**
  Apa pun yang ingin kamu tujukan ke MATA pengunjung (Aktor, Lampu sorot, Properti) WAJIB diletakkan di dalam `<body>` ... `</body>`. Teks, paragraf (`<p>`), judul (`<h1>`), gambar (`<img>`), hingga tombol, jika ditulis di luar `<body>` tidak akan dirender dengan benar/sah oleh browser.

### 2. Mempercantik Tab dengan Favicon (Favorite Icon)

Pernahkah kamu memperhatikan logo-logo berukuran amat mungil di tab browser saat membuka web besar? Logo kotak biru berhuruf 'F' milik Facebook, ikon keranjang oranye milik Shopee, atau logo huruf 'G' milik Google. Ikon mini yang nongkrong berdampingan dengan teks Title tersebut dinamai **Favicon**.

Favicon mampu meningkatkan prestise dan kejelasan navigasi websitemu jika pengguna sedang membuka puluhan tab sekaligus.

**Bagaimana cara menampilkannya?**
Karena settingan tab browser masuk teritori "sistem", maka kita harus mengatur Favicon di dalam kurungan `<head>`.

```html
<head>
  <meta charset="UTF-8" />
  <title>Website dengan Favicon</title>

  <!-- Cara menyisipkan Favicon -->
  <link rel="icon" type="image/x-icon" href="logo-website.png" />
</head>
```

Langkah kerjanya:

1. Tag yang dipakai adalah `<link>`, ia adalah tag tunggal yang mengatur hubungan luar file.
2. Atribut `rel="icon"` adalah instruksi: "Relasikan (Relation) file ini sebagai 'icon'."
3. Atribut `href="logo-website.png"` menunjuk nama lokasi file fotonya yang ada di komputermu.

_Tips: Sangat disarankan rasio gambar Favicon-mu berbentuk persegi sama sisi (contoh: 512x512 pixel) dan menggunakan format .png agar transparansi latar belakang tetap terjaga._
