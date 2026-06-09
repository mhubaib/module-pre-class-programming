# Bab 11: CSS Margin

## Tujuan Pembelajaran

- Memahami Margin sebagai ruang pemisah antar elemen di luar batas border.
- Menguasai cara penulisan Margin pada tiap sisi secara fleksibel, termasuk penulisan shorthand.
- Menerapkan teknik pemusatan elemen secara horizontal menggunakan `margin: auto`.
- Memahami perilaku _Margin Collapse_ dan dampaknya terhadap perhitungan jarak vertikal.

---

## Materi Utama

Jika Padding — yang telah dibahas di Bab 10 — mengatur ruang di **dalam** kotak antara konten dan batas bordernya, maka Margin mengatur jarak di **luar** kotak: yaitu jarak antara suatu elemen dengan elemen-elemen lain di sekitarnya.

Tanpa Margin, dua buah paragraf yang berurutan akan tampil berhimpit tanpa jarak, sehingga sulit dibaca dan terlihat tidak terstruktur. Margin bertugas menciptakan jarak antar elemen di halaman web.

---

### 1. Apa Itu Margin?

**Margin** adalah ruang kosong yang memisahkan batas luar (_border_) sebuah elemen dengan elemen lain di sekitarnya. Berbeda dengan padding yang mengikuti warna latar belakang elemen, area margin selalu **transparan** — tidak dapat diberi warna apa pun.

**Analogi — Jarak Antarelemen:**
Jika padding ibarat menambah ketebalan lapisan dalam kemasan agar isi tetap terlindungi, maka margin ibarat jarak bebas di sisi luar kemasan yang memastikan kemasan tersebut tidak bersentuhan langsung dengan objek lain di sekitarnya.

**Contoh dasar:**

```html
<!-- HTML -->
<p class="paragraf-atas">Ini adalah paragraf pertama.</p>
<p class="paragraf-bawah">Ini adalah paragraf kedua.</p>
```

```css
/* CSS */
.paragraf-atas {
  margin-bottom: 32px; /* Memberikan jarak 32px antara elemen ini dan elemen di bawahnya */
  background-color: #d6eaf8;
  padding: 12px;
}

.paragraf-bawah {
  background-color: #d5f5e3;
  padding: 12px;
}
```

Hasilnya, paragraf pertama dan kedua akan dipisahkan oleh ruang kosong selebar 32 piksel.

---

### 2. Penulisan Margin pada Setiap Sisi

Sama seperti padding, margin dapat ditentukan untuk keempat sisi secara terpisah menggunakan properti individual, atau digabungkan dalam satu baris menggunakan penulisan shorthand.

| Properti        | Sisi yang Dipengaruhi |
| --------------- | --------------------- |
| `margin-top`    | Atas                  |
| `margin-right`  | Kanan                 |
| `margin-bottom` | Bawah                 |
| `margin-left`   | Kiri                  |
| `margin`        | Shorthand semua sisi  |

```css
.kotak {
  margin-top: 50px;
  margin-bottom: 30px;
  margin-left: 10px;
  margin-right: 10px;
}
```

**Penulisan shorthand margin — urutan: atas, kanan, bawah, kiri (searah jarum jam):**

```css
/* 1 nilai: semua sisi sama */
margin: 20px;

/* 2 nilai: [atas-bawah] [kiri-kanan] */
margin: 20px 40px;

/* 3 nilai: [atas] [kiri-kanan] [bawah] */
margin: 10px 40px 20px;

/* 4 nilai: [atas] [kanan] [bawah] [kiri] */
margin: 10px 20px 30px 40px;
```

**Contoh penerapan pada komponen kartu:**

```html
<!-- HTML -->
<div class="kartu">Kartu Pertama</div>
<div class="kartu">Kartu Kedua</div>
<div class="kartu kartu-pembeda">Kartu Pembeda</div>
<div class="kartu">Kartu Terakhir</div>
```

```css
/* CSS */
.kartu {
  background-color: #f0f0f0;
  padding: 16px;
  border: 1px solid #ccc;
  border-radius: 6px;
  margin-bottom: 12px; /* Jarak seragam antar kartu */
}

/* Kartu dengan jarak atas yang lebih besar untuk memisahkannya secara visual dari kartu sebelumnya */
.kartu-pembeda {
  margin-top: 40px;
  background-color: #eaf4fb;
  border-color: #3498db;
}
```

---

### 3. Pemusatan Elemen Horizontal dengan `margin: auto`

Salah satu teknik paling umum dalam pengembangan web adalah memusatkan sebuah elemen block secara horizontal di dalam kontainernya. Teknik ini menggunakan nilai `auto` pada margin horizontal.

Ketika `margin-left` dan `margin-right` keduanya diatur ke `auto`, browser akan menghitung sisa ruang yang tersedia secara otomatis dan membaginya secara merata ke kiri dan ke kanan — sehingga elemen tampak terpusat.

```css
.konten-tengah {
  width: 600px; /* Syarat wajib: elemen harus memiliki lebar yang ditentukan */
  margin: 0 auto; /* Atas/bawah: 0; kiri/kanan: otomatis sama besar */
}
```

> **Catatan:** Teknik `margin: auto` hanya bekerja pada sumbu **horizontal** (kiri-kanan). Untuk pemusatan secara vertikal (atas-bawah), diperlukan pendekatan lain seperti Flexbox atau Grid yang akan dibahas di bab-bab selanjutnya.

**Contoh penggunaan umum — Kontainer halaman:**

```html
<!-- HTML -->
<div class="kontainer">
  <h1>Judul Halaman</h1>
  <p>
    Konten utama yang terletak di tengah halaman ini dibatasi lebarnya agar
    tidak terlalu melebar di layar berukuran besar.
  </p>
</div>
```

```css
/* CSS */
.kontainer {
  width: 100%;
  max-width: 960px; /* Batas lebar maksimum agar konten tetap terbaca dengan baik di layar lebar */
  margin: 0 auto; /* Elemen selalu terpusat secara horizontal */
  padding: 0 24px; /* Jarak pada sisi kiri-kanan agar konten tidak terlalu mepet di layar kecil */
}
```

Pola `max-width` yang dikombinasikan dengan `margin: 0 auto` merupakan pola yang sangat umum digunakan di hampir semua situs web modern untuk membatasi dan memusatkan area konten utama.

---

### 4. Margin Collapse (Penggabungan Margin)

**Margin Collapse** adalah perilaku CSS di mana dua margin vertikal yang saling berhadapan tidak dijumlahkan, melainkan digabungkan menjadi satu — menggunakan nilai yang lebih besar di antara keduanya.

**Ilustrasi kasus:**

```html
<!-- HTML -->
<div class="kotak-a">Kotak A</div>
<div class="kotak-b">Kotak B</div>
```

```css
/* CSS */
.kotak-a {
  margin-bottom: 50px; /* Kotak A menentukan jarak 50px ke arah bawah */
  background-color: #fadbd8;
  padding: 16px;
}

.kotak-b {
  margin-top: 30px; /* Kotak B menentukan jarak 30px ke arah atas */
  background-color: #d5f5e3;
  padding: 16px;
}

/*
  Perhitungan yang diharapkan: 50px + 30px = 80px.
  Hasil aktual di browser:     50px (nilai terbesar yang digunakan).
  Nilai 30px kolaps dan diabaikan.
*/
```

**Kondisi terjadinya Margin Collapse:**

- Margin **vertikal** (atas dan bawah) antar dua elemen block yang bersebelahan langsung.
- Margin **vertikal** antara elemen induk dan elemen anak pertama atau terakhirnya, apabila tidak terdapat border atau padding sebagai pemisah di antara keduanya.

**Kondisi di mana Margin Collapse tidak terjadi:**

- Margin **horizontal** (kiri dan kanan) — margin horizontal selalu dijumlahkan.
- Elemen yang menggunakan `display: flex` atau `display: grid`.

**Contoh perbandingan — vertikal vs horizontal:**

```html
<!-- HTML -->

<!-- Kasus vertikal: Margin Collapse terjadi -->
<div class="kotak-atas">Kotak Atas (margin-bottom: 40px)</div>
<div class="kotak-tengah">Kotak Tengah (margin-top: 20px)</div>

<hr />

<!-- Kasus horizontal: Margin Collapse tidak terjadi -->
<div class="baris-horizontal">
  <div class="kotak-kiri">Kotak Kiri (margin-right: 40px)</div>
  <div class="kotak-kanan">Kotak Kanan (margin-left: 20px)</div>
</div>
```

```css
/* CSS */

/* Kasus vertikal — Margin Collapse terjadi */
.kotak-atas {
  margin-bottom: 40px;
  background-color: #fadbd8;
  padding: 16px;
  /* Jarak aktual ke kotak-tengah: 40px, bukan 60px */
}

.kotak-tengah {
  margin-top: 20px;
  background-color: #fdebd0;
  padding: 16px;
}

/* Kasus horizontal — Margin Collapse tidak terjadi */
.baris-horizontal {
  display: flex; /* Flexbox menonaktifkan Margin Collapse */
}

.kotak-kiri {
  margin-right: 40px;
  background-color: #d5f5e3;
  padding: 16px;
  /* Jarak aktual ke kotak-kanan: 40px + 20px = 60px (dijumlahkan) */
}

.kotak-kanan {
  margin-left: 20px;
  background-color: #d6eaf8;
  padding: 16px;
}
```

---

### Kesimpulan

Margin merupakan properti utama untuk mengatur jarak antar elemen dalam tata letak halaman web. Pemahaman yang baik terhadap cara kerja margin — termasuk perilaku Margin Collapse — akan membantu menghindari ketidaksesuaian antara hasil tampilan di browser dan perhitungan yang direncanakan.

**Panduan singkat penggunaan:**

- Perlu mengatur jarak antar elemen? → Gunakan **Margin**.
- Perlu memusatkan elemen block secara horizontal? → Gunakan `margin: 0 auto` dengan `width` yang ditentukan.
- Jarak vertikal tidak sesuai perhitungan? → Periksa kemungkinan terjadinya **Margin Collapse**.

**Ringkasan Properti:**

| Properti        | Fungsi                                               |
| --------------- | ---------------------------------------------------- |
| `margin`        | Shorthand untuk mengatur margin semua sisi sekaligus |
| `margin-top`    | Margin sisi atas                                     |
| `margin-right`  | Margin sisi kanan                                    |
| `margin-bottom` | Margin sisi bawah                                    |
| `margin-left`   | Margin sisi kiri                                     |

**Panduan Pemilihan Nilai:**

| Kebutuhan                                            | Pendekatan yang Disarankan                                                         |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Jarak seragam antar elemen dalam daftar              | `margin-bottom` pada setiap elemen                                                 |
| Memusatkan elemen block secara horizontal            | `margin: 0 auto` dengan `width` atau `max-width`                                   |
| Pemisah jarak yang lebih besar antar kelompok elemen | `margin-top` yang lebih besar pada elemen pertama kelompok berikutnya              |
| Mencegah Margin Collapse secara vertikal             | Gunakan `display: flex` atau tambahkan `padding` maupun `border` pada elemen induk |
