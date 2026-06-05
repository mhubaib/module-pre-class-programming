# Bab 20: CSS Grid

## Tujuan Pembelajaran

- Memahami keterbatasan Flexbox dan alasan diperlukannya CSS Grid.
- Menguasai sistem tata letak dua dimensi (baris dan kolom secara bersamaan).
- Memahami anatomi dan terminologi dalam CSS Grid.
- Mampu mendefinisikan struktur petak menggunakan `grid-template-columns` dan `grid-template-rows`.
- Menggunakan satuan `fr` (Fraction) dan fungsi `repeat()` untuk tata letak yang efisien dan responsif.

---

## Materi Utama

Pada Bab 19 yang lalu, kita telah mempelajari Flexbox sebagai sistem tata letak satu dimensi. Flexbox sangat handal untuk menyusun elemen dalam satu arah — baik secara horizontal maupun vertikal — namun tidak keduanya secara bersamaan.

Ketika kita perlu membangun tata letak yang lebih kompleks — seperti kerangka halaman dengan navigasi di atas, sidebar di kiri, area konten utama di tengah, dan footer di bawah — kita membutuhkan sistem yang mampu bekerja dalam **dua dimensi secara simultan**.

Di sinilah **CSS Grid** berperan. CSS Grid adalah sistem tata letak dua dimensi yang memungkinkan pengembang mengatur elemen berdasarkan **baris dan kolom sekaligus**.

---

### Terminologi Penting dalam CSS Grid

Sebelum mulai menulis kode, penting untuk memahami istilah-istilah yang digunakan dalam sistem CSS Grid. Berikut penjelasannya dengan analogi pembangunan kawasan perumahan:

| Istilah | Penjelasan | Analogi |
|:---|:---|:---|
| **Grid Container** | Elemen induk yang memiliki `display: grid` | Seluruh area lahan kawasan perumahan |
| **Grid Item** | Elemen anak langsung di dalam container | Bangunan-bangunan yang berdiri di kawasan tersebut |
| **Grid Line** | Garis pembagi horizontal dan vertikal yang membentuk struktur grid | Pagar batas antar kaveling |
| **Grid Track** | Ruang di antara dua garis grid (satu baris atau satu kolom) | Deretan blok bangunan atau jalan utama |
| **Grid Cell** | Unit terkecil dari grid (pertemuan satu baris dan satu kolom) | Satu petak kaveling terkecil |
| **Grid Area** | Ruang yang dikelilingi oleh empat garis grid, dapat mencakup beberapa cell | Gabungan beberapa kaveling untuk satu fungsi tertentu |

---

### Daftar Properti CSS Grid

**A. Properti untuk Elemen Induk (Container)**

| Properti | Fungsi |
|:---|:---|
| `display: grid` | Mengaktifkan mode Grid pada elemen induk |
| `grid-template-columns` | Menentukan jumlah dan lebar kolom |
| `grid-template-rows` | Menentukan jumlah dan tinggi baris |
| `gap` | Mengatur jarak antar elemen secara horizontal dan vertikal sekaligus |
| `row-gap` / `column-gap` | Mengatur jarak khusus untuk baris atau kolom saja |
| `justify-items` | Meratakan konten elemen anak secara horizontal di dalam cell-nya |
| `align-items` | Meratakan konten elemen anak secara vertikal di dalam cell-nya |
| `justify-content` | Meratakan keseluruhan grid secara horizontal jika ukurannya lebih kecil dari container |
| `align-content` | Meratakan keseluruhan grid secara vertikal jika ukurannya lebih kecil dari container |
| `grid-template-areas` | Mendefinisikan area bernama untuk memudahkan penempatan elemen |
| `grid-auto-rows` / `grid-auto-columns` | Menentukan ukuran baris atau kolom yang dibuat secara otomatis (implicit grid) |
| `grid-auto-flow` | Menentukan arah pengisian slot yang tersedia secara otomatis |

**B. Properti untuk Elemen Anak (Item)**

| Properti | Fungsi |
|:---|:---|
| `grid-column-start` / `grid-column-end` | Menentukan garis awal dan akhir kolom yang ditempati elemen |
| `grid-row-start` / `grid-row-end` | Menentukan garis awal dan akhir baris yang ditempati elemen |
| `grid-column` | Penulisan singkat untuk `grid-column-start` dan `grid-column-end` |
| `grid-row` | Penulisan singkat untuk `grid-row-start` dan `grid-row-end` |
| `grid-area` | Menghubungkan elemen dengan nama area dari `grid-template-areas`, atau penulisan singkat untuk posisi baris dan kolom |
| `justify-self` | Perataan horizontal individual untuk satu elemen tertentu |
| `align-self` | Perataan vertikal individual untuk satu elemen tertentu |

---

### 1. Mengaktifkan CSS Grid

Sama seperti Flexbox, Grid diaktifkan pada **elemen induk**, bukan pada elemen anak.

```css
.wadah-grid {
  display: grid;
}
```

Setelah `display: grid` diterapkan, seluruh elemen anak langsung menjadi **grid item** dan akan ditempatkan secara otomatis mengikuti struktur grid yang didefinisikan.

**Contoh Awal — Grid Dasar:**

```html
<!-- HTML -->
<div class="wadah-grid">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
  <div class="item">Item 4</div>
  <div class="item">Item 5</div>
  <div class="item">Item 6</div>
</div>
```

```css
/* CSS */
.wadah-grid {
  display: grid;
  grid-template-columns: 200px 200px 200px; /* Tiga kolom, masing-masing 200px */
  gap: 12px;
}

.item {
  background-color: steelblue;
  color: white;
  padding: 20px;
  text-align: center;
  border-radius: 4px;
}
```

Enam item di atas akan otomatis tersusun dalam dua baris dengan masing-masing tiga kolom.

---

### 2. Mendefinisikan Kolom dan Baris (`grid-template-columns` & `grid-template-rows`)

Kedua properti ini adalah inti dari CSS Grid. Mereka menentukan jumlah dan ukuran kolom serta baris yang membentuk struktur grid.

```css
.papan {
  display: grid;

  /* Mendefinisikan 3 kolom dengan lebar berbeda */
  grid-template-columns: 100px 200px 100px;

  /* Mendefinisikan 2 baris dengan tinggi berbeda */
  grid-template-rows: 80px 160px;
}
```

**Satuan `fr` (Fraction):**

CSS Grid memperkenalkan satuan `fr` yang merepresentasikan **satu bagian dari ruang kosong yang tersedia** di dalam container. Satuan ini membuat grid menjadi elastis dan proporsional tanpa perlu menghitung persentase secara manual.

```css
.grid-fr {
  display: grid;
  /* Membagi lebar container menjadi tiga kolom yang sama besar */
  grid-template-columns: 1fr 1fr 1fr;
}
```

`fr` juga dapat dikombinasikan dengan satuan tetap:

```css
.grid-campuran {
  display: grid;
  /* Kolom pertama tetap 200px, dua kolom sisanya membagi ruang yang tersisa secara merata */
  grid-template-columns: 200px 1fr 1fr;
}
```

**Fungsi `repeat()`:**

Daripada menuliskan nilai yang sama berulang kali, gunakan fungsi `repeat()` untuk menyederhanakan penulisan:

```css
/* Penulisan panjang */
grid-template-columns: 1fr 1fr 1fr 1fr 1fr;

/* Penulisan ringkas dengan repeat() */
grid-template-columns: repeat(5, 1fr);
```

**Fungsi `minmax()`:**

Fungsi `minmax()` mendefinisikan ukuran minimum dan maksimum sebuah track grid. Ini sangat berguna untuk membuat grid yang responsif tanpa media query:

```css
/* Buat sebanyak mungkin kolom secara otomatis, dengan lebar minimum 200px dan maksimum 1fr */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

**Contoh Lengkap — Galeri Foto Responsif:**

```html
<!-- HTML -->
<div class="galeri">
  <div class="foto">Foto 1</div>
  <div class="foto">Foto 2</div>
  <div class="foto">Foto 3</div>
  <div class="foto">Foto 4</div>
  <div class="foto">Foto 5</div>
  <div class="foto">Foto 6</div>
</div>
```

```css
/* CSS */
.galeri {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 16px;
  padding: 24px;
}

.foto {
  height: 140px;
  background-color: #4a90d9;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  font-weight: bold;
}
```

> **Catatan:** `auto-fit` akan membuat kolom sebanyak yang muat, dan meregangkan kolom yang ada untuk mengisi sisa ruang. Bandingkan dengan `auto-fill` yang mempertahankan ukuran kolom dan membiarkan ruang kosong jika tidak ada cukup item.

---

### 3. Explicit Grid vs Implicit Grid

Terdapat perbedaan penting antara grid yang didefinisikan secara eksplisit dan grid yang dibuat secara otomatis oleh browser.

- **Explicit Grid (Grid Terencana)**: Baris dan kolom yang didefinisikan secara langsung menggunakan `grid-template-columns` atau `grid-template-rows`.
- **Implicit Grid (Grid Otomatis)**: Baris atau kolom baru yang **dibuat otomatis oleh browser** ketika jumlah elemen anak melebihi kapasitas grid yang telah didefinisikan.

**Analogi:**

Bayangkan kamu menyiapkan 10 kursi untuk sebuah pertemuan. Jika ternyata ada 15 orang yang hadir, panitia akan menambahkan kursi tambahan secara spontan. Kursi yang disiapkan sejak awal adalah *explicit*; kursi tambahan yang ditarik mendadak adalah *implicit*.

Ukuran baris atau kolom yang dihasilkan secara otomatis dapat diatur dengan properti `grid-auto-rows` atau `grid-auto-columns`:

```css
.papan {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Terencana: 3 kolom */
  grid-auto-rows: 120px; /* Setiap baris baru yang dibuat otomatis akan memiliki tinggi 120px */
  gap: 12px;
}
```

**Contoh Lengkap — Daftar Kartu Produk:**

```html
<!-- HTML -->
<div class="daftar-produk">
  <div class="kartu">Produk A</div>
  <div class="kartu">Produk B</div>
  <div class="kartu">Produk C</div>
  <div class="kartu">Produk D</div>
  <div class="kartu">Produk E</div>
  <!-- Item ke-4 dan ke-5 akan masuk ke baris baru secara otomatis (implicit) -->
</div>
```

```css
/* CSS */
.daftar-produk {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 140px; /* Baris implicit memiliki tinggi tetap 140px */
  gap: 16px;
  padding: 16px;
}

.kartu {
  background-color: #f0f4f8;
  border: 1px solid #d0d7de;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}
```

---

### 4. Jarak Antar Elemen (`gap`)

Properti `gap` mengatur jarak antara elemen-elemen di dalam grid, baik secara horizontal maupun vertikal sekaligus, tanpa perlu menambahkan `margin` pada setiap elemen anak secara individual.

```css
.album-foto {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px; /* Jarak 20px pada semua sisi antar elemen */
}
```

Jarak horizontal dan vertikal juga dapat diatur secara terpisah:

```css
.album-foto {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  row-gap: 24px;    /* Jarak antar baris */
  column-gap: 16px; /* Jarak antar kolom */
}
```

---

### 5. Penempatan Elemen Merentang Beberapa Cell (Grid Spanning)

Salah satu kemampuan utama CSS Grid yang tidak dimiliki Flexbox adalah kemampuan sebuah elemen untuk **merentang dan menempati lebih dari satu cell**, baik secara horizontal (beberapa kolom) maupun vertikal (beberapa baris).

Untuk memahami ini, perlu diingat bahwa grid dengan tiga kolom memiliki **empat garis kolom** — garis 1 di sisi kiri, hingga garis 4 di sisi kanan.

```
Garis:  1       2       3       4
        |  Kol  |  Kol  |  Kol  |
```

Gunakan properti `grid-column` dan `grid-row` dengan format `[garis-mulai] / [garis-akhir]`:

```css
.header {
  grid-column: 1 / 4; /* Merentang dari garis 1 hingga garis 4 (mencakup seluruh 3 kolom) */
  grid-row: 1 / 2;    /* Menempati baris pertama saja */
}
```

Alternatifnya, gunakan kata kunci `span` untuk menentukan **jumlah** cell yang direntangkan:

```css
.header {
  grid-column: span 3; /* Merentang selebar 3 kolom dari posisi awalnya */
}
```

**Contoh Lengkap — Tata Letak Halaman dengan Header, Sidebar, Konten, dan Footer:**

```html
<!-- HTML -->
<div class="layout-halaman">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="konten">Konten Utama</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
/* CSS */
.layout-halaman {
  display: grid;
  grid-template-columns: 240px 1fr; /* Kolom pertama (sidebar) tetap, kolom kedua elastis */
  grid-template-rows: 64px 1fr 56px; /* Header, area tengah, footer */
  gap: 0;
  height: 100vh;
}

.header {
  grid-column: 1 / 3; /* Merentang di seluruh lebar (2 kolom) */
  background-color: #2c3e50;
  color: white;
  display: flex;
  align-items: center;
  padding: 0 24px;
}

.sidebar {
  background-color: #ecf0f1;
  padding: 24px;
  border-right: 1px solid #ddd;
}

.konten {
  padding: 24px;
  overflow-y: auto;
}

.footer {
  grid-column: 1 / 3; /* Merentang di seluruh lebar (2 kolom) */
  background-color: #34495e;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.875rem;
}
```

---

### 6. Tata Letak Berbasis Nama Area (`grid-template-areas`)

CSS Grid menyediakan cara yang lebih intuitif untuk mendefinisikan tata letak menggunakan **nama area**. Pendekatan ini membuat struktur grid lebih mudah dibaca dan dipahami, terutama untuk tata letak halaman yang kompleks.

Cara kerjanya adalah dengan mendefinisikan nama area pada elemen induk menggunakan `grid-template-areas`, lalu menghubungkan setiap elemen anak ke nama area tersebut menggunakan properti `grid-area`.

```css
/* Elemen induk mendefinisikan peta tata letak */
.layout-halaman {
  display: grid;
  grid-template-columns: 240px 1fr;
  grid-template-rows: 64px 1fr 56px;
  grid-template-areas:
    "header  header"
    "sidebar konten"
    "footer  footer";
  height: 100vh;
}

/* Setiap elemen anak dihubungkan ke nama areanya */
.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.konten  { grid-area: konten; }
.footer  { grid-area: footer; }
```

> **Catatan:** Setiap baris pada nilai `grid-template-areas` merepresentasikan satu baris grid. Nama yang ditulis berulang di beberapa cell menandakan bahwa elemen tersebut merentang di seluruh cell tersebut. Gunakan tanda titik (`.`) untuk menandai cell yang dibiarkan kosong.

**Contoh Lengkap — Tata Letak Majalah:**

```html
<!-- HTML -->
<div class="layout-majalah">
  <header class="mj-header">Header</header>
  <nav class="mj-nav">Navigasi</nav>
  <article class="mj-artikel">Artikel Utama</article>
  <aside class="mj-iklan">Iklan / Widget</aside>
  <footer class="mj-footer">Footer</footer>
</div>
```

```css
/* CSS */
.layout-majalah {
  display: grid;
  grid-template-columns: 1fr 3fr 1fr;
  grid-template-rows: auto auto 1fr auto;
  grid-template-areas:
    "header  header  header"
    "nav     nav     nav"
    "iklan   artikel iklan"
    "footer  footer  footer";
  gap: 16px;
  padding: 16px;
  min-height: 100vh;
}

.mj-header  { grid-area: header;  background-color: #2c3e50; color: white; padding: 16px; }
.mj-nav     { grid-area: nav;     background-color: #34495e; color: white; padding: 12px; }
.mj-artikel { grid-area: artikel; background-color: #fafafa; padding: 24px; border: 1px solid #eee; }
.mj-iklan   { grid-area: iklan;   background-color: #ecf0f1; padding: 16px; }
.mj-footer  { grid-area: footer;  background-color: #2c3e50; color: white; padding: 16px; text-align: center; }
```

---

### Kesimpulan

CSS Grid adalah sistem tata letak dua dimensi yang menjadi solusi standar untuk membangun struktur halaman web yang kompleks. Dengan kemampuan mendefinisikan baris dan kolom secara bersamaan, merentangkan elemen di beberapa cell, serta pendekatan berbasis nama area, Grid memungkinkan pengembang membangun tata letak yang presisi dan mudah dipelihara.

**Perbandingan Flexbox vs Grid:**

| Aspek | Flexbox | CSS Grid |
|---|---|---|
| Dimensi | Satu dimensi (baris **atau** kolom) | Dua dimensi (baris **dan** kolom) |
| Kendali tata letak | Dari dalam ke luar (konten menentukan ukuran) | Dari luar ke dalam (struktur menentukan ukuran) |
| Cocok untuk | Komponen UI kecil, navigasi, deretan tombol | Tata letak halaman, galeri, struktur kompleks |

**Ringkasan Properti Utama CSS Grid:**

| Properti | Diterapkan Pada | Fungsi |
|---|---|---|
| `display: grid` | Induk | Mengaktifkan CSS Grid |
| `grid-template-columns` | Induk | Mendefinisikan jumlah dan lebar kolom |
| `grid-template-rows` | Induk | Mendefinisikan jumlah dan tinggi baris |
| `grid-template-areas` | Induk | Mendefinisikan tata letak berbasis nama area |
| `gap` | Induk | Jarak antar elemen |
| `grid-auto-rows` | Induk | Tinggi baris yang dibuat secara otomatis |
| `grid-column` | Anak | Posisi dan rentang kolom elemen |
| `grid-row` | Anak | Posisi dan rentang baris elemen |
| `grid-area` | Anak | Nama area atau posisi elemen |
