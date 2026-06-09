# Bab 9: Gradasi & Shadow di CSS

## Tujuan Pembelajaran

- Mampu membuat gradasi warna menggunakan `linear-gradient` dan `radial-gradient`.
- Memahami cara memberikan efek bayangan pada elemen (`box-shadow`).
- Mengetahui cara memberikan efek bayangan pada teks (`text-shadow`).
- Mengenal teknik desain modern: Neumorphism dan Glassmorphism.

---

## Materi Utama

Setelah mempelajari warna solid di Bab 5, kini saatnya menambahkan kesan kedalaman dan dimensi pada elemen. Gradasi warna dan bayangan adalah dua teknik utama yang membuat tampilan web terlihat lebih modern dan tidak datar.

---

### 1. Gradasi Warna (Gradient)

Gradasi adalah transisi halus antara dua warna atau lebih. Dalam CSS, gradasi bukan dikategorikan sebagai properti `color`, melainkan sebagai _gambar_ — sehingga ditulis pada properti `background` atau `background-image`.

#### A. `linear-gradient` — Gradasi Garis Lurus

Warna bertransisi mengikuti garis lurus ke arah tertentu.

```css
/* Dari atas ke bawah (default) */
.banner {
  background: linear-gradient(#2c3e50, #3498db);
}

/* Ke arah kanan */
.header {
  background: linear-gradient(to right, #e74c3c, #f39c12);
}

/* Sudut 135 derajat */
.hero {
  background: linear-gradient(135deg, #667eea, #764ba2);
}

/* Tiga warna */
.pelangi {
  background: linear-gradient(to right, #e74c3c, #f1c40f, #2ecc71);
}
```

**Mengatur titik henti warna (_color stop_):**

```css
/* Merah mengisi 30% pertama, lalu transisi ke biru */
.banner {
  background: linear-gradient(to right, #e74c3c 30%, #3498db);
}
```

#### B. `radial-gradient` — Gradasi Melingkar

Warna memancar dari titik tengah ke luar seperti lingkaran cahaya.

```css
/* Dari tengah ke luar */
.lingkaran {
  background: radial-gradient(#f39c12, #e74c3c);
}

/* Ukuran dan posisi dapat dikontrol */
.sorotan {
  background: radial-gradient(circle at 30% 70%, #3498db, #1a1a2e);
}
```

**Contoh lengkap — Header dengan gradasi:**

```html
<!-- HTML -->
<header class="hero-header">
  <h1>Selamat Datang</h1>
  <p>Temukan pengalaman terbaik bersama kami.</p>
</header>
```

```css
/* CSS */
.hero-header {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  color: white;
  padding: 80px 40px;
  text-align: center;
  min-height: 300px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.hero-header h1 {
  font-size: 3rem;
  margin: 0 0 12px;
}

.hero-header p {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.75);
}
```

---

### 2. Bayangan Kotak (`box-shadow`)

`box-shadow` memberikan efek bayangan pada sebuah elemen sehingga tampak "mengambang" di atas permukaan.

**Sintaks:**

```
box-shadow: [offset-x] [offset-y] [blur] [spread] [warna];
```

| Nilai      | Keterangan                                                          |
| ---------- | ------------------------------------------------------------------- |
| `offset-x` | Geser horizontal (positif = ke kanan, negatif = ke kiri)            |
| `offset-y` | Geser vertikal (positif = ke bawah, negatif = ke atas)              |
| `blur`     | Tingkat kehalusan bayangan (0 = tajam, semakin besar semakin halus) |
| `spread`   | Ukuran bayangan (positif = lebih besar, negatif = lebih kecil)      |
| `warna`    | Warna bayangan (biasanya menggunakan `rgba`)                        |

```css
/* Bayangan standar */
.kartu {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Bayangan lebih tegas */
.tombol {
  box-shadow: 2px 4px 8px rgba(0, 0, 0, 0.3);
}

/* Bayangan ke atas (offset-y negatif) */
.footer {
  box-shadow: 0 -2px 8px rgba(0, 0, 0, 0.1);
}

/* Tanpa geser, hanya blur merata — bayangan bersih */
.kartu-bersih {
  box-shadow: 0 0 16px rgba(0, 0, 0, 0.12);
}
```

**Beberapa bayangan sekaligus:**

```css
.kartu-berlapis {
  box-shadow:
    0 2px 4px rgba(0, 0, 0, 0.08),
    0 8px 24px rgba(0, 0, 0, 0.12);
}
```

**Bayangan ke dalam (`inset`):**

```css
.input-aktif {
  box-shadow: inset 0 2px 6px rgba(0, 0, 0, 0.2);
}
```

---

### 3. Bayangan Teks (`text-shadow`)

`text-shadow` memberikan efek bayangan pada teks, berguna untuk meningkatkan keterbacaan teks di atas gambar atau latar belakang yang kompleks.

**Sintaks:**

```
text-shadow: [offset-x] [offset-y] [blur] [warna];
```

```css
/* Bayangan tipis untuk keterbacaan di atas foto */
.teks-di-atas-foto {
  color: white;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
}

/* Efek cahaya (glow) */
.teks-neon {
  color: #00ffcc;
  text-shadow:
    0 0 8px #00ffcc,
    0 0 20px #00ffcc;
}

/* Beberapa lapisan bayangan untuk efek 3D */
.teks-timbul {
  color: white;
  text-shadow:
    1px 1px 0 #aaa,
    2px 2px 0 #999,
    3px 3px 0 #888;
}
```

---

### 4. Teknik Desain Modern

#### A. Neumorphism

Neumorphism menciptakan ilusi elemen yang **timbul dari permukaan** menggunakan dua `box-shadow` berlawanan arah — satu bayangan gelap di kanan-bawah dan satu bayangan terang di kiri-atas.

> **Kunci:** Warna `background` elemen harus sama dengan warna latar belakang halaman agar efeknya bekerja.

```html
<!-- HTML -->
<div class="neuo-bg">
  <button class="btn-neuo">Klik Aku</button>
  <button class="btn-neuo">Simpan</button>
</div>
```

```css
/* CSS */
.neuo-bg {
  background: #e0e5ec;
  padding: 40px;
  display: flex;
  gap: 20px;
}

.btn-neuo {
  padding: 14px 36px;
  border-radius: 12px;
  border: none;
  cursor: pointer;
  font-size: 15px;
  font-weight: 500;
  color: #6b7a99;
  background: #e0e5ec; /* Sama dengan .neuo-bg */
  box-shadow:
    6px 6px 14px #b8bec8,
    /* Bayangan gelap */ -6px -6px 14px #ffffff; /* Bayangan terang */
  transition:
    box-shadow 0.15s,
    transform 0.15s;
}

/* Efek tenggelam saat ditekan */
.btn-neuo:active {
  box-shadow:
    inset 4px 4px 10px #b8bec8,
    inset -4px -4px 10px #ffffff;
  transform: scale(0.98);
}
```

#### B. Glassmorphism

Glassmorphism membuat elemen tampak seperti **kaca buram** yang melapiskan warna di belakangnya. Efek ini memerlukan background berwarna-warni di belakang elemen.

> **Kunci:** `backdrop-filter: blur()` hanya bekerja jika ada konten berwarna di belakang elemen. Selalu tambahkan `-webkit-backdrop-filter` untuk kompatibilitas dengan Safari.

```html
<!-- HTML -->
<div class="glass-bg">
  <button class="btn-glass">Klik Aku</button>
  <button class="btn-glass">Masuk</button>
</div>
```

```css
/* CSS */
.glass-bg {
  background: linear-gradient(135deg, #6a11cb 0%, #2575fc 50%, #f093fb 100%);
  padding: 40px;
  display: flex;
  gap: 20px;
}

.btn-glass {
  padding: 14px 36px;
  border-radius: 12px;
  cursor: pointer;
  font-size: 15px;
  font-weight: 500;
  color: #ffffff;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.35);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.15);
  transition:
    background 0.15s,
    transform 0.15s;
}

.btn-glass:hover {
  background: rgba(255, 255, 255, 0.25);
}

.btn-glass:active {
  background: rgba(255, 255, 255, 0.08);
  transform: scale(0.98);
}
```

---

### Kesimpulan

Gradasi dan bayangan adalah teknik yang mengubah tampilan dua dimensi menjadi terasa memiliki kedalaman. Digunakan dengan tepat, keduanya meningkatkan hierarki visual dan memandu perhatian pengguna ke elemen yang penting.

**Panduan penggunaan:**

- Gunakan bayangan dengan nilai `rgba` beropaticy rendah agar terlihat elegan.
- Gradasi dengan tiga warna atau lebih sebaiknya menggunakan _color stop_ agar transisi lebih terkontrol.
- Neumorphism cocok untuk antarmuka yang minimalis dan monokromatik.
- Glassmorphism cocok untuk antarmuka dengan latar belakang berwarna-warni atau bergambar.

**Ringkasan Properti:**

| Properti                  | Fungsi                                                    |
| ------------------------- | --------------------------------------------------------- |
| `linear-gradient()`       | Gradasi warna mengikuti garis lurus                       |
| `radial-gradient()`       | Gradasi warna melingkar dari titik tengah ke luar         |
| `box-shadow`              | Bayangan pada elemen (kotak)                              |
| `box-shadow: inset`       | Bayangan ke dalam elemen                                  |
| `text-shadow`             | Bayangan pada teks                                        |
| `backdrop-filter: blur()` | Efek buram pada konten di belakang elemen (Glassmorphism) |
