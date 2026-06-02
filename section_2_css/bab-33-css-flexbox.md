# Bab 33: CSS Flexbox

## Tujuan Pembelajaran

- Memahami konsep Flexbox sebagai sistem tata letak satu dimensi yang fleksibel.
- Menguasai pengaturan poros utama (`Main Axis`) dan poros silang (`Cross Axis`).
- Mampu mendistribusikan ruang antar elemen dengan berbagai variasi `justify-content` dan `align-items`.
- Mengatur properti individual pada elemen anak seperti `flex-grow`, `flex-shrink`, dan `flex-basis`.
- Mampu memusatkan elemen secara sempurna secara horizontal maupun vertikal.

---

## Materi Utama

Sebelum Flexbox hadir, pengembang web harus mengandalkan teknik seperti `float` atau perhitungan `margin` dan persentase secara manual hanya untuk membuat beberapa kotak berjajar secara horizontal. Pendekatan tersebut rentan terhadap inkonsistensi tampilan di berbagai ukuran layar.

Sejak diperkenalkannya **Flexbox (Flexible Box Layout)**, pengelolaan tata letak elemen — baik berjajar maupun bertumpuk — menjadi jauh lebih terstruktur, ringkas, dan andal.

---

### 1. Konsep Poros: Main Axis & Cross Axis

Flexbox adalah sistem tata letak **satu dimensi**, artinya pada satu waktu ia hanya mengelola satu arah — baik secara horizontal (baris) maupun vertikal (kolom).

Untuk memahami Flexbox, penting untuk terlebih dahulu memahami dua poros utamanya:

- **Main Axis (Poros Utama)**: Arah utama di mana elemen anak disusun. Secara default, arahnya adalah dari kiri ke kanan.
- **Cross Axis (Poros Silang)**: Arah yang tegak lurus terhadap Main Axis. Secara default, arahnya adalah dari atas ke bawah.

Kedua poros ini akan bertukar orientasi apabila arah susunan diubah. Jika `flex-direction` diubah menjadi `column`, maka Main Axis berubah menjadi arah atas ke bawah, dan Cross Axis menjadi kiri ke kanan.

**Ilustrasi Poros:**

```
flex-direction: row (default)

Main Axis  →  [ Item 1 ] [ Item 2 ] [ Item 3 ]
                ↕
          Cross Axis
```

```
flex-direction: column

Main Axis  ↓  [ Item 1 ]
              [ Item 2 ]
              [ Item 3 ]
               ↔
          Cross Axis
```

---

### 2. Mengaktifkan Flexbox (Properti pada Elemen Induk)

Untuk mengaktifkan Flexbox, properti `display: flex` diterapkan pada **elemen induk (container/parent)**, bukan pada elemen anaknya. Seluruh elemen anak di dalamnya akan secara otomatis menjadi **flex item**.

```css
.wadah {
  display: flex;
  border: 2px solid black;
  height: 300px;
}

.kotak-anak {
  background-color: orange;
  width: 50px;
}
```

Setelah `display: flex` diterapkan, elemen anak yang sebelumnya bersifat `block` (mengambil satu baris penuh secara vertikal) akan langsung berjajar secara horizontal dari kiri ke kanan.

**Contoh Lengkap — Daftar Menu Navigasi:**

```html
<!-- HTML -->
<nav class="navigasi">
  <a class="nav-item" href="#">Beranda</a>
  <a class="nav-item" href="#">Produk</a>
  <a class="nav-item" href="#">Tentang Kami</a>
  <a class="nav-item" href="#">Kontak</a>
</nav>
```

```css
/* CSS */
.navigasi {
  display: flex;
  background-color: #2c3e50;
  padding: 12px 24px;
}

.nav-item {
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 4px;
}

.nav-item:hover {
  background-color: #34495e;
}
```

---

### 3. Menentukan Arah Susunan (`flex-direction`)

Properti `flex-direction` menentukan arah Main Axis, yaitu arah di mana elemen anak disusun.

- `row` *(default)*: Elemen anak berjajar dari kiri ke kanan.
- `row-reverse`: Elemen anak berjajar dari kanan ke kiri (urutan elemen terbalik).
- `column`: Elemen anak bertumpuk dari atas ke bawah.
- `column-reverse`: Elemen anak bertumpuk dari bawah ke atas (urutan elemen terbalik).

**Contoh:**

```html
<!-- HTML -->
<div class="wadah-kolom">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>
```

```css
/* CSS */
.wadah-kolom {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.item {
  background-color: steelblue;
  color: white;
  padding: 12px;
  border-radius: 4px;
}
```

---

### 4. Distribusi Ruang pada Main Axis (`justify-content`)

Properti `justify-content` mengatur bagaimana ruang kosong yang tersisa pada Main Axis didistribusikan di antara elemen anak.

- `flex-start` *(default)*: Semua elemen anak berkumpul di awal Main Axis (ujung kiri pada `row`).
- `flex-end`: Semua elemen anak berkumpul di akhir Main Axis (ujung kanan pada `row`).
- `center`: Semua elemen anak dikelompokkan di titik tengah Main Axis.
- `space-between`: Elemen pertama menempel di awal, elemen terakhir menempel di akhir, dan ruang kosong dibagi rata di antara elemen-elemen yang tersisa.
- `space-around`: Ruang kosong dibagi rata di sekeliling setiap elemen, sehingga jarak di tepi (kiri dan kanan terluar) setengah dari jarak antar elemen.
- `space-evenly`: Seluruh ruang kosong — termasuk di tepi — dibagi secara benar-benar merata sehingga setiap jarak memiliki ukuran yang identik.

**Contoh Lengkap — Baris Tombol Aksi:**

```html
<!-- HTML -->
<div class="baris-tombol">
  <button class="tombol">Batal</button>
  <button class="tombol">Simpan Draft</button>
  <button class="tombol tombol-utama">Publikasikan</button>
</div>
```

```css
/* CSS */
.baris-tombol {
  display: flex;
  justify-content: flex-end; /* Semua tombol menempel ke kanan */
  gap: 12px;
  padding: 16px;
  border-top: 1px solid #ddd;
}

.tombol {
  padding: 8px 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: white;
  cursor: pointer;
}

.tombol-utama {
  background-color: steelblue;
  color: white;
  border-color: steelblue;
}
```

> **Catatan:** `justify-content` bekerja pada arah Main Axis. Jika `flex-direction: column`, maka `justify-content` mengatur distribusi secara vertikal, bukan horizontal.

---

### 5. Perataan pada Cross Axis (`align-items`)

Properti `align-items` mengatur bagaimana elemen anak diposisikan pada Cross Axis (arah tegak lurus terhadap Main Axis).

- `stretch` *(default)*: Elemen anak diregangkan untuk mengisi seluruh tinggi elemen induk.
- `flex-start`: Elemen anak diposisikan di awal Cross Axis (ujung atas pada `row`).
- `center`: Elemen anak diposisikan di titik tengah Cross Axis.
- `flex-end`: Elemen anak diposisikan di akhir Cross Axis (ujung bawah pada `row`).
- `baseline`: Elemen anak disejajarkan berdasarkan garis dasar teksnya (baseline tipografi).

**Analogi:**

Bayangkan elemen induk sebagai sebuah rel kereta panjang. Elemen anak adalah gerbong-gerbong yang berjalan di atasnya:
- `justify-content` mengatur jarak antar gerbong di sepanjang rel (Main Axis).
- `align-items` mengatur posisi vertikal setiap gerbong terhadap rel — apakah menempel ke atas, ke bawah, atau mengambang di tengah (Cross Axis).

**Contoh Lengkap — Kartu Produk dengan Tinggi Berbeda:**

```html
<!-- HTML -->
<div class="galeri-produk">
  <div class="kartu">
    <h3>Produk A</h3>
    <p>Deskripsi singkat.</p>
  </div>
  <div class="kartu">
    <h3>Produk B</h3>
    <p>Deskripsi yang lebih panjang dan memerlukan dua baris teks untuk ditampilkan.</p>
  </div>
  <div class="kartu">
    <h3>Produk C</h3>
    <p>Deskripsi singkat.</p>
  </div>
</div>
```

```css
/* CSS */
.galeri-produk {
  display: flex;
  align-items: stretch; /* Semua kartu memiliki tinggi yang sama */
  gap: 16px;
  padding: 24px;
}

.kartu {
  flex: 1;
  padding: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #fafafa;
}
```

---

### 6. Properti pada Elemen Anak (Flex Item)

Selain properti pada elemen induk, setiap elemen anak dapat memiliki properti tersendiri untuk mengatur perilakunya secara individual.

- **`flex-grow`**: Menentukan seberapa besar porsi ruang kosong yang akan diserap oleh elemen ini. Nilai `0` berarti tidak menyerap ruang tambahan; nilai `1` berarti menyerap seluruh ruang kosong yang tersedia. Jika beberapa elemen anak memiliki `flex-grow: 1`, ruang kosong dibagi rata di antara mereka.
- **`flex-shrink`**: Menentukan seberapa besar elemen ini akan menyusut ketika ruang yang tersedia tidak cukup. Nilai default adalah `1` (boleh menyusut). Nilai `0` berarti elemen tidak akan menyusut.
- **`flex-basis`**: Menentukan ukuran awal elemen sebelum ruang kosong didistribusikan. Dapat menggunakan nilai piksel, persentase, atau `auto`.
- **`align-self`**: Mengganti nilai `align-items` dari elemen induk untuk elemen tertentu saja, sehingga satu elemen dapat memiliki perataan Cross Axis yang berbeda dari elemen lainnya.

**Properti Singkat `flex`:**

Ketiga properti `flex-grow`, `flex-shrink`, dan `flex-basis` dapat ditulis dalam satu baris menggunakan properti singkat `flex`:

```css
/* flex: <grow> <shrink> <basis> */
.item {
  flex: 1 1 auto; /* grow=1, shrink=1, basis=auto */
}

/* Penulisan singkat yang umum */
.item {
  flex: 1; /* Setara dengan flex: 1 1 0 */
}
```

**Contoh Lengkap — Tata Letak Artikel dengan Sidebar:**

```html
<!-- HTML -->
<div class="layout-artikel">
  <main class="konten-utama">
    <h1>Judul Artikel</h1>
    <p>Isi artikel yang panjang...</p>
  </main>
  <aside class="sidebar">
    <h2>Artikel Terkait</h2>
    <p>Tautan ke artikel lainnya.</p>
  </aside>
</div>
```

```css
/* CSS */
.layout-artikel {
  display: flex;
  gap: 24px;
  padding: 24px;
  align-items: flex-start; /* Tinggi masing-masing kolom mengikuti kontennya */
}

.konten-utama {
  flex: 3; /* Mengambil 3 bagian dari total ruang yang tersedia */
}

.sidebar {
  flex: 1; /* Mengambil 1 bagian dari total ruang yang tersedia */
  background-color: #f5f5f5;
  padding: 16px;
  border-radius: 8px;
}
```

---

### 7. Penanganan Baris Baru (`flex-wrap`)

Secara default, seluruh elemen anak dipaksa masuk dalam satu baris meskipun lebar totalnya melebihi lebar elemen induk. Properti `flex-wrap` mengatur perilaku ini.

- `nowrap` *(default)*: Semua elemen anak berada dalam satu baris; elemen dapat menyusut jika ruang tidak cukup.
- `wrap`: Elemen anak akan berpindah ke baris baru jika ruang tidak mencukupi.
- `wrap-reverse`: Sama seperti `wrap`, namun baris baru terbentuk ke arah atas.

**Contoh Lengkap — Galeri Foto Responsif:**

```html
<!-- HTML -->
<div class="galeri-foto">
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
.galeri-foto {
  display: flex;
  flex-wrap: wrap;   /* Elemen yang tidak muat akan turun ke baris berikutnya */
  gap: 12px;
  padding: 16px;
}

.foto {
  flex-basis: calc(33.333% - 8px); /* Tiga kolom per baris */
  min-width: 150px;                /* Lebar minimum sebelum turun baris */
  height: 120px;
  background-color: steelblue;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
}
```

---

### 8. Memusatkan Elemen Secara Sempurna

Salah satu penggunaan Flexbox yang paling umum adalah menempatkan sebuah elemen tepat di tengah layar secara horizontal maupun vertikal sekaligus. Teknik ini mengatasi tantangan klasik yang sebelumnya memerlukan solusi yang rumit.

```css
.super-parent-layar {
  display: flex;
  justify-content: center; /* Memusatkan pada Main Axis (horizontal) */
  align-items: center;     /* Memusatkan pada Cross Axis (vertikal) */
  height: 100vh;           /* Tinggi penuh viewport agar pemusatan vertikal bekerja */
}
```

**Contoh Lengkap — Halaman Login Terpusat:**

```html
<!-- HTML -->
<div class="halaman-login">
  <div class="form-login">
    <h2>Masuk ke Akun Anda</h2>
    <input type="email" placeholder="Alamat Email" />
    <input type="password" placeholder="Kata Sandi" />
    <button class="tombol-masuk">Masuk</button>
  </div>
</div>
```

```css
/* CSS */
.halaman-login {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f2f5;
}

.form-login {
  background-color: white;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 360px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.form-login h2 {
  margin: 0;
  font-size: 1.5rem;
  text-align: center;
}

.form-login input {
  padding: 10px 14px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
}

.tombol-masuk {
  padding: 10px;
  background-color: steelblue;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
}

.tombol-masuk:hover {
  background-color: #2a6496;
}
```

---

### Kesimpulan

Flexbox adalah sistem tata letak CSS yang dirancang untuk menyusun elemen dalam satu dimensi secara efisien dan responsif. Dengan memahami konsep poros, properti pada elemen induk, serta properti individual pada elemen anak, hampir semua kebutuhan tata letak horizontal dan vertikal dapat diselesaikan dengan kode yang bersih dan ringkas.

**Ringkasan Properti Flexbox:**

| Properti | Diterapkan Pada | Fungsi |
|---|---|---|
| `display: flex` | Induk | Mengaktifkan Flexbox pada elemen induk |
| `flex-direction` | Induk | Menentukan arah Main Axis |
| `justify-content` | Induk | Distribusi ruang pada Main Axis |
| `align-items` | Induk | Perataan elemen pada Cross Axis |
| `flex-wrap` | Induk | Mengatur perpindahan ke baris baru |
| `gap` | Induk | Jarak antar elemen anak |
| `flex-grow` | Anak | Porsi penyerapan ruang kosong |
| `flex-shrink` | Anak | Tingkat penyusutan saat ruang sempit |
| `flex-basis` | Anak | Ukuran awal elemen sebelum distribusi ruang |
| `align-self` | Anak | Perataan Cross Axis individual |
| `flex` | Anak | Singkatan dari grow, shrink, dan basis |
