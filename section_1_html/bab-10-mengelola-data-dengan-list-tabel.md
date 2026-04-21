# Bab 10: Mengelola Data dengan List & Tabel

## Tujuan Pembelajaran

- Mampu membedakan penggunaan _Ordered List_ dan _Unordered List_.
- Menguasai cara membuat daftar bersarang (_Nested List_).
- Memahami struktur hirarki pembuatan Tabel (Baris, Kolom, Header, dan Data).
- Mampu menyatukan sel tabel yang bersebelahan (_rowspan_ & _colspan_).

## Materi Utama

Dalam menyajikan informasi di website, menulis paragraf panjang tak berujung akan membuat pembaca bosan. Terkadang data lebih enak dibaca jika disusun ke bawah berupa poin-poin (Daftar/List) atau diatur menyamping layaknya baris Excel (Tabel).

HTML menyediakan tag khusus agar penyusunan data ini rapi secara otomatis.

### 1. Membuat Daftar (List)

Ada dua tipe utama pembuat poin-poin daftar di HTML:

1. **Unordered List (`<ul>`)**: Daftar tidak berurutan. Format defaultnya berupa simbol titik hitam/bulatan (_bullet_). Cocok untuk daftar belanjaan.
2. **Ordered List (`<ol>`)**: Daftar berurutan. Format defaultnya berupa angka (1, 2, 3..). Cocok untuk menulis langkah-langkah resep masakan.

**Bagaimana cara kerjanya?**
Baik `<ul>` maupun `<ol>` hanyalah bungkus luar (kardusnya). Untuk membuat isi poin-poin daftarnya, kamu wajib menggunakan tag `<li>` (List Item) di dalamnya.

Contoh Unordered List:

```html
<h3>Daftar Belanja Pasar:</h3>
<ul>
  <li>Bawang Merah</li>
  <li>Minyak Goreng</li>
  <li>Telur Ayam</li>
</ul>
```

Contoh Ordered List:

```html
<h3>Cara Merebus Mie Instan:</h3>
<ol>
  <li>Didihkan air 400cc.</li>
  <li>Masukkan mie ke dalam panci.</li>
  <li>Tunggu 3 menit, lalu angkat dan tiriskan.</li>
</ol>
```

**Daftar Bersarang (Nested List)**
Kamu bahkan bisa menaruh daftar di dalam daftar! (Mirip membuat sub-menu).

```html
<ul>
  <li>
    Buah-buahan
    <ul>
      <li>Mangga</li>
      <li>Pisang</li>
    </ul>
  </li>
  <li>Sayuran</li>
</ul>
```

### 2. Membangun Tabel (`<table>`)

Membuat tabel di HTML pada awalnya terasa seperti bermain _puzzle_ karena kita tidak menggambar garis, melainkan menyusun blok baris per baris dari atas ke bawah.

**Anatomi Wajib Tabel:**

1. `<table>`: Membungkus keseluruhan tabel.
2. `<tr>` (Table Row): Berfungsi menciptakan 1 Baris horizontal (menyamping dari kiri ke kanan).
3. `<th>` (Table Header): Membuat sel/kolom judul tabel. Teks otomatis menjadi tebal dan ke tengah.
4. `<td>` (Table Data): Membuat sel/kolom data biasa (mengisi kotak-kotak di bawah judul).

**Analogi Membangun Apartemen:**
Bayangkan tabel adalah apartemen.
Setiap kali kamu memanggil `<tr>`, kamu sedang membangun lantai baru. Di setiap lantai tersebut, kamu harus menentukan ada berapa banyak kamar (`<td>`) yang berjejer.

Contoh Tabel Biodata Sederhana:
_(Trik: Gunakan atribut `border="1"` pada tag `<table>` agar garis tabelnya terlihat, karena default tabel HTML itu transparan/ghaib)_

```html
<table border="1">
  <!-- Baris Pertama (Judul) -->
  <tr>
    <th>No.</th>
    <th>Nama Siswa</th>
    <th>Nilai Ujian</th>
  </tr>

  <!-- Baris Kedua (Data Pertama) -->
  <tr>
    <td>1</td>
    <td>Budi Santoso</td>
    <td>95</td>
  </tr>

  <!-- Baris Ketiga (Data Kedua) -->
  <tr>
    <td>2</td>
    <td>Siti Aminah</td>
    <td>88</td>
  </tr>
</table>
```

### 3. Menggabungkan Sel Tabel (Merge Cells)

Mirip seperti fitur "Merge & Center" di Microsoft Excel, di HTML kita bisa menjebol tembok pemisah antar kotak menggunakan atribut sakti:

- `colspan`: Menyatukan sel secara horizontal (menyimping / meleburkan tiang pilar).
- `rowspan`: Menyatukan sel secara vertikal (ke bawah / menjebol lantai atap).

Contoh menggabungkan 2 kolom ke samping:

```html
<table border="1">
  <tr>
    <th>Nama Item</th>
    <th colspan="2">Aksi (Gabung 2 Kolom)</th>
  </tr>
  <tr>
    <td>Buku Tulis</td>
    <td>Edit</td>
    <td>Hapus</td>
  </tr>
</table>
```
