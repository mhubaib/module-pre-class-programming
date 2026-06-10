# Bab 13: Teks, Format Teks, & Font di CSS

## Tujuan Pembelajaran

- Mampu memodifikasi format tampilan teks: perataan, dekorasi, dan transformasi huruf.
- Mengatur jarak antar huruf dan antar baris untuk keterbacaan yang lebih baik.
- Menguasai properti `font`: ukuran, ketebalan, kemiringan, dan jenis huruf.
- Memahami strategi Font Fallback untuk memastikan tampilan konsisten di semua perangkat.

---

## Materi Utama

Tampilan halaman web yang menarik harus didukung oleh tipografi yang baik. CSS menyediakan serangkaian properti yang lengkap untuk mengontrol semua aspek tampilan teks — mulai dari perataan, dekorasi, jenis huruf, hingga keterbacaan bacaan panjang.

---

### 1. Format Tampilan Teks

#### A. Perataan Teks (`text-align`)

Mengatur posisi horizontal teks di dalam elemennya.

| Nilai     | Efek                  |
| --------- | --------------------- |
| `left`    | Rata kiri _(default)_ |
| `right`   | Rata kanan            |
| `center`  | Rata tengah           |
| `justify` | Rata kanan dan kiri   |

```css
.judul {
  text-align: center;
}
.artikel {
  text-align: justify;
}
.harga-kanan {
  text-align: right;
}
```

#### B. Dekorasi Teks (`text-decoration`)

Menambahkan atau menghapus garis pada teks.

```css
/* Menghapus garis bawah bawaan pada tautan */
a {
  text-decoration: none;
}

/* Harga asli yang dicoret */
.harga-lama {
  text-decoration: line-through;
  color: #aaa;
}

/* Garis bawah kustom */
.tautan-kustom {
  text-decoration: underline;
  text-decoration-color: steelblue;
  text-underline-offset: 4px; /* Jarak garis bawah dari teks */
}
```

#### C. Transformasi Huruf (`text-transform`)

Mengubah kapitalisasi teks secara visual tanpa mengubah konten aslinya di HTML.

```css
.judul-besar {
  text-transform: uppercase;
} /* SEMUA HURUF KAPITAL */
.label-kecil {
  text-transform: lowercase;
} /* semua huruf kecil */
.nama-produk {
  text-transform: capitalize;
} /* Setiap Kata Dikapitalkan */
```

**Contoh:**

```html
<!-- HTML -->
<h2 class="judul-seksi">fitur unggulan kami</h2>
<span class="label">dalam stok</span>
```

```css
/* CSS */
.judul-seksi {
  text-transform: capitalize;
} /* Fitur Unggulan Kami */
.label {
  text-transform: uppercase;
} /* DALAM STOK */
```

---

### 2. Jarak dan Keterbacaan

#### A. Jarak Antar Huruf (`letter-spacing`)

Mengatur ruang antara setiap karakter. Nilai positif memperlebar jarak, nilai negatif merapatkan.

```css
.judul-longgar {
  letter-spacing: 4px;
} /* J u d u l  L o n g g a r */
.label-rapi {
  letter-spacing: 1.5px;
} /* Sering digunakan pada label/badge */
.logo-text {
  letter-spacing: -0.5px;
} /* Sedikit lebih rapat — terlihat bersih */
```

#### B. Jarak Antar Baris (`line-height`)

Mengatur tinggi setiap baris teks. Nilai tanpa satuan (misalnya `1.6`) bersifat relatif terhadap ukuran font saat ini — ini adalah cara penulisan yang paling fleksibel.

```css
/* Untuk teks konten artikel — jarak longgar agar mudah dibaca */
.artikel p {
  line-height: 1.7;
}

/* Untuk judul besar — jarak lebih rapat agar tidak terlalu berjauhan */
.judul {
  line-height: 1.2;
}

/* Untuk navigasi satu baris — tidak perlu jarak ekstra */
.nav-item {
  line-height: 1;
}
```

**Panduan umum:**

| Konteks                 | Nilai `line-height` |
| ----------------------- | ------------------- |
| Judul besar             | `1.1` – `1.3`       |
| Teks paragraf           | `1.5` – `1.8`       |
| Teks UI (tombol, label) | `1` – `1.3`         |

#### C. Jarak Antar Kata (`word-spacing`)

Mengatur ruang antara setiap kata.

```css
.teks-longgar {
  word-spacing: 4px;
}
```

---

### 3. Properti Font

#### A. Ukuran Huruf (`font-size`)

```css
h1 {
  font-size: 2.5rem;
} /* Relatif terhadap ukuran root */
p {
  font-size: 1rem;
} /* Sama dengan ukuran default browser (16px) */
small {
  font-size: 0.875rem;
} /* 14px jika default 16px */
```

#### B. Ketebalan Huruf (`font-weight`)

```css
.tipis {
  font-weight: 300;
} /* Tipis */
.normal {
  font-weight: 400;
} /* Normal — sama dengan "normal" */
.sedang {
  font-weight: 500;
} /* Medium */
.tebal {
  font-weight: 700;
} /* Tebal — sama dengan "bold" */
.ekstra {
  font-weight: 900;
} /* Ekstra tebal */
```

> **Catatan:** Tidak semua font mendukung semua nilai ketebalan. Jika nilai tertentu tidak tersedia, browser akan menggunakan nilai terdekat yang ada.

#### C. Kemiringan Huruf (`font-style`)

```css
.normal {
  font-style: normal;
}
.miring {
  font-style: italic;
}
.sedikit {
  font-style: oblique;
}
```

---

### 4. Jenis Huruf (`font-family`)

`font-family` adalah properti yang menentukan tampilan keseluruhan teks di halaman. Kamu dapat mendefinisikan beberapa font sebagai cadangan (fallback) dipisahkan koma — browser akan mencoba menggunakan font pertama, dan jika tidak tersedia, beralih ke font berikutnya.

```css
body {
  font-family: "Helvetica Neue", Arial, sans-serif;
}
```

Urutan di atas berarti:

1. Gunakan **Helvetica Neue** jika tersedia di perangkat pengguna.
2. Jika tidak, gunakan **Arial** sebagai cadangan.
3. Jika keduanya tidak ada, gunakan font `sans-serif` bawaan sistem.

**Keluarga font generik bawaan browser:**

| Nama         | Karakteristik                                         | Contoh                    |
| ------------ | ----------------------------------------------------- | ------------------------- |
| `serif`      | Memiliki kait di ujung huruf, kesan klasik dan formal | Times New Roman, Georgia  |
| `sans-serif` | Tanpa kait, kesan modern dan bersih                   | Arial, Helvetica, Calibri |
| `monospace`  | Setiap karakter memiliki lebar yang sama              | Courier New, Consolas     |
| `cursive`    | Menyerupai tulisan tangan                             | Comic Sans, Brush Script  |
| `fantasy`    | Dekoratif                                             | Impact, Papyrus           |

**Menggunakan Google Fonts:**

Untuk menggunakan font yang tidak tersedia di semua perangkat, gunakan layanan seperti Google Fonts:

```html
<!-- Tambahkan di dalam <head> HTML -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
```

```css
body {
  font-family: "Inter", sans-serif;
}
```

---

### 5. Properti Singkat `font`

Semua properti font utama dapat digabungkan dalam satu baris:

```css
/* font: [style] [weight] [size]/[line-height] [family] */

p {
  font:
    400 1rem/1.7 "Inter",
    sans-serif;
}

h1 {
  font:
    700 2.5rem/1.2 "Georgia",
    serif;
}
```

---

### 6. Contoh Lengkap — Halaman Artikel dengan Tipografi Lengkap

```html
<!-- HTML -->
<article class="konten-artikel">
  <span class="label-kategori">Tutorial CSS</span>
  <h1 class="judul-artikel">Membangun Tipografi yang Baik</h1>
  <p class="meta-info">Oleh Budi Santoso · 4 Juni 2026</p>

  <p class="isi">
    Tipografi yang baik bukan hanya soal memilih font yang cantik. Ia mencakup
    ukuran teks yang tepat, jarak baris yang nyaman, dan kontras warna yang
    memudahkan pembacaan dalam waktu lama.
  </p>

  <blockquote class="kutipan">
    "Tipografi yang baik hampir tidak terlihat — ia membuat pembaca fokus pada
    isi, bukan pada tampilan."
  </blockquote>
</article>
```

```css
/* CSS */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap");

* {
  box-sizing: border-box;
}

body {
  font-family: "Inter", sans-serif;
  color: #1e293b;
}

.konten-artikel {
  max-width: 680px;
  margin: 40px auto;
  padding: 0 24px;
}

.label-kategori {
  display: inline-block;
  background-color: #dbeafe;
  color: #1d4ed8;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  padding: 4px 10px;
  border-radius: 99px;
  margin-bottom: 16px;
}

.judul-artikel {
  font-size: 2.25rem;
  font-weight: 700;
  line-height: 1.2;
  margin: 0 0 8px;
  color: #0f172a;
}

.meta-info {
  font-size: 0.875rem;
  color: #94a3b8;
  margin: 0 0 28px;
}

.isi {
  font-size: 1.05rem;
  line-height: 1.8;
  color: #334155;
  margin: 0 0 24px;
  text-align: justify;
}

.kutipan {
  font-style: italic;
  font-size: 1.05rem;
  line-height: 1.7;
  color: #475569;
  border-left: 4px solid steelblue;
  padding: 12px 20px;
  margin: 0;
  background-color: #f8fafc;
}
```

---

### Kesimpulan

Tipografi yang baik meningkatkan keterbacaan dan kenyamanan pengguna secara signifikan. Dengan menguasai properti format teks dan font di CSS, kamu dapat membuat halaman web yang enak dibaca sekaligus terlihat profesional.

**Ringkasan Properti:**

| Properti          | Fungsi                                               |
| ----------------- | ---------------------------------------------------- |
| `text-align`      | Perataan teks: `left`, `right`, `center`, `justify`  |
| `text-decoration` | Dekorasi teks: `none`, `underline`, `line-through`   |
| `text-transform`  | Kapitalisasi: `uppercase`, `lowercase`, `capitalize` |
| `letter-spacing`  | Jarak antar karakter                                 |
| `line-height`     | Jarak antar baris                                    |
| `word-spacing`    | Jarak antar kata                                     |
| `font-size`       | Ukuran huruf                                         |
| `font-weight`     | Ketebalan huruf                                      |
| `font-style`      | Kemiringan huruf                                     |
| `font-family`     | Jenis huruf dengan sistem fallback                   |
| `font`            | Properti singkat untuk semua nilai font              |
