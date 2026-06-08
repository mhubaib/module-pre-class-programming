# Bab 5: Warna di CSS

## Tujuan Pembelajaran

- Mengenal berbagai format penulisan warna di CSS: Color Names, HEX, RGB, dan HSL.
- Mampu menerapkan warna pada teks dan latar belakang elemen.
- Memahami konsep transparansi menggunakan RGBA dan HSLA.

---

## Materi Utama

Warna adalah salah satu aspek terpenting dalam desain antarmuka web. CSS menyediakan beberapa format penulisan warna, masing-masing dengan karakteristik dan kegunaan yang berbeda.

---

### 1. Color Names (Nama Warna)

Cara paling sederhana adalah menggunakan nama warna dalam bahasa Inggris. Terdapat sekitar 140 nama warna standar yang dikenali oleh semua browser modern.

```css
h1 {
  color: tomato;
}

p {
  color: steelblue;
}

div {
  background-color: lightyellow;
}
```

**Beberapa nama warna yang sering digunakan:**

| Nama        | Tampilan     | Nama         | Tampilan          |
| ----------- | ------------ | ------------ | ----------------- |
| `red`       | Merah        | `navy`       | Biru gelap        |
| `tomato`    | Merah jingga | `steelblue`  | Biru baja         |
| `gold`      | Kuning emas  | `teal`       | Hijau kebiruan    |
| `limegreen` | Hijau segar  | `gray`       | Abu-abu           |
| `coral`     | Merah muda   | `whitesmoke` | Putih keabu-abuan |

Color Names mudah ditulis dan dibaca, namun terbatas — tidak semua warna yang dibutuhkan dalam desain tersedia dalam daftar ini.

---

### 2. Format HEX (Hexadecimal)

Format HEX adalah yang paling umum digunakan dalam desain web profesional. Ditulis dengan tanda pagar (`#`) diikuti enam karakter yang terdiri dari angka `0–9` dan huruf `A–F`.

Keenam karakter tersebut terbagi menjadi tiga pasang yang masing-masing merepresentasikan intensitas warna merah, hijau, dan biru:

```
#  R  R  G  G  B  B
   F  F  0  0  0  0  →  Merah murni (#FF0000)
   0  0  F  F  0  0  →  Hijau murni (#00FF00)
   0  0  0  0  F  F  →  Biru murni  (#0000FF)
   F  F  F  F  F  F  →  Putih       (#FFFFFF)
   0  0  0  0  0  0  →  Hitam       (#000000)
```

```css
h1 {
  color: #ff5733; /* Merah jingga */
}

.kartu {
  background-color: #f8f9fa; /* Abu-abu sangat terang */
  border: 1px solid #dee2e6; /* Abu-abu muda */
}

.tombol-utama {
  background-color: #2c3e50; /* Biru gelap */
  color: #ffffff;
}
```

**HEX singkat:** Jika setiap pasang karakter sama, bisa disingkat menjadi 3 karakter:

```css
color: #ff0000; /* Bisa disingkat menjadi */
color: #f00;

color: #aabbcc; /* Bisa disingkat menjadi */
color: #abc;
```

> **Keunggulan HEX:** Kode ini spesifik dan konsisten — `#FF5733` akan menghasilkan warna yang persis sama di browser mana pun. Desainer profesional biasanya bekerja dengan kode HEX karena dapat disalin langsung dari aplikasi desain seperti Figma atau Adobe XD.

---

### 3. Format RGB dan RGBA

**RGB** (Red, Green, Blue) mencampurkan tiga warna primer cahaya dengan rentang nilai `0` hingga `255` untuk setiap saluran.

```css
/* rgb(merah, hijau, biru) */
p {
  color: rgb(255, 87, 51); /* Merah jingga — sama dengan #FF5733 */
}

.latar {
  background-color: rgb(44, 62, 80); /* Biru gelap */
}
```

**Membuat variasi warna dengan mengubah nilai:**

```css
/* Semua menggunakan saluran merah yang sama, berbeda di hijau dan biru */
.merah-murni {
  color: rgb(255, 0, 0);
}
.merah-muda {
  color: rgb(255, 150, 150);
}
.merah-gelap {
  color: rgb(139, 0, 0);
}
```

**RGBA — Menambahkan Transparansi:**

Huruf `a` (Alpha) mengontrol tingkat transparansi dengan rentang `0` (sepenuhnya transparan) hingga `1` (sepenuhnya pekat).

```css
/* Overlay gelap semi-transparan di atas gambar */
.overlay {
  background-color: rgba(0, 0, 0, 0.6); /* Hitam 60% */
}

/* Latar belakang putih transparan */
.kartu-kaca {
  background-color: rgba(255, 255, 255, 0.8); /* Putih 80% */
}

/* Warna biru transparan */
.sorotan {
  background-color: rgba(70, 130, 180, 0.3); /* Biru 30% */
}
```

**Contoh penggunaan RGBA:**

```html
<!-- HTML -->
<div class="gambar-hero">
  <div class="overlay">
    <h1>Judul di Atas Gambar</h1>
  </div>
</div>
```

```css
/* CSS */
.gambar-hero {
  background-image: url("foto.jpg");
  height: 400px;
  position: relative;
}

.overlay {
  position: absolute;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5); /* Gelap 50% di atas gambar */
  display: flex;
  align-items: center;
  justify-content: center;
}

.overlay h1 {
  color: white;
}
```

---

### 4. Format HSL dan HSLA

**HSL** (Hue, Saturation, Lightness) adalah format yang paling intuitif untuk memodifikasi warna secara manual, karena setiap nilainya memiliki makna yang mudah dipahami.

- **Hue (Warna)**: Nilai `0–360` yang merepresentasikan posisi warna pada lingkaran warna. `0` = merah, `120` = hijau, `240` = biru, `360` = kembali ke merah.
- **Saturation (Saturasi/Kepekatan)**: `0%` = abu-abu (tanpa warna), `100%` = warna penuh dan mencolok.
- **Lightness (Kecerahan)**: `0%` = hitam, `50%` = warna normal, `100%` = putih.

```css
/* hsl(hue, saturation, lightness) */
.tombol-hijau {
  background-color: hsl(120, 100%, 35%); /* Hijau gelap */
}

.tombol-hijau:hover {
  background-color: hsl(120, 100%, 45%); /* Hijau lebih terang saat hover */
}
```

**Keunggulan HSL:** Membuat variasi warna menjadi sangat mudah — cukup ubah nilai Lightness untuk mendapatkan versi terang/gelap, atau ubah Saturation untuk versi pudar.

```css
/* Variasi dari satu warna dasar hanya dengan mengubah Lightness */
.sangat-gelap {
  background-color: hsl(210, 70%, 20%);
}
.gelap {
  background-color: hsl(210, 70%, 35%);
}
.normal {
  background-color: hsl(210, 70%, 50%);
}
.terang {
  background-color: hsl(210, 70%, 65%);
}
.sangat-terang {
  background-color: hsl(210, 70%, 80%);
}
```

**HSLA** menambahkan nilai Alpha untuk transparansi, sama seperti RGBA:

```css
.notifikasi {
  background-color: hsla(48, 100%, 60%, 0.85); /* Kuning transparan 85% */
}
```

---

### 5. Properti Warna Utama di CSS

```css
.elemen {
  color: #333; /* Warna teks */
  background-color: #f5f5f5; /* Warna latar belakang */
  border: 2px solid #ccc; /* Warna border */
  outline: 2px solid blue; /* Warna outline */
}
```

**Contoh lengkap — Kartu Profil:**

```html
<!-- HTML -->
<div class="kartu-profil">
  <div class="avatar">BS</div>
  <h2 class="nama">Budi Santoso</h2>
  <p class="jabatan">Front-End Developer</p>
  <p class="deskripsi">
    Spesialis dalam membangun antarmuka web yang responsif.
  </p>
</div>
```

```css
/* CSS */
.kartu-profil {
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 24px;
  max-width: 300px;
  text-align: center;
}

.avatar {
  background-color: hsl(210, 70%, 50%);
  color: #ffffff;
  width: 64px;
  height: 64px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: bold;
  margin: 0 auto 16px;
}

.nama {
  color: #2c3e50;
  font-size: 1.25rem;
  margin: 0 0 4px;
}

.jabatan {
  color: hsl(210, 70%, 50%);
  font-weight: bold;
  margin: 0 0 12px;
}

.deskripsi {
  color: #666;
  font-size: 0.9rem;
  line-height: 1.5;
}
```

---

### Kesimpulan

CSS menyediakan berbagai format warna yang masing-masing memiliki kegunaannya sendiri. Untuk tampilan profesional, kombinasi HEX untuk warna tetap dan RGBA/HSLA untuk warna dengan transparansi adalah yang paling umum digunakan.

**Ringkasan Format Warna:**

| Format      | Contoh                     | Keunggulan                                         |
| ----------- | -------------------------- | -------------------------------------------------- |
| Color Names | `tomato`, `steelblue`      | Mudah ditulis, untuk prototipe cepat               |
| HEX         | `#FF5733`, `#2C3E50`       | Presisi tinggi, mudah disalin dari aplikasi desain |
| RGB         | `rgb(255, 87, 51)`         | Nilai intuitif per saluran warna                   |
| RGBA        | `rgba(0, 0, 0, 0.5)`       | RGB dengan kontrol transparansi                    |
| HSL         | `hsl(120, 100%, 50%)`      | Mudah membuat variasi terang/gelap satu warna      |
| HSLA        | `hsla(210, 70%, 50%, 0.8)` | HSL dengan kontrol transparansi                    |
