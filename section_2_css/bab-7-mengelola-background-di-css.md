# Bab 21: Mengelola Background di CSS

## Tujuan Pembelajaran

- Mampu menambahkan gambar latar belakang menggunakan `background-image`.
- Mengatur perulangan gambar dengan `background-repeat`.
- Mengontrol posisi dan ukuran gambar latar belakang (`background-position` & `background-size`).
- Memahami konsep _Fixed Background_ (efek Parallax sederhana).

## Materi Utama

Setelah kita belajar memberikan warna pada latar belakang di Bab 19, kini saatnya kita melangkah lebih jauh. Memasang gambar pemandangan atau pola tekstur sebagai latar belakang bisa memberikan kesan mewah dan bercerita pada websitemu.

### 1. Memasang Gambar Latar (`background-image`)

Instruksi ini digunakan untuk menempelkan file gambar tepat di balik konten teks atau elemen lainnya.

```css
body {
  background-image: url("pemandangan.jpg");
}
```

**Analogi Memasang Wallpaper:**
Menggunakan `background-color` ibarat mengecat tembok polosan. Sedangkan menggunakan `background-image` ibarat memasang wallpaper bermotif di seluruh dinding ruangan.

### 2. Mengatur Perulangan (`background-repeat`)

Secara _default_, jika gambar latar belakangmu ukurannya lebih kecil dari layar browser, browser akan otomatis menjiplak gambar tersebut berulang-ulang sampai memenuhi layar (seperti ubin lantai). Kamu bisa mengaturnya:

- `repeat` (Bawaan): Mengulang ke samping dan ke bawah.
- `repeat-x`: Hanya mengulang mendatar (horisontal).
- `repeat-y`: Hanya mengulang tegak (vertikal).
- `no-repeat`: Gambar hanya muncul SATU KALI saja di pojok kiri atas.

```css
div {
  background-image: url("logo.png");
  background-repeat: no-repeat;
}
```

### 3. Menentukan Ukuran Gambar (`background-size`)

Seringkali gambar yang kita punya ukurannya tidak pas dengan layar. Ada dua nilai saktinya:

- **`cover`**: Memaksa gambar menutupi seluruh area kotak latar belakang. Jika gambarnya terlalu kecil, dia akan diperbesar. (Hasilnya rapi, tapi sisi gambar bisa terpotong).
- **`contain`**: Memaksa seluruh gambar masuk ke dalam kotak tanpa terpotong sama sekali. (Hasilnya mungkin akan ada area kosong jika rasio kotak dan gambar tidak sama).

```css
header {
  background-image: url("foto-hero.jpg");
  background-size: cover;
}
```

### 4. Mengatur Posisi (`background-position`)

Kamu bisa menentukan di titik mana gambar tersebut harus "nempel". Gunakan koordinat bahasa Inggris seperti `center`, `top`, `bottom`, `left`, atau `right`.

```css
body {
  background-position: center bottom; /* Tengah bawah */
}
```

### 5. Efek Menempel (`background-attachment`)

Pernah melihat website yang saat kita _scroll_ ke bawah, gambarnya tetap diam membeku di tempat sementara tulisannya bergerak naik? Itu dinamakan efek **Fixed Background**.

- `scroll` (Bawaan): Gambar ikut bergerak saat di-scroll.
- `fixed`: Gambar menempel mati di layar, menciptakan kesan kedalaman (parallax sederhana).

```css
.bagian-parallax {
  background-image: url("gunung.jpg");
  background-attachment: fixed;
  background-size: cover;
}
```

**Tips Kombinasi (Shorthand):**
Daripada menulis 5 baris kode latar belakang yang panjang, kamu bisa menuliskannya dalam satu baris irit:
`background: [warna] [image] [repeat] [attachment] [position];`

```css
body {
  background: lightblue url("awan.png") no-repeat fixed center;
}
```
