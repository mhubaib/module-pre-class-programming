# Bab 7: Mengelola Background di CSS

## Tujuan Pembelajaran

- Memahami properti `background-image` untuk menerapkan gambar sebagai latar belakang elemen.
- Mampu mengatur perulangan gambar latar menggunakan `background-repeat`.
- Mengontrol ukuran dan posisi gambar latar dengan `background-size` dan `background-position`.
- Memahami properti `background-attachment` dan penerapan efek parallax sederhana.
- Menguasai penulisan ringkas menggunakan properti shorthand `background`.

---

## Materi Utama

Setiap elemen HTML pada dasarnya menempati ruang berbentuk kotak di halaman web. Selain memberikan warna polos pada latar belakang — yang telah dibahas di Bab 5 — CSS juga memungkinkan penerapan gambar sebagai latar belakang elemen. Kemampuan ini membuka banyak kemungkinan visual, mulai dari foto hero, pola tekstur, hingga efek kedalaman parallax.

---

### 1. Memasang Gambar Latar (`background-image`)

- **`background-image`**: Menentukan file gambar yang akan ditampilkan sebagai latar belakang suatu elemen.

```css
body {
  background-image: url("pemandangan.jpg");
}
```

**Analogi:**
Menggunakan `background-color` ibarat mengecat tembok dengan warna polos. Sedangkan menggunakan `background-image` ibarat memasang wallpaper bermotif di seluruh dinding ruangan — tampilannya lebih berkarakter dan dekoratif.

**Contoh dengan elemen spesifik:**

```html
<!-- HTML -->
<section class="hero">
  <h1>Selamat Datang</h1>
  <p>Temukan produk terbaik kami di sini.</p>
</section>
```

```css
/* CSS */
.hero {
  background-image: url("pegunungan.jpg");
  height: 400px;
  color: white;
}
```

Hasilnya, gambar `pegunungan.jpg` akan tampil sebagai latar belakang di dalam elemen `.hero`. Jika gambar lebih kecil dari elemen, browser akan mengulangnya secara otomatis — perilaku ini dapat dikendalikan menggunakan `background-repeat`.

---

### 2. Mengatur Perulangan Gambar (`background-repeat`)

Secara bawaan (_default_), jika gambar latar berukuran lebih kecil dari area elemen, browser akan mengulang gambar tersebut ke arah horizontal dan vertikal hingga memenuhi seluruh area — mirip seperti susunan ubin lantai. Properti `background-repeat` digunakan untuk mengendalikan perilaku ini.

| Nilai       | Keterangan                                             |
| ----------- | ------------------------------------------------------ |
| `repeat`    | **(Bawaan)** Mengulang ke arah horizontal dan vertikal |
| `repeat-x`  | Hanya mengulang ke arah horizontal                     |
| `repeat-y`  | Hanya mengulang ke arah vertikal                       |
| `no-repeat` | Gambar hanya ditampilkan satu kali, di pojok kiri atas |

```css
div {
  background-image: url("logo.png");
  background-repeat: no-repeat;
}
```

**Contoh penerapan setiap nilai:**

```css
/* Mengulang ke segala arah — cocok untuk pola tekstur */
.kotak-tekstur {
  background-image: url("pola.png");
  background-repeat: repeat;
}

/* Hanya mengulang ke arah horizontal — cocok untuk garis dekoratif di bagian atas */
.header-dekorasi {
  background-image: url("garis.png");
  background-repeat: repeat-x;
}

/* Hanya mengulang ke arah vertikal — cocok untuk border atau panel samping */
.sidebar {
  background-image: url("border-sisi.png");
  background-repeat: repeat-y;
}

/* Gambar hanya muncul satu kali — umum digunakan untuk logo atau watermark */
.kartu {
  background-image: url("watermark.png");
  background-repeat: no-repeat;
}
```

---

### 3. Menentukan Ukuran Gambar (`background-size`)

Gambar yang tersedia seringkali tidak memiliki rasio yang sama dengan area elemen. Properti `background-size` digunakan untuk mengatur skala gambar latar belakang agar sesuai dengan kebutuhan.

- **`cover`**: Gambar diperbesar atau diperkecil secara proporsional hingga **menutupi seluruh area** elemen. Bagian gambar yang melebihi batas area akan terpotong.
- **`contain`**: Gambar diperbesar atau diperkecil secara proporsional hingga **seluruh bagian gambar terlihat** di dalam area elemen. Jika rasio aspek berbeda, akan muncul area kosong di sisi tertentu.

```css
header {
  background-image: url("foto-hero.jpg");
  background-size: cover;
}
```

**Contoh perbandingan `cover` dan `contain`:**

```css
/* cover: gambar mengisi penuh area — sisi tertentu mungkin terpotong */
.banner {
  background-image: url("foto-alam.jpg");
  background-size: cover;
  height: 300px;
}

/* contain: seluruh gambar terlihat — mungkin ada ruang kosong di sisi tertentu */
.thumbnail {
  background-image: url("logo-perusahaan.png");
  background-size: contain;
  background-repeat: no-repeat;
  height: 150px;
}

/* Ukuran eksplisit menggunakan piksel */
.kotak-pola {
  background-image: url("tekstur.png");
  background-size: 200px 150px; /* lebar x tinggi */
}
```

**Keterbatasan `contain`:** Jika rasio aspek gambar tidak sesuai dengan rasio elemen, akan muncul area kosong. Gunakan `background-color` sebagai warna cadangan untuk mengisi ruang tersebut.

---

### 4. Mengatur Posisi Gambar (`background-position`)

Properti `background-position` digunakan untuk menentukan titik awal penempatan gambar latar belakang di dalam area elemen. Nilai yang dapat digunakan antara lain: `center`, `top`, `bottom`, `left`, dan `right`, atau kombinasi keduanya. Nilai koordinat dalam piksel maupun persen juga didukung.

```css
body {
  background-position: center bottom;
}
```

**Contoh penggunaan berbagai nilai posisi:**

```html
<!-- HTML -->
<div class="banner-utama">Banner Utama</div>
<div class="panel-samping">Panel Samping</div>
<div class="kartu-logo">Kartu dengan Logo</div>
```

```css
/* CSS */

/* Gambar dipusatkan — umum digunakan untuk foto hero agar subjek utama selalu terlihat */
.banner-utama {
  background-image: url("foto-hero.jpg");
  background-position: center center;
  background-size: cover;
  height: 400px;
}

/* Gambar diposisikan di kanan atas — cocok untuk elemen dekoratif */
.panel-samping {
  background-image: url("dekorasi.png");
  background-position: right top;
  background-repeat: no-repeat;
  height: 200px;
}

/* Menggunakan nilai piksel untuk presisi penempatan yang lebih tinggi */
.kartu-logo {
  background-image: url("logo.png");
  background-position: 20px 15px; /* 20px dari kiri, 15px dari atas */
  background-repeat: no-repeat;
  height: 100px;
}
```

---

### 5. Efek Latar Diam saat Scroll (`background-attachment`)

Properti `background-attachment` menentukan apakah gambar latar belakang ikut bergerak ketika halaman di-_scroll_, atau tetap diam di posisi layar. Properti ini yang menghasilkan efek visual yang dikenal sebagai **parallax sederhana**.

| Nilai    | Keterangan                                                                |
| -------- | ------------------------------------------------------------------------- |
| `scroll` | **(Bawaan)** Gambar ikut bergerak mengikuti scroll halaman                |
| `fixed`  | Gambar tetap diam di posisi layar, menciptakan kesan kedalaman (parallax) |
| `local`  | Gambar ikut bergerak mengikuti scroll di dalam elemen itu sendiri         |

```css
.bagian-parallax {
  background-image: url("gunung.jpg");
  background-attachment: fixed;
  background-size: cover;
}
```

**Contoh — Halaman dengan efek parallax:**

```html
<!-- HTML -->
<section class="bagian-atas">
  <p>Konten bagian pertama halaman.</p>
</section>

<section class="bagian-parallax">
  <h2>Momen yang Tak Terlupakan</h2>
</section>

<section class="bagian-bawah">
  <p>Konten bagian ketiga halaman.</p>
</section>
```

```css
/* CSS */
.bagian-atas,
.bagian-bawah {
  height: 300px;
  background-color: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bagian-parallax {
  background-image: url("pemandangan-gunung.jpg");
  background-attachment: fixed;
  background-size: cover;
  background-position: center;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 2rem;
}
```

Saat pengguna men-_scroll_ halaman, gambar `pemandangan-gunung.jpg` akan tetap berada di posisinya, sementara teks di atasnya bergerak — menciptakan ilusi kedalaman yang menarik.

---

### 6. Penulisan Ringkas (`background` Shorthand)

Alih-alih menuliskan setiap properti latar belakang secara terpisah, CSS menyediakan properti `background` sebagai penulisan ringkas (_shorthand_) yang menggabungkan semua nilai dalam satu baris.

**Urutan nilai shorthand:**

```
background: [warna] [image] [repeat] [attachment] [position];
```

```css
body {
  background: lightblue url("awan.png") no-repeat fixed center;
}
```

**Contoh — Berbagai kasus penggunaan shorthand:**

```css
/* Contoh 1: Latar hero dengan warna cadangan jika gambar gagal dimuat */
.header {
  background: #1a1a2e url("foto-hero.jpg") no-repeat scroll center center;
  background-size: cover;
}

/* Contoh 2: Pola dekoratif yang diulang secara horizontal */
.dekorasi-atas {
  background: #f0f0f0 url("garis-tipis.png") repeat-x top left;
  height: 8px;
}

/* Contoh 3: Latar parallax menggunakan sintaks shorthand modern */
/* background-size dapat ditulis setelah background-position, dipisahkan oleh '/' */
.parallax-section {
  background: url("langit.jpg") fixed center / cover no-repeat;
  height: 500px;
}
```

> **Catatan:** Nilai `background-size` dapat dimasukkan ke dalam _shorthand_ dengan menuliskannya tepat setelah nilai `background-position`, dipisahkan oleh karakter garis miring (`/`). Contoh: `center / cover`.

---

### Kesimpulan

Mengelola latar belakang adalah salah satu cara paling efektif untuk membangun identitas visual sebuah halaman web. Kombinasi antara `background-image` untuk konten gambar, `background-size: cover` untuk cakupan penuh, dan `background-attachment: fixed` untuk efek parallax adalah pola yang sangat umum digunakan dalam pengembangan web modern.

**Ringkasan Properti:**

| Properti                | Fungsi                                                |
| ----------------------- | ----------------------------------------------------- |
| `background-image`      | Menentukan gambar latar belakang                      |
| `background-repeat`     | Mengatur perulangan gambar latar                      |
| `background-size`       | Mengatur skala ukuran gambar latar                    |
| `background-position`   | Menentukan titik penempatan gambar latar              |
| `background-attachment` | Menentukan perilaku gambar saat halaman di-_scroll_   |
| `background`            | Penulisan ringkas untuk semua properti latar belakang |

**Panduan Pemilihan Nilai:**

| Kebutuhan                                 | Nilai yang Disarankan          |
| ----------------------------------------- | ------------------------------ |
| Gambar mengisi penuh area elemen          | `background-size: cover`       |
| Seluruh gambar terlihat tanpa terpotong   | `background-size: contain`     |
| Pola kecil mengisi seluruh latar belakang | `background-repeat: repeat`    |
| Gambar hanya muncul satu kali             | `background-repeat: no-repeat` |
| Subjek gambar selalu terlihat di tengah   | `background-position: center`  |
| Efek parallax saat halaman di-_scroll_    | `background-attachment: fixed` |
| Semua properti latar dalam satu baris     | Shorthand `background`         |
