# Bab 1: Web Browser, HTML, & Sejarah HTML

## Tujuan Pembelajaran

- Memahami pengertian dan peran Web Browser dalam ekosistem internet.
- Mengenal cara kerja website secara umum.
- Memahami pengertian HTML dan perannya dalam membangun website.
- Mengetahui perkembangan HTML dari awal kemunculannya hingga standar modern HTML5.

---

## Materi Utama

---

### 1. Apa Itu Web Browser dan Bagaimana Cara Kerjanya?

Sebelum mempelajari cara membuat website, penting untuk memahami terlebih dahulu di mana website itu ditampilkan dan bagaimana cara kerjanya. Jawabannya adalah melalui **Web Browser**.

**Web Browser** (atau peramban web) adalah perangkat lunak yang bertugas mengambil dan menampilkan konten dari internet — berupa teks, gambar, video, dan elemen interaktif — ke layar perangkat pengguna.

Contoh Web Browser yang populer: Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, dan Opera.

**Analogi — Cara Kerja Browser seperti Restoran:**
Proses kerja sebuah website dapat dianalogikan dengan pengalaman memesan makanan di restoran:

1. **Pengguna** mengetikkan alamat website (misalnya `youtube.com`) di browser dan menekan Enter — sama seperti pelanggan memilih menu dari daftar.
2. **Web Browser** meneruskan permintaan tersebut ke server yang sesuai — sama seperti pelayan yang mencatat dan menyampaikan pesanan ke dapur.
3. **Server** memproses permintaan dan mengirimkan kode website (HTML, CSS, JavaScript) sebagai respons — sama seperti dapur yang menyiapkan dan menyerahkan hidangan kepada pelayan.
4. **Browser merender (menampilkan) kode tersebut** menjadi tampilan visual yang dapat dibaca dan digunakan oleh pengguna — sama seperti pelayan yang menyajikan hidangan ke meja pelanggan.

Tanpa Web Browser, konten internet hanyalah kumpulan kode teks yang tidak dapat dibaca oleh pengguna awam.

**Contoh alur proses secara teknis:**

```
Pengguna mengetik: https://www.example.com
        ↓
Browser mengirim permintaan ke server example.com
        ↓
Server mengirim kembali file HTML, CSS, dan JavaScript
        ↓
Browser membaca dan merender file tersebut
        ↓
Halaman web ditampilkan di layar pengguna
```

---

### 2. Apa Itu HTML?

**HTML** merupakan singkatan dari **HyperText Markup Language**.

Hal yang paling mendasar untuk dipahami adalah: **HTML bukan bahasa pemrograman (_programming language_).** HTML adalah **bahasa markup (_markup language_).**

Perbedaan keduanya:

| Aspek            | Bahasa Pemrograman (contoh: JavaScript, Python)  | Bahasa Markup (HTML)                        |
| ---------------- | ------------------------------------------------ | ------------------------------------------- |
| Logika           | Memiliki kondisi (`if-else`), perulangan, fungsi | Tidak memiliki logika komputasi             |
| Tujuan utama     | Memproses dan memanipulasi data                  | Menandai dan menstrukturkan dokumen         |
| Contoh instruksi | "Jika pengguna klik tombol, tampilkan pesan"     | "Teks ini adalah judul. Teks ini paragraf." |

Tugas HTML hanya satu: **memberi tanda dan struktur pada konten dokumen**, sehingga browser mengetahui bagian mana yang merupakan judul, paragraf, gambar, tautan, atau tombol.

**Analogi — Tiga Pilar Pembangunan Website:**
Peran HTML dalam pengembangan web dapat dipahami melalui analogi membangun sebuah rumah:

- **HTML adalah Struktur Bangunan** (pondasi, dinding, tiang, dan rangka). HTML menentukan apa saja yang ada di halaman: di mana letak judul, isi, gambar, dan navigasi. Tanpa HTML, halaman web tidak akan memiliki bentuk apa pun.
- **CSS adalah Dekorasi dan Estetika** (cat dinding, keramik lantai, perabotan). CSS mengatur tampilan visual dari struktur yang telah dibuat HTML — warna, ukuran, jarak, dan tata letak.
- **JavaScript adalah Sistem Fungsional** (instalasi listrik, sistem pintu otomatis, pendingin ruangan). JavaScript memberikan interaktivitas dan logika pada halaman — seperti tombol yang merespons klik, formulir yang memvalidasi input, atau konten yang berubah secara dinamis.

**Contoh sederhana struktur HTML:**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Halaman Pertama Saya</title>
  </head>
  <body>
    <h1>Selamat Datang</h1>
    <p>Ini adalah paragraf pertama saya.</p>
    <img src="foto.jpg" alt="Foto contoh" />
    <a href="https://www.example.com">Kunjungi tautan ini</a>
  </body>
</html>
```

Pada contoh di atas, browser membaca setiap tag HTML dan mengetahui fungsinya masing-masing:

- `<h1>` → ditampilkan sebagai judul utama berukuran besar.
- `<p>` → ditampilkan sebagai paragraf teks biasa.
- `<img>` → ditampilkan sebagai gambar.
- `<a>` → ditampilkan sebagai tautan yang dapat diklik.

---

### 3. Sejarah Perkembangan HTML

Memahami sejarah HTML membantu kita memahami mengapa HTML5 — versi yang digunakan saat ini — dirancang dengan fitur-fitur yang ada sekarang.

**1989–1991 — Kelahiran HTML:**
HTML diciptakan oleh **Tim Berners-Lee**, seorang ilmuwan di CERN (lembaga penelitian fisika di Swiss). Tujuan awalnya sangat spesifik: menciptakan sistem yang memungkinkan dokumen penelitian di berbagai komputer saling terhubung melalui tautan (_hyperlink_). Tidak ada bayangan tentang desain visual atau aplikasi web yang kompleks. Tampilan awalnya murni teks hitam-putih tanpa format grafis.

**1995 — HTML 2.0:**
Versi ini merupakan standarisasi resmi pertama. Mulai memperkenalkan elemen-elemen dasar seperti formulir input (`<form>`) dan tabel (`<table>`), yang membuka kemungkinan interaksi sederhana antara pengguna dan halaman web.

**1997–1999 — HTML 3.2 hingga HTML 4.01:**
Era perkembangan internet secara komersial (_dotcom boom_). Desain website mulai menggunakan warna dan CSS sederhana untuk mengatur tampilan. HTML 4.01 menjadi standar yang digunakan selama lebih dari satu dekade dan menjadi fondasi bagi jutaan website di seluruh dunia.

**Era 2000-an — XHTML:**
Sebuah upaya untuk memperketat aturan penulisan HTML agar lebih konsisten dan terstruktur secara teknis. Namun, aturannya terlalu ketat — satu karakter yang salah dapat menyebabkan seluruh halaman gagal ditampilkan. Karena sulitnya adopsi, standar ini secara bertahap ditinggalkan.

**2014 – Sekarang — HTML5:**
HTML5 dirilis sebagai revisi besar yang merevolusi cara kerja web modern. Fitur-fitur utama yang diperkenalkan antara lain:

1. Dukungan pemutaran video dan audio secara langsung di browser tanpa memerlukan perangkat lunak tambahan seperti Adobe Flash Player.
2. Elemen-elemen semantik (`<header>`, `<nav>`, `<article>`, `<footer>`, dan lain-lain) yang membuat struktur dokumen lebih bermakna dan lebih mudah diindeks oleh mesin pencari.
3. Dukungan terhadap desain web responsif yang dapat menyesuaikan tampilan dengan berbagai ukuran layar.
4. Kemampuan untuk menjalankan sebagian fungsi web secara _offline_ menggunakan teknologi Service Worker dan Cache API.

**Ringkasan Garis Waktu:**

| Tahun         | Versi       | Pencapaian Utama                                                       |
| ------------- | ----------- | ---------------------------------------------------------------------- |
| 1989–1991     | HTML (awal) | Diciptakan oleh Tim Berners-Lee untuk menghubungkan dokumen penelitian |
| 1995          | HTML 2.0    | Standarisasi resmi pertama; formulir dan tabel diperkenalkan           |
| 1997          | HTML 3.2    | Dukungan CSS awal; tampilan web mulai lebih terstruktur                |
| 1999          | HTML 4.01   | Standar dominan selama lebih dari satu dekade                          |
| 2000-an       | XHTML       | Upaya pengetatan aturan; tidak berhasil diadopsi secara luas           |
| 2014–sekarang | HTML5       | Standar modern; video, audio, semantik, responsif, dan offline support |

---

### Kesimpulan

Web Browser adalah perangkat lunak yang menerjemahkan kode menjadi tampilan visual yang dapat digunakan oleh pengguna. HTML adalah bahasa markup yang menjadi fondasi dari setiap halaman web — bertugas menentukan struktur dan konten, bukan logika atau tampilan. Seiring perkembangannya selama lebih dari tiga dekade, HTML kini telah mencapai standar HTML5 yang mendukung kebutuhan web modern secara komprehensif.

**Ringkasan Konsep:**

| Konsep      | Pengertian                                                                  |
| ----------- | --------------------------------------------------------------------------- |
| Web Browser | Perangkat lunak yang mengambil dan menampilkan konten dari internet         |
| HTML        | Bahasa markup untuk menandai dan menstrukturkan konten halaman web          |
| CSS         | Bahasa untuk mengatur tampilan visual elemen HTML                           |
| JavaScript  | Bahasa pemrograman untuk menambahkan interaktivitas dan logika pada website |
| HTML5       | Standar HTML modern yang mendukung multimedia, semantik, dan responsivitas  |

**Panduan Pemahaman Awal:**

| Pertanyaan                              | Jawaban Singkat                                      |
| --------------------------------------- | ---------------------------------------------------- |
| Di mana website ditampilkan?            | Di dalam Web Browser                                 |
| Apakah HTML bahasa pemrograman?         | Tidak — HTML adalah bahasa markup                    |
| Apa peran HTML dalam sebuah website?    | Menentukan struktur dan konten halaman               |
| Apa peran CSS?                          | Mengatur tampilan visual (warna, ukuran, tata letak) |
| Apa peran JavaScript?                   | Menambahkan interaktivitas dan logika                |
| Versi HTML apa yang digunakan saat ini? | HTML5, yang dirilis secara resmi pada tahun 2014     |
