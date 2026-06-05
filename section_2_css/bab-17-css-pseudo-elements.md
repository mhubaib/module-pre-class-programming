# Bab 17: CSS Pseudo Elements

## Tujuan Pembelajaran

- Membedakan antara Pseudo-Class (status) dan Pseudo-Element (bagian fisik buatan).
- Menguasai penggunaan titik dua ganda (`::`).
- Memanipulasi tipografi tingkat lanjut lewat `::first-letter` dan `::selection`.
- Memahami cara menyisipkan elemen dekoratif tanpa HTML menggunakan `::before` dan `::after`.

---

## Materi Utama

Jika Pseudo-**Class** di Bab 30 membahas tentang "Status Keadaan" (seperti sedang disentuh mouse), maka Pseudo-**Element** adalah fitur CSS untuk memanipulasi atau menciptakan **bagian spesifik fisik** dari suatu elemen teks maupun kotak.

Ciri khas penulisan Pseudo-Element yang disepakati standar modern adalah menggunakan **titik dua ganda (`::`)**, dengan tujuan agar tidak tertukar dengan Pseudo-Class yang hanya menggunakan satu titik dua.

**Perbedaan Pseudo-Class vs Pseudo-Element:**

| | Pseudo-Class | Pseudo-Element |
|---|---|---|
| Simbol | `:` (satu titik dua) | `::` (dua titik dua) |
| Fungsi | Menargetkan **status/keadaan** elemen | Menargetkan atau menciptakan **bagian fisik** elemen |
| Contoh | `:hover`, `:focus` | `::before`, `::first-letter` |

**Sintaks Dasar:**

```css
selektor::pseudo-element {
  properti: nilai;
}
```

**Contoh sederhana:**

```html
<!-- HTML -->
<p class="intro">Ini adalah paragraf pembuka artikel kami.</p>
```

```css
/* CSS — huruf pertama paragraf diperbesar menyerupai gaya tipografi majalah */
.intro::first-letter {
  font-size: 250%;
  font-weight: bold;
  color: darkred;
}
```

---

### 1. Manipulasi Tampilan Sebagian Teks

Terdapat situasi di mana kita perlu menerapkan gaya hanya pada **sebagian kecil** dari sebuah teks — misalnya hanya pada huruf pertama suatu paragraf, atau hanya pada teks yang sedang disorot oleh pengguna. Pseudo-element menyediakan cara yang tepat untuk kebutuhan tersebut tanpa perlu menambahkan tag HTML tambahan.

```css
/* Memperbesar huruf pertama pada paragraf (Efek Drop-Cap) */
p::first-letter {
  font-size: 300%;
  color: maroon;
  font-weight: bold;
}
/* Mengubah tampilan teks yang disorot/diblok oleh mouse */
p::selection {
  background-color: yellow; /* Latar belakang sorotan menjadi kuning */
  color: red;               /* Warna teks yang disorot menjadi merah */
}
```

**Contoh Lengkap — Artikel Blog Bergaya Majalah:**

```html
<!-- HTML -->
<article class="artikel-blog">
  <p>Dahulu kala, di sebuah desa kecil yang dikelilingi hutan lebat,
  hiduplah seorang anak bernama Budi yang gemar membaca buku. Setiap
  hari ia duduk di bawah pohon besar sambil membuka halamannya.</p>

  <p>Suatu pagi, ia menemukan sebuah buku misterius berwarna merah tua
  yang tidak pernah ia lihat sebelumnya di rak perpustakaan desa.</p>
</article>
```

```css
/* CSS */

/* Efek Drop-Cap: huruf pertama hanya pada paragraf pertama */
.artikel-blog p:first-child::first-letter {
  font-size: 400%;
  font-weight: bold;
  color: maroon;
  float: left;        /* huruf besar diposisikan mengapung ke kiri */
  line-height: 0.8;
  margin-right: 6px;
  font-family: Georgia, serif;
}

/* Gaya sorotan teks saat pengguna memblok teks */
.artikel-blog::selection {
  background-color: gold;
  color: darkred;
}

/* Firefox memerlukan prefix -moz- */
.artikel-blog::-moz-selection {
  background-color: gold;
  color: darkred;
}
```

> **Catatan:** `::first-letter` hanya bekerja pada elemen _block_ (seperti `<p>`, `<h1>`, `<div>`), tidak pada elemen _inline_ seperti `<span>`. Sementara `::selection` dapat diterapkan ke hampir semua elemen teks.

---

### 2. Menyisipkan Konten Dekoratif: `::before` dan `::after`

Pseudo-element `::before` dan `::after` merupakan fitur yang sangat sering digunakan dalam pengembangan web profesional, dan kerap menjadi topik pembahasan dalam sesi wawancara teknis.

Keduanya berfungsi untuk **menyisipkan konten tambahan** tepat _sebelum_ atau _sesudah_ konten asli suatu elemen HTML, tanpa perlu menambahkan tag baru ke dalam dokumen HTML.

Pendekatan ini umumnya dimanfaatkan untuk menambahkan ikon, tanda centang, label, maupun elemen dekoratif lainnya.

**Aturan Wajib:**

Setiap kali menggunakan `::before` atau `::after`, properti `content` **wajib dideklarasikan**. Tanpa properti tersebut — meskipun nilainya berupa string kosong `""` — elemen yang disisipkan tidak akan ditampilkan di layar.

**Contoh 1: Menyisipkan Teks Tambahan**

```css
/* Menambahkan teks sapaan di depan setiap elemen H1 */
h1::before {
  content: "Halo Bapak/Ibu ";
  color: grey;
}
/* Jika HTML aslinya <h1>Budi</h1>, maka yang tampil di layar adalah: Halo Bapak/Ibu Budi */
```

**Contoh 2: Membuat Elemen Dekoratif Kosong**

```css
/* Elemen H2 dijadikan acuan posisi untuk elemen dekoratif */
h2 {
  position: relative;
}
/* Garis pendek dekoratif di bawah judul menggunakan ::after */
h2::after {
  content: "";        /* dikosongkan karena berfungsi sebagai elemen visual, bukan teks */
  position: absolute;
  bottom: -5px;       /* diposisikan tepat di bawah elemen H2 */
  left: 0;
  width: 50px;        /* lebar garis dekoratif */
  height: 4px;        /* ketebalan garis dekoratif */
  background-color: green;
}
```

**Analogi: Elemen Pendamping:**

`::before` dan `::after` dapat diibaratkan sebagai dua elemen pendamping yang selalu mengikuti elemen utama — satu di depan dan satu di belakang. Keduanya tampil secara visual di halaman, namun tidak tercatat sebagai bagian dari struktur dokumen HTML. Keduanya sepenuhnya dikendalikan melalui CSS.

**Contoh Lengkap — Kartu Produk dengan Badge dan Ornamen:**

```html
<!-- HTML -->
<div class="kartu-produk">
  <h2 class="nama-produk">Sepatu Lari ProMax</h2>
  <p class="harga">Rp 450.000</p>
  <ul class="fitur-list">
    <li>Sol anti-selip</li>
    <li>Bahan breathable</li>
    <li>Garansi 1 tahun</li>
  </ul>
</div>
```

```css
/* CSS */

/* --- Label "BARU" disisipkan sebelum nama produk --- */
.nama-produk::before {
  content: "BARU ";
  background-color: tomato;
  color: white;
  font-size: 12px;
  font-weight: bold;
  padding: 2px 6px;
  border-radius: 4px;
  margin-right: 8px;
  vertical-align: middle;
}

/* --- Garis dekoratif pendek di bawah judul produk --- */
.nama-produk {
  position: relative;
  display: inline-block;
}

.nama-produk::after {
  content: "";
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 60px;
  height: 3px;
  background-color: tomato;
  border-radius: 2px;
}

/* --- Ikon centang disisipkan di depan setiap item fitur --- */
.fitur-list li::before {
  content: "✓ ";
  color: green;
  font-weight: bold;
}

/* --- Label keterangan disisipkan di depan harga --- */
.harga::before {
  content: "Harga: ";
  color: gray;
  font-size: 14px;
}
```

> **Catatan:** Nilai properti `content` dapat berupa teks biasa `"Teks"`, karakter/simbol `"✓"`, atau string kosong `""` untuk elemen dekoratif. Perlu diperhatikan bahwa nilai `content` **tidak mendukung tag HTML** seperti `content: "<span>"` — penulisan seperti itu tidak akan diproses oleh browser.

---

### 3. Pseudo-Element Lainnya

Selain keempat pseudo-element yang telah dibahas, terdapat dua lainnya yang juga umum digunakan:

- **`::first-line`**: Menargetkan hanya **baris pertama** dari sebuah blok teks, yaitu baris yang tampil pertama secara visual di layar.
- **`::placeholder`**: Menargetkan teks _placeholder_ yang tampil di dalam elemen input form sebelum pengguna mengisi data.

**Contoh:**

```html
<!-- HTML -->
<p class="artikel">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>

<input class="input-nama" type="text" placeholder="Masukkan nama lengkap..." />
```

```css
/* CSS */

/* Baris pertama paragraf ditampilkan dengan gaya berbeda */
.artikel::first-line {
  font-weight: bold;
  color: darkslateblue;
  letter-spacing: 1px;
}

/* Teks placeholder pada input diubah tampilannya */
.input-nama::placeholder {
  color: lightcoral;
  font-style: italic;
}
```

> **Catatan `::first-line`:** Panjang "baris pertama" ditentukan oleh lebar kontainer dan ukuran font yang digunakan, sehingga dapat berubah ketika ukuran jendela browser berubah.

---

### Kesimpulan

Pseudo-Element adalah fitur CSS yang memungkinkan pengembang menargetkan bagian-bagian spesifik dari suatu elemen yang tidak dapat dijangkau dengan selektor biasa — mulai dari huruf pertama, baris pertama, hingga teks yang sedang disorot. Selain itu, `::before` dan `::after` membuka kemampuan untuk menyisipkan elemen visual dekoratif tanpa perlu memodifikasi struktur HTML sama sekali.

**Ringkasan Pseudo-Element yang Telah Dipelajari:**

| Pseudo-Element | Fungsi |
|---|---|
| `::first-letter` | Menargetkan huruf pertama dari sebuah blok teks |
| `::first-line` | Menargetkan baris pertama yang tampil dari sebuah blok teks |
| `::selection` | Menargetkan teks yang sedang disorot oleh pengguna |
| `::before` | Menyisipkan konten tambahan tepat **sebelum** konten asli elemen |
| `::after` | Menyisipkan konten tambahan tepat **sesudah** konten asli elemen |
| `::placeholder` | Menargetkan teks placeholder di dalam elemen input form |
