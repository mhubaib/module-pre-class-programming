# Bab 6: Mengatur Width & Height Elemen

## Tujuan Pembelajaran

- Memahami properti `width` dan `height` untuk mengatur dimensi elemen.
- Mampu membedakan satuan tetap (px) dan satuan relatif (%, vw, vh).
- Mengenal properti pembatas ukuran: `max-width`, `min-width`, `max-height`, `min-height`.
- Memahami perilaku dimensi pada elemen Block vs Inline.

---

## Materi Utama

Setiap elemen HTML pada dasarnya menempati ruang berbentuk kotak di halaman web. Mengontrol lebar dan tinggi kotak-kotak tersebut adalah keterampilan dasar yang menentukan keseluruhan tata letak halaman.

---

### 1. Properti `width` dan `height`

- **`width`**: Mengatur lebar elemen (dimensi horizontal).
- **`height`**: Mengatur tinggi elemen (dimensi vertikal).

```css
.kotak-iklan {
  width: 300px;
  height: 250px;
  background-color: steelblue;
}
```

**Contoh dengan beberapa elemen:**

```html
<!-- HTML -->
<div class="kartu-kecil">Kartu Kecil</div>
<div class="kartu-sedang">Kartu Sedang</div>
<div class="kartu-besar">Kartu Besar</div>
```

```css
/* CSS */
.kartu-kecil {
  width: 100px;
  height: 100px;
  background-color: #e74c3c;
}
.kartu-sedang {
  width: 200px;
  height: 150px;
  background-color: #3498db;
}
.kartu-besar {
  width: 350px;
  height: 200px;
  background-color: #2ecc71;
}
```

---

### 2. Satuan Ukuran: Tetap vs Relatif

Pilihan satuan sangat memengaruhi bagaimana elemen terlihat di berbagai ukuran layar.

#### A. Pixel (`px`) — Satuan Tetap

Ukuran dalam pixel selalu sama terlepas dari ukuran layar atau elemen induk. Elemen dengan `width: 400px` akan selalu selebar 400 pixel, baik di layar laptop maupun di layar ponsel.

```css
.kotak-tetap {
  width: 400px;
  height: 200px;
}
```

**Keterbatasan:** Elemen dengan lebar tetap yang besar dapat terpotong atau menyebabkan scroll horizontal di layar yang lebih kecil.

#### B. Persentase (`%`) — Relatif terhadap Elemen Induk

Nilai persentase dihitung berdasarkan dimensi elemen induknya. `width: 50%` berarti elemen akan mengambil setengah dari lebar elemen induk.

```html
<!-- HTML -->
<div class="wadah">
  <div class="anak">Anak (50% lebar wadah)</div>
</div>
```

```css
/* CSS */
.wadah {
  width: 800px;
  background-color: #f0f0f0;
  padding: 16px;
}

.anak {
  width: 50%; /* 50% dari 800px = 400px */
  background-color: steelblue;
  color: white;
  padding: 12px;
}
```

Persentase sangat berguna untuk membuat tata letak yang responsif — elemen akan menyesuaikan diri secara otomatis ketika ukuran layar berubah.

---

### 3. Properti Pembatas Ukuran

Kombinasi properti pembatas memungkinkan elemen bersifat fleksibel dalam rentang yang diinginkan.

#### `max-width` dan `min-width`

```css
.artikel {
  width: 100%; /* Isi lebar tersedia */
  max-width: 800px; /* Tidak lebih dari 800px meskipun layarnya sangat lebar */
  min-width: 280px; /* Tidak lebih kecil dari 280px */
}
```

#### `max-height` dan `min-height`

```css
.deskripsi {
  min-height: 100px; /* Minimal 100px, akan bertambah jika konten lebih panjang */
  max-height: 300px; /* Tidak lebih dari 300px; konten berlebih bisa di-scroll */
  overflow: auto; /* Tampilkan scrollbar jika konten melebihi max-height */
}
```

**Contoh umum — Membatasi lebar konten agar tidak terlalu lebar di monitor besar:**

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto; /* Otomatis terpusat secara horizontal */
  padding: 0 16px;
}
```

Pola ini sangat umum digunakan di hampir semua website — konten mengisi penuh layar kecil, namun dibatasi dan dipusatkan di layar besar.

---

### 4. Satuan Viewport (`vw` dan `vh`)

Satuan viewport mengukur dimensi berdasarkan ukuran area tampilan browser.

- **`vw` (Viewport Width)**: `1vw` = 1% dari lebar viewport. `100vw` = lebar penuh viewport.
- **`vh` (Viewport Height)**: `1vh` = 1% dari tinggi viewport. `100vh` = tinggi penuh viewport.

```css
/* Bagian hero yang mengisi seluruh tinggi layar */
.hero-section {
  width: 100%;
  height: 100vh;
  background-color: #2c3e50;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

**Contoh — Hero section dengan teks terpusat:**

```html
<!-- HTML -->
<section class="hero">
  <div class="hero-konten">
    <h1>Selamat Datang</h1>
    <p>Temukan produk terbaik kami di sini.</p>
  </div>
</section>
```

```css
/* CSS */
.hero {
  width: 100vw;
  height: 100vh;
  background-color: #1a1a2e;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.hero-konten h1 {
  color: white;
  font-size: 3rem;
}

.hero-konten p {
  color: #aaa;
  font-size: 1.2rem;
}
```

---

### 5. Perilaku Dimensi: Block vs Inline

Elemen HTML memiliki nilai `display` bawaan yang memengaruhi bagaimana properti `width` dan `height` bekerja.

| Jenis Elemen     | Contoh Tag                  | Perilaku Width/Height                                                      |
| ---------------- | --------------------------- | -------------------------------------------------------------------------- |
| **Block**        | `<div>`, `<p>`, `<h1>`      | Mengambil lebar penuh secara default; `width` dan `height` dapat diatur    |
| **Inline**       | `<span>`, `<a>`, `<strong>` | Lebar mengikuti konten; `width` dan `height` diabaikan                     |
| **Inline-Block** | (diatur via CSS)            | Berjajar horizontal seperti inline, tapi `width` dan `height` dapat diatur |

```css
/* Elemen inline secara default */
span {
  width: 200px; /* Diabaikan — tidak berefek */
  height: 50px; /* Diabaikan — tidak berefek */
}

/* Setelah diubah ke inline-block */
span {
  display: inline-block;
  width: 200px; /* Sekarang berefek */
  height: 50px; /* Sekarang berefek */
}
```

Konsep `display` akan dibahas lebih lengkap di bab selanjutnya.

---

### 6. Properti `box-sizing`

Secara default, `width` dan `height` hanya mengukur area konten — tidak termasuk `padding` dan `border`. Ini sering menyebabkan elemen menjadi lebih besar dari yang diharapkan.

```css
/* Tanpa box-sizing — total lebar menjadi 240px (200 + 20 + 20) */
.kotak {
  width: 200px;
  padding: 20px;
}

/* Dengan box-sizing: border-box — total lebar tetap 200px */
.kotak {
  width: 200px;
  padding: 20px;
  box-sizing: border-box; /* padding masuk ke dalam hitungan width */
}
```

Sebaiknya terapkan `box-sizing: border-box` ke seluruh elemen sejak awal menggunakan Universal Selector:

```css
* {
  box-sizing: border-box;
}
```

---

### Kesimpulan

Mengontrol dimensi elemen adalah fondasi dari semua pekerjaan tata letak CSS. Kombinasi antara satuan tetap (`px`) untuk detail presisi, satuan relatif (`%`) untuk fleksibilitas, dan satuan viewport (`vw`, `vh`) untuk elemen yang mengikuti ukuran layar adalah pendekatan yang paling umum digunakan dalam pengembangan web modern.

**Ringkasan Properti:**

| Properti                 | Fungsi                                                        |
| ------------------------ | ------------------------------------------------------------- |
| `width`                  | Mengatur lebar elemen                                         |
| `height`                 | Mengatur tinggi elemen                                        |
| `max-width`              | Batas lebar maksimum                                          |
| `min-width`              | Batas lebar minimum                                           |
| `max-height`             | Batas tinggi maksimum                                         |
| `min-height`             | Batas tinggi minimum                                          |
| `box-sizing: border-box` | Menyertakan padding dan border dalam perhitungan width/height |

**Panduan Pemilihan Satuan:**

| Situasi                              | Satuan yang Disarankan     |
| ------------------------------------ | -------------------------- |
| Detail presisi (border, icon)        | `px`                       |
| Lebar elemen yang perlu responsif    | `%`                        |
| Membatasi lebar konten               | `max-width` + `px`         |
| Elemen setinggi layar (hero section) | `100vh`                    |
| Elemen selebar layar                 | `100vw` atau `width: 100%` |
