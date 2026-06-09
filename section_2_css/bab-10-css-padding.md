# Bab 10: CSS Padding

## Tujuan Pembelajaran

- Memahami fungsi Padding sebagai ruang dalam elemen.
- Menguasai penulisan Padding secara spesifik per sisi.
- Menggunakan teknik penulisan singkat (shorthand) untuk efisiensi kode.

---

## Materi Utama

Mengingat kembali konsep **Box Model** di Bab 8, setiap elemen HTML adalah sebuah kotak. Teks di dalam kotak yang terlalu mepet ke tepinya terlihat sesak dan sulit dibaca. **Padding** adalah properti yang memberikan ruang antara konten dan tepi elemen.

---

### 1. Apa itu Padding?

**Padding** adalah jarak kosong yang berada **di antara konten elemen dan batas (border) kotaknya**. Karena padding berada di dalam kotak, area ini mengikuti warna `background-color` elemen.

**Analogi:**

Bayangkan sebuah kartu undangan. Teks di dalamnya tidak dicetak persis di tepi kertas — ada margin putih kosong di sekeliling teks agar mudah dibaca dan terlihat rapi. Itulah fungsi padding pada elemen HTML.

**Perbandingan tanpa dan dengan padding:**

```html
<!-- HTML -->
<div class="tanpa-padding">Teks ini mepet ke tepi.</div>
<div class="dengan-padding">Teks ini memiliki ruang yang cukup.</div>
```

```css
/* CSS */
.tanpa-padding {
  background-color: #cfe2ff;
  border: 1px solid #9ec5fe;
}

.dengan-padding {
  background-color: #cfe2ff;
  border: 1px solid #9ec5fe;
  padding: 16px;
}
```

---

### 2. Mengatur Padding per Sisi

Padding dapat diatur secara berbeda untuk masing-masing dari keempat sisi elemen:

```css
.kotak-pengumuman {
  background-color: #d1fae5;
  border: 1px solid #6ee7b7;

  padding-top: 20px; /* Atas */
  padding-right: 15px; /* Kanan */
  padding-bottom: 20px; /* Bawah */
  padding-left: 15px; /* Kiri */
}
```

**Contoh penggunaan per sisi:**

```css
/* Hanya atas dan bawah yang diberi padding */
.judul-seksi {
  padding-top: 40px;
  padding-bottom: 16px;
}

/* Hanya kiri yang diberi padding — untuk indentasi */
.kutipan {
  padding-left: 24px;
  border-left: 4px solid steelblue;
  background-color: #f0f4ff;
}
```

---

### 3. Penulisan Singkat (Shorthand)

Daripada menulis empat baris terpisah, gunakan properti `padding` dengan satu hingga empat nilai. Urutan nilainya mengikuti arah jarum jam: **Atas → Kanan → Bawah → Kiri**.

#### A. Satu Nilai — Semua Sisi Sama

```css
.kartu {
  padding: 20px;
  /* Atas, kanan, bawah, kiri = 20px */
}
```

#### B. Dua Nilai — Atas/Bawah dan Kiri/Kanan

```css
.tombol {
  padding: 10px 24px;
  /* Atas-bawah = 10px, kiri-kanan = 24px */
}
```

Ini adalah pola yang paling umum digunakan untuk tombol — nilai vertikal lebih kecil dari horizontal menghasilkan proporsi yang enak secara visual.

#### C. Tiga Nilai — Atas, Kiri/Kanan, Bawah

```css
.banner {
  padding: 40px 24px 20px;
  /* Atas = 40px, kiri-kanan = 24px, bawah = 20px */
}
```

#### D. Empat Nilai — Semua Sisi Berbeda

```css
.kotak {
  padding: 25px 50px 75px 100px;
  /* Atas = 25px, kanan = 50px, bawah = 75px, kiri = 100px */
}
```

**Ringkasan pola shorthand:**

| Penulisan                       | Nilai Atas | Nilai Kanan | Nilai Bawah | Nilai Kiri |
| ------------------------------- | ---------- | ----------- | ----------- | ---------- |
| `padding: 20px`                 | 20px       | 20px        | 20px        | 20px       |
| `padding: 10px 24px`            | 10px       | 24px        | 10px        | 24px       |
| `padding: 40px 24px 20px`       | 40px       | 24px        | 20px        | 24px       |
| `padding: 25px 50px 75px 100px` | 25px       | 50px        | 75px        | 100px      |

---

### 4. Padding dan `box-sizing`

Seperti yang dibahas di Bab 8, menambahkan padding secara default akan memperbesar ukuran total elemen melebihi nilai `width` yang ditetapkan. Pastikan `box-sizing: border-box` sudah diterapkan agar padding tidak menyebabkan elemen membesar.

```css
/* Terapkan di awal proyek */
* {
  box-sizing: border-box;
}

/* Dengan border-box, total lebar tetap 300px meskipun ada padding */
.kotak {
  width: 300px;
  padding: 24px;
  /* Tanpa border-box: total = 300 + 24 + 24 = 348px */
  /* Dengan border-box: total tetap = 300px */
}
```

---

### 5. Contoh Lengkap — Komponen Kartu dan Tombol

```html
<!-- HTML -->
<div class="kartu-artikel">
  <div class="label">Tips Desain</div>
  <h2>Menggunakan Padding dengan Benar</h2>
  <p>
    Padding yang tepat membuat konten lebih mudah dibaca dan tampilan lebih
    bersih.
  </p>
  <blockquote class="kutipan">
    "Ruang kosong (whitespace) adalah elemen desain yang sering diremehkan."
  </blockquote>
  <button class="tombol-baca">Baca Selengkapnya</button>
</div>
```

```css
/* CSS */
* {
  box-sizing: border-box;
}

.kartu-artikel {
  width: 420px;
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 28px; /* Ruang merata di semua sisi */
}

.label {
  display: inline-block;
  background-color: #dbeafe;
  color: #1d4ed8;
  font-size: 0.75rem;
  font-weight: bold;
  padding: 4px 10px; /* Atas-bawah kecil, kiri-kanan lebih besar */
  border-radius: 99px;
  margin-bottom: 12px;
}

.kartu-artikel h2 {
  color: #1e293b;
  font-size: 1.25rem;
  margin: 0 0 8px;
}

.kartu-artikel p {
  color: #64748b;
  line-height: 1.6;
  margin: 0 0 16px;
}

.kutipan {
  padding: 12px 16px; /* Ruang atas-bawah dan kiri-kanan berbeda */
  background-color: #f0f4ff;
  border-left: 4px solid steelblue;
  border-radius: 0 6px 6px 0;
  color: #334155;
  font-style: italic;
  margin: 0 0 20px;
}

.tombol-baca {
  padding: 10px 24px; /* Shorthand 2 nilai — standar tombol */
  background-color: steelblue;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.95rem;
}

.tombol-baca:hover {
  background-color: #2a6496;
}
```

---

### Kesimpulan

Padding adalah salah satu properti CSS yang paling sering digunakan. Memberikan padding yang cukup pada elemen membuat konten lebih mudah dibaca, tampilan lebih rapi, dan antarmuka terasa lebih nyaman digunakan.

**Ringkasan:**

| Properti         | Fungsi                     |
| ---------------- | -------------------------- |
| `padding`        | Shorthand untuk semua sisi |
| `padding-top`    | Padding sisi atas          |
| `padding-right`  | Padding sisi kanan         |
| `padding-bottom` | Padding sisi bawah         |
| `padding-left`   | Padding sisi kiri          |

**Panduan Nilai Shorthand:**

| Jumlah Nilai | Pola                        | Contoh                        |
| ------------ | --------------------------- | ----------------------------- |
| 1            | Semua sisi sama             | `padding: 16px`               |
| 2            | Atas/Bawah — Kiri/Kanan     | `padding: 10px 24px`          |
| 3            | Atas — Kiri/Kanan — Bawah   | `padding: 20px 16px 12px`     |
| 4            | Atas — Kanan — Bawah — Kiri | `padding: 10px 20px 15px 5px` |
