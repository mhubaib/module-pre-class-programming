# Bab 10: Mengelola Data dengan List & Tabel

## Tujuan Pembelajaran

- Membedakan penggunaan _Ordered List_ dan _Unordered List_ sesuai konteks konten.
- Membuat daftar bersarang (_Nested List_) untuk merepresentasikan hierarki informasi.
- Memahami struktur elemen tabel HTML: baris, kolom, header, dan data.
- Menggabungkan sel tabel secara horizontal dan vertikal menggunakan `colspan` dan `rowspan`.

---

## Materi Utama

Tidak semua informasi paling efektif disampaikan dalam bentuk paragraf. Data yang bersifat enumeratif — seperti langkah-langkah, daftar item, atau informasi perbandingan — jauh lebih mudah dibaca jika disajikan dalam bentuk daftar (_list_) atau tabel. HTML menyediakan elemen khusus untuk kedua kebutuhan tersebut.

---

### 1. Membuat Daftar (List)

HTML menyediakan dua jenis daftar utama:

| Jenis          | Tag    | Format Bawaan           | Kapan Digunakan                                 |
| -------------- | ------ | ----------------------- | ----------------------------------------------- |
| Unordered List | `<ul>` | Simbol bulat (_bullet_) | Daftar item yang tidak memiliki urutan tertentu |
| Ordered List   | `<ol>` | Angka (1, 2, 3...)      | Daftar item yang memiliki urutan atau tahapan   |

Baik `<ul>` maupun `<ol>` berfungsi sebagai wadah daftar. Setiap item di dalamnya ditandai dengan tag `<li>` (_List Item_).

#### Unordered List (`<ul>`)

Digunakan untuk daftar yang urutan itemnya tidak relevan — seperti daftar belanjaan, fitur produk, atau daftar pilihan.

```html
<!-- HTML -->
<h3>Daftar Belanja:</h3>
<ul>
  <li>Bawang Merah</li>
  <li>Minyak Goreng</li>
  <li>Telur Ayam</li>
</ul>
```

**Contoh penerapan — Daftar fitur produk:**

```html
<!-- HTML -->
<h2>Fitur Unggulan Aplikasi</h2>
<ul>
  <li>Antarmuka yang mudah digunakan</li>
  <li>Sinkronisasi data secara otomatis</li>
  <li>Tersedia di Android dan iOS</li>
  <li>Dukungan pelanggan 24 jam</li>
</ul>
```

#### Ordered List (`<ol>`)

Digunakan untuk daftar yang urutan itemnya penting — seperti langkah-langkah prosedur, peringkat, atau instruksi berurutan.

```html
<!-- HTML -->
<h3>Cara Merebus Mie Instan:</h3>
<ol>
  <li>Didihkan air sebanyak 400 ml.</li>
  <li>Masukkan mie ke dalam panci berisi air mendidih.</li>
  <li>Tunggu selama 3 menit hingga mie matang.</li>
  <li>Angkat dan tiriskan, lalu campurkan dengan bumbu.</li>
</ol>
```

**Contoh penerapan — Panduan instalasi perangkat lunak:**

```html
<!-- HTML -->
<h2>Langkah Instalasi Aplikasi</h2>
<ol>
  <li>Unduh file instalasi dari halaman resmi.</li>
  <li>
    Buka file yang telah diunduh dan klik
    <strong>Jalankan sebagai Administrator</strong>.
  </li>
  <li>Ikuti panduan instalasi yang muncul di layar.</li>
  <li>Masukkan kunci lisensi yang tertera di email konfirmasi pembelian.</li>
  <li>Klik <strong>Selesai</strong> untuk menyelesaikan instalasi.</li>
</ol>
```

#### Daftar Bersarang (Nested List)

Sebuah daftar dapat disisipkan di dalam item daftar lain untuk merepresentasikan sub-kategori atau hierarki informasi.

```html
<!-- HTML -->
<ul>
  <li>
    Buah-buahan
    <ul>
      <li>Mangga</li>
      <li>Pisang</li>
      <li>Jeruk</li>
    </ul>
  </li>
  <li>
    Sayuran
    <ul>
      <li>Bayam</li>
      <li>Wortel</li>
    </ul>
  </li>
</ul>
```

**Contoh penerapan — Menu navigasi bersarang:**

```html
<!-- HTML -->
<nav>
  <ul>
    <li><a href="index.html">Beranda</a></li>
    <li>
      <a href="produk.html">Produk</a>
      <ul>
        <li><a href="produk/sepatu.html">Sepatu</a></li>
        <li><a href="produk/tas.html">Tas</a></li>
        <li><a href="produk/aksesoris.html">Aksesoris</a></li>
      </ul>
    </li>
    <li><a href="tentang.html">Tentang Kami</a></li>
    <li><a href="kontak.html">Kontak</a></li>
  </ul>
</nav>
```

> **Catatan:** Gabungan `<ul>` dan `<ol>` juga dapat digunakan dalam satu nested list. Misalnya, kategori utama menggunakan `<ul>` (tidak berurutan), sementara langkah-langkah di dalam tiap kategori menggunakan `<ol>` (berurutan).

---

### 2. Membangun Tabel (`<table>`)

Tabel HTML dibangun dengan menyusun baris dan kolom secara hierarkis — bukan dengan menggambar garis secara manual. Pemahaman terhadap urutan elemen tabel sangat penting agar strukturnya tidak berantakan.

**Elemen-elemen utama tabel:**

| Elemen    | Fungsi                                                                   |
| --------- | ------------------------------------------------------------------------ |
| `<table>` | Membungkus keseluruhan tabel                                             |
| `<thead>` | Mengelompokkan baris-baris header tabel (opsional, namun disarankan)     |
| `<tbody>` | Mengelompokkan baris-baris data utama tabel (opsional, namun disarankan) |
| `<tfoot>` | Mengelompokkan baris-baris penutup atau ringkasan tabel (opsional)       |
| `<tr>`    | Membuat satu baris horizontal dalam tabel                                |
| `<th>`    | Membuat sel header — teks otomatis tebal dan terpusat                    |
| `<td>`    | Membuat sel data biasa                                                   |

**Cara membaca struktur tabel:**
Tabel dibangun baris demi baris dari atas ke bawah. Setiap `<tr>` mendefinisikan satu baris, dan di dalamnya terdapat beberapa `<th>` atau `<td>` yang membentuk kolom-kolom dalam baris tersebut.

**Contoh tabel dasar:**

```html
<!-- HTML -->
<table border="1">
  <thead>
    <tr>
      <th>No.</th>
      <th>Nama Siswa</th>
      <th>Nilai Ujian</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Budi Santoso</td>
      <td>95</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Siti Aminah</td>
      <td>88</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Andi Pratama</td>
      <td>91</td>
    </tr>
  </tbody>
</table>
```

> **Catatan:** Atribut `border="1"` digunakan agar garis tabel terlihat secara langsung di browser, karena secara bawaan tabel HTML ditampilkan tanpa garis. Dalam praktik pengembangan web yang sesungguhnya, tampilan garis tabel sebaiknya diatur menggunakan CSS.

**Contoh penerapan — Tabel jadwal kegiatan:**

```html
<!-- HTML -->
<h2>Jadwal Kursus Web Development</h2>
<table border="1">
  <thead>
    <tr>
      <th>Hari</th>
      <th>Sesi</th>
      <th>Materi</th>
      <th>Durasi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Senin</td>
      <td>Pagi</td>
      <td>Dasar-Dasar HTML</td>
      <td>2 Jam</td>
    </tr>
    <tr>
      <td>Selasa</td>
      <td>Pagi</td>
      <td>CSS Dasar dan Box Model</td>
      <td>2 Jam</td>
    </tr>
    <tr>
      <td>Rabu</td>
      <td>Siang</td>
      <td>Flexbox dan Grid Layout</td>
      <td>3 Jam</td>
    </tr>
    <tr>
      <td>Kamis</td>
      <td>Siang</td>
      <td>JavaScript untuk Pemula</td>
      <td>3 Jam</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Total Durasi Kursus</td>
      <td>10 Jam</td>
    </tr>
  </tfoot>
</table>
```

---

### 3. Menggabungkan Sel Tabel (`colspan` dan `rowspan`)

HTML menyediakan dua atribut untuk menggabungkan sel-sel yang bersebelahan, serupa dengan fitur _Merge Cells_ di Microsoft Excel:

- **`colspan`**: Menggabungkan sejumlah sel secara **horizontal** (menyamping). Nilai atribut menentukan berapa banyak kolom yang digabungkan.
- **`rowspan`**: Menggabungkan sejumlah sel secara **vertikal** (ke bawah). Nilai atribut menentukan berapa banyak baris yang digabungkan.

**Contoh `colspan` — Menggabungkan sel secara horizontal:**

```html
<!-- HTML -->
<table border="1">
  <thead>
    <tr>
      <th>Nama Item</th>
      <th colspan="2">Aksi</th>
      <!-- Sel ini menempati 2 kolom -->
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Buku Tulis</td>
      <td>Edit</td>
      <td>Hapus</td>
    </tr>
    <tr>
      <td>Pulpen</td>
      <td>Edit</td>
      <td>Hapus</td>
    </tr>
  </tbody>
</table>
```

**Contoh `rowspan` — Menggabungkan sel secara vertikal:**

```html
<!-- HTML -->
<table border="1">
  <thead>
    <tr>
      <th>Kategori</th>
      <th>Nama Produk</th>
      <th>Harga</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="3">Elektronik</td>
      <!-- Sel ini menempati 3 baris ke bawah -->
      <td>Laptop</td>
      <td>Rp 8.000.000</td>
    </tr>
    <tr>
      <!-- Kolom "Kategori" tidak perlu ditulis — sudah diisi rowspan di atas -->
      <td>Smartphone</td>
      <td>Rp 4.500.000</td>
    </tr>
    <tr>
      <td>Earphone</td>
      <td>Rp 350.000</td>
    </tr>
    <tr>
      <td rowspan="2">Pakaian</td>
      <td>Kemeja</td>
      <td>Rp 150.000</td>
    </tr>
    <tr>
      <td>Celana Jeans</td>
      <td>Rp 280.000</td>
    </tr>
  </tbody>
</table>
```

**Contoh penerapan gabungan `colspan` dan `rowspan` — Laporan ringkasan:**

```html
<!-- HTML -->
<h2>Ringkasan Penjualan Kuartal I</h2>
<table border="1">
  <thead>
    <tr>
      <th rowspan="2">Kategori</th>
      <!-- Menempati 2 baris header -->
      <th colspan="3">Bulan (2025)</th>
      <!-- Menempati 3 kolom -->
      <th rowspan="2">Total</th>
    </tr>
    <tr>
      <!-- Baris header kedua untuk sub-kolom bulan -->
      <th>Januari</th>
      <th>Februari</th>
      <th>Maret</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Elektronik</td>
      <td>Rp 42.000.000</td>
      <td>Rp 38.500.000</td>
      <td>Rp 51.000.000</td>
      <td>Rp 131.500.000</td>
    </tr>
    <tr>
      <td>Pakaian</td>
      <td>Rp 18.000.000</td>
      <td>Rp 22.000.000</td>
      <td>Rp 19.500.000</td>
      <td>Rp 59.500.000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td><strong>Total Keseluruhan</strong></td>
      <td>Rp 60.000.000</td>
      <td>Rp 60.500.000</td>
      <td>Rp 70.500.000</td>
      <td><strong>Rp 191.000.000</strong></td>
    </tr>
  </tfoot>
</table>
```

---

### Kesimpulan

List dan tabel adalah dua cara utama untuk menyajikan data yang terstruktur di halaman web. List digunakan untuk informasi yang bersifat enumeratif, sementara tabel digunakan untuk informasi yang memiliki hubungan antar baris dan kolom. Penguasaan `colspan` dan `rowspan` memungkinkan pembuatan tabel yang kompleks dan representatif, seperti laporan, jadwal, atau tabel perbandingan.

**Ringkasan Elemen:**

| Elemen    | Fungsi                                        |
| --------- | --------------------------------------------- |
| `<ul>`    | Daftar tidak berurutan (dengan _bullet_)      |
| `<ol>`    | Daftar berurutan (dengan angka)               |
| `<li>`    | Item dalam daftar `<ul>` atau `<ol>`          |
| `<table>` | Wadah utama tabel                             |
| `<thead>` | Bagian header tabel                           |
| `<tbody>` | Bagian data utama tabel                       |
| `<tfoot>` | Bagian penutup atau ringkasan tabel           |
| `<tr>`    | Satu baris dalam tabel                        |
| `<th>`    | Sel header — teks otomatis tebal dan terpusat |
| `<td>`    | Sel data biasa                                |

**Panduan Pemilihan Elemen:**

| Kebutuhan                                 | Elemen yang Digunakan                            |
| ----------------------------------------- | ------------------------------------------------ |
| Daftar item tanpa urutan tertentu         | `<ul>` + `<li>`                                  |
| Daftar langkah atau prosedur berurutan    | `<ol>` + `<li>`                                  |
| Sub-kategori atau hierarki dalam daftar   | Nested list (`<ul>` atau `<ol>` di dalam `<li>`) |
| Data tabular dengan baris dan kolom       | `<table>` + `<tr>` + `<th>` / `<td>`             |
| Menggabungkan beberapa kolom menjadi satu | Atribut `colspan` pada `<th>` atau `<td>`        |
| Menggabungkan beberapa baris menjadi satu | Atribut `rowspan` pada `<th>` atau `<td>`        |
