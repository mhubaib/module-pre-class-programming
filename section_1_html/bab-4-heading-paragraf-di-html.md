# Bab 4: Heading & Paragraf di HTML

## Tujuan Pembelajaran

- Memahami konsep hierarki Judul (Heading) dari tingkat 1 hingga 6.
- Mengetahui cara yang tepat menggunakan elemen Paragraf.
- Membaca dan menata paragraf menggunakan elemen pemisah baris dan garis horizontal.

## Materi Utama

Setelah kita berhasil merangkai kerangka dasar HTML di materi sebelumnya, kini saatnya kita mulai mengisi "Panggung Utama" alias bagian `<body>`. Komponen teks yang paling mendasar untuk mengisi sebuah website adalah Judul (Heading) dan Paragraf.

### 1. Heading (Judul Bersusun)

Pernah membaca koran pagi atau buku pelajaran tebal? Dalam sebuah artikel koran, pasti ada Judul Utama paling atas yang hurufnya sangat besar. Di bawahnya, mungkin ada Sub-Judul pendukung. Begitu pula saat kamu membuat struktur dokumen HTML.

Tag untuk membuat judul disebut **Heading**, dilambangkan dengan huruf `h` diikuti dengan angka tingkatannya. HTML menyediakan 6 tingkatan heading, mulai dari `<h1>` sampai `<h6>`.

- `<h1>`: Ini adalah Judul Utama (Level 1). Tingkat paling tinggi, ukurannya paling besar tebal, dan sangat krusial.
- `<h2>`: Sub Judul Utama (Level 2).
- `<h3>`: Sub sub-judul, dan seterusnya.
- `<h6>`: Tingkat heading paling rendah (Level 6), ukurannya paling kekecilan.

**Aturan Emas Penggunaan Heading (Analogi Judul Buku):**
Bayangkan websitemu adalah sebuah buku biografi:

- `<h1>` adalah Judul Buku Besar yang tercetak di cover depan. Secara logika, setiap buku hanya boleh punya 1 Judul Utama. Begitu pula di HTML, sangat disarankan tiap halaman website hanya memiliki **SATU tag `<h1>`** demi aturan SEO (agar Google paham topik utama halamanmu).
- `<h2>` adalah Judul Bab.
- `<h3>` adalah Sub-Bab di bawahnya.

Coba tuliskan kode ini di dalam `<body>` kamu:

```html
<h1>Biografi Penemu Komputer</h1>
<h2>Masa Kecil</h2>
<h3>Lahir di London</h3>
<h2>Masa Dewasa</h2>
<h6>Teks kecil ini digunakan untuk judul yang sangat minor.</h6>
```

### 2. Paragraf (`<p>`)

Jika Heading adalah judulnya, maka Paragraf adalah "daging" alias isi dari artikel tersebut. Tag yang digunakan sangat sederhana, yakni `<p>` (singkatan dari Paragraph).

Setiap kali kamu menggunakan tag `<p>`, browser secara otomatis akan menambahkan semacam bantalan kosong (margin) di atas dan di bawah teks tersebut sebagai jeda dengan elemen lain.

```html
<p>
  Halo, nama saya Budi. Saya baru saja lulus SMA dan bertekad ingin menjadi
  seorang Web Developer profesional dalam 6 bulan ke depan.
</p>
<p>
  Ini adalah paragraf kedua. Perhatikan bahwa di antara paragraf pertama dan
  kedua akan ada jarak kosong secara otomatis.
</p>
```

### 3. Mengontrol Baris Teks: Line Break (`<br>`) dan Garis Pemisah (`<hr>`)

Ada kalanya perilaku _default_ browser cukup mengganggu. Di dalam dunia HTML, jika kamu menekan tombol `Enter` sejuta kali pun di Code Editor, browser hanya akan menganggapnya sebagai 1 spasi biasa.
Lalu, bagaimana caranya jika kita ingin memotong kalimat pindah ke baris baru, tanpa perlu membuat paragraf baru?

Gunakan **Self-Closing Tag/Tag Tunggal**: `<br>` (Line Break).

```html
<p>
  Alamat Rumahku:<br />
  Jalan Mawar Merah No. 10<br />
  Jakarta Selatan
</p>
```

Selain `<br>`, jika kamu ingin memisahkan antara bagian teks atas dan bawah menggunakan garis mendatar ibarat memotong halaman dengan penggaris, kamu bisa menggunakan `<hr>` (Horizontal Rule). `<hr>` juga merupakan tag tunggal yang tidak butuh penutup.

```html
<h2>Sejarah Singkat</h2>
<p>Teks tentang sejarah diletakkan di sini.</p>

<!-- Garis Pemisah -->
<hr />

<h2>Kondisi Saat Ini</h2>
<p>Teks kondisi saat ini ada di bagian bawah garis.</p>
```
