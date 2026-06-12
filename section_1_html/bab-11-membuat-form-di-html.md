# Bab 11: Membuat Form di HTML

## Tujuan Pembelajaran

- Memahami fungsi Form sebagai sarana komunikasi dua arah antara pengguna dan server.
- Menguasai elemen dasar pembentuk formulir menggunakan tag `<form>`.
- Memahami peran dan perbedaan atribut `action` dan `method` dalam pengiriman data formulir.
- Mengetahui kapan menggunakan metode `GET` dan kapan menggunakan metode `POST`.

---

## Materi Utama

Seluruh konten yang telah dipelajari sebelumnya — teks, gambar, tautan, tabel — bersifat **satu arah**: pengguna hanya dapat membaca atau melihat informasi yang disajikan. Namun sebagian besar aplikasi web modern membutuhkan interaksi **dua arah** — pengguna perlu dapat mengirimkan data kembali ke server.

Proses login, pendaftaran akun, pengiriman pesan, formulir pencarian, hingga transaksi pembayaran online — semuanya dibangun di atas teknologi yang sama: **HTML Form**.

---

### 1. Apa Itu Form?

**Form** (formulir web) adalah komponen antarmuka yang memungkinkan pengguna memasukkan data — berupa teks, pilihan, atau file — dan mengirimkannya ke server untuk diproses. Setelah tombol kirim (_submit_) ditekan, data yang telah diisi akan diteruskan ke server sesuai konfigurasi yang ditentukan oleh pengembang.

**Contoh penggunaan Form di aplikasi nyata:**

| Aplikasi            | Bentuk Penggunaan Form                                        |
| ------------------- | ------------------------------------------------------------- |
| Google              | Kolom pencarian untuk mengirim kata kunci ke server pencarian |
| Media sosial        | Formulir login dan pendaftaran akun baru                      |
| Toko online         | Formulir pengisian alamat pengiriman dan data pembayaran      |
| Platform e-learning | Formulir pendaftaran kursus dan pengumpulan tugas             |

---

### 2. Tag Induk `<form>`

Seluruh elemen input di dalam sebuah formulir harus dibungkus oleh tag `<form>`. Tag ini bertugas sebagai wadah yang mengelompokkan semua elemen isian dan mendefinisikan bagaimana data dari elemen-elemen tersebut akan dikirimkan.

**Sintaks dasar:**

```html
<form action="URL_TUJUAN" method="METODE_PENGIRIMAN">
  <!-- Elemen-elemen input ditempatkan di dalam sini -->
</form>
```

**Analogi — Amplop Surat:**
Tag `<form>` dapat dianalogikan sebagai amplop surat. Elemen-elemen input di dalamnya — seperti kolom nama, email, dan kata sandi — adalah lembaran isi surat. Amplop inilah yang membungkus semua isian tersebut dan menentukan alamat tujuan serta cara pengirimannya.

**Contoh sederhana:**

```html
<!-- HTML -->
<form action="/proses-kontak.php" method="POST">
  <!-- Elemen input akan ditempatkan di sini -->
  <p>Formulir kontak akan tersedia di sini.</p>
</form>
```

---

### 3. Atribut `action` dan `method`

Dua atribut utama pada tag `<form>` adalah `action` dan `method`. Keduanya bekerja sama untuk menentukan **ke mana** dan **bagaimana** data formulir dikirimkan.

#### Atribut `action`

Atribut `action` menentukan URL tujuan — yaitu alamat file atau endpoint di server yang akan menerima dan memproses data formulir setelah tombol kirim ditekan.

```html
<!-- Data dikirim ke file proses-register.php di server -->
<form action="/proses-register.php" method="POST">...</form>

<!-- Jika action kosong, data dikirim ke URL halaman yang sedang aktif -->
<form action="" method="POST">...</form>
```

#### Atribut `method`

Atribut `method` menentukan metode pengiriman data yang digunakan oleh protokol HTTP. Terdapat dua nilai utama: `GET` dan `POST`.

**Metode GET:**
Data formulir dikirimkan dengan cara ditambahkan langsung pada URL sebagai _query string_. Seluruh isian pengguna akan terlihat di bilah alamat browser.

```
Contoh URL setelah submit dengan GET:
https://www.contoh.com/cari?kata=html&kategori=tutorial
```

```html
<!-- GET cocok untuk formulir pencarian — data tidak sensitif -->
<form action="/cari" method="GET">
  <!-- Elemen input pencarian -->
</form>
```

**Metode POST:**
Data formulir dikirimkan di dalam badan (_body_) permintaan HTTP, tidak terlihat di URL browser.

```html
<!-- POST wajib digunakan untuk data sensitif -->
<form action="/proses-login.php" method="POST">
  <!-- Elemen input email dan kata sandi -->
</form>
```

**Perbandingan GET dan POST:**

| Aspek                 | GET                                               | POST                                            |
| --------------------- | ------------------------------------------------- | ----------------------------------------------- |
| Posisi data           | Ditampilkan di URL (_query string_)               | Tersembunyi di dalam body permintaan HTTP       |
| Keamanan              | Rendah — data terlihat di URL dan riwayat browser | Lebih aman untuk data sensitif                  |
| Batas panjang data    | Terbatas (bergantung pada batas panjang URL)      | Tidak terbatas secara praktis                   |
| Dapat di-_bookmark_   | Ya — URL berisi seluruh data formulir             | Tidak — data tidak tersimpan di URL             |
| Penggunaan yang tepat | Pencarian, filter, navigasi                       | Login, pendaftaran, transaksi, pengiriman pesan |

> **Catatan Keamanan:** Jangan menggunakan metode `GET` untuk mengirim data sensitif seperti kata sandi, nomor kartu kredit, atau informasi pribadi lainnya. Data tersebut akan terlihat secara langsung di URL browser dan tersimpan di riwayat browsing.

---

### 4. Batasan HTML Form: Peran Back-End

HTML Form hanya bertanggung jawab atas **tampilan antarmuka** (_front-end_) — menyediakan kolom isian dan tombol kirim. HTML tidak memiliki kemampuan untuk menyimpan data ke dalam basis data, memvalidasi data di sisi server, atau mengirimkan email konfirmasi.

Semua pemrosesan data setelah formulir dikirim — seperti menyimpan data ke basis data, mengautentikasi pengguna, atau mengirim email — dilakukan oleh teknologi **Back-End** seperti PHP, Node.js, Python, atau Ruby.

```
Alur kerja Form secara lengkap:

[Pengguna mengisi Form]
        ↓
[Pengguna menekan tombol Submit]
        ↓
[Browser mengirim data ke server sesuai action dan method]
        ↓
[Server (Back-End) menerima dan memproses data]
        ↓
[Server mengirim respons kembali ke browser]
        ↓
[Browser menampilkan hasil (berhasil / gagal / halaman baru)]
```

**Contoh struktur form pendaftaran yang lengkap (tampilan saja):**

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Formulir Pendaftaran</title>
  </head>
  <body>
    <h1>Daftar Akun Baru</h1>

    <form action="/proses-daftar.php" method="POST">
      <!--
        Elemen-elemen input akan dibahas secara lengkap pada bab berikutnya.
        Struktur form ini menunjukkan cara penggunaan action dan method yang benar.
      -->

      <p>
        Sudah memiliki akun?
        <a href="/login.html">Masuk di sini</a>.
      </p>
    </form>
  </body>
</html>
```

**Contoh form pencarian dengan metode GET:**

```html
<!-- HTML -->
<form action="/hasil-pencarian.html" method="GET">
  <!--
    Dengan method GET, saat pengguna mencari "laptop gaming",
    URL akan menjadi: /hasil-pencarian.html?q=laptop+gaming
    Hal ini memungkinkan hasil pencarian untuk di-bookmark atau dibagikan.
  -->
  <p>Masukkan kata kunci pencarian dan tekan Enter.</p>
</form>
```

---

### Kesimpulan

Tag `<form>` adalah fondasi dari setiap interaksi dua arah di halaman web. Memahami perbedaan antara metode `GET` dan `POST` sangat penting untuk memastikan data pengguna dikirimkan melalui jalur yang tepat dan aman. Elemen-elemen input yang mengisi formulir — seperti kolom teks, tombol radio, kotak centang, dan tombol submit — akan dibahas secara lengkap pada bab berikutnya.

**Ringkasan Elemen dan Atribut:**

| Elemen / Atribut | Fungsi                                                    |
| ---------------- | --------------------------------------------------------- |
| `<form>`         | Wadah utama yang membungkus seluruh elemen input formulir |
| `action`         | Menentukan URL tujuan pengiriman data formulir            |
| `method`         | Menentukan metode pengiriman data (`GET` atau `POST`)     |

**Panduan Pemilihan Metode:**

| Kebutuhan                                              | Metode yang Disarankan |
| ------------------------------------------------------ | ---------------------- |
| Formulir pencarian atau filter konten                  | `GET`                  |
| Formulir login atau autentikasi                        | `POST`                 |
| Formulir pendaftaran akun baru                         | `POST`                 |
| Formulir pengiriman pesan atau kontak                  | `POST`                 |
| Formulir yang mengandung kata sandi atau data sensitif | `POST`                 |
| Formulir yang hasilnya perlu dapat di-_bookmark_       | `GET`                  |
