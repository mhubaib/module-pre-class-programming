# Bab 23: Gradasi & Shadow di CSS

## Tujuan Pembelajaran

- Mampu membuat warna gradasi (perpindahan warna) menggunakan `linear-gradient` dan `radial-gradient`.
- Memahami cara memberikan efek bayangan pada kotak (`box-shadow`).
- Mengetahui cara memberikan efek bayangan pada tulisan (`text-shadow`).
- Menambahkan kesan kedalaman (depth) dan modernitas pada desain web.

---

## Materi Utama

Setelah kita belajar warna pekat (solid), sekarang kita akan belajar memberikan efek "kedalaman" agar elemen website terlihat menonjol dan tidak datar (_flat_). Kita akan menggunakan teknik gradasi warna dan bayangan.

---

### 1. Warna Gradasi (Gradients)

Gradasi adalah perpaduan halus antara dua warna atau lebih. Gradasi bukanlah "Warna" (`color`), melainkan dianggap sebagai "Gambar" oleh CSS, sehingga ia dipasang pada properti `background` atau `background-image`.

#### A. Linear Gradient (Garis Lurus)

Perpindahan warna yang mengalir searah (bisa dari atas ke bawah, atau menyamping).

```css
.banner {
  /* Gradasi dari Biru ke Hijau */
  background: linear-gradient(blue, green);

  /* Bisa juga diarahkan (ke kanan) */
  background: linear-gradient(to right, red, yellow);
}
```

#### B. Radial Gradient (Melingkar)

Perpindahan warna yang memancar dari titik tengah keluar (seperti bentuk matahari atau lampu senter).

```css
.bulatan {
  background: radial-gradient(white, blue);
}
```

---

### 2. Bayangan Kotak (Box Shadow)

Bayangan memberikan efek seolah-olah elemen tersebut "mengambang" di atas kertas. Properti ini membutuhkan 4 nilai utama:

```
box-shadow: [geser-kanan] [geser-bawah] [tingkat-blur] [warna];
```

```css
.kartu {
  /* Bayangan geser 5px ke kanan, 5px ke bawah, blur 10px, warna hitam samar */
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}
```

>  **Tips:** Nilai blur yang lebih tinggi akan membuat bayangan terlihat lebih halus dan realistis.

---

### 3. Bayangan Teks (Text Shadow)

Sama seperti bayangan kotak, tapi ini khusus diterapkan pada tulisan agar teks lebih mudah dibaca jika diletakkan di atas gambar yang ramai.

```css
h1 {
  /* Bayangan tipis agar teks menyala */
  text-shadow: 2px 2px 4px black;
  color: white;
}
```

---

### 4. Desain Neumorphism dan Glassmorphism (Tren Modern)

Dengan gabungan gradasi dan bayangan, kamu bisa membuat gaya web kekinian:

| Gaya | Efek | Teknik Utama |
|---|---|---|
| **Neumorphism** | Tombol terlihat "timbul" atau "tenggelam" dari permukaan | Dua `box-shadow` berlawanan arah |
| **Glassmorphism** | Kotak terlihat seperti kaca transparan buram | `backdrop-filter: blur()` + background semi-transparan |

---

#### A. Neumorphism

Neumorphism menciptakan ilusi bahwa elemen seolah **timbul dari permukaan**. Triknya adalah menggunakan dua `box-shadow` sekaligus: satu bayangan gelap di sisi kanan-bawah, dan satu bayangan terang di sisi kiri-atas.

>  **Kunci:** Warna `background` tombol **harus sama** dengan warna background halaman agar efeknya bekerja.

**HTML:**

```html
<!-- Background halaman membungkus tombol -->
<div class="neuo-bg">
  <button class="btn-neuo">Klik Aku</button>
  <button class="btn-neuo">Simpan</button>
</div>
```

**CSS:**

```css
/* Background halaman — warna ini HARUS sama dengan tombol */
.neuo-bg {
  background: #e0e5ec;
  padding: 40px;
  display: flex;
  gap: 20px;
}

/* Tombol Neumorphism — efek timbul */
.btn-neuo {
  padding: 14px 36px;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  font-size: 15px;
  font-weight: 500;
  color: #6b7a99;
  background: #e0e5ec; /* SAMA dengan .neuo-bg */

  /* Dua bayangan: gelap kanan-bawah, terang kiri-atas */
  box-shadow:
     6px  6px 14px #b8bec8,  /* bayangan gelap */
    -6px -6px 14px #ffffff;  /* bayangan terang */

  transition: box-shadow 0.15s, transform 0.15s;
}

/* Saat tombol ditekan: bayangan dibalik ke dalam (efek tenggelam) */
.btn-neuo:active {
  box-shadow:
    inset  4px  4px 10px #b8bec8,
    inset -4px -4px 10px #ffffff;
  transform: scale(0.98);
}
```

---

#### B. Glassmorphism

Glassmorphism membuat elemen tampak seperti **kaca buram** yang melapiskan warna di belakangnya. Efek ini membutuhkan background berwarna-warni di belakang elemen agar terlihat maksimal.

>  **Kunci:** `backdrop-filter: blur()` hanya bekerja jika ada konten (warna/gambar) di belakang elemen. Tanpa background berwarna, efek kaca tidak akan terlihat.

**HTML:**

```html
<!-- Background gradasi diperlukan agar efek kaca terlihat -->
<div class="glass-bg">
  <button class="btn-glass">Klik Aku</button>
  <button class="btn-glass">Masuk</button>
</div>
```

**CSS:**

```css
/* Background gradasi warna-warni sebagai "pemandangan" di balik kaca */
.glass-bg {
  background: linear-gradient(
    135deg,
    #6a11cb 0%,
    #2575fc 50%,
    #f093fb 100%
  );
  padding: 40px;
  display: flex;
  gap: 20px;
}

/* Tombol Glassmorphism — efek kaca buram */
.btn-glass {
  padding: 14px 36px;
  border-radius: 12px;
  cursor: pointer;
  font-size: 15px;
  font-weight: 500;
  color: #ffffff;

  /* Latar belakang semi-transparan */
  background: rgba(255, 255, 255, 0.15);

  /* INI kuncinya: memburamkan konten di belakang elemen */
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px); /* untuk browser Safari */

  /* Border tipis seperti tepian kaca */
  border: 1px solid rgba(255, 255, 255, 0.35);

  /* Bayangan halus untuk kedalaman */
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.15);

  transition: background 0.15s, transform 0.15s;
}

/* Saat hover: kaca sedikit lebih terang */
.btn-glass:hover {
  background: rgba(255, 255, 255, 0.25);
}

/* Saat ditekan */
.btn-glass:active {
  background: rgba(255, 255, 255, 0.08);
  transform: scale(0.98);
}
```

---

### Analogi Pencahayaan

Menggunakan gradasi dan bayangan ibarat sedang **memberikan lampu sorot** pada sebuah gambar. Tanpa bayangan, mata kita akan menganggap elemen tersebut rata menempel di layar. Dengan bayangan, kita memberi isyarat ke mata pengunjung bahwa elemen tersebut lebih penting dan bisa diklik.

### Tips Profesional

- Jangan terlalu berlebihan menggunakan bayangan hitam pekat dan tajam.
- Gunakan warna bayangan yang sangat lembut (`rgba` dengan opacity rendah) agar websitemu terlihat elegan dan tidak norak.
- Untuk Neumorphism, pastikan kontras warna teks dan background cukup agar tetap mudah dibaca.
- Untuk Glassmorphism, selalu tambahkan `-webkit-backdrop-filter` untuk kompatibilitas dengan browser Safari.
