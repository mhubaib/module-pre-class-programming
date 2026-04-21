# Bab 23: Gradasi & Shadow di CSS

## Tujuan Pembelajaran

- Mampu membuat warna gradasi (perpindahan warna) menggunakan `linear-gradient` dan `radial-gradient`.
- Memahami cara memberikan efek bayangan pada kotak (`box-shadow`).
- Mengetahui cara memberikan efek bayangan pada tulisan (`text-shadow`).
- Menambahkan kesan kedalaman (depth) dan modernitas pada desain web.

## Materi Utama

Setelah kita belajar warna pekat (solid), sekarang kita akan belajar memberikan efek "kedalaman" agar elemen website terlihat menonjol dan tidak datar (_flat_). Kita akan menggunakan teknik gradasi warna dan bayangan.

### 1. Warna Gradasi (Gradients)

Gradasi adalah perpaduan halus antara dua warna atau lebih. Gradasi bukanlah "Warna" (`color`), melainkan dianggap sebagai "Gambar" oleh CSS, sehingga ia dipasang pada properti `background` atau `background-image`.

**A. Linear Gradient (Garis Lurus)**
Perpindahan warna yang mengalir searah (bisa dari atas ke bawah, atau menyamping).

```css
.banner {
  /* Gradasi dari Biru ke Hijau */
  background: linear-gradient(blue, green);

  /* Bisa juga diarahkan (ke kanan) */
  background: linear-gradient(to right, red, yellow);
}
```

**B. Radial Gradient (Melingkar)**
Perpindahan warna yang memancar dari titik tengah keluar (seperti bentuk matahari atau lampu senter).

```css
.bulatan {
  background: radial-gradient(white, blue);
}
```

### 2. Bayangan Kotak (Box Shadow)

Bayangan memberikan efek seolah-olah elemen tersebut "mengambang" di atas kertas. Properti ini membutuhkan 4 nilai utama:
`box-shadow: [geser-kanan] [geser-bawah] [tingkat-blur] [warna];`

```css
.kartu {
  /* Bayangan geser 5px ke kanan, 5px ke bawah, blur 10px, warna hitam samar */
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}
```

_Tips: Nilai blur yang lebih tinggi akan membuat bayangan terlihat lebih halus dan realistis._

### 3. Bayangan Teks (Text Shadow)

Sama seperti bayangan kotak, tapi ini khusus diterapkan pada tulisan agar teks lebih mudah dibaca jika diletakkan di atas gambar yang ramai.

```css
h1 {
  /* Bayangan tipis agar teks menyala */
  text-shadow: 2px 2px 4px black;
  color: white;
}
```

### 4. Desain Neumorphism dan Glassmorphism (Tren Modern)

Dengan gabungan gradasi dan bayangan, kamu bisa membuat gaya web kekinian:

- **Neumorphism**: Membuat tombol terlihat seperti "timbul" atau "tenggelam" dari permukaan latar.
- **Glassmorphism**: Membuat kotak terlihat seperti kaca transparan yang buram di atas background yang berwarna-warni.

**Analogi Pencahayaan:**
Menggunakan gradasi dan bayangan ibarat sedang **memberikan lampu sorot** pada sebuah gambar. Tanpa bayangan, mata kita akan menganggap elemen tersebut rata menempel di layar. Dengan bayangan, kita memberi isyarat ke mata pengunjung bahwa elemen tersebut lebih penting dan bisa diklik.

**Tips Profesional:**
Jangan terlalu berlebihan menggunakan bayangan yang hitam pekat dan tajam. Gunakanlah warna bayangan yang sangat lembut (rgba dengan opacity rendah) agar websitemu terlihat elegan dan tidak norak.
