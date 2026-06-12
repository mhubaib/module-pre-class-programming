# Bab 9: Optimasi SEO di HTML

## Tujuan Pembelajaran

- Memahami definisi SEO dan perannya terhadap visibilitas halaman web di mesin pencari.
- Menerapkan Meta Tags (`title`, `description`) di dalam elemen `<head>` untuk keperluan SEO.
- Mengimplementasikan elemen Semantic HTML yang membantu mesin pencari memahami struktur halaman.
- Menerapkan hierarki heading (`<h1>`–`<h6>`) yang benar sesuai standar SEO.

---

## Materi Utama

Sebuah halaman web yang sudah dibangun dengan baik secara teknis belum tentu dapat ditemukan oleh pengguna internet. Jika halaman tersebut tidak muncul di hasil pencarian mesin pencari seperti Google, seluruh konten di dalamnya tidak akan menjangkau audiens yang dituju.

Di sinilah peran **SEO** (_Search Engine Optimization_) — serangkaian praktik terstruktur yang bertujuan meningkatkan visibilitas halaman web di hasil pencarian organik. Fondasi dari SEO yang baik dimulai dari penulisan kode HTML yang tepat.

---

### 1. Meta Tags di Dalam Elemen `<head>`

Mesin pencari seperti Google menggunakan program otomatis yang disebut _crawler_ atau _bot_ untuk membaca dan mengindeks halaman web. Program ini tidak mengevaluasi tampilan visual — ia membaca kode HTML dari atas ke bawah untuk menentukan topik dan relevansi halaman.

Area `<head>` adalah tempat utama yang dibaca oleh _crawler_ untuk mendapatkan informasi ringkas tentang halaman. Dua elemen yang paling berpengaruh di area ini adalah `<title>` dan `<meta name="description">`.

#### A. Title Tag

Elemen `<title>` menentukan judul halaman yang ditampilkan di tab browser dan sebagai judul tautan di hasil pencarian Google. Judul ini adalah salah satu faktor SEO yang paling signifikan.

**Panduan penulisan title yang baik:**

- Maksimal 60 karakter agar tidak terpotong di hasil pencarian.
- Sertakan kata kunci utama yang relevan dengan isi halaman.
- Hindari judul yang terlalu umum seperti "Beranda" atau "Home" karena tidak memberikan informasi yang berguna kepada mesin pencari maupun pengguna.

```html
<!-- Kurang baik: terlalu umum, tidak informatif -->
<title>Beranda</title>

<!-- Baik: spesifik, mengandung kata kunci, dan menyebutkan nama bisnis -->
<title>Kursus Potong Rambut Pria Terbaik Jakarta - BudiBarber</title>
```

**Contoh penerapan pada berbagai jenis halaman:**

```html
<!-- HTML -->

<!-- Halaman utama toko online -->
<title>Sepatu Lari Pria & Wanita Terlengkap - TokoSepatu.id</title>

<!-- Halaman artikel blog -->
<title>10 Tips Belajar HTML untuk Pemula di 2025 - WebDev Academy</title>

<!-- Halaman produk spesifik -->
<title>Nike Air Max 270 - Sepatu Lari Pria | TokoSepatu.id</title>

<!-- Halaman kontak -->
<title>Hubungi Kami - BudiBarber Jakarta Selatan</title>
```

#### B. Meta Description

Elemen `<meta name="description">` menyediakan ringkasan singkat tentang isi halaman. Teks ini ditampilkan di bawah judul tautan pada halaman hasil pencarian, dan berperan penting dalam mendorong pengguna untuk mengklik tautan tersebut.

**Panduan penulisan meta description yang baik:**

- Panjang optimal: 150–160 karakter.
- Tulis dalam kalimat yang jelas dan meyakinkan.
- Sertakan kata kunci yang relevan secara alami dalam kalimat.
- Hindari pengulangan kata kunci yang berlebihan (_keyword stuffing_).

```html
<!-- HTML -->
<head>
  <meta charset="UTF-8" />
  <title>Kursus Potong Rambut Pria Terbaik Jakarta - BudiBarber</title>
  <meta
    name="description"
    content="Daftar sekarang di BudiBarber — akademi potong rambut terkemuka di Jakarta. Diajarkan oleh instruktur berpengalaman lebih dari 15 tahun. Tersedia kelas untuk pemula."
  />
</head>
```

**Contoh penerapan pada berbagai jenis halaman:**

```html
<!-- HTML -->

<!-- Halaman artikel -->
<meta
  name="description"
  content="Pelajari 10 tips praktis belajar HTML untuk pemula, mulai dari alat yang dibutuhkan hingga langkah membangun halaman web pertama Anda dari nol."
/>

<!-- Halaman produk -->
<meta
  name="description"
  content="Nike Air Max 270 tersedia dalam berbagai ukuran dan warna. Sepatu lari pria dengan teknologi bantalan udara terbaru. Gratis ongkir ke seluruh Indonesia."
/>
```

---

### 2. Semantic HTML (Elemen Berstruktur Bermakna)

Sebelum HTML5, struktur halaman web umumnya dibangun menggunakan tag `<div>` untuk semua bagian — header, navigasi, konten utama, sidebar, dan footer semuanya menggunakan `<div>`. Pendekatan ini membuat _crawler_ mesin pencari sulit memahami struktur dan hierarki konten halaman.

HTML5 memperkenalkan **elemen semantik** — tag yang memiliki nama sesuai fungsi dan maknanya, sehingga baik mesin pencari maupun pengembang lain dapat memahami struktur halaman hanya dengan membaca kode HTML.

**Perbandingan struktur non-semantik dan semantik:**

```html
<!-- Struktur lama (non-semantik) — semua bagian menggunakan <div> -->
<div id="header">...</div>
<div id="nav">...</div>
<div id="content">...</div>
<div id="footer">...</div>

<!-- Struktur modern (semantik) — setiap bagian memiliki tag yang bermakna -->
<header>...</header>
<nav>...</nav>
<main>...</main>
<footer>...</footer>
```

**Elemen semantik utama dan fungsinya:**

| Elemen      | Fungsi                                                                                      |
| ----------- | ------------------------------------------------------------------------------------------- |
| `<header>`  | Area kepala halaman — umumnya berisi logo, judul situs, dan navigasi utama                  |
| `<nav>`     | Kumpulan tautan navigasi utama — Google mengidentifikasi area ini sebagai peta situs        |
| `<main>`    | Konten utama halaman — hanya boleh ada satu per halaman; berguna untuk aksesibilitas        |
| `<article>` | Konten mandiri yang dapat berdiri sendiri — seperti postingan blog atau berita              |
| `<section>` | Pengelompokan konten yang saling berkaitan di dalam halaman                                 |
| `<aside>`   | Konten pendukung yang terkait namun tidak termasuk konten utama — seperti widget atau iklan |
| `<footer>`  | Area penutup halaman — umumnya berisi informasi hak cipta, kontak, dan tautan sekunder      |

**Contoh struktur halaman web modern dengan elemen semantik:**

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Gaya Rambut Pria Terpopuler 2025 - BudiBarber</title>
    <meta
      name="description"
      content="Temukan inspirasi gaya rambut pria terpopuler di 2025. Panduan lengkap dari kapster profesional BudiBarber Jakarta."
    />
  </head>
  <body>
    <header>
      <h1>BudiBarber</h1>
      <p>Akademi Potong Rambut Profesional Jakarta</p>
    </header>

    <nav>
      <a href="index.html">Beranda</a> |
      <a href="kursus.html">Program Kursus</a> |
      <a href="galeri.html">Galeri</a> |
      <a href="kontak.html">Kontak</a>
    </nav>

    <main>
      <article>
        <h2>Gaya Rambut Pria Terpopuler 2025</h2>
        <p>
          Tahun 2025 menghadirkan sejumlah tren gaya rambut pria yang dominan,
          mulai dari potongan Comma Hair hingga French Crop yang kembali naik
          daun.
        </p>

        <section>
          <h3>1. Comma Hair</h3>
          <p>
            Gaya ini ditandai dengan poni yang melengkung ke satu sisi,
            menyerupai bentuk tanda koma. Cocok untuk wajah oval dan lonjong.
          </p>
        </section>

        <section>
          <h3>2. French Crop</h3>
          <p>
            Potongan pendek di bagian samping dengan poni tipis lurus di depan.
            Memberikan kesan rapi dan tegas sesuai untuk berbagai kesempatan.
          </p>
        </section>
      </article>

      <aside>
        <h3>Program Kursus Pilihan</h3>
        <ul>
          <li><a href="kursus.html#dasar">Kursus Dasar (3 Hari)</a></li>
          <li><a href="kursus.html#lanjutan">Kursus Lanjutan (7 Hari)</a></li>
          <li>
            <a href="kursus.html#profesional">Kursus Profesional (14 Hari)</a>
          </li>
        </ul>
      </aside>
    </main>

    <footer>
      <p>&copy; 2025 BudiBarber. Hak Cipta Dilindungi.</p>
      <p>
        Jl. Melati No. 25, Jakarta Selatan |
        <a href="mailto:info@budibarber.id">info@budibarber.id</a>
      </p>
    </footer>
  </body>
</html>
```

---

### 3. Hierarki Heading yang Benar

Mesin pencari membaca heading sebagai daftar isi dari halaman — mulai dari topik utama (`<h1>`) hingga sub-topik yang semakin spesifik. Hierarki heading yang tidak teratur akan menyulitkan mesin pencari dalam memahami struktur konten.

**Tiga aturan utama penggunaan heading untuk SEO:**

**1. Satu `<h1>` per halaman.**
`<h1>` merepresentasikan topik utama halaman. Menggunakan lebih dari satu `<h1>` membingungkan mesin pencari mengenai fokus utama halaman. Jika dibutuhkan teks berukuran besar untuk keperluan visual, gunakan CSS — bukan dengan menduplikasi `<h1>`.

**2. Urutan tingkatan heading harus berurutan.**
Setiap sub-topik berada satu tingkat di bawah topik induknya. Dari `<h1>` turun ke `<h2>`, dari `<h2>` turun ke `<h3>`, dan seterusnya. Setelah sub-topik selesai, kembali ke tingkat yang sesuai untuk topik berikutnya.

**3. Hindari melompati tingkatan heading.**
Berpindah langsung dari `<h2>` ke `<h4>` tanpa `<h3>` di antaranya adalah pelanggaran struktur yang merusak logika hierarki dokumen.

**Perbandingan — hierarki yang salah vs benar:**

```html
<!-- SALAH: melompati tingkatan heading -->
<h1>Panduan Belajar Web Development</h1>
<h3>Apa itu HTML?</h3>
<!-- Salah: dari h1 langsung ke h3 -->
<h5>Tag Dasar HTML</h5>
<!-- Salah: dari h3 langsung ke h5 -->
<h2>Belajar CSS</h2>
```

```html
<!-- BENAR: urutan tingkatan berurutan dan logis -->
<h1>Panduan Belajar Web Development</h1>

<h2>Bab 1: HTML</h2>
<h3>Apa itu HTML?</h3>
<h3>Tag Dasar HTML</h3>
<h4>Tag Heading</h4>
<h4>Tag Paragraf</h4>

<h2>Bab 2: CSS</h2>
<h3>Apa itu CSS?</h3>
<h3>Cara Menghubungkan CSS ke HTML</h3>
```

**Contoh penerapan hierarki heading pada halaman artikel lengkap:**

```html
<!-- HTML -->
<main>
  <article>
    <!-- Satu h1 sebagai judul utama artikel -->
    <h1>Panduan Lengkap Merawat Tanaman Hias di Dalam Ruangan</h1>

    <h2>Mengapa Tanaman Hias Penting untuk Ruangan?</h2>
    <p>Tanaman hias tidak hanya memperindah ruangan, tetapi juga...</p>

    <h2>Jenis Tanaman yang Cocok untuk Pemula</h2>

    <h3>1. Tanaman Lidah Mertua</h3>
    <p>Tanaman ini dikenal sangat mudah dirawat karena...</p>
    <h4>Cara Menyiram yang Benar</h4>
    <p>Lidah mertua hanya perlu disiram setiap...</p>

    <h3>2. Pothos</h3>
    <p>Pothos adalah pilihan populer karena tahan terhadap...</p>

    <h2>Kesalahan Umum dalam Merawat Tanaman Hias</h2>
    <p>Banyak pemula melakukan kesalahan berikut...</p>
  </article>
</main>
```

---

### Kesimpulan

SEO berbasis HTML mencakup tiga area utama: penulisan `<title>` dan `<meta description>` yang informatif dan relevan di dalam `<head>`, penggunaan elemen semantik yang membantu mesin pencari memahami struktur halaman, dan penerapan hierarki heading yang teratur. Ketiga aspek ini tidak hanya meningkatkan visibilitas di mesin pencari, tetapi juga meningkatkan aksesibilitas halaman bagi semua pengguna.

**Ringkasan Elemen SEO:**

| Elemen / Atribut            | Lokasi   | Fungsi SEO                                                        |
| --------------------------- | -------- | ----------------------------------------------------------------- |
| `<title>`                   | `<head>` | Judul halaman di tab browser dan hasil pencarian                  |
| `<meta name="description">` | `<head>` | Ringkasan halaman yang ditampilkan di bawah judul hasil pencarian |
| `<header>`                  | `<body>` | Menandai area kepala halaman                                      |
| `<nav>`                     | `<body>` | Menandai area navigasi utama                                      |
| `<main>`                    | `<body>` | Menandai area konten utama halaman                                |
| `<article>`                 | `<body>` | Menandai konten mandiri yang dapat berdiri sendiri                |
| `<section>`                 | `<body>` | Mengelompokkan konten yang saling berkaitan                       |
| `<aside>`                   | `<body>` | Menandai konten pendukung di luar konten utama                    |
| `<footer>`                  | `<body>` | Menandai area penutup halaman                                     |
| `<h1>`–`<h6>`               | `<body>` | Menyatakan hierarki topik dan sub-topik halaman                   |

**Panduan Pemilihan Praktik SEO:**

| Kebutuhan                                            | Praktik yang Disarankan                                          |
| ---------------------------------------------------- | ---------------------------------------------------------------- |
| Judul halaman yang muncul di hasil pencarian         | `<title>` maksimal 60 karakter, sertakan kata kunci              |
| Ringkasan halaman di bawah judul hasil pencarian     | `<meta name="description">` 150–160 karakter                     |
| Memisahkan bagian-bagian halaman agar mudah diindeks | Gunakan elemen semantik (`<header>`, `<nav>`, `<main>`, dll.)    |
| Menyatakan topik utama halaman                       | Satu `<h1>` per halaman                                          |
| Menyatakan sub-topik secara bertahap                 | Gunakan `<h2>` hingga `<h6>` secara berurutan tanpa melompat     |
| Memperbesar teks untuk keperluan visual saja         | Gunakan CSS — jangan menggunakan heading hanya untuk ukuran teks |
