# Bab 14: Display & Position di CSS

## Tujuan Pembelajaran

- Memahami properti `display` dan cara mengubah perilaku bawaan elemen HTML.
- Menguasai properti `position` untuk menempatkan elemen di luar alur dokumen normal.
- Membedakan perilaku `static`, `relative`, `fixed`, `absolute`, dan `sticky`.

---

## Materi Utama

Dua properti yang dibahas di bab ini — `display` dan `position` — adalah fondasi dari semua pekerjaan tata letak CSS yang lebih kompleks. Memahami keduanya membuka kemampuan untuk menempatkan elemen di posisi yang tepat, kapan pun diperlukan.

---

### 1. Properti `display` — Mengubah Perilaku Elemen

Setiap elemen HTML memiliki nilai `display` bawaan yang menentukan bagaimana ia berperilaku dalam alur dokumen. CSS memungkinkan kita mengubah nilai tersebut.

| Nilai          | Perilaku                                                                |
| -------------- | ----------------------------------------------------------------------- |
| `block`        | Elemen menempati satu baris penuh; `width` dan `height` dapat diatur    |
| `inline`       | Elemen berbagi baris dengan elemen lain; `width` dan `height` diabaikan |
| `inline-block` | Berbagi baris seperti `inline`, namun `width` dan `height` dapat diatur |
| `none`         | Elemen dihapus dari tampilan dan tidak menempati ruang                  |
| `flex`         | Mengaktifkan Flexbox pada elemen (dibahas di Bab 33)                    |
| `grid`         | Mengaktifkan CSS Grid pada elemen (dibahas di Bab 34)                   |

**Contoh:**

```html
<!-- HTML -->
<span class="label-block">Span yang berperilaku seperti div</span>
<div class="div-inline">Div pertama berbagi baris</div>
<div class="div-inline">Div kedua di sebelahnya</div>
<button class="menu-item">Beranda</button>
<button class="menu-item">Produk</button>
<button class="menu-item">Kontak</button>
<p class="tersembunyi">Elemen ini tidak terlihat dan tidak menempati ruang.</p>
```

```css
/* CSS */

/* span diubah ke block — dapat diatur lebar dan tingginya */
.label-block {
  display: block;
  width: 220px;
  padding: 8px 12px;
  background-color: #fca5a5;
  margin-bottom: 8px;
}

/* div diubah ke inline — berbagi baris */
.div-inline {
  display: inline;
  background-color: #bae6fd;
  padding: 4px 8px;
}

/* Tombol menu sejajar dengan ukuran seragam */
.menu-item {
  display: inline-block;
  width: 100px;
  height: 40px;
  text-align: center;
  line-height: 40px;
  background-color: steelblue;
  color: white;
  border: none;
  cursor: pointer;
}

/* Elemen disembunyikan sepenuhnya */
.tersembunyi {
  display: none;
}
```

> **Perbedaan `display: none` vs `visibility: hidden`:** Keduanya menyembunyikan elemen, namun `display: none` menghapus elemen dari tata letak sehingga tidak menempati ruang sama sekali. `visibility: hidden` menyembunyikan tampilan elemen tetapi ruangnya tetap ada.

---

### 2. Properti `position` — Menempatkan Elemen

Secara default, semua elemen mengikuti **alur dokumen normal** (_Document Flow_) — disusun dari atas ke bawah dan dari kiri ke kanan. Properti `position` memungkinkan elemen dikeluarkan dari alur ini dan ditempatkan di posisi tertentu.

Saat menggunakan `position` selain `static`, gunakan properti **`top`, `right`, `bottom`, `left`** untuk menentukan posisinya.

---

#### A. `static` — Posisi Default

Semua elemen memiliki `position: static` secara default. Elemen mengikuti alur dokumen normal dan properti `top`, `right`, `bottom`, `left` tidak berefek.

```css
.elemen-normal {
  position: static; /* Ini adalah nilai default — tidak perlu ditulis eksplisit */
}
```

---

#### B. `relative` — Bergeser dari Posisi Asli

Elemen digeser dari posisi aslinya, namun ruang yang ditinggalkan tetap dipertahankan dalam alur dokumen — elemen lain tidak mengisi posisi yang ditinggalkan.

```css
.kotak-geser {
  position: relative;
  top: 20px; /* Bergeser 20px ke bawah dari posisi aslinya */
  left: 50px; /* Bergeser 50px ke kanan dari posisi aslinya */
}
```

```html
<!-- HTML -->
<div class="kotak-normal">Kotak A</div>
<div class="kotak-geser">Kotak B (bergeser)</div>
<div class="kotak-normal">Kotak C</div>
```

```css
/* CSS */
.kotak-normal {
  background-color: #e2e8f0;
  padding: 12px;
  margin-bottom: 4px;
}

.kotak-geser {
  position: relative;
  top: 20px;
  left: 50px;
  background-color: #fed7aa;
  padding: 12px;
}
```

Kotak C tidak naik mengisi "bekas posisi" Kotak B — ruang tersebut tetap dikosongkan.

> **Penggunaan utama `relative`:** Menjadi elemen induk (wadah) bagi elemen anak yang menggunakan `position: absolute`.

---

#### C. `fixed` — Menempel pada Viewport

Elemen dikeluarkan dari alur dokumen dan posisinya ditetapkan relatif terhadap **viewport** (area tampilan browser). Elemen tetap di posisinya meskipun halaman di-scroll.

```html
<!-- HTML -->
<main class="konten-panjang">
  <p>Artikel panjang yang bisa di-scroll...</p>
</main>

<a class="tombol-wa" href="https://wa.me/6281234567890"> 💬 Chat WA </a>
```

```css
/* CSS */
.konten-panjang {
  height: 2000px;
  padding: 24px;
}

.tombol-wa {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background-color: #25d366;
  color: white;
  padding: 12px 18px;
  border-radius: 50px;
  text-decoration: none;
  font-weight: bold;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  z-index: 100;
}
```

Tombol WhatsApp selalu terlihat di pojok kanan bawah layar, tidak peduli seberapa jauh pengunjung men-scroll halaman.

---

#### D. `absolute` — Menempel pada Elemen Induk

Elemen dikeluarkan dari alur dokumen dan posisinya ditetapkan relatif terhadap **elemen leluhur terdekat yang memiliki `position` selain `static`**. Jika tidak ada, posisinya mengacu pada `<body>`.

> **Pola standar:** Elemen induk diberi `position: relative` sebagai batas referensi, elemen anak diberi `position: absolute` untuk ditempatkan di dalam batas tersebut.

```html
<!-- HTML -->
<div class="kartu-produk">
  <img src="baju.jpg" alt="Baju Keren" />
  <h3>Baju Keren Limited</h3>
  <span class="label-diskon">SALE 50%</span>
</div>
```

```css
/* CSS */
.kartu-produk {
  position: relative; /* Menjadi batas referensi untuk elemen absolute di dalamnya */
  width: 220px;
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
}

.kartu-produk img {
  width: 100%;
  display: block;
}

.label-diskon {
  position: absolute;
  top: 12px;
  right: 12px;
  background-color: #ef4444;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: bold;
}
```

Label "SALE 50%" selalu menempel di pojok kanan atas gambar kartu, tanpa memengaruhi posisi elemen lain di dalam kartu.

---

#### E. `sticky` — Mengikuti Scroll Hingga Titik Tertentu

Elemen berperilaku seperti `relative` hingga posisinya mencapai nilai `top` (atau `bottom`) yang ditetapkan saat di-scroll — setelah itu ia berperilaku seperti `fixed` hingga melewati batas wadah induknya.

```html
<!-- HTML -->
<header class="navbar">
  <nav>
    <a href="#">Beranda</a>
    <a href="#">Produk</a>
    <a href="#">Kontak</a>
  </nav>
</header>

<main>
  <p>Konten artikel yang sangat panjang...</p>
</main>
```

```css
/* CSS */
.navbar {
  position: sticky;
  top: 0; /* Mulai menempel saat menyentuh tepi atas viewport */
  background-color: white;
  padding: 16px 32px;
  border-bottom: 1px solid #e2e8f0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  z-index: 100;
}

.navbar a {
  margin-right: 24px;
  text-decoration: none;
  color: #334155;
  font-weight: 500;
}
```

Navbar muncul di posisi normalnya saat halaman dimuat. Ketika halaman di-scroll dan navbar menyentuh tepi atas viewport, navbar langsung menempel dan tidak ikut terbawa scroll.

> **Syarat `sticky` bekerja:** Elemen induk tidak boleh memiliki `overflow: hidden` atau `overflow: auto`, dan elemen sticky harus berada di dalam wadah yang cukup tinggi untuk menampung efek sticky.

---

### 3. Properti `z-index` — Urutan Lapisan

Ketika elemen saling tumpang tindih akibat penggunaan `position`, `z-index` menentukan elemen mana yang tampil di lapisan paling atas. Nilai yang lebih tinggi berarti elemen tampil di atas elemen lain.

```css
.modal-overlay {
  position: fixed;
  inset: 0;
  z-index: 200; /* Di atas navbar */
}

.navbar {
  position: sticky;
  top: 0;
  z-index: 100; /* Di atas konten biasa */
}

.konten {
  position: relative;
  z-index: 1; /* Lapisan paling bawah */
}
```

> **Catatan:** `z-index` hanya berefek pada elemen yang memiliki `position` selain `static`.

---

### 4. Perbandingan Nilai `position`

| Nilai      | Referensi Posisi                        | Keluar dari Alur Dokumen? | Ruang Asli Dipertahankan? |
| ---------- | --------------------------------------- | ------------------------- | ------------------------- |
| `static`   | Alur dokumen normal                     | Tidak                     | Ya                        |
| `relative` | Posisi asli elemen                      | Tidak                     | Ya                        |
| `fixed`    | Viewport                                | Ya                        | Tidak                     |
| `absolute` | Leluhur terdekat yang ber-`position`    | Ya                        | Tidak                     |
| `sticky`   | Alur normal → Viewport (saat threshold) | Sebagian                  | Ya                        |

---

### Kesimpulan

`display` dan `position` adalah dua properti yang memberikan kontrol penuh atas penempatan elemen di halaman. Kombinasi `position: relative` pada induk dan `position: absolute` pada anak adalah pola yang sangat umum digunakan untuk menempatkan elemen overlay, badge, dan dekorasi. Sementara `sticky` adalah solusi elegan untuk navbar yang mengikuti scroll pengguna.

**Ringkasan:**

| Properti                | Nilai Utama | Kegunaan Umum                                                         |
| ----------------------- | ----------- | --------------------------------------------------------------------- |
| `display: block`        | —           | Elemen menempati satu baris penuh                                     |
| `display: inline`       | —           | Elemen berbagi baris                                                  |
| `display: inline-block` | —           | Berbagi baris dengan ukuran yang dapat diatur                         |
| `display: none`         | —           | Menyembunyikan elemen dan menghapus ruangnya                          |
| `position: relative`    | —           | Bergeser dari posisi asli; atau sebagai wadah untuk elemen `absolute` |
| `position: fixed`       | —           | Menempel pada viewport; tidak ikut scroll                             |
| `position: absolute`    | —           | Menempel pada elemen induk yang ber-`position`; dikeluarkan dari alur |
| `position: sticky`      | —           | Relatif hingga threshold tercapai, lalu menempel seperti `fixed`      |
| `z-index`               | Angka       | Mengatur urutan lapisan elemen yang saling tumpang tindih             |
