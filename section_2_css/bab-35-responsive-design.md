# Bab 35: Responsive Design

## Tujuan Pembelajaran

- Memahami pentingnya tampilan yang dapat menyesuaikan diri di berbagai ukuran layar.
- Memahami konsep dan filosofi Responsive Web Design.
- Menguasai pendekatan **Mobile First Design** dan alasan penggunaannya.
- Menguasai penggunaan `@media` (Media Queries) sebagai mekanisme utama desain responsif.
- Memahami peran tag `<meta viewport>` dalam memastikan tampilan yang benar di perangkat mobile.

---

## Materi Utama

Bayangkan kamu telah membangun sebuah halaman web yang tampilannya sempurna di layar laptop. Tata letak terstruktur rapi, teks terbaca jelas, dan tombol-tombol tersusun dengan baik. Namun ketika halaman yang sama dibuka di layar ponsel, tampilannya berantakan — teks terlalu kecil, gambar terpotong, dan elemen-elemen saling bertumpukan.

Inilah tantangan nyata yang dihadapi oleh setiap pengembang web. Pengunjung sebuah website dapat mengaksesnya dari berbagai perangkat dengan ukuran layar yang sangat beragam — mulai dari ponsel kecil hingga monitor desktop yang lebar. Solusi untuk tantangan ini adalah **Responsive Web Design**.

---

### 1. Apa Itu Responsive Design?

Responsive Design adalah pendekatan dalam pembuatan tampilan web di mana tata letak dan ukuran elemen **menyesuaikan diri secara otomatis** berdasarkan ukuran layar perangkat yang digunakan oleh pengunjung.

Sebuah website yang responsif berperilaku seperti air — ketika dituangkan ke dalam wadah kecil (ponsel), ia menyesuaikan bentuknya menjadi satu kolom vertikal; ketika dialirkan ke dalam wadah yang lebih lebar (tablet atau desktop), ia merentang dan mengisi ruang yang tersedia secara optimal.

**Contoh perubahan tata letak yang umum:**

| Ukuran Layar | Tampilan Tata Letak |
|---|---|
| Ponsel (`< 600px`) | Satu kolom, elemen bertumpuk dari atas ke bawah |
| Tablet (`600px – 992px`) | Dua kolom |
| Desktop (`> 992px`) | Tiga kolom atau lebih, dengan sidebar |

---

### 2. Tag Meta Viewport — Syarat Wajib di HTML

Sebelum menulis satu baris Media Query pun, terdapat satu baris kode HTML yang **wajib ada** di dalam elemen `<head>` pada setiap halaman web. Tanpa baris ini, browser pada perangkat mobile akan menampilkan halaman dalam versi desktop yang diperkecil paksa, sehingga seluruh teks dan elemen menjadi sangat kecil dan tidak terbaca.

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

**Penjelasan atribut:**

- `width=device-width` — Memerintahkan browser agar menggunakan lebar layar fisik perangkat sebagai lebar viewport, bukan lebar layar desktop yang disimulasikan.
- `initial-scale=1.0` — Menetapkan skala zoom awal halaman menjadi 1:1, sehingga tidak ada pembesaran atau perkecilan otomatis saat halaman pertama kali dimuat.

> **Catatan:** Jika kamu menggunakan VSCode dengan shortcut `!` + Enter untuk membuat template HTML awal (Emmet boilerplate), tag meta viewport ini sudah otomatis disertakan.

---

### 3. Strategi Mobile First Design

Terdapat dua pendekatan dalam menulis CSS responsif:

- **Desktop First**: Menulis gaya untuk tampilan desktop terlebih dahulu, kemudian menambahkan aturan pengecualian untuk layar yang lebih kecil menggunakan `max-width`.
- **Mobile First**: Menulis gaya untuk tampilan mobile terlebih dahulu, kemudian menambahkan aturan tambahan untuk layar yang lebih besar menggunakan `min-width`.

Pendekatan **Mobile First** adalah standar industri yang direkomendasikan saat ini, dengan alasan sebagai berikut:

1. **Data penggunaan:** Mayoritas pengunjung web saat ini mengakses melalui perangkat mobile. Dengan mendahulukan mobile, kita memastikan pengalaman terbaik bagi sebagian besar pengguna.
2. **Performa:** Perangkat mobile umumnya memiliki kemampuan prosesor dan koneksi yang lebih terbatas. CSS default yang ringan (tanpa perhitungan media query) akan dimuat lebih cepat di ponsel.
3. **Prioritas konten:** Mendesain untuk layar kecil terlebih dahulu memaksa kita untuk hanya menampilkan konten yang benar-benar penting, sehingga menghasilkan desain yang lebih bersih dan terfokus.

**Alur penulisan CSS dengan Mobile First:**

```
1. Tulis CSS dasar → untuk tampilan ponsel (layar terkecil)
2. Tambahkan @media (min-width: 600px) → penyesuaian untuk tablet
3. Tambahkan @media (min-width: 992px) → penyesuaian untuk laptop/desktop
4. Tambahkan @media (min-width: 1200px) → penyesuaian untuk layar lebar
```

---

### 4. Media Queries (`@media`)

Media Query adalah mekanisme CSS yang memungkinkan kita menulis aturan gaya yang hanya akan diterapkan ketika kondisi tertentu terpenuhi — dalam hal ini, ketika lebar layar berada dalam rentang yang didefinisikan.

**Sintaks Dasar:**

```css
@media screen and (kondisi) {
  /* Aturan CSS yang hanya berlaku saat kondisi terpenuhi */
}
```

**Contoh — Mobile First (menggunakan `min-width`):**

```css
/* CSS dasar: untuk ponsel */
.wadah-artikel {
  display: flex;
  flex-direction: column; /* Satu kolom vertikal */
}

/* Untuk layar tablet ke atas (min lebar 768px) */
@media screen and (min-width: 768px) {
  .wadah-artikel {
    flex-direction: row; /* Beralih ke tata letak horizontal */
  }
}

/* Untuk layar desktop ke atas (min lebar 992px) */
@media screen and (min-width: 992px) {
  .wadah-artikel {
    max-width: 1200px;
    margin: 0 auto; /* Konten dibatasi lebarnya dan dicentrasi */
  }
}
```

**Contoh — Desktop First (menggunakan `max-width`):**

```css
/* CSS dasar: untuk desktop */
.wadah-artikel {
  display: flex;
  flex-direction: row; /* Tiga kolom horizontal */
}

/* Untuk layar tablet ke bawah (maks lebar 768px) */
@media screen and (max-width: 768px) {
  .wadah-artikel {
    flex-direction: column; /* Beralih ke satu kolom vertikal */
  }

  h1 {
    font-size: 22px; /* Ukuran judul diperkecil */
  }

  .wadah-artikel {
    width: 100%; /* Lebar penuh layar */
  }
}
```

> **Catatan:** Pada pendekatan Mobile First, gunakan `min-width` (kondisi "mulai dari lebar ini ke atas"). Pada pendekatan Desktop First, gunakan `max-width` (kondisi "mulai dari lebar ini ke bawah").

---

### 5. Breakpoint — Titik Perubahan Tata Letak

**Breakpoint** adalah nilai lebar layar tertentu di mana tata letak halaman akan berubah. Berikut adalah nilai breakpoint yang umum digunakan sebagai referensi, mengacu pada konvensi framework CSS seperti Bootstrap dan Tailwind CSS:

| Breakpoint | Lebar | Target Perangkat |
|---|---|---|
| Extra Small | `< 576px` | Ponsel kecil (portrait) |
| Small | `≥ 576px` | Ponsel besar / ponsel landscape |
| Medium | `≥ 768px` | Tablet (portrait) |
| Large | `≥ 992px` | Laptop / desktop kecil |
| Extra Large | `≥ 1200px` | Desktop / monitor lebar |
| XXL | `≥ 1400px` | Monitor sangat lebar / TV |

> **Catatan:** Nilai breakpoint di atas adalah panduan umum, bukan aturan mutlak. Dalam praktiknya, breakpoint sebaiknya ditentukan berdasarkan titik di mana desain spesifik kamu mulai terlihat kurang optimal, bukan sekadar mengikuti nilai standar.

---

### 6. Contoh Lengkap — Halaman Responsif dari Awal

Berikut adalah contoh implementasi lengkap halaman responsif menggunakan pendekatan Mobile First:

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Blog Responsif</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header class="header">
    <div class="logo">BlogKu</div>
    <nav class="navigasi">
      <a href="#">Beranda</a>
      <a href="#">Artikel</a>
      <a href="#">Tentang</a>
      <a href="#">Kontak</a>
    </nav>
  </header>

  <main class="wadah-konten">
    <section class="daftar-artikel">
      <article class="kartu-artikel">
        <h2>Judul Artikel Pertama</h2>
        <p>Ringkasan isi artikel pertama yang cukup menarik untuk dibaca...</p>
      </article>
      <article class="kartu-artikel">
        <h2>Judul Artikel Kedua</h2>
        <p>Ringkasan isi artikel kedua yang tidak kalah menariknya...</p>
      </article>
      <article class="kartu-artikel">
        <h2>Judul Artikel Ketiga</h2>
        <p>Ringkasan isi artikel ketiga sebagai penutup daftar...</p>
      </article>
    </section>
  </main>

  <footer class="footer">
    <p>© 2026 BlogKu. Hak cipta dilindungi.</p>
  </footer>

</body>
</html>
```

```css
/* ============================================
   style.css — Mobile First
   ============================================ */

/* --- Reset dan Dasar --- */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
  font-size: 1rem;
  color: #333;
  line-height: 1.6;
}

/* --- Header --- */
.header {
  background-color: #2c3e50;
  color: white;
  padding: 16px 24px;
  display: flex;
  flex-direction: column; /* Mobile: logo dan nav bertumpuk */
  gap: 12px;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.navigasi {
  display: flex;
  flex-direction: column; /* Mobile: link navigasi bertumpuk */
  gap: 8px;
}

.navigasi a {
  color: white;
  text-decoration: none;
  padding: 6px 0;
}

/* --- Konten Utama --- */
.wadah-konten {
  padding: 24px 16px;
}

.daftar-artikel {
  display: flex;
  flex-direction: column; /* Mobile: satu kolom vertikal */
  gap: 16px;
}

.kartu-artikel {
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #fafafa;
}

.kartu-artikel h2 {
  font-size: 1.25rem;
  margin-bottom: 8px;
}

/* --- Footer --- */
.footer {
  background-color: #34495e;
  color: white;
  text-align: center;
  padding: 16px;
  font-size: 0.875rem;
}


/* ============================================
   Breakpoint: Tablet ke atas (≥ 768px)
   ============================================ */
@media screen and (min-width: 768px) {

  /* Header: logo dan navigasi berdampingan */
  .header {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  /* Navigasi: link berjajar horizontal */
  .navigasi {
    flex-direction: row;
    gap: 16px;
  }

  /* Artikel: dua kolom */
  .daftar-artikel {
    flex-direction: row;
    flex-wrap: wrap;
  }

  .kartu-artikel {
    flex: 1 1 calc(50% - 8px); /* Dua kolom dengan jarak */
  }

}


/* ============================================
   Breakpoint: Desktop ke atas (≥ 992px)
   ============================================ */
@media screen and (min-width: 992px) {

  /* Konten dibatasi lebar maksimumnya dan dicentrasi */
  .wadah-konten {
    max-width: 1100px;
    margin: 0 auto;
    padding: 40px 24px;
  }

  /* Artikel: tiga kolom */
  .kartu-artikel {
    flex: 1 1 calc(33.333% - 11px); /* Tiga kolom dengan jarak */
  }

}
```

---

### 7. Properti CSS yang Mendukung Responsivitas

Selain Media Queries, terdapat beberapa teknik dan properti CSS lain yang secara alami mendukung tampilan responsif:

- **`max-width`**: Membatasi lebar maksimum sebuah elemen agar tidak terlalu lebar di layar besar, sementara tetap fleksibel di layar kecil.
- **`min-width`**: Menentukan lebar minimum sehingga elemen tidak terlalu menyusut.
- **Satuan `%`, `vw`, `rem`**: Satuan relatif yang telah dibahas di Bab 32 secara inheren bersifat responsif.
- **`flex-wrap`** pada Flexbox: Memungkinkan elemen berpindah ke baris baru secara otomatis.
- **`repeat(auto-fit, minmax())`** pada Grid: Membuat kolom grid menyesuaikan jumlahnya secara otomatis berdasarkan ruang yang tersedia.

**Contoh — Gambar Responsif:**

```css
/* Gambar tidak akan pernah melebihi lebar kontainernya */
img {
  max-width: 100%;
  height: auto; /* Tinggi menyesuaikan secara proporsional */
  display: block;
}
```

**Contoh — Kontainer Konten yang Terpusat:**

```css
/* Pola umum untuk membatasi lebar konten di layar besar */
.container {
  width: 100%;           /* Mengisi penuh di layar kecil */
  max-width: 1200px;     /* Tidak melebihi 1200px di layar lebar */
  margin: 0 auto;        /* Otomatis terpusat secara horizontal */
  padding: 0 16px;       /* Jarak dari pinggir layar di mobile */
}
```

---

### Kesimpulan

Responsive Web Design bukan sekadar fitur tambahan, melainkan **standar minimum** dalam pengembangan web modern. Setiap halaman web yang dibangun harus dapat berfungsi dan terlihat baik di seluruh ukuran layar — dari ponsel kecil hingga monitor lebar.

Dengan menguasai tiga komponen utama berikut, kamu telah memiliki fondasi yang kuat untuk membangun tampilan web yang responsif:

1. **Meta Viewport** — Memastikan browser mobile menggunakan lebar layar sebenarnya.
2. **Mobile First CSS** — Menulis gaya dasar untuk mobile, lalu menambahkan penyesuaian untuk layar yang lebih besar.
3. **Media Queries** — Mendefinisikan titik-titik perubahan tata letak berdasarkan lebar layar.

Selamat! Kamu telah menyelesaikan seluruh modul CSS — mulai dari selektor dasar, model kotak, tipografi, Flexbox, Grid, hingga Responsive Design. Pemahaman ini adalah fondasi penting yang akan kamu gunakan terus dalam perjalanan pengembangan web berikutnya.

**Ringkasan Breakpoint Umum (Mobile First):**

| Breakpoint | `min-width` | Target |
|---|---|---|
| Mobile (default) | — | Ponsel (tidak perlu `@media`) |
| Small | `576px` | Ponsel besar / landscape |
| Medium | `768px` | Tablet |
| Large | `992px` | Laptop / desktop kecil |
| Extra Large | `1200px` | Desktop / monitor lebar |
| XXL | `1400px` | Monitor sangat lebar |
