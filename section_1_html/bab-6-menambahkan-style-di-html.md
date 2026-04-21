# Bab 6: Menambahkan Style di HTML

## Tujuan Pembelajaran

- Memahami konsep dasar memberikan warna dan gaya desain langsung ke dalam kode HTML.
- Mampu menggunakan atribut `style` (Inline CSS) untuk mendesain teks per baris.
- Menguasai properti esensial penyusun desain dasar (warna tulisan, warna latar belakang, dan spesifikasi Font).

## Materi Utama

Sejauh ini yang kita buat di HTML hanyalah teks hitam di atas kanvas yang serba putih. Ini membosankan. Padahal di dunia nyata, sebuah web itu penuh gaya pewarnaan, jenis font modern, dan tipografi rapi.

Untuk menyuntikkan keindahan arsitektur desain, kita membutuhkan CSS. Secara umum, CSS adalah pelajaran terpisah (yang akan kamu temui di **Bagian 2** modul ini secara mendalam). Namun sebelum terjun bebas ke sana, HTML menawarkan cara curang instan untuk merias elemen dengan menyisipkan desain secara langsung. Trik ini disebut **Inline Style** menggunakan perantara _Atribut Style_.

### 1. Atribut Style

Fokus pada Bab 2, kita telah sepakat bahwa Atribut bertugas "menitipkan instruksi ekstra di dalam Tag Pembuka".
Atribut `style` bisa ditempel di tag visual manapun (`<h>`, `<p>`, `<body>`, dsb).

Rumus mutlak atribut style:

```html
<tag style="properti_desain: nilai_desain;">Konten kamu</tag>
```

_Perhatikan: di atribut ini menggunakan simbol `titik-dua (:)` untuk menetapkan nilai dan diakhiri `titik-koma (;)` sebagai pemisah jika ada lebih dari 1 desain._

### 2. Properti Desain Paling Dasar

Mari kita merombak tampilan teks kaku menggunakan 5 kelompok kekuatan properti paling sakti:

**A. Warna Teks Dasar (`color`)**
Untuk mengubah warna tinta tulisan, panggil properti `color`. Nilainya bisa berupa rujukan nama warna berbahasa Inggris (red, blue, green).

```html
<p style="color: blue;">Ini paragraf berwarna biru langit.</p>
```

**B. Warna Latar Belakang (`background-color`)**
Ingin memberikan warna kanvas di balik tulisan layaknya mengecat tembok rumah? Gunakan `background-color`.
Mari kita coba mengecat satu halaman full dengan memanggil `<body style="...">`.

```html
<body style="background-color: lightgray;">
  <h1>Halaman ini asyik sekali!</h1>
</body>
```

_Note: Ini akan membuat selimut seluruh halaman web berwarna abu-abu terang._

**C. Nama Font (`font-family`)**
Standar font Web selalu memakai wujud huruf _Times New Roman_ yang kaku seperti teks sekolahan. Untuk menggantinya menjadi gaya luwes seperti Arial, Verdana, atau Courier, propertinya adalah `font-family`.

```html
<h1 style="font-family: Arial;">Judul dengan font Arial</h1>
```

**D. Skala Font (`font-size`)**
Apakah elemen `<h1>` terlampau besar menurutmu? Atau paragraf kurang bisa dibaca? Kendalikan kemudinya dengan `font-size`. Kita bisa memakai ukuran presentase (%) atau pixel (px).

```html
<p style="font-size: 20px;">Teks berukuran kustom, pas mantap 20 pixel.</p>
<!-- Trik: kamu juga bisa memasang ukuran super raksasa -->
<h1 style="font-size: 100px;">RAKSASA</h1>
```

**E. Rata Kanan, Rata Kiri (`text-align`)**
Teks HTML selalu _nempel_ mepet ke sudut kiri. Bayangkan kalau kamu sedang menyusun laporan Puisi dan butuh disebar agar posisinya Rata Tengah (_Center_).

```html
<h1 style="text-align: center;">Judul Puisi Rata Tengah</h1>
<p style="text-align: right;">Penulis: Sang Pujangga Misterius</p>
```

### 3. Merangkai Gaya Kombinasi (Combo Style)

Apakah kita boleh mencampurkan beberapa properti sekaligus ke dalam satu elemen? TENTU SAJA!
Di sinilah letak gunanya titik-koma (`;`). Titik koma berfungsi ibarat sekat pemisah antar bumbu resep.

**Contoh Kolaborasi Ekstrem:**

```html
<p
  style="color: white; background-color: black; font-size: 24px; text-align: center;"
>
  Saya teks sakti! Warnaku putih menyala di balut dinding kegelapan, di tengah
  panggung!
</p>
```

> **Catatan Masa Depan:**
> Praktek menyuntikkan `style` secara langsung ke dalam tag (Inline Style) sebenarnya sangat dihindari oleh profesional _Developer_ kelas kakap jika projek besar, karena hal tersebut menjadikan HTML susah diurus. Ini hanya teknik _survival kit_ darurat dasar saja. Pembuktian ilmu yang sesungguhnya nanti ada di modul eksplorasi khusus CSS!
