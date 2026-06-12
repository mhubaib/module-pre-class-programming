# Bab 13: Elemen Container & Elemen Semantik

## Tujuan Pembelajaran

- Membedakan perilaku tata letak bawaan antara _Block-level Element_ dan _Inline Element_.
- Menerapkan tag `<div>` dan `<span>` sebagai elemen pembungkus untuk keperluan tata letak.
- Memahami alasan penggunaan _Semantic Tag_ HTML5 sebagai pengganti `<div>` dalam membangun struktur halaman yang bermakna.

---

## Materi Utama

Pada bab-bab sebelumnya, setiap elemen HTML digunakan secara individual untuk menampilkan konten tertentu. Namun dalam praktik pengembangan web, seringkali beberapa elemen perlu dikelompokkan menjadi satu kesatuan — misalnya menggabungkan gambar profil, nama pengguna, dan deskripsi jabatan menjadi sebuah komponen kartu yang dapat diposisikan dan didesain secara bersamaan.

Untuk kebutuhan tersebut, HTML menyediakan **elemen container** — elemen yang berfungsi sebagai pembungkus atau pengelompok elemen-elemen lain.

---

### 1. Perilaku Tata Letak Bawaan: Block vs Inline

Setiap elemen HTML memiliki perilaku tata letak bawaan yang menentukan bagaimana elemen tersebut ditempatkan relatif terhadap elemen lain di sekitarnya. Terdapat dua kategori utama:

#### Block-Level Element

Elemen block selalu dimulai dari baris baru dan secara bawaan mengambil lebar penuh dari elemen induknya — dari tepi kiri hingga tepi kanan area tampilan. Elemen berikutnya akan ditempatkan di bawahnya, bukan di sampingnya.

Contoh elemen block: `<p>`, `<h1>`–`<h6>`, `<table>`, `<ul>`, `<ol>`, `<div>`.

```html
<!-- HTML: Setiap elemen block dimulai dari baris baru -->
<p>Paragraf pertama mengambil satu baris penuh.</p>
<p>Paragraf kedua dimulai dari baris baru di bawah paragraf pertama.</p>
<h2>Judul ini juga dimulai dari baris baru.</h2>
```

#### Inline Element

Elemen inline tidak memulai baris baru — ia mengikuti aliran teks dan hanya mengambil lebar sesuai dengan ukuran kontennya. Beberapa elemen inline dapat berjajar dalam satu baris selama ruang horizontal masih tersedia.

Contoh elemen inline: `<a>`, `<b>`, `<i>`, `<strong>`, `<em>`, `<span>`, `<img>`.

```html
<!-- HTML: Elemen inline berjajar dalam satu baris -->
<p>
  Kunjungi <a href="https://developer.mozilla.org">MDN Web Docs</a> untuk
  referensi <strong>HTML</strong> dan <em>CSS</em> yang lengkap.
</p>
```

**Perbandingan perilaku Block dan Inline:**

| Aspek                           | Block-Level Element            | Inline Element                             |
| ------------------------------- | ------------------------------ | ------------------------------------------ |
| Posisi awal                     | Selalu dimulai dari baris baru | Mengikuti aliran teks pada baris yang sama |
| Lebar bawaan                    | Mengambil lebar penuh induknya | Menyesuaikan lebar kontennya               |
| Dapat mengatur `width`/`height` | Ya                             | Tidak (kecuali diubah via CSS)             |
| Contoh                          | `<p>`, `<div>`, `<h1>`         | `<span>`, `<a>`, `<strong>`                |

---

### 2. Elemen Container: `<div>` dan `<span>`

Elemen container adalah elemen yang tidak memiliki tampilan visual bawaan — tidak menghasilkan perubahan gaya apa pun jika digunakan tanpa CSS. Kegunaannya adalah mengelompokkan beberapa elemen menjadi satu unit yang dapat diatur tampilannya secara bersamaan menggunakan CSS.

#### `<div>` — Container Block

`<div>` (_Division_) adalah elemen block yang digunakan untuk mengelompokkan beberapa elemen menjadi satu blok. Ketika CSS diterapkan pada `<div>`, seluruh elemen di dalamnya ikut terpengaruh.

```html
<!-- HTML -->
<div style="background-color: #eaf4fb; padding: 16px; border-radius: 8px;">
  <h2>Andi Pratama</h2>
  <p>Frontend Developer</p>
  <p>Yogyakarta, Indonesia</p>
</div>
```

**Contoh penerapan — Dua kartu yang dikelompokkan secara terpisah:**

```html
<!-- HTML -->
<div style="background-color: #d5f5e3; padding: 16px; margin-bottom: 12px;">
  <h3>Produk A</h3>
  <p>Harga: Rp 250.000</p>
  <p>Stok: Tersedia</p>
</div>

<div style="background-color: #fadbd8; padding: 16px;">
  <h3>Produk B</h3>
  <p>Harga: Rp 175.000</p>
  <p>Stok: Habis</p>
</div>
```

Dengan `<div>`, setiap kartu produk dikelompokkan sebagai satu unit — sehingga pengaturan tampilan (warna latar, jarak, dan batas) dapat diterapkan pada seluruh isi kartu sekaligus.

#### `<span>` — Container Inline

`<span>` adalah elemen inline yang digunakan untuk menargetkan bagian kecil dari teks di dalam aliran kalimat — misalnya satu kata atau frasa — tanpa memulai baris baru.

```html
<!-- HTML -->
<p>
  Sistem mendeteksi
  <span style="color: red; font-weight: bold;">kesalahan kritis</span>
  pada modul autentikasi pukul 03.42 WIB.
</p>
```

**Contoh penerapan — Menyoroti informasi penting dalam teks:**

```html
<!-- HTML -->
<p>
  Pendaftaran dibuka mulai
  <span style="color: #27ae60; font-weight: bold;">1 Juli 2025</span>
  hingga
  <span style="color: #e74c3c; font-weight: bold;">31 Juli 2025</span>. Kuota
  terbatas untuk <span style="font-style: italic;">30 peserta</span> per kelas.
</p>
```

**Panduan memilih antara `<div>` dan `<span>`:**

| Kebutuhan                                                         | Elemen yang Digunakan |
| ----------------------------------------------------------------- | --------------------- |
| Mengelompokkan beberapa elemen sebagai satu blok                  | `<div>`               |
| Menargetkan bagian teks dalam satu baris tanpa memulai baris baru | `<span>`              |

---

### 3. Dari `<div>` ke Elemen Semantik HTML5

Penggunaan `<div>` secara berlebihan untuk membangun seluruh struktur halaman menghasilkan kode HTML yang sulit dibaca — baik oleh pengembang lain maupun oleh mesin pencari. Kondisi ini sering disebut _div soup_ atau _divitis_.

```html
<!-- Contoh struktur non-semantik yang sulit dibaca -->
<div id="kepala">...</div>
<div id="navigasi">...</div>
<div id="konten-utama">
  <div id="artikel">...</div>
  <div id="sidebar">...</div>
</div>
<div id="bawah">...</div>
```

Mesin pencari seperti Google tidak dapat membedakan secara otomatis mana bagian yang merupakan konten utama, mana navigasi, dan mana informasi penutup — karena semua menggunakan tag yang sama.

HTML5 memperkenalkan **elemen semantik** — tag dengan nama yang mencerminkan fungsi dan makna kontennya secara eksplisit. Elemen-elemen ini memungkinkan mesin pencari, aplikasi pembaca layar, dan pengembang lain untuk memahami struktur halaman hanya dengan membaca tag HTML-nya.

```html
<!-- Struktur yang sama, ditulis dengan elemen semantik -->
<header>...</header>
<nav>...</nav>
<main>
  <article>...</article>
  <aside>...</aside>
</main>
<footer>...</footer>
```

**Elemen semantik utama dan fungsinya:**

| Elemen      | Setara `<div>` Lama       | Fungsi                                                                        |
| ----------- | ------------------------- | ----------------------------------------------------------------------------- |
| `<header>`  | `<div id="header">`       | Area kepala halaman — umumnya berisi logo, judul, dan navigasi utama          |
| `<nav>`     | `<div id="nav">`          | Area navigasi — berisi kumpulan tautan menu utama                             |
| `<main>`    | `<div id="main-content">` | Area konten utama — hanya boleh ada satu per halaman                          |
| `<section>` | `<div class="section">`   | Pengelompokan konten yang saling berkaitan dalam satu topik                   |
| `<article>` | `<div class="article">`   | Konten mandiri yang dapat berdiri sendiri, seperti postingan blog atau berita |
| `<aside>`   | `<div id="sidebar">`      | Konten pendukung di sisi halaman, seperti widget atau iklan                   |
| `<footer>`  | `<div id="footer">`       | Area penutup halaman — umumnya berisi hak cipta dan tautan sekunder           |

**Contoh struktur halaman lengkap menggunakan elemen semantik:**

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Blog Teknologi - WebDev Academy</title>
  </head>
  <body>
    <header>
      <h1>WebDev Academy</h1>
      <p>Panduan Belajar Web Development untuk Pemula</p>
    </header>

    <nav>
      <a href="index.html">Beranda</a> | <a href="artikel.html">Artikel</a> |
      <a href="kursus.html">Kursus</a> |
      <a href="kontak.html">Kontak</a>
    </nav>

    <main>
      <article>
        <h2>Mengenal CSS Flexbox: Panduan Lengkap untuk Pemula</h2>
        <p>Diterbitkan: 10 Juni 2025 | Penulis: Tim Redaksi</p>

        <section>
          <h3>Apa Itu Flexbox?</h3>
          <p>
            Flexbox adalah model tata letak CSS yang dirancang untuk menyusun
            elemen-elemen dalam satu dimensi — baik secara horizontal maupun
            vertikal.
          </p>
        </section>

        <section>
          <h3>Kapan Menggunakan Flexbox?</h3>
          <p>
            Flexbox paling tepat digunakan untuk menyelaraskan elemen-elemen
            dalam satu baris atau satu kolom, seperti navigasi, kartu produk,
            atau baris tombol.
          </p>
        </section>
      </article>

      <aside>
        <h3>Artikel Terkait</h3>
        <ul>
          <li><a href="#">Mengenal CSS Grid</a></li>
          <li><a href="#">Dasar-Dasar HTML5</a></li>
          <li><a href="#">Cara Kerja Box Model</a></li>
        </ul>
      </aside>
    </main>

    <footer>
      <p>&copy; 2025 WebDev Academy. Hak Cipta Dilindungi.</p>
      <p>
        <a href="kebijakan-privasi.html">Kebijakan Privasi</a> |
        <a href="syarat-ketentuan.html">Syarat &amp; Ketentuan</a>
      </p>
    </footer>
  </body>
</html>
```

---

### Kesimpulan

Memahami perbedaan antara elemen block dan inline adalah fondasi dalam membangun tata letak halaman web. Elemen `<div>` dan `<span>` menyediakan fleksibilitas sebagai container umum, sementara elemen semantik HTML5 memberikan makna yang jelas pada setiap bagian struktur halaman. Penggunaan elemen semantik yang tepat meningkatkan keterbacaan kode, mendukung aksesibilitas, dan membantu mesin pencari memahami konten halaman secara akurat.

**Panduan singkat penggunaan:**

- Perlu mengelompokkan beberapa elemen menjadi satu blok? → Gunakan **`<div>`**.
- Perlu menargetkan bagian teks dalam satu baris? → Gunakan **`<span>`**.
- Membangun struktur bagian-bagian halaman utama? → Gunakan **elemen semantik** (`<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`).

**Ringkasan Elemen:**

| Elemen      | Kategori             | Fungsi                                                       |
| ----------- | -------------------- | ------------------------------------------------------------ |
| `<div>`     | Block, non-semantik  | Container umum untuk mengelompokkan elemen-elemen block      |
| `<span>`    | Inline, non-semantik | Container umum untuk menargetkan sebagian teks dalam kalimat |
| `<header>`  | Block, semantik      | Area kepala halaman                                          |
| `<nav>`     | Block, semantik      | Area navigasi                                                |
| `<main>`    | Block, semantik      | Area konten utama halaman (satu per halaman)                 |
| `<section>` | Block, semantik      | Pengelompokan konten berdasarkan topik                       |
| `<article>` | Block, semantik      | Konten mandiri yang dapat berdiri sendiri                    |
| `<aside>`   | Block, semantik      | Konten pendukung di luar alur konten utama                   |
| `<footer>`  | Block, semantik      | Area penutup halaman                                         |

**Panduan Pemilihan Elemen:**

| Kebutuhan                                                       | Elemen yang Digunakan |
| --------------------------------------------------------------- | --------------------- |
| Mengelompokkan elemen untuk keperluan CSS tanpa makna khusus    | `<div>`               |
| Menargetkan kata atau frasa dalam teks untuk diberi gaya CSS    | `<span>`              |
| Area kepala halaman dengan logo dan navigasi                    | `<header>`            |
| Kumpulan tautan menu navigasi                                   | `<nav>`               |
| Konten inti halaman                                             | `<main>`              |
| Postingan blog, artikel berita, atau ulasan produk              | `<article>`           |
| Sub-topik dalam sebuah artikel atau halaman                     | `<section>`           |
| Widget, iklan, atau tautan terkait di sisi halaman              | `<aside>`             |
| Informasi hak cipta dan tautan sekunder di bagian bawah halaman | `<footer>`            |
