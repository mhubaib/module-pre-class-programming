# Bab 14: Iframe & Ikon Eksternal

## Tujuan Pembelajaran

- Memahami konsep _embedding_ — menyematkan konten dari website lain ke dalam halaman HTML.
- Menerapkan tag `<iframe>` untuk menyematkan pemutar video YouTube dan peta Google Maps.
- Mengintegrasikan ikon dari pustaka FontAwesome ke dalam halaman web menggunakan tautan CDN.

---

## Materi Utama

Dalam pengembangan web, tidak semua fitur perlu dibangun dari nol. Membangun ulang fungsionalitas yang sudah tersedia secara gratis dari pihak ketiga — seperti peta interaktif atau pemutar video — akan membuang waktu dan sumber daya secara tidak efisien.

Web modern mendukung konsep _embedding_: menyematkan konten atau fungsionalitas dari layanan eksternal langsung ke dalam halaman HTML milik sendiri. Dua teknologi yang paling umum digunakan untuk keperluan ini adalah **`<iframe>`** dan **pustaka ikon eksternal**.

---

### 1. Tag `<iframe>` (Inline Frame)

Elemen `<iframe>` digunakan untuk menampilkan halaman web eksternal di dalam area tertentu pada halaman HTML. Pengguna dapat berinteraksi dengan konten di dalam iframe — seperti memutar video atau menggeser peta — tanpa meninggalkan halaman yang sedang dibuka.

**Sintaks dasar:**

```html
<iframe
  src="URL_HALAMAN_EKSTERNAL"
  width="500"
  height="400"
  title="Deskripsi konten iframe"
>
</iframe>
```

Atribut `title` pada `<iframe>` penting untuk aksesibilitas — aplikasi pembaca layar (_screen reader_) menggunakan nilai ini untuk memberi tahu pengguna tentang konten yang ada di dalam iframe.

**Contoh dasar:**

```html
<!-- HTML -->
<iframe
  src="https://id.wikipedia.org/"
  width="600"
  height="400"
  title="Halaman utama Wikipedia Bahasa Indonesia"
>
</iframe>
```

**Analogi — Jendela di Dalam Halaman:**
Iframe dapat dianalogikan sebagai jendela yang dibuka di dinding sebuah ruangan. Melalui jendela tersebut, pengguna dapat melihat dan berinteraksi dengan konten dari "ruangan lain" (website eksternal), tanpa benar-benar berpindah tempat.

> **Catatan:** Tidak semua website dapat disematkan menggunakan `<iframe>`. Banyak website — termasuk Google dan Facebook — mengaktifkan header keamanan `X-Frame-Options` yang mencegah halaman mereka ditampilkan di dalam iframe website lain. YouTube dan Google Maps secara khusus menyediakan URL embed yang memang dirancang untuk keperluan ini.

---

### 2. Menyematkan Video YouTube (`<iframe>` — Praktik Pertama)

YouTube menyediakan kode embed yang dapat langsung digunakan tanpa memerlukan pemrograman tambahan. Kode ini sudah dalam format `<iframe>` yang siap ditempelkan ke dalam HTML.

**Cara mendapatkan kode embed dari YouTube:**

1. Buka halaman video yang ingin disematkan di YouTube.
2. Klik tombol **Bagikan** (_Share_) di bawah video.
3. Pilih opsi **Sematkan** (_Embed_).
4. Salin seluruh kode `<iframe>` yang ditampilkan dan tempelkan ke dalam file HTML.

Pola URL yang digunakan YouTube untuk embed adalah:

```
https://www.youtube.com/embed/ID_VIDEO
```

```html
<!-- HTML -->
<h2>Tutorial: Pengantar HTML untuk Pemula</h2>
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/dQw4w9WgXcQ"
  title="Video tutorial HTML untuk pemula"
  frameborder="0"
  allowfullscreen
>
</iframe>
```

**Keterangan atribut yang digunakan:**

| Atribut           | Fungsi                                                               |
| ----------------- | -------------------------------------------------------------------- |
| `width`           | Lebar area pemutar video dalam piksel                                |
| `height`          | Tinggi area pemutar video dalam piksel                               |
| `src`             | URL embed video YouTube                                              |
| `title`           | Deskripsi video untuk keperluan aksesibilitas                        |
| `frameborder`     | Menghilangkan garis tepi bawaan iframe (nilai `0` = tidak ada garis) |
| `allowfullscreen` | Mengizinkan pengguna menampilkan video dalam mode layar penuh        |

**Contoh penerapan dalam halaman kursus online:**

```html
<!-- HTML -->
<article>
  <h2>Materi 1: Pengenalan HTML</h2>
  <p>Tonton video penjelasan berikut sebelum melanjutkan ke materi latihan.</p>

  <iframe
    width="720"
    height="405"
    src="https://www.youtube.com/embed/dQw4w9WgXcQ"
    title="Materi 1 - Pengenalan HTML"
    frameborder="0"
    allowfullscreen
  >
  </iframe>

  <p>
    Setelah menonton, lanjutkan ke
    <a href="latihan-1.html">halaman latihan</a>.
  </p>
</article>
```

---

### 3. Menyematkan Peta Google Maps (`<iframe>` — Praktik Kedua)

Google Maps juga menyediakan fitur embed yang memungkinkan peta interaktif ditampilkan langsung di halaman web. Peta yang disematkan dapat digeser, diperbesar, dan diklik — jauh lebih informatif dibandingkan gambar statis.

**Cara mendapatkan kode embed dari Google Maps:**

1. Buka [maps.google.com](https://maps.google.com) dan cari lokasi yang diinginkan.
2. Klik tombol **Bagikan** (_Share_).
3. Pilih tab **Sematkan Peta** (_Embed a map_).
4. Salin seluruh kode `<iframe>` yang ditampilkan dan tempelkan ke dalam file HTML.

```html
<!-- HTML — Contoh struktur kode embed Google Maps -->
<h2>Lokasi Kantor Kami</h2>
<iframe
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!..."
  width="600"
  height="450"
  style="border:0;"
  allowfullscreen
  loading="lazy"
  title="Peta lokasi kantor"
>
</iframe>
```

**Contoh penerapan dalam halaman kontak:**

```html
<!-- HTML -->
<section>
  <h2>Temukan Kami</h2>
  <p>
    Kantor kami berlokasi di Jl. Teknologi No. 15, Yogyakarta. Buka setiap hari
    Senin–Jumat pukul 09.00–17.00 WIB.
  </p>

  <iframe
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!..."
    width="100%"
    height="400"
    style="border:0;"
    allowfullscreen
    loading="lazy"
    title="Peta lokasi kantor WebDev Academy, Yogyakarta"
  >
  </iframe>

  <p>
    Butuh petunjuk arah? Buka di
    <a href="https://maps.google.com" target="_blank">Google Maps</a>.
  </p>
</section>
```

> **Catatan:** Atribut `loading="lazy"` pada `<iframe>` memerintahkan browser untuk menunda pemuatan iframe hingga pengguna mendekati area tersebut saat men-_scroll_. Ini membantu mempercepat waktu muat awal halaman.

---

### 4. Menggunakan Ikon Eksternal (FontAwesome)

Menggunakan file gambar (`.png` atau `.jpg`) untuk setiap ikon di halaman web memiliki beberapa keterbatasan: file gambar dapat terlihat buram saat diperbesar, menambah jumlah permintaan (_request_) ke server, dan memperlambat waktu muat halaman jika digunakan dalam jumlah banyak.

Solusi yang lebih efisien adalah menggunakan **Icon Font** — kumpulan ikon yang diimplementasikan sebagai font teks. Ikon jenis ini dapat diperbesar tanpa kehilangan kualitas (berbasis vektor), dapat diubah warnanya menggunakan CSS, dan hanya membutuhkan satu file untuk ribuan ikon.

**FontAwesome** adalah pustaka icon font yang paling banyak digunakan di web, menyediakan ribuan ikon yang dapat diakses secara gratis.

#### Langkah 1 — Menghubungkan FontAwesome via CDN

Tambahkan tautan berikut di dalam elemen `<head>` untuk memuat pustaka FontAwesome dari server CDN:

```html
<!-- HTML — di dalam <head> -->
<head>
  <meta charset="UTF-8" />
  <title>Halaman dengan Ikon FontAwesome</title>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
  />
</head>
```

Setelah tautan ini ditambahkan, seluruh ikon dari FontAwesome dapat digunakan di halaman tersebut.

#### Langkah 2 — Menggunakan Ikon dalam HTML

Ikon FontAwesome ditampilkan menggunakan tag `<i>` dengan kombinasi kelas CSS tertentu. Nama kelas ikon dapat ditemukan di [fontawesome.com](https://fontawesome.com/icons).

Format kelas yang digunakan: `fa-[gaya] fa-[nama-ikon]`

- Gaya yang umum: `fa-solid`, `fa-regular`, `fa-brands`
- Nama ikon: `fa-house`, `fa-user`, `fa-envelope`, `fa-download`, dan lainnya

```html
<!-- HTML -->
<p><i class="fa-solid fa-house"></i> Beranda</p>
<p><i class="fa-solid fa-user"></i> Profil Pengguna</p>
<button><i class="fa-solid fa-download"></i> Unduh File</button>
```

**Contoh penerapan dalam navigasi dan antarmuka:**

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Portofolio - Andi Pratama</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
  </head>
  <body>
    <header>
      <h1>Andi Pratama</h1>
      <p>Frontend Developer</p>
    </header>

    <nav>
      <a href="index.html"> <i class="fa-solid fa-house"></i> Beranda </a>
      <a href="portofolio.html">
        <i class="fa-solid fa-briefcase"></i> Portofolio
      </a>
      <a href="kontak.html"> <i class="fa-solid fa-envelope"></i> Kontak </a>
    </nav>

    <main>
      <h2>Hubungi Saya</h2>
      <ul>
        <li>
          <i class="fa-brands fa-github"></i>
          <a href="https://github.com/andipratama" target="_blank"
            >github.com/andipratama</a
          >
        </li>
        <li>
          <i class="fa-brands fa-linkedin"></i>
          <a href="https://linkedin.com/in/andipratama" target="_blank"
            >linkedin.com/in/andipratama</a
          >
        </li>
        <li>
          <i class="fa-solid fa-envelope"></i>
          <a href="mailto:andi@email.com">andi@email.com</a>
        </li>
      </ul>

      <a href="cv-andi-pratama.pdf">
        <i class="fa-solid fa-file-pdf"></i> Unduh CV (PDF)
      </a>
    </main>
  </body>
</html>
```

**Keunggulan Icon Font dibandingkan gambar:**

| Aspek                    | File Gambar (PNG/JPG)           | Icon Font (FontAwesome)                        |
| ------------------------ | ------------------------------- | ---------------------------------------------- |
| Kualitas saat diperbesar | Menurun (piksel terlihat buram) | Tetap tajam (berbasis vektor)                  |
| Pengubahan warna         | Membutuhkan file gambar baru    | Cukup ubah properti `color` di CSS             |
| Jumlah file              | Satu file per ikon              | Satu file untuk ribuan ikon                    |
| Kecepatan muat           | Lebih lambat jika banyak file   | Lebih cepat — satu permintaan untuk semua ikon |

---

### Kesimpulan

`<iframe>` memungkinkan integrasi konten interaktif dari layanan eksternal — seperti video YouTube dan peta Google Maps — langsung ke dalam halaman web tanpa memerlukan pemrograman yang kompleks. Sementara itu, pustaka icon font seperti FontAwesome menyediakan ribuan ikon berkualitas tinggi yang dapat diintegrasikan hanya dengan menambahkan tautan CDN dan kelas CSS yang sesuai.

**Panduan singkat penggunaan:**

- Perlu menyematkan video YouTube? → Gunakan kode embed dari fitur **Share → Embed** di YouTube.
- Perlu menyematkan peta interaktif? → Gunakan kode embed dari fitur **Bagikan → Sematkan Peta** di Google Maps.
- Perlu menampilkan ikon di antarmuka? → Hubungkan FontAwesome via CDN dan gunakan tag `<i>` dengan kelas yang sesuai.

**Ringkasan Elemen dan Atribut:**

| Elemen / Atribut          | Fungsi                                                              |
| ------------------------- | ------------------------------------------------------------------- |
| `<iframe>`                | Menyematkan halaman atau konten eksternal dalam area tertentu       |
| `src`                     | URL konten yang akan ditampilkan di dalam iframe                    |
| `width` / `height`        | Menentukan dimensi area iframe                                      |
| `title`                   | Deskripsi konten iframe untuk aksesibilitas                         |
| `allowfullscreen`         | Mengizinkan konten ditampilkan dalam mode layar penuh               |
| `loading="lazy"`          | Menunda pemuatan iframe hingga area tersebut terlihat oleh pengguna |
| `<link rel="stylesheet">` | Menghubungkan file CSS eksternal, termasuk pustaka FontAwesome      |
| `<i class="fa-...">`      | Menampilkan ikon dari pustaka FontAwesome                           |
