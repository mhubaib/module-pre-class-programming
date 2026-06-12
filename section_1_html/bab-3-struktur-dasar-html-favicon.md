# Bab 3: Struktur Dasar HTML

## Tujuan Pembelajaran

- Mengenali dan memahami struktur kerangka dasar (_boilerplate_) HTML.
- Memahami perbedaan fungsi antara bagian `<head>` dan `<body>`.
- Mampu membuat dan menjalankan file HTML di komputer secara mandiri.
- Mengetahui cara menambahkan Favicon untuk tampilan tab browser yang lebih profesional.

---

## Materi Utama

Sama seperti surat resmi yang memiliki struktur baku — tanggal, alamat tujuan, isi, dan tanda tangan — HTML juga memiliki kerangka dasar yang wajib ditulis di setiap file. Kerangka berulang yang selalu digunakan sebagai titik awal disebut **Boilerplate**.

---

### 1. Boilerplate HTML5

Setiap file dengan ekstensi `.html` harus dimulai dengan kerangka berikut:

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Website Pertamaku</title>
  </head>
  <body>
    <h1>Halo Dunia!</h1>
    <p>Ini adalah langkah pertamaku menjadi Web Developer.</p>
  </body>
</html>
```

> **Pintasan di VSCode:** Ketik `!` lalu tekan Tab atau Enter. VSCode akan menghasilkan boilerplate HTML5 secara otomatis.

---

### 2. Penjelasan Setiap Bagian

#### `<!DOCTYPE html>`

Ditulis di baris pertama, sebelum tag apa pun. Baris ini memberitahu browser bahwa dokumen ini menggunakan standar **HTML5** — versi HTML terbaru. Tanpa deklarasi ini, browser mungkin masuk ke mode kompatibilitas lama (_Quirks Mode_) yang dapat menyebabkan tampilan tidak konsisten.

```html
<!DOCTYPE html> ← Harus selalu ada di baris pertama
<html>
  ...
</html>
```

#### `<html lang="id">`

Element root yang membungkus seluruh konten dokumen. Atribut `lang` memberitahu browser dan mesin pencari bahwa konten halaman ini berbahasa Indonesia (`id`). Gunakan `en` untuk bahasa Inggris.

```html
<html lang="id">
  <!-- Bahasa Indonesia -->
  <html lang="en">
    <!-- Bahasa Inggris -->
  </html>
</html>
```

#### `<head>` — Area Metadata

Bagian `<head>` berisi informasi tentang halaman yang tidak ditampilkan secara visual kepada pengunjung. Isinya adalah instruksi teknis untuk browser, mesin pencari, dan layanan eksternal.

**Isi umum `<head>`:**

| Tag                          | Fungsi                                                      |
| ---------------------------- | ----------------------------------------------------------- |
| `<meta charset="UTF-8">`     | Mendukung semua karakter termasuk huruf non-Latin dan emoji |
| `<meta name="viewport" ...>` | Mengoptimalkan tampilan di perangkat mobile                 |
| `<title>`                    | Teks yang tampil di tab browser dan hasil pencarian Google  |
| `<link rel="stylesheet">`    | Menghubungkan file CSS eksternal                            |
| `<meta name="description">`  | Deskripsi halaman untuk mesin pencari                       |

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta
    name="description"
    content="Website portofolio Budi Santoso, Front-End Developer."
  />
  <title>Portofolio — Budi Santoso</title>
  <link rel="stylesheet" href="style.css" />
</head>
```

**Penjelasan meta viewport:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

- `width=device-width` — Lebar halaman mengikuti lebar layar perangkat.
- `initial-scale=1.0` — Halaman tidak diperbesar atau diperkecil saat pertama kali dimuat.

Tanpa tag ini, browser mobile akan menampilkan halaman dalam versi desktop yang diperkecil, sehingga teks menjadi sangat kecil dan sulit dibaca.

#### `<body>` — Area Konten Visual

Semua elemen yang ingin ditampilkan kepada pengunjung — teks, gambar, tombol, formulir, navigasi — ditulis di dalam `<body>`. Apa pun yang ditulis di luar `<body>` tidak akan dirender dengan benar oleh browser.

```html
<body>
  <header>
    <nav>...</nav>
  </header>

  <main>
    <h1>Selamat Datang</h1>
    <p>Ini adalah halaman utama.</p>
  </main>

  <footer>
    <p>© 2026 Nama Website</p>
  </footer>
</body>
```

**Perbedaan `<head>` vs `<body>`:**

|                           | `<head>`                                    | `<body>`                                    |
| ------------------------- | ------------------------------------------- | ------------------------------------------- |
| Terlihat oleh pengunjung? | Tidak (kecuali `<title>`)                   | Ya — semua kontennya terlihat               |
| Isinya                    | Metadata, pengaturan, tautan file eksternal | Teks, gambar, tombol, formulir, dll.        |
| Tag umum di dalamnya      | `<meta>`, `<title>`, `<link>`, `<script>`   | `<h1>–<h6>`, `<p>`, `<img>`, `<a>`, `<div>` |

---

### 3. Membuat dan Menjalankan File HTML

**Langkah-langkah:**

1. Buat folder baru di komputer, misalnya `belajar-html`.
2. Buka folder tersebut di VSCode: `File → Open Folder`.
3. Buat file baru bernama `index.html`.
4. Ketik `!` lalu tekan Enter untuk membuat boilerplate otomatis.
5. Tambahkan konten di dalam `<body>`.
6. Simpan file (`Ctrl+S` / `Cmd+S`).
7. Buka file di browser: klik kanan file → **Open with Live Server** (jika menggunakan ekstensi Live Server), atau buka langsung di browser dengan drag-and-drop.

**Contoh file pertama yang lengkap:**

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Halaman Pertama Saya</title>
  </head>
  <body>
    <h1>Halo, nama saya Budi!</h1>
    <p>Ini adalah halaman web pertama yang saya buat sendiri.</p>
    <p>Saya sedang belajar HTML dan CSS.</p>
  </body>
</html>
```

---

### 4. Favicon — Ikon di Tab Browser

**Favicon** (Favorite Icon) adalah ikon kecil yang tampil di tab browser di sebelah judul halaman. Favicon membantu pengguna mengenali website dengan cepat ketika membuka banyak tab sekaligus.

Karena favicon adalah pengaturan tampilan tab browser (bukan konten visual halaman), ia didefinisikan di dalam `<head>` menggunakan tag `<link>`.

```html
<head>
  <meta charset="UTF-8" />
  <title>Website dengan Favicon</title>
  <link rel="icon" type="image/png" href="favicon.png" />
</head>
```

**Penjelasan atribut:**

| Atribut | Nilai           | Fungsi                                  |
| ------- | --------------- | --------------------------------------- |
| `rel`   | `"icon"`        | Mendefinisikan relasi file sebagai ikon |
| `type`  | `"image/png"`   | Format file gambar                      |
| `href`  | `"favicon.png"` | Lokasi file gambar favicon              |

**Contoh dengan beberapa ukuran favicon:**

Browser modern dapat menggunakan ukuran favicon yang berbeda untuk berbagai konteks (tab, bookmark, layar ponsel). Kamu dapat mendefinisikan lebih dari satu:

```html
<head>
  <link rel="icon" type="image/png" sizes="32x32" href="favicon-32.png" />
  <link rel="icon" type="image/png" sizes="16x16" href="favicon-16.png" />
  <link rel="apple-touch-icon" sizes="180x180" href="favicon-apple.png" />
</head>
```

**Rekomendasi file favicon:**

- Format: `.png` (mendukung latar belakang transparan) atau `.ico` (format lama, kompatibel di semua browser)
- Ukuran: minimal `32x32` pixel; gunakan gambar persegi
- Nama file yang umum digunakan: `favicon.ico` atau `favicon.png`

**Contoh struktur folder proyek lengkap:**

```
proyek-website/
├── index.html
├── style.css
├── script.js
└── favicon.png
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Website portofolio saya." />
    <title>Portofolio Saya</title>
    <link rel="icon" type="image/png" href="favicon.png" />
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1>Selamat datang di portofolio saya.</h1>
  </body>
</html>
```

---

### Kesimpulan

Struktur boilerplate HTML5 adalah fondasi dari setiap halaman web. Memahami fungsi setiap bagiannya — bukan sekadar menghafalnya — akan memudahkan proses pembuatan dan pemeliharaan website di masa mendatang.

**Ringkasan:**

| Bagian                   | Fungsi                                                                       |
| ------------------------ | ---------------------------------------------------------------------------- |
| `<!DOCTYPE html>`        | Memberitahu browser untuk menggunakan standar HTML5                          |
| `<html lang="id">`       | Element root; atribut `lang` mendefinisikan bahasa konten                    |
| `<head>`                 | Berisi metadata dan pengaturan teknis; tidak terlihat secara visual          |
| `<meta charset="UTF-8">` | Mendukung seluruh karakter Unicode termasuk non-Latin                        |
| `<meta name="viewport">` | Mengoptimalkan tampilan di perangkat mobile                                  |
| `<title>`                | Teks yang tampil di tab browser dan hasil pencarian                          |
| `<body>`                 | Berisi seluruh konten visual yang ditampilkan ke pengunjung                  |
| Favicon                  | Ikon kecil di tab browser; didefinisikan via `<link rel="icon">` di `<head>` |
