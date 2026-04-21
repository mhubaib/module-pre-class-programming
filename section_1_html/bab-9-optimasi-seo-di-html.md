# Bab 9: Optimasi SEO di HTML

## Tujuan Pembelajaran

- Mengerti definisi SEO dan betapa vitalnya hal ini bagi laju bisnis/trafik web.
- Menguasai trik menyisipkan `Meta Tags` (Title, Description, Keywords) ke dalam `<head>`.
- Mengimplementasikan konsep elemen _"Semantic HTML"_ layaknya penulis profesional struktur web.
- Memahami strategi hirarki Judul (`<h1>`-`<h6>`) yang dicintai Google.

## Materi Utama

Bayangkan kamu sudah bekerja siang-malam membangun website HTML yang desainnya paling menawan sejagat raya. Namun ketika dirilis ke publik... tidak ada satupun manusia yang berkunjung. Saat namamu diketik di kotak pencari Google, browsermu tak pernah muncul sekalipun. Miris, bukan?

Nah, di sinilah ilmu **SEO (Search Engine Optimization)** masuk. SEO adalah serangkaian usaha terstruktur untuk merayu algoritma mesin-pencari (Google, Bing, Yahoo) agar memprioritaskan websitemu naik meroket ke urutan #1 Halaman Pertama saat orang mengetikkan kata kunci tertentu.

Dan ya, usaha merayu algoritma tersebut sejatinya dimulai langsung dari jantung paling dasar: **Kode HTML**.

### 1. Meta Tag di Area Backstage (`<head>`)

**Analogi Pustakawan Cerewet (Google Bot):**
Mesin Google mengirimkan jutaan robot laba-laba canggih (_Spider/Crawler_) untuk membaca seluruh dunia maya. Robot ini adalah pustakawan tunanetra yang datang ke rumah HTML-mu. Ia tidak peduli secantik apa desain CSS-mu. Ia hanya meraba kode teksmu dari atas ke bawah untuk menyimpulkan: _"Gedung ini membahas topik apa ya?"_

Fokus utama sang pustakawan terletak di ruang `<head>`.

**A. Title Tag (Raja SEO)**
`<title>` adalah nyawa websitemu. Judul ini akan tercetak raksasa berwarna biru tebal di deretan list pencarian Google.
_Kesalahan pemula:_ Menulis `<title>Home</title>`. Padahal, siapa yang akan mencari kata "Home" di Google?
_Praktek Benar:_ Tulis maksimal 60 karakter memuat inti sasaran pasar.

```html
<title>Kursus Potong Rambut Pria Terbaik Jakarta - BudiBarber</title>
```

**B. Meta Description (Sinopsis Pengeklik)**
Ini digunakan untuk menulis rangkuman kalimat sekitar 150-160 karakter yang akan muncul bertugas memikat orang agar mau mengklik _link_ Google-mu tadi.

```html
<meta
  name="description"
  content="Daftar sekarang di BudiBarber, akademi potong rambut terkemuka di Jakarta. Diajarkan oleh kapster berpengalaman 15 tahun. Diskon khusus pemula!"
/>
```

### 2. Semantic HTML (Struktur Ber-Makna)

Sadarkah kamu jika sebelum HTML5 rilis, semua _programmer_ memblok dan mempartisi bagian header, tubuh (konten), dan roda bawah (footer) website **hanyalah** menggunakan satu tag generik yang dinamakan `<div>`. Bagian navigasi adalah `<div>`, bagian artikel itu `<div>`, bagian hak cipta adalah `<div>`. Kekacaubalauan ini membuat robot Google sering salah identifikasi.

HTML5 membawa keajaiban revolusi bernama **Tag Semantik (Semantic Tag)**.
"Semantik" artinya memiliki arti/maksud yang terdefinisi kuat secara bahasa manusia, bukan sekadar pelindung teks buta.

Beberapa garda depan komponen Semantik pembantu SEO:

- `<header>`: Untuk mendeklarasikan area kepala halaman (biasanya memuat Logo Utama dan area banner).
- `<nav>` (Navigation): Penanda bahwa area ini mengandung kumpulan link menu navigasi (contoh: Home, About Us, Layanan, Kontak). Google akan mendeteksi area ini sebagai menu peta mutlak.
- `<main>`: Memberitahu sistem bahwa disinilah wadah utama isi esensial perbincangan halaman ini. Hanya ada satu elemen `<main>` per halaman (sangat disukai program pemantau difabel pembaca layar/Screen Reader untuk bisa langsung lompat masuk isi).
- `<article>` / `<section>`: Membungkus bagian postingan blog ruitn yang bisa berdiri sendiri independen dan dicerna.
- `<footer>`: Mengikat elemen penutup bawah rumah/kalimat _copyright_.

**Bentuk Web Modern yang Memuaskan SEO:**

```html
<body>
  <header>
    <h1>BudiBarber</h1>
    <nav>
      <a href="index.html">Beranda</a> |
      <a href="promo.html">Promo Potong</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>Gaya Rambut Pria Terpopuler 2026</h2>
      <p>
        Tahun ini, gaya potongan Comma Hair dan French Crop mendominasi
        panggung...
      </p>
    </article>
  </main>

  <footer>
    <p>&copy; 2026 BudiBarber. Hak Cipta Dilindungi.</p>
  </footer>
</body>
```

### 3. Hierarki Heading yang Ditaati Mutlak

Terakhir dan paling gampang diselewengkan: Jangan melompat-lompat menaruh derajat _Heading_!

Robot pendeteksi Google membaca topik website dengan membuat struktur layaknya menelusuri daftar isi makalan skripsi. Aturan Emas SEO:

1. Pastikan cuma ada **SATU `<h1>`** mewakili judul dominan tunggal perhalaman (Maksimal banget, tolong jangan menumpuk). Jika ingin memakai teks besar kedua, rubah besarnya pakai CSS, jangan mengorbankan sakralitas HTML `<h1>` demi mengejar visual "font besar"!
2. Urutan beranak. Dari `<h1>`, turun terstruktur ke `<h2>`, lalu ke `<h3>` jika bab tersebut punya sub-pembahasan inti... baru balik lagi ke `<h2>` untuk bahasan beda baru.
3. Hindari kebiasaan melompat ghaib dari pelukan `<h2>` langsung menuju ke `<h4>`! (Ini merusak daftar isi otomatis logis mesin pencari).

Selain dicintai mesin Crawler, menjaga kemurnian hal teknis pada HTML ini menandakan kamu telah lulus ujian mental sebagai Front-End Developer yang rapi, elit, dan menjunjung standar global Web Accessibility bagi penyandang hambatan.
