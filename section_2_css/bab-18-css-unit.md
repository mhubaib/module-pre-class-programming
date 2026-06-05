# Bab 18: CSS Unit

## Tujuan Pembelajaran

- Mengetahui perbedaan mendasar antara Unit Absolut dan Unit Relatif.
- Memahami karakteristik dan keterbatasan satuan Pixel (`px`).
- Menguasai penggunaan persentase (`%`) untuk menciptakan tata letak yang elastis.
- Memahami konsep pengukuran berbasis ukuran font: `em` dan `rem`.
- Mengenal satuan berbasis dimensi layar: `vh` dan `vw`.

---

## Materi Utama

Dalam pelajaran Matematika, panjang suatu benda diukur menggunakan satuan seperti Meter atau Centimeter. Dalam CSS, ketika kita perlu mendefinisikan ukuran seperti lebar sebuah elemen atau ukuran teks, kita menggunakan satuan ukur tersendiri yang disebut **CSS Unit**.

Secara garis besar, CSS Unit dibagi menjadi dua kelompok: **Unit Absolut** dan **Unit Relatif**.

---

### 1. Satuan Absolut

Satuan absolut menetapkan ukuran yang **bersifat tetap dan tidak berubah** terlepas dari konteks tampilan — baik dibuka di layar monitor besar maupun di layar ponsel yang sempit.

Satuan absolut yang paling umum digunakan dalam pengembangan web adalah **`px` (Pixel)**.

Satuan lain seperti `cm` (Centimeter) atau `in` (Inch) secara teknis tersedia, namun penggunaannya hanya relevan untuk stylesheet yang dikhususkan bagi media cetak (`@media print`), dan tidak direkomendasikan untuk tampilan layar.

```css
p {
  /* 1 pixel merepresentasikan satu titik cahaya pada layar monitor */
  font-size: 16px;
  margin-bottom: 20px;
}
```

**Contoh Lengkap — Kartu Informasi dengan Ukuran Tetap:**

```html
<!-- HTML -->
<div class="kartu-info">
  <h2 class="judul-kartu">Informasi Produk</h2>
  <p class="deskripsi">Deskripsi singkat mengenai produk ini.</p>
</div>
```

```css
/* CSS */
.kartu-info {
  width: 320px;
  padding: 24px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.judul-kartu {
  font-size: 20px;
  margin-bottom: 12px;
}

.deskripsi {
  font-size: 14px;
  line-height: 22px;
}
```

**Keterbatasan Satuan `px`:**

Karena ukurannya tetap, penggunaan `px` untuk dimensi utama seperti lebar elemen dapat menimbulkan masalah pada perangkat dengan layar kecil. Sebagai contoh, sebuah elemen dengan `width: 900px` akan tampil baik di layar laptop, namun akan terpotong di layar ponsel yang hanya memiliki lebar 400px, sehingga pengguna terpaksa melakukan scroll horizontal.

---

### 2. Satuan Relatif

Satuan relatif **tidak memiliki ukuran baku yang tetap**. Ukurannya dihitung berdasarkan referensi tertentu — seperti ukuran elemen induk, ukuran font dasar, atau dimensi layar. Pendekatan ini menjadi fondasi utama dalam pembuatan tampilan web yang responsif.

---

#### A. Persentase (`%`)

Persentase menghitung ukuran elemen berdasarkan **proporsi terhadap elemen induk (parent)** yang membungkusnya.

```css
.container {
  width: 1000px; /* Elemen induk memiliki lebar tetap 1000px */
}

.foto-anak {
  width: 50%; /* Elemen ini mengambil 50% dari lebar induknya = 500px */
}
```

**Contoh Lengkap — Tata Letak Dua Kolom Responsif:**

```html
<!-- HTML -->
<div class="wrapper">
  <div class="kolom-kiri">Konten Utama</div>
  <div class="kolom-kanan">Sidebar</div>
</div>
```

```css
/* CSS */
.wrapper {
  width: 100%;
  display: flex;
}

.kolom-kiri {
  width: 70%; /* Mengisi 70% lebar wrapper */
  padding: 16px;
  background-color: #f0f0f0;
}

.kolom-kanan {
  width: 30%; /* Mengisi 30% lebar wrapper */
  padding: 16px;
  background-color: #e0e0e0;
}
```

> **Catatan:** Persentase pada properti `width` mengacu pada lebar elemen induk. Namun persentase pada `padding` dan `margin` juga mengacu pada **lebar** elemen induk, bukan tingginya.

---

#### B. Em (`em`)

Satuan `em` mengacu pada **ukuran font elemen induk langsungnya**. Jika elemen induk memiliki `font-size: 16px`, maka `1em` pada elemen anak setara dengan `16px`, dan `2em` setara dengan `32px`.

```css
.kontainer {
  font-size: 16px;
}

.teks-anak {
  font-size: 1.5em;   /* 1.5 × 16px = 24px */
  padding: 2em;       /* 2 × 16px = 32px */
}
```

**Contoh Lengkap — Komponen Kutipan:**

```html
<!-- HTML -->
<div class="blok-kutipan">
  <p class="teks-kutipan">"Pendidikan adalah senjata paling ampuh untuk mengubah dunia."</p>
  <span class="sumber">— Nelson Mandela</span>
</div>
```

```css
/* CSS */
.blok-kutipan {
  font-size: 18px; /* Ukuran font induk sebagai acuan em */
  padding: 1.5em;  /* 1.5 × 18px = 27px */
  border-left: 0.25em solid steelblue; /* 0.25 × 18px = 4.5px */
}

.teks-kutipan {
  font-size: 1.2em; /* 1.2 × 18px = 21.6px */
  font-style: italic;
}

.sumber {
  font-size: 0.85em; /* 0.85 × 18px = 15.3px */
  color: gray;
}
```

**Keterbatasan `em`:** Apabila elemen-elemen tersusun bertingkat (parent → child → grandchild), nilai `em` akan terus dikalikan secara berantai, sehingga hasil akhirnya bisa sulit diprediksi dan rentan terhadap kesalahan perhitungan.

---

#### C. Rem (`rem` — Root Em)

`rem` bekerja dengan prinsip yang sama seperti `em`, namun acuannya **hanya satu dan tetap**: ukuran font elemen `<html>` (root), bukan elemen induk langsung. Nilai default browser pada umumnya adalah `16px`.

Karena acuannya selalu sama, `rem` jauh lebih mudah diprediksi dibandingkan `em` dan menjadi pilihan utama para pengembang web profesional untuk mendefinisikan ukuran font, padding, dan margin.

```css
html {
  font-size: 16px; /* Nilai acuan root — dapat diubah sesuai kebutuhan */
}

h1 {
  font-size: 2rem;      /* 2 × 16px = 32px */
  margin-bottom: 1.5rem; /* 1.5 × 16px = 24px */
}

p {
  font-size: 1rem;    /* 1 × 16px = 16px */
  line-height: 1.75rem; /* 1.75 × 16px = 28px */
}
```

**Contoh Lengkap — Sistem Tipografi Konsisten:**

```html
<!-- HTML -->
<article class="artikel">
  <h1 class="judul">Panduan Memilih Laptop</h1>
  <h2 class="sub-judul">Pertimbangan Utama</h2>
  <p class="isi">Memilih laptop yang tepat memerlukan pertimbangan matang...</p>
  <small class="catatan">Terakhir diperbarui: Juni 2026</small>
</article>
```

```css
/* CSS */
html {
  font-size: 16px; /* Satu titik acuan untuk seluruh halaman */
}

.judul {
  font-size: 2.5rem;     /* 40px */
  margin-bottom: 1rem;   /* 16px */
}

.sub-judul {
  font-size: 1.5rem;     /* 24px */
  margin-bottom: 0.75rem; /* 12px */
}

.isi {
  font-size: 1rem;       /* 16px */
  line-height: 1.75rem;  /* 28px */
}

.catatan {
  font-size: 0.75rem;    /* 12px */
  color: gray;
}
```

> **Keunggulan `rem` untuk aksesibilitas:** Pengguna yang mengubah ukuran font default di pengaturan browser mereka (misalnya karena gangguan penglihatan) akan mendapatkan pengalaman yang lebih baik jika halaman menggunakan `rem` dibandingkan `px`, karena seluruh ukuran teks akan ikut menyesuaikan secara proporsional.

---

#### D. Satuan Berbasis Viewport (`vw` dan `vh`)

Satuan ini mengukur dimensi berdasarkan **ukuran area tampilan (viewport) browser pengunjung** secara langsung.

- **`vw` (Viewport Width):** `1vw` setara dengan 1% dari lebar total viewport.
- **`vh` (Viewport Height):** `1vh` setara dengan 1% dari tinggi total viewport.

```css
/* Elemen mengisi penuh seluruh lebar dan tinggi layar */
.hero-banner {
  width: 100vw;
  height: 100vh;
}
```

**Contoh Lengkap — Hero Section Halaman Utama:**

```html
<!-- HTML -->
<section class="hero">
  <h1 class="hero-judul">Selamat Datang</h1>
  <p class="hero-subjudul">Temukan produk terbaik untuk kebutuhan Anda.</p>
  <button class="hero-tombol">Jelajahi Sekarang</button>
</section>

<section class="konten-bawah">
  <p>Konten halaman berikutnya...</p>
</section>
```

```css
/* CSS */
.hero {
  width: 100vw;          /* Melebar penuh mengikuti lebar layar */
  height: 100vh;         /* Mengisi penuh tinggi layar saat pertama kali dibuka */
  background-color: #1a1a2e;
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.hero-judul {
  font-size: 5vw;        /* Ukuran teks ikut menyesuaikan lebar layar */
}

.hero-subjudul {
  font-size: 2vw;
  margin-top: 1rem;
}

.hero-tombol {
  margin-top: 2rem;
  padding: 0.75rem 2rem;
  font-size: 1rem;
}
```

> **Catatan:** Penggunaan `vw` dan `vh` pada ukuran teks dapat membuat teks terlalu kecil di layar sempit atau terlalu besar di layar lebar. Untuk mengatasi hal ini, pertimbangkan penggunaan fungsi `clamp()` yang akan dibahas pada modul selanjutnya.

---

### Kesimpulan

Pemilihan satuan ukur yang tepat sangat berpengaruh pada kualitas tampilan dan ketangguhan sebuah halaman web di berbagai ukuran layar. Berikut panduan singkat penggunaannya:

| Satuan | Jenis | Acuan | Digunakan Untuk |
|---|---|---|---|
| `px` | Absolut | Tetap | Border tipis, shadow, detail presisi kecil |
| `%` | Relatif | Elemen induk | Lebar/tinggi elemen yang perlu elastis |
| `em` | Relatif | Font elemen induk langsung | Spasi dan ukuran yang terkait komponen tertentu |
| `rem` | Relatif | Font elemen `<html>` | Font, padding, dan margin secara konsisten |
| `vw` | Relatif | Lebar viewport | Elemen yang perlu mengikuti lebar layar |
| `vh` | Relatif | Tinggi viewport | Hero section, modal, elemen full-screen |
