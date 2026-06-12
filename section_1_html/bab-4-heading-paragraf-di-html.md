# Bab 4: Heading & Paragraf di HTML

## Tujuan Pembelajaran

- Memahami konsep hierarki judul (_heading_) dari tingkat 1 hingga 6.
- Menerapkan elemen paragraf dengan cara yang tepat.
- Mengontrol tampilan teks menggunakan elemen pemisah baris (`<br>`) dan garis horizontal (`<hr>`).
- Memahami aturan penggunaan heading yang baik dalam konteks struktur dokumen dan SEO.

---

## Materi Utama

Setelah memahami kerangka dasar HTML pada bab-bab sebelumnya, kini saatnya mengisi bagian `<body>` dengan konten. Dua elemen teks yang paling mendasar dalam sebuah halaman web adalah **Heading** (judul) dan **Paragraf**.

---

### 1. Heading (Judul Bersusun)

**Heading** adalah elemen HTML yang digunakan untuk menandai judul dan subjudul dalam sebuah halaman. HTML menyediakan enam tingkatan heading, dari `<h1>` hingga `<h6>`, di mana `<h1>` merupakan tingkat tertinggi dengan ukuran teks terbesar, dan `<h6>` merupakan tingkat terendah dengan ukuran teks terkecil.

| Tag    | Tingkat | Fungsi Umum                             |
| ------ | ------- | --------------------------------------- |
| `<h1>` | 1       | Judul utama halaman                     |
| `<h2>` | 2       | Judul bagian utama                      |
| `<h3>` | 3       | Subjudul di bawah `<h2>`                |
| `<h4>` | 4       | Subjudul di bawah `<h3>`                |
| `<h5>` | 5       | Jarang digunakan; judul minor           |
| `<h6>` | 6       | Tingkat paling rendah; jarang digunakan |

**Analogi — Struktur Buku:**
Hierarki heading dalam HTML mirip dengan susunan judul dalam sebuah buku:

- `<h1>` adalah judul buku yang tercetak di sampul — hanya ada satu dalam seluruh buku.
- `<h2>` adalah judul setiap bab.
- `<h3>` adalah judul sub-bab di dalam setiap bab.
- `<h4>` hingga `<h6>` adalah tingkatan lebih dalam, digunakan untuk bagian yang lebih spesifik.

**Aturan Penggunaan `<h1>`:**
Setiap halaman web sangat disarankan hanya memiliki **satu tag `<h1>`**. Hal ini penting karena:

- Mesin pencari (seperti Google) membaca `<h1>` sebagai penanda topik utama halaman.
- Lebih dari satu `<h1>` dapat membingungkan mesin pencari dan menurunkan kualitas SEO (_Search Engine Optimization_) halaman tersebut.

**Contoh penggunaan heading:**

```html
<!-- HTML -->
<h1>Biografi Penemu Komputer</h1>

<h2>Masa Kecil</h2>
<h3>Lahir di London</h3>
<h3>Pendidikan Awal</h3>

<h2>Masa Dewasa</h2>
<h3>Karier dan Pencapaian</h3>
<h4>Penghargaan Internasional</h4>

<h2>Warisan dan Pengaruh</h2>
<h6>Catatan: Sumber referensi tercantum di bagian akhir halaman.</h6>
```

Pada contoh di atas, struktur heading membentuk hierarki yang jelas: satu judul utama (`<h1>`), diikuti beberapa bagian utama (`<h2>`), dengan subjudul di bawah masing-masing bagian (`<h3>` dan `<h4>`).

> **Catatan:** Heading sebaiknya digunakan untuk menyatakan **struktur konten**, bukan sekadar untuk memperbesar atau mempertebal teks. Jika tujuannya hanya mengubah ukuran teks, gunakan CSS.

---

### 2. Paragraf (`<p>`)

Elemen `<p>` digunakan untuk menandai blok teks sebagai sebuah paragraf. Browser secara otomatis menambahkan jarak (_margin_) di atas dan di bawah setiap elemen `<p>`, sehingga antar paragraf memiliki jarak yang terlihat secara visual tanpa perlu konfigurasi tambahan.

```html
<!-- HTML -->
<p>
  Ini adalah paragraf pertama. Browser akan menambahkan jarak otomatis di bawah
  paragraf ini sebelum menampilkan paragraf berikutnya.
</p>
<p>
  Ini adalah paragraf kedua. Perhatikan bahwa terdapat jarak kosong antara
  paragraf pertama dan paragraf ini.
</p>
```

**Perilaku penting yang perlu diketahui:**
Browser mengabaikan spasi berlebih dan baris baru (_enter_) yang ditulis di dalam kode HTML. Seluruh spasi dan baris baru tersebut akan diperlakukan sebagai satu spasi tunggal. Artinya, memformat teks dengan cara menekan Enter berkali-kali di dalam editor tidak akan berdampak pada tampilan di browser.

```html
<!-- HTML: Tiga baris Enter di sini tidak berpengaruh pada tampilan -->
<p>
  Baris pertama teks. Baris ini ditulis setelah tiga baris kosong di editor,
  namun di browser akan menyambung langsung tanpa jarak.
</p>
```

**Contoh penerapan paragraf pada konten artikel:**

```html
<!-- HTML -->
<h1>Sejarah Internet</h1>

<h2>Awal Mula</h2>
<p>
  Internet bermula dari proyek penelitian militer Amerika Serikat pada tahun
  1960-an yang dikenal dengan nama ARPANET. Proyek ini bertujuan menciptakan
  jaringan komunikasi yang tetap berfungsi meskipun sebagian infrastrukturnya
  mengalami kerusakan.
</p>

<h2>Perkembangan Modern</h2>
<p>
  Pada tahun 1991, Tim Berners-Lee memperkenalkan World Wide Web kepada publik,
  yang memungkinkan dokumen saling terhubung melalui tautan (_hyperlink_) dan
  dapat diakses menggunakan browser.
</p>
<p>
  Sejak saat itu, internet berkembang pesat dan menjadi infrastruktur utama
  dalam komunikasi, perdagangan, pendidikan, dan berbagai aspek kehidupan
  modern.
</p>
```

---

### 3. Pemisah Baris (`<br>`) dan Garis Horizontal (`<hr>`)

#### Pemisah Baris: `<br>`

Karena browser mengabaikan baris baru dalam kode HTML, digunakan elemen `<br>` (_Line Break_) untuk memindahkan teks ke baris berikutnya tanpa membuat paragraf baru. `<br>` adalah **tag tunggal** (_self-closing tag_) yang tidak memerlukan tag penutup.

`<br>` paling tepat digunakan untuk konten yang memang memiliki struktur baris, seperti alamat, puisi, atau lirik.

```html
<!-- HTML -->
<p>
  Alamat Pengiriman:<br />
  Jalan Mawar No. 10<br />
  Kelurahan Kebayoran Baru<br />
  Jakarta Selatan, 12160
</p>
```

**Contoh perbandingan — dengan dan tanpa `<br>`:**

```html
<!-- Tanpa <br>: seluruh teks tampil dalam satu baris -->
<p>Nama: Andi Pratama Pekerjaan: Web Developer Kota: Surabaya</p>

<!-- Dengan <br>: setiap informasi tampil di baris terpisah -->
<p>
  Nama: Andi Pratama<br />
  Pekerjaan: Web Developer<br />
  Kota: Surabaya
</p>
```

> **Catatan:** `<br>` sebaiknya tidak digunakan untuk menciptakan jarak antara paragraf atau bagian konten. Untuk keperluan tersebut, gunakan elemen `<p>` yang terpisah atau atur jarak menggunakan CSS dengan properti `margin`.

#### Garis Horizontal: `<hr>`

Elemen `<hr>` (_Horizontal Rule_) digunakan untuk menampilkan garis mendatar yang memisahkan dua bagian konten secara visual. Sama seperti `<br>`, elemen `<hr>` adalah tag tunggal yang tidak memerlukan tag penutup.

```html
<!-- HTML -->
<h2>Sejarah Singkat</h2>
<p>Teks tentang sejarah diletakkan di sini.</p>

<hr />

<h2>Kondisi Saat Ini</h2>
<p>Teks tentang kondisi saat ini diletakkan di bagian bawah garis.</p>
```

**Contoh penerapan lengkap — halaman profil sederhana:**

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Profil Singkat</title>
  </head>
  <body>
    <h1>Profil: Andi Pratama</h1>

    <h2>Informasi Pribadi</h2>
    <p>
      Nama: Andi Pratama<br />
      Usia: 27 tahun<br />
      Kota: Surabaya, Jawa Timur
    </p>

    <hr />

    <h2>Latar Belakang Pendidikan</h2>
    <p>
      Andi menyelesaikan pendidikan sarjana di bidang Teknik Informatika pada
      tahun 2019. Selama masa studi, ia aktif mengikuti berbagai kompetisi
      pemrograman tingkat nasional.
    </p>

    <hr />

    <h2>Pengalaman Kerja</h2>
    <h3>Frontend Developer — PT Teknologi Maju (2020–2022)</h3>
    <p>
      Bertanggung jawab atas pengembangan antarmuka pengguna untuk aplikasi web
      internal perusahaan menggunakan HTML, CSS, dan JavaScript.
    </p>

    <h3>Web Developer — Freelance (2022–Sekarang)</h3>
    <p>
      Menangani berbagai proyek pembuatan website untuk klien dari sektor
      perdagangan, pendidikan, dan layanan profesional.
    </p>
  </body>
</html>
```

---

### Kesimpulan

Heading dan paragraf adalah elemen teks paling dasar yang membentuk konten sebuah halaman web. Heading digunakan untuk menyatakan hierarki informasi, sementara paragraf digunakan untuk menyampaikan isi. Elemen `<br>` dan `<hr>` melengkapi keduanya dengan memberikan kontrol atas pemisahan baris dan bagian konten.

**Panduan singkat penggunaan:**

- Perlu menampilkan judul atau subjudul? → Gunakan **`<h1>` hingga `<h6>`** sesuai tingkatan hierarki.
- Perlu menampilkan isi konten dalam blok teks? → Gunakan **`<p>`**.
- Perlu memindahkan teks ke baris baru tanpa paragraf baru? → Gunakan **`<br>`**.
- Perlu memisahkan dua bagian konten dengan garis horizontal? → Gunakan **`<hr>`**.

**Ringkasan Elemen:**

| Elemen        | Jenis Tag       | Fungsi                                                  |
| ------------- | --------------- | ------------------------------------------------------- |
| `<h1>`        | Tag berpasangan | Judul utama halaman — disarankan hanya satu per halaman |
| `<h2>`–`<h6>` | Tag berpasangan | Judul tingkatan di bawah `<h1>`                         |
| `<p>`         | Tag berpasangan | Menandai blok teks sebagai paragraf                     |
| `<br>`        | Tag tunggal     | Memindahkan teks ke baris baru                          |
| `<hr>`        | Tag tunggal     | Menampilkan garis horizontal pemisah bagian konten      |

**Panduan Pemilihan Elemen:**

| Kebutuhan                                         | Elemen yang Digunakan                          |
| ------------------------------------------------- | ---------------------------------------------- |
| Judul utama halaman                               | `<h1>` — satu per halaman                      |
| Judul tiap bagian atau topik                      | `<h2>`                                         |
| Subjudul di dalam sebuah bagian                   | `<h3>` hingga `<h6>` sesuai kedalaman hierarki |
| Blok teks isi artikel atau konten                 | `<p>`                                          |
| Teks dengan struktur baris (alamat, data singkat) | `<p>` dengan `<br>` di setiap pemisah baris    |
| Pemisah visual antara dua bagian konten           | `<hr>`                                         |
| Mengubah ukuran teks tanpa makna struktural       | Jangan gunakan heading — gunakan CSS           |
