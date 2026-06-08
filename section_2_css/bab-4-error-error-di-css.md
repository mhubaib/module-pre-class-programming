# Bab 4: Error dan Debugging di CSS

## Tujuan Pembelajaran

- Mengenali kesalahan umum yang sering terjadi saat menulis CSS.
- Mampu melakukan debugging menggunakan Browser Developer Tools.
- Memahami konsep _Cascading_ (urutan aturan) dan _Specificity_ (kekuatan selektor).

---

## Materi Utama

Menulis CSS terkadang menghasilkan situasi yang membingungkan — kode sudah ditulis dengan benar, tetapi tampilan tidak berubah. Ini adalah pengalaman yang umum dialami oleh semua pengembang web, tidak terkecuali yang sudah berpengalaman sekalipun.

Bab ini membahas penyebab-penyebab paling umum dari masalah CSS dan cara mendiagnosisnya secara sistematis.

---

### 1. Kesalahan Penulisan (Syntax Error)

Ini adalah penyebab paling umum dari CSS yang tidak berfungsi. Browser tidak menampilkan pesan error seperti JavaScript — ia hanya diam-diam mengabaikan aturan yang tidak valid.

#### A. Lupa Titik Koma (`;`)

Jika sebuah deklarasi tidak diakhiri titik koma, browser dapat salah menginterpretasikan aturan berikutnya sebagai bagian dari aturan yang sama, sehingga keduanya diabaikan.

```css
/* Bermasalah — titik koma hilang di baris pertama */
p {
  color: red      /* tidak ada ; */
  font-size: 16px;
}

/* Benar */
p {
  color: red;
  font-size: 16px;
}
```

#### B. Salah Ketik Nama Properti atau Nilai

Browser tidak mengenali nama properti yang salah eja dan akan mengabaikannya tanpa peringatan.

```css
/* Salah — properti tidak dikenali browser */
p {
  collor: red; /* seharusnya "color" */
  font-wight: bold; /* seharusnya "font-weight" */
  backgrond: yellow; /* seharusnya "background" */
}

/* Benar */
p {
  color: red;
  font-weight: bold;
  background: yellow;
}
```

#### C. Lupa Simbol Selektor

```css
/* Bermasalah — titik hilang untuk class selector */
teks-penting {
  /* menargetkan tag <teks-penting> yang tidak ada */
  color: red;
}

/* Benar */
.teks-penting {
  /* menargetkan elemen dengan class="teks-penting" */
  color: red;
}
```

---

### 2. Masalah Jalur File (Path Error)

Jika menggunakan External CSS, pastikan atribut `href` pada tag `<link>` menunjuk ke lokasi file yang benar.

```html
<!-- Struktur folder -->
<!--
proyek/
├── index.html
└── css/
    └── style.css
-->

<!-- Salah — file style.css ada di dalam folder css/ -->
<link rel="stylesheet" href="style.css" />

<!-- Benar -->
<link rel="stylesheet" href="css/style.css" />
```

**Hal yang perlu diperiksa:**

- Nama file bersifat case-sensitive di sebagian sistem operasi: `Style.css` berbeda dengan `style.css`.
- Ekstensi file harus lengkap: `style` saja tidak cukup, harus `style.css`.
- Jika file HTML dipindahkan ke folder lain, jalur relatif perlu disesuaikan.

---

### 3. Konsep Cascading — Aturan yang Ditulis Terakhir Menang

Kata "Cascading" dalam CSS merujuk pada cara browser menangani konflik antara beberapa aturan yang menargetkan elemen yang sama. Ketika dua aturan memiliki tingkat kekuatan yang sama, aturan yang ditulis **paling akhir** dalam file CSS yang akan diterapkan.

```css
p {
  color: red;
}

/* Aturan ini ditulis belakangan dan akan menimpa yang di atas */
p {
  color: blue;
}

/* Hasil akhir: semua <p> berwarna biru */
```

**Contoh cascading dengan beberapa file:**

```html
<head>
  <link rel="stylesheet" href="reset.css" />
  <!-- Dimuat pertama -->
  <link rel="stylesheet" href="style.css" />
  <!-- Dimuat kedua, menang jika ada konflik -->
</head>
```

Urutan pemuatan file juga berpengaruh — aturan dari file yang dimuat belakangan dapat menimpa aturan dari file yang dimuat lebih awal.

---

### 4. Specificity — Tingkat Kekuatan Selektor

Selain urutan penulisan, browser juga mempertimbangkan **seberapa spesifik** sebuah selektor dalam menentukan aturan mana yang diterapkan. Selektor yang lebih spesifik selalu menang, terlepas dari urutan penulisannya.

**Tingkatan kekuatan selektor (dari tertinggi ke terendah):**

| Tingkat       | Selektor         | Contoh               |
| ------------- | ---------------- | -------------------- |
| 4 (tertinggi) | Inline style     | `style="color: red"` |
| 3             | ID Selector      | `#header`            |
| 2             | Class Selector   | `.tombol`            |
| 1 (terendah)  | Element Selector | `p`, `h1`            |

```css
#teks-biru {
  color: blue; /* ID — kekuatan tertinggi */
}

.teks-biru {
  color: green; /* Class — kekuatan menengah */
}

p {
  color: red; /* Element — kekuatan terendah */
}
```

```html
<p id="teks-biru" class="teks-biru">Teks ini berwarna apa?</p>
```

Meskipun aturan `color: red` ditulis paling akhir, teks tetap akan berwarna **biru** karena ID Selector memiliki kekuatan yang jauh lebih tinggi dari Element Selector.

**Visualisasi perhitungan specificity:**

```
Selektor              | Inline | ID | Class | Element | Total
----------------------|--------|----|----- -|---------|-------
p                     |   0    |  0 |   0   |    1    |  0,0,0,1
.tombol               |   0    |  0 |   1   |    0    |  0,0,1,0
#header               |   0    |  1 |   0   |    0    |  0,1,0,0
#header .tombol       |   0    |  1 |   1   |    0    |  0,1,1,0
style="..."           |   1    |  0 |   0   |    0    |  1,0,0,0
```

Semakin besar angkanya (dibaca dari kiri), semakin kuat selektor tersebut.

> **Panduan praktis:** Hindari menggunakan `!important` untuk memaksa sebuah aturan menang atas segalanya. Meskipun secara teknis berfungsi, penggunaannya yang berlebihan membuat CSS sangat sulit dipelihara karena memutus rantai specificity yang seharusnya terstruktur.

---

### 5. Debugging dengan Browser Developer Tools

Ketika CSS tidak berfungsi seperti yang diharapkan, langkah paling efektif adalah menggunakan **Browser Developer Tools** (tersedia di semua browser modern).

**Cara membukanya:**

- Klik kanan pada elemen yang bermasalah → pilih **Inspect**
- Atau tekan `F12` / `Ctrl+Shift+I` (Windows) / `Cmd+Option+I` (Mac)

**Apa yang dapat dilihat di panel Styles:**

```
Panel Styles menampilkan:

✓ color: blue;                    ← Aturan yang sedang diterapkan
✗ color: red;                     ← Aturan yang kalah (dicoret)
  (from p selector — specificity: 0,0,0,1)
```

- **Tanda centang**: Aturan aktif dan diterapkan.
- **Teks dicoret**: Aturan kalah karena ditimpa oleh aturan lain yang lebih spesifik atau ditulis lebih akhir.
- **Tanda peringatan**: Nama properti atau nilai tidak valid (salah eja).

**Langkah debugging yang disarankan:**

1. Buka Developer Tools dan pilih tab **Elements**.
2. Klik elemen yang bermasalah di panel HTML.
3. Lihat panel **Styles** di sebelah kanan — periksa apakah aturan CSS kamu muncul.
4. Jika aturan dicoret, lacak selektor mana yang menimpanya.
5. Kamu dapat mengedit nilai properti langsung di Developer Tools untuk mencoba perubahan sebelum memperbaikinya di file CSS.

> **Catatan:** Perubahan yang dilakukan di Developer Tools bersifat sementara dan akan hilang saat halaman di-refresh. Selalu salin perubahan tersebut ke file CSS aslimu.

---

### Kesimpulan

Sebagian besar masalah CSS dapat ditelusuri dengan memeriksa tiga hal: apakah ada kesalahan penulisan, apakah ada konflik urutan aturan (cascading), atau apakah ada aturan lain dengan specificity lebih tinggi yang menimpa aturan kita. Developer Tools adalah alat yang paling efektif untuk mendiagnosis ketiga hal tersebut secara langsung.

**Ringkasan:**

| Masalah                | Penyebab Umum              | Cara Mengatasi                              |
| ---------------------- | -------------------------- | ------------------------------------------- |
| Gaya tidak diterapkan  | Salah eja properti/nilai   | Periksa ejaan di Developer Tools            |
| Gaya diabaikan         | Lupa titik koma            | Tambahkan `;` di akhir setiap deklarasi     |
| CSS tidak dimuat       | Jalur file salah           | Periksa atribut `href` pada tag `<link>`    |
| Aturan ditimpa         | Cascading atau specificity | Periksa aturan yang dicoret di panel Styles |
| Gaya tidak bisa diubah | Specificity rendah         | Gunakan selektor yang lebih spesifik        |
