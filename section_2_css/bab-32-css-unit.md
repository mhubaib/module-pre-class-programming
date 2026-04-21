# Bab 32: CSS Unit

## Tujuan Pembelajaran

- Mengetahui perbedaan mendasar tipe Unit Absolute (Pasti) vs Unit Relative (Pembanding).
- Memahami kapabilitas batas-kaku angka Pixel (`px`).
- Menguasai kekuatan persentase (`%`) sebagai dewa elastisitas.
- Memahami pengukuran mutakhir berbasis ukuran dasar font: `em` dan `rem`.
- Berkenalan sekilas dengan ukuran yang bersandar murni pada layar monitor (`vh` dan `vw`).

## Materi Utama

Di pelajaran Matematika, jika mau mengukur panjang tali, kita pakai satuan (Unit) Meter atau Centimeter. Jika CSS mau mengukur seberapa panjang Margin atau Gede tebalnya Font, kita tak pakai Meter. Kita punya Gudang Senjata Satuan Jaraknya sendiri!

Garis Besarnya, CSS Unit dibelah menjadi Dua Sekte: **Sekte Absolute (Kaku Pasti)** dan **Sekte Relative (Menyesuaikan Sekitar)**.

### 1. Satuan Absolut (Kaku dan Pantang Mundur)

Satuan absolut mencap suatu angka dan dimensi itu akan **selalu dan abadi persis kaku sebesar itu** sepanjang masa, nggak peduli websitenya di buka di TV 50 Inch ataupun HP layar lipat kecil.

Satu-satunya raja penguasa satuan absolut yang paling ngetren hanyalah **`px` (Pixel)**.
(Ada yang lain seperti `cm` (Centimeter) atau `in` (Inch), tapi itu murni hanya dipakai khusus kalau kamu bikin CSS khusus buat "Print-Out/Mesin Cetak Kertas HVS", dan sama sekali diharamkan untuk dipasang di Layar Web Tampilan).

```css
p {
  /* 1 Pixel adalah 1 titik dot lampu cahaya di monitormu */
  font-size: 16px;
  margin-bottom: 20px;
}
```

**Kekurangan Px:** Terlalu tegar. Bayangin kamu bikin kotak `width: 900px`, dibuka di Laptop cakep... pas di buka di HP layar sempit (lebar layar cuma 400px), ya kotaknya bablas kepotong memaksamu scroll paksa parah.

### 2. Satuan Relative (Si Karet Fleksibel yang Menyesuaikan Diri)

Inilah kunci masa depan Web Design kekinian. Unit relatif **TIDAK punya ukuran baku sendiri**. Ukurannya harus berdiskusi & meminta ijin melihat seberapa besar ukuran Induk/Bapaknya si elemen (atau patokan layar sistem).

**A. Persentase (`%`)**
Mengambil rasio porsi ukuran terhadap lebar/tinggi wadah `induk_pembungkusnya` secara eksak.

```css
.container {
  width: 1000px; /* Bapaknya fix 1000 pixel */
}
.foto-anak {
  width: 50%; /* Si Anak ngemaling 50% dari dompet bapaknya = Jadinya foto lebar 500px! */
}
```

**B. Pengganda Tipografi Induk (`em`)**
Berasal dari istilah cetak mesin kuno "Huruf M". Angka `em` merujuk seberapa "Kali Lipat" terhadap **ukuran font elemen Bapak pembungkus aslinya langsung**.
Jika si Bapak punya `font-size: 16px;`, lalu kamu set Anaknya pakai `width: 2em;`, berarti itu perkalian `2 x 16px` = Jadinya 32px.
_Kelemahan `em`:_ Kadang sangat sulit dilacak berantai dan salah ngitung berlipat lipat kalkulasinya kalau ketumpuk anak cucu buyut bersarang jauh.

**C. Pengganda Induk Sakti Bawaan Raja (`rem` - Root EM)**
"Root" artinya Akar. Konsep `rem` sama kayak `em` namun lebih canggih dan anti pelupa karena... Nilai rasio pengalinya **HANYA BERGANTUNG PADA SATU SAJA: Standar Ukuran Font Tertinggi bawaan Induk HTML Browser utamanya mutlak! (Bawaan aselinya rata-rata selalu 16px)**.

```css
html {
  /* Anggaplah default browser ini gak diubah, standarnya 16px */
}

h1 {
  font-size: 2rem; /* Artinya ngambil kalkulator cuman 1 x rumus murni: 2 x 16px = 32px konstan rapi */
  margin-bottom: 1.5rem; /* 1.5 x 16px = 24px */
}
```

_(`rem` adalah jurus rahasia Programmer Profesional UI zaman Now untuk urusan Padding dan Font-size menggusur `px` karena jauh lebih ramah untuk tuna netra yang settingan komputernya di zoom-in layarnya)._

**D. Merayu Dimensi Monitor Fisik (`vw` dan `vh`)**
Sudah kita singgung super sedikit di Bab 20!

- `vw` (Viewport Width): 1vw artinya mengkapling ukur 1% dari Lebar Kaca Beling Monitor Fisik Pengunjung layarmu.
- `vh` (Viewport Height): 1vh artinya mengkopling ukur 1% dari TINGGI FULL Kaca Beling Monitor Pengunjung layarmu.

_(Cocok buat bikin Spanduk gambar full screen penuh sebadan HP saat ngedrop scroll pertama kali dengan `height: 100vh;`_)

### Kesimpulan Metrik Cepat Panduan:

- Bikin Tebal Border Tipis? Pakai **`px`**.
- Bikin Lebar Kotak Kaca Elastis? Pakai **`%`**.
- Bikin Font, Spasi Teks, Pad Margin? Mulai biasakan pakai **`rem`**!
- Bikin Hero Layar Sentuh Banner Raksasa Penuh? Pakai **`vh`**.
