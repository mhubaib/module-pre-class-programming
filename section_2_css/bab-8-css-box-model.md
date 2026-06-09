# Bab 8: CSS Box Model

## Tujuan Pembelajaran

- Memahami konsep Box Model sebagai dasar tata letak CSS.
- Membedakan antara Content, Padding, Border, dan Margin.
- Memahami cara menghitung lebar total sebuah elemen.
- Menggunakan `box-sizing: border-box` untuk mempermudah perhitungan tata letak.

---

## Materi Utama

Setiap elemen HTML diperlakukan oleh browser sebagai sebuah kotak berlapis-lapis. Pemahaman tentang lapisan-lapisan ini — yang disebut **Box Model** — adalah fondasi dari semua pekerjaan tata letak CSS. Tanpa memahaminya, ukuran elemen yang tiba-tiba tidak sesuai ekspektasi akan sulit untuk didiagnosis.

---

### 1. Lapisan-lapisan Box Model

Dari lapisan paling dalam ke lapisan paling luar:

```
┌─────────────────────────────────┐  ← Margin (luar)
│  ┌───────────────────────────┐  │
│  │  ┌─────────────────────┐  │  │  ← Border
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │               │  │  │  │  ← Padding
│  │  │  │    Content    │  │  │  │
│  │  │  │               │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

1. **Content** — Area tempat teks, gambar, atau elemen anak berada. Ukurannya dikontrol oleh `width` dan `height`.
2. **Padding** — Ruang kosong antara konten dan border. Padding berada di **dalam** kotak, sehingga warnanya mengikuti `background-color` elemen.
3. **Border** — Garis yang membungkus padding dan konten. Dapat diatur ketebalan, gaya, dan warnanya.
4. **Margin** — Ruang kosong di **luar** kotak, antara elemen ini dan elemen-elemen di sekitarnya. Margin selalu transparan.

**Analogi Paket Pengiriman:**

- **Content** — Barang yang dikirim (misalnya gelas kaca).
- **Padding** — Bahan pelindung seperti bubble wrap yang membungkus barang dari dalam.
- **Border** — Kotak kardus pembungkus.
- **Margin** — Jarak antara kardus ini dengan kardus lain di dalam truk pengiriman.

---

### 2. Penulisan Padding, Border, dan Margin

Setiap properti dapat diterapkan ke keempat sisi secara bersamaan atau ke sisi tertentu saja.

```css
/* Padding — ruang dalam */
.kotak {
  padding: 20px; /* Semua sisi 20px */
  padding: 20px 40px; /* Atas-bawah 20px, kiri-kanan 40px */
  padding: 10px 20px 30px 40px; /* Atas, kanan, bawah, kiri (searah jarum jam) */

  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 10px;
  padding-left: 20px;
}

/* Border — garis tepi */
.kotak {
  border: 2px solid #333; /* Ketebalan, gaya, warna */
  border-top: 4px solid steelblue; /* Hanya sisi atas */
  border-radius: 8px; /* Sudut membulat */
}

/* Margin — jarak luar */
.kotak {
  margin: 24px; /* Semua sisi 24px */
  margin: 16px auto; /* Atas-bawah 16px, kiri-kanan otomatis (terpusat) */
  margin-bottom: 12px; /* Hanya sisi bawah */
}
```

**Gaya border yang tersedia:**

```css
border: 2px solid #333; /* Garis lurus */
border: 2px dashed #333; /* Garis putus-putus */
border: 2px dotted #333; /* Titik-titik */
border: 2px double #333; /* Garis ganda */
```

---

### 3. Masalah Perhitungan Lebar Default

Secara default, `width` hanya mengukur area **Content** — tidak termasuk padding dan border. Ini berarti ukuran total elemen di layar bisa berbeda dari nilai `width` yang ditulis.

```css
.kotak {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
}
```

```
Perhitungan total lebar:
  Content : 300px
  Padding : 20px (kiri) + 20px (kanan) = 40px
  Border  : 5px (kiri)  + 5px (kanan)  = 10px
  ─────────────────────────────────────────────
  Total   : 350px  ← lebih lebar dari yang diharapkan
```

Masalah ini sering menjadi penyebab elemen meluap keluar dari wadahnya atau mendorong elemen lain ke bawah secara tidak terduga.

---

### 4. Solusi: `box-sizing: border-box`

Dengan nilai `border-box`, `width` dan `height` akan mencakup konten, padding, **dan** border sekaligus. Browser akan otomatis menyesuaikan area konten agar ukuran total tetap sesuai dengan nilai `width` yang ditetapkan.

```css
.kotak {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Lebar total tetap 300px — bukan 350px */
}
```

```
Dengan border-box:
  Total lebar  : 300px (sesuai width)
  Border       : 5px + 5px = 10px
  Padding      : 20px + 20px = 40px
  Content      : 300 - 10 - 40 = 250px (dikecilkan otomatis)
```

Karena keunggulan ini, hampir semua pengembang web menerapkan `border-box` ke seluruh elemen sejak awal proyek:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

---

### 5. Margin Collapse

Terdapat perilaku CSS yang perlu dipahami: ketika dua elemen block bertetangga secara vertikal, margin mereka tidak dijumlahkan — melainkan yang lebih besar yang digunakan. Fenomena ini disebut **Margin Collapse**.

```css
.paragraf-atas {
  margin-bottom: 30px;
}
.paragraf-bawah {
  margin-top: 20px;
}

/*
  Jarak antara keduanya bukan 50px (30 + 20),
  melainkan 30px (yang terbesar di antara keduanya).
*/
```

Margin Collapse **tidak terjadi** pada:

- Margin horizontal (kiri-kanan)
- Elemen dengan `display: flex` atau `display: grid`
- Elemen yang memiliki padding atau border di antara margin yang bertabrakan

---

### 6. Contoh Lengkap — Kartu Konten

```html
<!-- HTML -->
<div class="kartu">
  <div class="kartu-gambar"></div>
  <div class="kartu-isi">
    <h3 class="kartu-judul">Judul Artikel</h3>
    <p class="kartu-teks">
      Ringkasan singkat dari artikel ini yang menjelaskan isinya secara umum.
    </p>
    <button class="kartu-tombol">Baca Selengkapnya</button>
  </div>
</div>
```

```css
/* CSS */
*,
*::before,
*::after {
  box-sizing: border-box;
}

.kartu {
  width: 300px;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  overflow: hidden;
  margin: 16px;
}

.kartu-gambar {
  width: 100%;
  height: 180px;
  background-color: #cfe2ff;
}

.kartu-isi {
  padding: 20px; /* Jarak antara tepi kartu dengan teks */
}

.kartu-judul {
  margin: 0 0 8px; /* Tidak ada margin atas, 8px margin bawah */
  color: #2c3e50;
  font-size: 1.1rem;
}

.kartu-teks {
  color: #666;
  font-size: 0.9rem;
  line-height: 1.5;
  margin: 0 0 16px;
}

.kartu-tombol {
  width: 100%;
  padding: 10px;
  background-color: steelblue;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.kartu-tombol:hover {
  background-color: #2a6496;
}
```

---

### Kesimpulan

Box Model adalah konsep yang mendasari semua pekerjaan tata letak CSS. Memahami perbedaan antara padding (ruang dalam), border (garis tepi), dan margin (jarak luar), serta menerapkan `box-sizing: border-box` secara konsisten, akan menghilangkan sebagian besar kebingungan tentang mengapa ukuran elemen tidak sesuai ekspektasi.

**Panduan Cepat:**

| Ingin melakukan apa?                          | Gunakan                                           |
| --------------------------------------------- | ------------------------------------------------- |
| Memberi jarak antara teks dan tepi kotak      | `padding`                                         |
| Memberi garis tepi pada kotak                 | `border`                                          |
| Memberi jarak antara kotak ini dan kotak lain | `margin`                                          |
| Memastikan width mencakup padding dan border  | `box-sizing: border-box`                          |
| Memusatkan elemen secara horizontal           | `margin: 0 auto` (dengan `width` yang ditetapkan) |

**Ringkasan Properti:**

| Properti                  | Fungsi                                             |
| ------------------------- | -------------------------------------------------- |
| `padding`                 | Ruang dalam antara konten dan border               |
| `border`                  | Garis yang mengelilingi padding dan konten         |
| `margin`                  | Ruang luar antara elemen ini dan elemen sekitarnya |
| `box-sizing: content-box` | Default — width hanya mengukur area konten         |
| `box-sizing: border-box`  | Width mencakup konten, padding, dan border         |
