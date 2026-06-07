# Bab 2: Jenis-jenis Selektor di CSS

## Tujuan Pembelajaran

- Memahami konsep Selektor sebagai cara menargetkan elemen HTML tertentu.
- Mampu menggunakan Element Selector, Class Selector, dan ID Selector dengan tepat.
- Mengenal Universal Selector dan penggunaannya.
- Memahami perbedaan dan kapan menggunakan Class vs ID.

---

## Materi Utama

Di materi sebelumnya, kita tahu bahwa **Selector** bertugas menentukan elemen HTML mana yang akan diberi gaya. Namun, bagaimana jika kita punya sepuluh paragraf tetapi hanya ingin mewarnai satu paragraf saja? Atau bagaimana jika kita ingin menerapkan gaya yang sama pada beberapa elemen yang berbeda jenis?

Inilah mengapa terdapat berbagai jenis Selektor yang dirancang untuk kebutuhan yang berbeda.

---

### 1. Element Selector

Element Selector menargetkan elemen berdasarkan nama tag HTML-nya. Semua elemen dengan tag yang sama akan mendapatkan gaya yang sama.

```css
p {
  color: green;
}
```

Seluruh elemen `<p>` di halaman akan berubah warna menjadi hijau.

**Contoh dengan beberapa element selector:**

```html
<!-- HTML -->
<h1>Judul Halaman</h1>
<p>Paragraf pertama.</p>
<p>Paragraf kedua.</p>
<a href="#">Tautan</a>
```

```css
/* CSS */
h1 {
  color: #2c3e50;
  font-size: 2rem;
}

p {
  color: #555;
  line-height: 1.6;
}

a {
  color: steelblue;
  text-decoration: none;
}
```

> **Catatan:** Element Selector bersifat massal — seluruh elemen bertag sama akan terdampak. Gunakan ini untuk mendefinisikan gaya dasar yang memang ingin diterapkan secara menyeluruh.

---

### 2. Class Selector

Class Selector menargetkan elemen berdasarkan nilai atribut `class`-nya. Satu class dapat digunakan pada banyak elemen berbeda, dan satu elemen dapat memiliki lebih dari satu class.

Di CSS, Class Selector ditulis dengan **tanda titik (`.`)** diikuti nama class-nya.

```html
<!-- HTML -->
<p class="teks-penting">Ini paragraf penting.</p>
<h2 class="teks-penting">Ini judul yang juga penting.</h2>
<span class="teks-penting">Ini span yang penting.</span>
```

```css
/* CSS */
.teks-penting {
  font-weight: bold;
  color: red;
}
```

Ketiga elemen di atas — meskipun berbeda jenis tag — akan mendapatkan gaya yang sama karena berbagi class yang sama.

**Menggunakan beberapa class pada satu elemen:**

```html
<!-- Satu elemen dapat memiliki beberapa class, dipisahkan spasi -->
<button class="tombol tombol-utama besar">Kirim</button>
```

```css
.tombol {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.tombol-utama {
  background-color: steelblue;
  color: white;
}

.besar {
  font-size: 1.2rem;
  padding: 12px 24px;
}
```

**Analogi:**

Bayangkan class seperti seragam. Semua murid yang mengenakan seragam Pramuka akan diperlakukan sebagai anggota Pramuka — tidak peduli kelas berapa mereka. Satu murid pun bisa mengenakan lebih dari satu seragam untuk berbagai kegiatan.

---

### 3. ID Selector

ID Selector menargetkan satu elemen spesifik berdasarkan nilai atribut `id`-nya. Dalam satu halaman HTML, setiap nilai `id` **hanya boleh digunakan sekali**.

Di CSS, ID Selector ditulis dengan **tanda pagar (`#`)** diikuti nama ID-nya.

```html
<!-- HTML -->
<header id="header-utama">
  <h1>Nama Website</h1>
</header>

<footer id="footer-utama">
  <p>© 2026 Hak Cipta Dilindungi</p>
</footer>
```

```css
/* CSS */
#header-utama {
  background-color: #2c3e50;
  color: white;
  padding: 20px 40px;
}

#footer-utama {
  background-color: #34495e;
  color: #ccc;
  text-align: center;
  padding: 16px;
}
```

**Analogi:**

ID seperti Nomor Induk Kependudukan (NIK). Setiap orang mungkin bisa memakai seragam yang sama (class), tetapi NIK setiap orang berbeda dan tidak ada duanya. ID digunakan untuk menunjuk satu target yang benar-benar spesifik dan unik di halaman.

---

### 4. Universal Selector

Universal Selector menggunakan tanda **bintang (`*`)** dan menargetkan **semua elemen** di halaman tanpa terkecuali. Selektor ini paling sering digunakan di awal penulisan CSS untuk menyeragamkan pengaturan dasar browser.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

Setiap browser memiliki nilai default bawaan yang berbeda-beda untuk `margin` dan `padding`. Penggunaan Universal Selector di awal untuk mereset nilai-nilai tersebut memastikan tampilan halaman konsisten di semua browser.

**Contoh CSS Reset sederhana:**

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}
```

> **Catatan:** Gunakan Universal Selector dengan hati-hati karena ia diterapkan ke semua elemen, yang dapat memengaruhi performa pada halaman dengan banyak elemen.

---

### 5. Selektor Kombinasi

CSS juga mendukung penulisan beberapa selector sekaligus untuk menerapkan gaya yang sama.

```css
/* Menerapkan gaya yang sama pada h1, h2, dan h3 sekaligus */
h1,
h2,
h3 {
  color: #2c3e50;
  font-family: Georgia, serif;
}

/* Menargetkan elemen p yang memiliki class "intro" */
p.intro {
  font-size: 1.2rem;
  color: steelblue;
}
```

**Contoh lengkap — Halaman artikel:**

```html
<!-- HTML -->
<article>
  <h1 id="judul-artikel">Panduan Belajar CSS</h1>
  <p class="intro">
    CSS adalah bahasa yang digunakan untuk mendesain tampilan halaman web.
  </p>
  <p>
    Dengan CSS, kamu dapat mengatur warna, ukuran, tata letak, dan masih banyak
    lagi.
  </p>
  <p class="catatan">Catatan: Artikel ini ditujukan untuk pemula.</p>
</article>
```

```css
/* CSS */
* {
  box-sizing: border-box;
}

#judul-artikel {
  color: #2c3e50;
  font-size: 2rem;
  border-bottom: 3px solid steelblue;
  padding-bottom: 8px;
}

.intro {
  font-size: 1.1rem;
  font-style: italic;
  color: steelblue;
}

p {
  color: #444;
  line-height: 1.7;
  margin-bottom: 12px;
}

.catatan {
  background-color: #fff3cd;
  border-left: 4px solid orange;
  padding: 8px 12px;
}
```

---

### Kesimpulan

Setiap jenis selektor dirancang untuk kebutuhan yang berbeda. Memilih selektor yang tepat membuat CSS lebih terstruktur, mudah dipelihara, dan tidak menimbulkan konflik gaya yang tidak diinginkan.

**Ringkasan Jenis Selektor:**

| Selektor      |  Simbol  | Sifat                         | Kapan Digunakan                                     |
| :------------ | :------: | :---------------------------- | :-------------------------------------------------- |
| **Element**   | nama tag | Massal                        | Gaya dasar untuk semua elemen bertag sama           |
| **Class**     |   `.`    | Dapat digunakan ulang         | Gaya yang diterapkan ke banyak elemen berbeda       |
| **ID**        |   `#`    | Unik (hanya satu per halaman) | Elemen yang benar-benar unik seperti header, footer |
| **Universal** |   `*`    | Seluruh halaman               | CSS Reset di awal stylesheet                        |

**Aturan Penamaan Class dan ID:**

- Tidak boleh diawali dengan angka (`1tombol` ✗, `tombol1` ✓)
- Tidak boleh mengandung spasi (gunakan tanda hubung `-` atau garis bawah `_`)
- Gunakan nama yang mendeskripsikan fungsi atau tampilan (`tombol-utama`, `teks-peringatan`)
- Penulisan huruf bersifat case-sensitive: `.tombol` dan `.Tombol` adalah dua class yang berbeda
