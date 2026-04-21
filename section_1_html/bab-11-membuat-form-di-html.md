# Bab 11: Membuat Form di HTML

## Tujuan Pembelajaran

- Mengetahui fungsi vital Form sebagai gerbang komunikasi antara User dan Server.
- Memahami elemen dasar pembentuk formulir (`<form>`).
- Mengerti penggunaan atribut `action` dan `method` dalam pengiriman data.

## Materi Utama

Sejauh ini, website yang kita pelajari hanya bersifat **Satu Arah**: Kitalah pembuat web yang menyediakan teks atau gambar, dan pengunjung cuma bisa membaca secara pasif.
Lalu, bagaimana caranya pengunjung bisa _"berbicara"_ balik kepada web kita? Di sinilah pahlawan bernama **Web Form (Formulir Web)** beraksi!

Mulai dari proses Login Facebook, membuat Tweet baru, mendaftar akun game online, sampai fitur _Search_ di Google... semua itu menggunakan teknologi dasar yang sama, yaitu Form HTML.

### 1. Apa itu Form?

Formulir (Form) adalah komponen antarmuka yang memungkinkan interaksi "Dua Arah". Pengguna bisa mengetikkan teks, memilih opsi, mencentang kotak centang, lalu menekan sebuah tombol "Kirim" (_Submit_) untuk mengirim data tersebut ke _"Dapur Server"_.

### 2. Tag Induk `<form>`

Untuk membuat formulir, kamu membutuhkan sebuah bungkus atau wadah raksasa. Wadah ini bernama tag `<form>`. **Ingat baik-baik:** Semua kotak isian/input yang kamu buat harus berada di dalam pelukan tag `<form>` dan jangan sampai tercecer di luarnya.

**Analogi Amplop Surat:**
Tag `<form>` itu ibarat Amplop Coklat. Kotak isian nama, email, dan pasword adalah lembaran kertas isinya. Amplop inilah yang bertanggung jawab membungkus kertas-kertas tersebut lalu diantarkan oleh Pak Pos menuju tujuan akhir (Server).

### 3. Dua Atribut Wajib Form: `action` dan `method`

Sebuah formulir tidak akan bisa mengirim kemana-mana jika sistem tidak tahu **"Dikirim ke siapa?"** dan **"Dikirim lewat jalur mana?"**. Atribut `action` dan `method` menjawab kedua pertanyaan ini.

- **`action` (Tujuan Paket):**
  Atribut ini mendefinisikan URL/Alamat file Server (backend) yang bertugas meracik dan mengolah data usai tombol "Kirim" diklik. Untuk contoh latihan Front-End, kita biasanya membiarkannya kosong (`action=""`) atau diisi alamat dummy.

- **`method` (Jalur Pengiriman):**
  Ini adalah teknik pengirimannya. Hanya ada dua metode paling populer:
  1. **GET**:
     Metode pengiriman transparan/terbuka. Data yang diketik pengguna akan dirubah dan ditempelkan langsung pada _link URL_ browser.
     _Contoh:_ Saat kamu mencari kata "Kucing" di URL Google, URL akan berubah menjadi `google.com/search?q=kucing`.
     _Kekurangan:_ Sangat berbahaya! Jangan pernah memakai GET untuk mengirim data sensitif seperti _Password_ atau kartu kredit, karena akan terpampang jelas di URL.
  2. **POST**:
     Metode pengiriman tertutup/rahasia dalam "koper baja". Data dikemas tersembunyi di badan pesan sistem HTTP. Selalu gunakan `POST` untuk form pendaftaran akun, form login, atau transaksi finansial!

**Sintaks Dasar Deklarasi Form:**

```html
<!-- Form mengamankan data pengguna di jalan tol rahasia (POST) -->
<form action="/proses-register.php" method="POST">
  <!-- Area ini nanti dicadangkan untuk elemen-elemen kotak input (dibahas di Bab selanjutnya) -->

  <p>Silakan isi data di sini...</p>
</form>
```

> **Sekilas Info:** Menguasai ilmu HTML Form hanyalah menyusun "tampilannya" (Front-End) belaka. Otak cerdas yang merekam input ke dalam Database _(Log In Berhasil! / Log In Gagal!)_ dikerjakan oleh ilmu gabungan yang disebut **Back-End Engineering** (seperti menggunakan bahasa PHP, Node.js, atau Python) yang berkolaborasi dengan Form HTML ini.
