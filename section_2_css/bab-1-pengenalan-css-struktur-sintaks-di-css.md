# Bab 1: Pengenalan CSS & Struktur Sintaks

## Tujuan Pembelajaran

- Memahami pengertian CSS dan perannya dalam tampilan halaman web.
- Mengetahui struktur sintaks dasar CSS: Selector, Property, dan Value.
- Memahami fungsi tanda kurung kurawal `{}` dan titik koma `;` dalam penulisan CSS.

---

## Materi Utama

Setelah mempelajari HTML sebagai fondasi struktur halaman web, kini saatnya mempelajari CSS — bahasa yang mengatur tampilannya.

---

### 1. Apa itu CSS?

**CSS** (Cascading Style Sheets) adalah bahasa yang digunakan untuk mendefinisikan tampilan dan tata letak elemen-elemen HTML. Jika HTML menentukan **apa** yang tampil di halaman, CSS menentukan **bagaimana** tampilan tersebut terlihat — warna, ukuran, jarak, posisi, hingga animasi.

Tanpa CSS, halaman web hanyalah deretan teks hitam di atas latar putih. Dengan CSS, tampilan tersebut dapat diubah menjadi antarmuka yang terstruktur, estetis, dan profesional.

**Analogi:**

- **HTML** adalah struktur bangunan — dinding, lantai, pintu, dan jendela.
- **CSS** adalah desain interior — cat tembok, pilihan furnitur, pencahayaan, dan ornamen yang membuat ruangan terlihat menarik.

**Contoh perbedaan halaman tanpa dan dengan CSS:**

```html
<!-- HTML tanpa CSS -->
<h1>Toko Online Kami</h1>
<p>Temukan produk terbaik dengan harga terjangkau.</p>
<button>Belanja Sekarang</button>
```

Hasilnya adalah teks hitam biasa tanpa tata letak. Dengan CSS:

```css
h1 {
  color: #2c3e50;
  font-size: 2rem;
}

p {
  color: #555;
  font-size: 1rem;
}

button {
  background-color: steelblue;
  color: white;
  padding: 10px 24px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
```

Elemen yang sama kini tampil dengan warna, ukuran, dan gaya yang terstruktur.

---

### 2. Struktur Sintaks Dasar CSS

CSS tidak menggunakan tag seperti HTML. CSS menggunakan **aturan (rule)** yang terdiri dari tiga komponen: **Selector**, **Property**, dan **Value**.

```css
h1 {
  color: blue;
  font-size: 24px;
}
```

**Anatomi aturan CSS:**

| Komponen     | Contoh               | Peran                                             |
| ------------ | -------------------- | ------------------------------------------------- |
| **Selector** | `h1`                 | Menentukan elemen HTML mana yang akan diberi gaya |
| **Property** | `color`, `font-size` | Aspek tampilan yang ingin diubah                  |
| **Value**    | `blue`, `24px`       | Nilai yang diterapkan pada properti tersebut      |

**Penjelasan per bagian:**

```css
h1 {
  /* Selector: targetkan semua elemen <h1> */
  color: blue; /* Property: color | Value: blue */
  font-size: 24px; /* Property: font-size | Value: 24px */
}
```

**Contoh dengan beberapa elemen:**

```css
/* Mengatur paragraf */
p {
  color: #333;
  font-size: 16px;
  line-height: 1.6;
}

/* Mengatur tombol */
button {
  background-color: steelblue;
  color: white;
  padding: 8px 16px;
}

/* Mengatur gambar */
img {
  width: 100%;
  border-radius: 8px;
}
```

---

### 3. Aturan Penulisan dan Tanda Baca

Tanda baca dalam CSS bersifat wajib — melewatkan satu karakter pun dapat menyebabkan aturan tidak diterapkan.

| Tanda | Fungsi                                                    | Contoh         |
| ----- | --------------------------------------------------------- | -------------- |
| `{}`  | Membungkus seluruh properti dan nilai untuk satu selector | `h1 { ... }`   |
| `:`   | Memisahkan property dari value                            | `color: blue`  |
| `;`   | Mengakhiri setiap deklarasi property                      | `color: blue;` |

**Akibat tanda baca yang hilang:**

```css
/* Titik koma hilang — properti berikutnya tidak akan terbaca */
p {
  color: red     /* Tidak ada ; — browser bingung */
  font-size: 16px;
}

/* Versi yang benar */
p {
  color: red;
  font-size: 16px;
}
```

**Penulisan satu baris vs banyak baris:**

```css
/* Penulisan satu baris — valid secara teknis, tapi sulit dibaca */
p {
  color: red;
  font-size: 16px;
  text-align: center;
}

/* Penulisan banyak baris — direkomendasikan untuk keterbacaan */
p {
  color: red;
  font-size: 16px;
  text-align: center;
}
```

Penulisan banyak baris adalah standar yang digunakan dalam pengembangan profesional karena lebih mudah dibaca, ditelusuri, dan diperbaiki saat terjadi kesalahan.

---

### 4. Komentar dalam CSS

Sama seperti HTML dan JavaScript, CSS mendukung komentar untuk menjelaskan kode. Komentar tidak ditampilkan di browser.

```css
/* Ini adalah komentar — tidak akan berpengaruh pada tampilan */

/* Gaya untuk bagian header */
header {
  background-color: #2c3e50;
  color: white;
  padding: 20px;
}

/* 
  Gaya ini dinonaktifkan sementara selama pengembangan
  p {
    font-style: italic;
  }
*/
```

---

### Kesimpulan

CSS adalah bahasa yang mengubah struktur HTML menjadi tampilan yang terlihat menarik dan terstruktur. Dengan memahami sintaks dasar — Selector, Property, Value — serta aturan penulisan yang benar, kamu memiliki fondasi yang diperlukan untuk mulai merancang tampilan halaman web.

**Ringkasan:**

| Konsep   | Penjelasan                                                       |
| -------- | ---------------------------------------------------------------- |
| CSS      | Bahasa untuk mendefinisikan tampilan elemen HTML                 |
| Selector | Menentukan elemen mana yang akan diberi gaya                     |
| Property | Aspek tampilan yang ingin diubah (misalnya `color`, `font-size`) |
| Value    | Nilai yang diterapkan pada properti                              |
| `{}`     | Membungkus blok deklarasi CSS untuk satu selector                |
| `;`      | Mengakhiri setiap deklarasi properti                             |
