# Bab 6: Menambahkan Style di HTML

## Tujuan Pembelajaran

- Memahami konsep dasar penerapan gaya desain secara langsung ke dalam elemen HTML.
- Menerapkan atribut `style` (Inline CSS) untuk mendesain elemen secara individual.
- Menguasai properti-properti dasar yang mengatur warna teks, warna latar belakang, jenis font, ukuran font, dan perataan teks.

---

## Materi Utama

Sejauh ini, seluruh konten yang dibuat di HTML ditampilkan dengan teks hitam di atas latar putih — tampilan bawaan browser tanpa gaya apa pun. Untuk mengubah tampilan tersebut, dibutuhkan **CSS** (_Cascading Style Sheets_).

CSS akan dibahas secara mendalam di bagian selanjutnya dari modul ini. Namun sebelum itu, HTML menyediakan cara untuk menerapkan gaya desain secara langsung pada elemen menggunakan atribut `style`. Pendekatan ini disebut **Inline Style**.

---

### 1. Atribut `style`

Atribut `style` disisipkan langsung ke dalam tag pembuka sebuah elemen dan dapat diterapkan pada hampir semua elemen HTML yang menghasilkan tampilan visual (`<h1>`, `<p>`, `<body>`, `<div>`, dan lain-lain).

**Sintaks dasar:**

```html
<tag style="properti: nilai;">Konten elemen</tag>
```

Dua hal yang perlu diperhatikan:

- Tanda titik dua (`:`) digunakan untuk memisahkan nama properti dengan nilainya.
- Tanda titik koma (`;`) digunakan sebagai pemisah antara satu deklarasi dengan deklarasi berikutnya.

**Contoh dasar:**

```html
<!-- HTML -->
<p style="color: red;">Teks ini berwarna merah.</p>
<h2 style="text-align: center;">Judul ini berada di tengah.</h2>
```

---

### 2. Properti Desain Paling Dasar

Berikut adalah lima properti CSS yang paling sering digunakan dalam tahap awal desain halaman web.

#### A. Warna Teks (`color`)

Properti `color` digunakan untuk mengubah warna teks sebuah elemen. Nilai dapat berupa nama warna dalam bahasa Inggris, kode HEX, atau format warna lainnya yang akan dibahas lebih lanjut di bab CSS.

```html
<!-- HTML -->
<p style="color: blue;">Teks ini berwarna biru.</p>
<p style="color: crimson;">Teks ini berwarna merah tua.</p>
```

**Contoh penerapan pada konten:**

```html
<!-- HTML -->
<h1 style="color: #2c3e50;">Laporan Keuangan Semester I</h1>
<p style="color: gray;">
  Dokumen ini disusun oleh tim keuangan dan bersifat internal.
</p>
<p style="color: green;">Status: <strong>Disetujui</strong></p>
```

---

#### B. Warna Latar Belakang (`background-color`)

Properti `background-color` digunakan untuk memberikan warna latar belakang pada suatu elemen. Jika diterapkan pada elemen `<body>`, seluruh latar halaman akan berubah.

```html
<!-- HTML -->
<body style="background-color: lightgray;">
  <h1>Halaman dengan latar abu-abu terang</h1>
</body>
```

**Contoh penerapan pada elemen individual:**

```html
<!-- HTML -->
<h2>Status Pesanan</h2>
<p style="background-color: #d5f5e3; color: #1e8449;">
  Pesanan Anda telah berhasil diproses.
</p>
<p style="background-color: #fdebd0; color: #935116;">
  Pembayaran menunggu konfirmasi.
</p>
<p style="background-color: #fadbd8; color: #922b21;">
  Pesanan dibatalkan karena stok habis.
</p>
```

---

#### C. Jenis Font (`font-family`)

Properti `font-family` digunakan untuk mengubah jenis huruf (_typeface_) yang digunakan pada suatu elemen. Browser memiliki font bawaan yang bervariasi tergantung sistem operasi, sehingga umumnya disebutkan beberapa alternatif font sebagai cadangan.

```html
<!-- HTML -->
<h1 style="font-family: Arial;">Judul dengan font Arial</h1>
<p style="font-family: Georgia;">Paragraf dengan font Georgia.</p>
```

**Contoh penerapan:**

```html
<!-- HTML -->
<h1 style="font-family: Arial, sans-serif;">Panduan Penggunaan Aplikasi</h1>
<p style="font-family: Georgia, serif;">
  Dokumen ini menjelaskan langkah-langkah dasar penggunaan aplikasi untuk
  pengguna baru yang baru pertama kali mendaftar.
</p>
<code style="font-family: 'Courier New', monospace;">
  npm install my-package
</code>
```

---

#### D. Ukuran Font (`font-size`)

Properti `font-size` digunakan untuk menentukan ukuran teks. Nilai dapat dinyatakan dalam piksel (`px`), persentase (`%`), atau satuan relatif lainnya yang akan dibahas lebih lanjut di bab CSS.

```html
<!-- HTML -->
<p style="font-size: 20px;">Teks dengan ukuran 20 piksel.</p>
<p style="font-size: 14px;">Teks dengan ukuran 14 piksel — lebih kecil.</p>
```

**Contoh penerapan untuk membedakan hierarki teks secara manual:**

```html
<!-- HTML -->
<p style="font-size: 28px; font-family: Arial;">Pengumuman Penting</p>
<p style="font-size: 16px;">
  Kegiatan belajar mengajar akan diliburkan pada tanggal 17 Agustus 2025 dalam
  rangka peringatan Hari Kemerdekaan Republik Indonesia.
</p>
<p style="font-size: 12px; color: gray;">
  Dikeluarkan oleh: Bagian Akademik — 10 Agustus 2025
</p>
```

---

#### E. Perataan Teks (`text-align`)

Properti `text-align` digunakan untuk mengatur perataan teks secara horizontal. Nilai yang tersedia antara lain `left` (kiri), `center` (tengah), `right` (kanan), dan `justify` (rata kiri-kanan).

```html
<!-- HTML -->
<h1 style="text-align: center;">Judul Terpusat</h1>
<p style="text-align: right;">Hak cipta © 2025</p>
<p style="text-align: justify;">
  Teks dengan perataan justify akan memiliki tepi kiri dan kanan yang rapi,
  seperti tampilan teks pada buku atau dokumen formal.
</p>
```

**Contoh penerapan pada halaman puisi:**

```html
<!-- HTML -->
<h1 style="text-align: center; font-family: Georgia;">Senja di Tepi Kota</h1>

<p style="text-align: center; font-family: Georgia; font-size: 18px;">
  Langit jingga menyapa hari,<br />
  Burung-burung kembali ke sarang.<br />
  Angin membawa daun yang pergi,<br />
  Meninggalkan kenangan yang tak hilang.
</p>

<p style="text-align: right; font-size: 14px; color: gray;">— Penulis Anonim</p>
```

---

### 3. Menggabungkan Beberapa Properti (Kombinasi Style)

Beberapa properti dapat diterapkan sekaligus pada satu elemen dengan memisahkan setiap deklarasi menggunakan tanda titik koma (`;`).

```html
<!-- HTML -->
<p
  style="color: white; background-color: #2c3e50; font-size: 18px; text-align: center;"
>
  Teks dengan kombinasi warna, ukuran, dan perataan sekaligus.
</p>
```

**Contoh penerapan — Kartu notifikasi sederhana:**

```html
<!-- HTML -->
<h3 style="font-family: Arial; text-align: center; color: #2c3e50;">
  Notifikasi Sistem
</h3>

<p
  style="
  background-color: #d5f5e3;
  color: #1e8449;
  font-family: Arial;
  font-size: 15px;
  text-align: center;
"
>
  ✓ Data berhasil disimpan ke dalam sistem.
</p>

<p
  style="
  background-color: #fadbd8;
  color: #922b21;
  font-family: Arial;
  font-size: 15px;
  text-align: center;
"
>
  ✗ Koneksi ke server terputus. Silakan coba lagi.
</p>
```

---

### 4. Keterbatasan Inline Style

Meskipun Inline Style mudah diterapkan, pendekatan ini memiliki keterbatasan yang signifikan dalam konteks pengembangan web yang lebih besar:

- **Sulit dipelihara**: Jika gaya yang sama diterapkan pada banyak elemen, setiap perubahan harus dilakukan satu per satu pada masing-masing elemen.
- **Tidak efisien**: Tidak memungkinkan penggunaan ulang (_reuse_) gaya yang sama di berbagai tempat.
- **Mencampurkan struktur dan tampilan**: Praktik terbaik pengembangan web memisahkan kode HTML (struktur) dan CSS (tampilan) agar keduanya lebih mudah dikelola secara independen.

Inline Style paling tepat digunakan untuk:

- Prototyping atau pengujian tampilan secara cepat.
- Menerapkan gaya unik pada satu elemen tertentu yang tidak digunakan di tempat lain.
- Situasi di mana penulisan file CSS terpisah tidak memungkinkan.

Penggunaan CSS yang terstruktur — melalui file `.css` terpisah atau tag `<style>` — akan dibahas secara mendalam di bagian selanjutnya.

---

### Kesimpulan

Atribut `style` memungkinkan penerapan gaya desain langsung pada elemen HTML tanpa memerlukan file CSS terpisah. Dengan menguasai lima properti dasar — `color`, `background-color`, `font-family`, `font-size`, dan `text-align` — tampilan teks dan latar belakang elemen sudah dapat dikontrol secara langsung. Namun untuk proyek yang lebih besar, gaya sebaiknya dikelola melalui CSS yang terpisah dari struktur HTML.

**Ringkasan Properti:**

| Properti           | Fungsi                                   | Contoh Nilai                         |
| ------------------ | ---------------------------------------- | ------------------------------------ |
| `color`            | Mengubah warna teks                      | `red`, `#2c3e50`, `rgb(0,0,255)`     |
| `background-color` | Mengubah warna latar belakang elemen     | `lightgray`, `#d5f5e3`               |
| `font-family`      | Mengubah jenis huruf                     | `Arial`, `Georgia`, `monospace`      |
| `font-size`        | Mengubah ukuran teks                     | `16px`, `20px`, `150%`               |
| `text-align`       | Mengatur perataan teks secara horizontal | `left`, `center`, `right`, `justify` |

**Panduan Pemilihan Properti:**

| Kebutuhan                                             | Properti yang Digunakan                              |
| ----------------------------------------------------- | ---------------------------------------------------- |
| Mengubah warna tulisan                                | `color`                                              |
| Memberikan warna latar belakang pada elemen           | `background-color`                                   |
| Mengganti jenis huruf                                 | `font-family`                                        |
| Memperbesar atau memperkecil teks                     | `font-size`                                          |
| Memusatkan, meratakan kanan, atau menjustifikasi teks | `text-align`                                         |
| Menerapkan beberapa gaya sekaligus                    | Kombinasi dalam satu atribut `style`, dipisahkan `;` |
