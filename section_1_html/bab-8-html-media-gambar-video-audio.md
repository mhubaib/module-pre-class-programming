# Bab 8: HTML Media (Gambar, Video, Audio)

## Tujuan Pembelajaran

- Memahami cara menyisipkan konten multimedia ke dalam halaman HTML.
- Menguasai penggunaan tag `<img>` beserta atribut `src` dan `alt`.
- Menerapkan tag `<audio>` dan `<video>` yang diperkenalkan oleh HTML5.
- Menggunakan atribut kontrol media seperti `controls`, `autoplay`, `muted`, `loop`, dan `poster`.

---

## Materi Utama

Halaman web yang hanya berisi teks akan terlihat kering dan sulit menarik perhatian pengguna. Web modern memanfaatkan multimedia — gambar, audio, dan video — untuk menyampaikan informasi secara lebih efektif dan menarik. Bab ini membahas cara menyisipkan ketiga jenis konten tersebut langsung ke dalam halaman HTML.

---

### 1. Menampilkan Gambar (`<img>`)

Tag `<img>` digunakan untuk menampilkan file gambar di dalam halaman HTML. Berbeda dengan sebagian besar tag HTML, `<img>` merupakan **tag tunggal** (_self-closing tag_) — tidak memiliki tag penutup dan tidak dapat membungkus konten teks.

Dua atribut yang wajib disertakan pada setiap tag `<img>` adalah:

- **`src` (Source)**: Menentukan alamat atau jalur (_path_) file gambar yang akan ditampilkan.
- **`alt` (Alternative Text)**: Menyediakan deskripsi teks dari gambar. Teks ini ditampilkan jika gambar gagal dimuat, dan dibacakan oleh aplikasi pembaca layar (_screen reader_) untuk pengguna dengan keterbatasan penglihatan. Atribut ini juga dibaca oleh mesin pencari.

**Sintaks dasar:**

```html
<img src="alamat-gambar.jpg" alt="Deskripsi gambar" />
```

**Contoh penggunaan — absolute path dan relative path:**

```html
<!-- HTML -->

<!-- Mengambil gambar dari internet (absolute path) -->
<img
  src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/PNG_Test.png/280px-PNG_Test.png"
  alt="Contoh gambar dari Wikipedia"
/>

<!-- Mengambil gambar dari folder yang sama (relative path) -->
<img src="foto-produk.jpg" alt="Foto produk sepatu olahraga warna merah" />

<!-- Mengambil gambar dari subfolder -->
<img src="aset/gambar/logo.png" alt="Logo perusahaan" />
```

**Mengatur ukuran gambar:**
Atribut `width` dan `height` dapat digunakan untuk menentukan dimensi gambar dalam piksel. Jika hanya salah satu yang ditentukan, browser akan menyesuaikan dimensi yang lain secara proporsional.

```html
<!-- HTML -->
<img src="logo.png" alt="Logo Perusahaan" width="200" height="200" />

<!-- Hanya lebar yang ditentukan — tinggi menyesuaikan secara proporsional -->
<img src="banner.jpg" alt="Banner utama halaman" width="800" />
```

> **Catatan:** Untuk pengaturan ukuran yang lebih fleksibel dan responsif, disarankan menggunakan CSS (`width` dan `height`) daripada atribut HTML. Atribut HTML untuk ukuran berguna sebagai cadangan atau untuk mencegah pergeseran tata letak (_layout shift_) saat halaman sedang dimuat.

**Contoh penerapan dalam konten artikel:**

```html
<!-- HTML -->
<article>
  <h2>Mengenal Komodo, Kadal Terbesar di Dunia</h2>

  <img
    src="komodo.jpg"
    alt="Seekor komodo berjalan di Taman Nasional Komodo, Nusa Tenggara Timur"
    width="700"
  />

  <p>
    Komodo (<i>Varanus komodoensis</i>) adalah spesies kadal terbesar yang masih
    hidup di dunia. Hewan endemik Indonesia ini dapat ditemukan di Pulau Komodo,
    Rinca, Flores, dan beberapa pulau kecil di sekitarnya.
  </p>
</article>
```

---

### 2. Memutar Audio (`<audio>`)

Sebelum era HTML5, menyisipkan audio di halaman web memerlukan plugin pihak ketiga seperti Adobe Flash Player. HTML5 memperkenalkan tag `<audio>` yang memungkinkan pemutaran audio langsung di browser tanpa plugin tambahan. Format file yang paling umum didukung adalah `.mp3` dan `.ogg`.

Untuk menampilkan antarmuka pemutar audio (tombol play, pause, pengatur volume, dan durasi), atribut `controls` harus disertakan. Tanpa atribut ini, audio tidak dapat dioperasikan oleh pengguna.

**Sintaks dasar:**

```html
<audio controls>
  <source src="nama-file.mp3" type="audio/mpeg" />
</audio>
```

**Penggunaan beberapa `<source>`:**
Tidak semua browser mendukung format audio yang sama. Dengan menyediakan beberapa format menggunakan tag `<source>`, browser akan mencoba memuat file pertama, dan jika gagal, akan mencoba file berikutnya. Teks di luar tag `<source>` akan ditampilkan jika browser tidak mendukung tag `<audio>` sama sekali.

```html
<!-- HTML -->
<audio controls>
  <source src="lagu-santai.mp3" type="audio/mpeg" />
  <source src="lagu-santai.ogg" type="audio/ogg" />
  Browser Anda tidak mendukung pemutaran audio HTML5.
</audio>
```

**Contoh penerapan dalam halaman podcast:**

```html
<!-- HTML -->
<section>
  <h2>Episode 12: Pengantar Pemrograman Web</h2>
  <p>Durasi: 42 menit | Diterbitkan: 5 Juni 2025</p>

  <audio controls>
    <source src="podcast/episode-12.mp3" type="audio/mpeg" />
    <source src="podcast/episode-12.ogg" type="audio/ogg" />
    Browser Anda tidak mendukung pemutaran audio HTML5. Silakan
    <a href="podcast/episode-12.mp3">unduh file audio</a> secara langsung.
  </audio>

  <p>
    Dalam episode ini, kami membahas dasar-dasar pengembangan web dan langkah
    pertama yang perlu diambil oleh pemula.
  </p>
</section>
```

---

### 3. Menampilkan Video (`<video>`)

Tag `<video>` bekerja dengan konsep yang sama seperti `<audio>`, namun menampilkan konten visual dan audio sekaligus. Format yang paling umum dan didukung secara luas oleh browser modern adalah `.mp4`. Format alternatif yang juga sering digunakan adalah `.webm`.

Atribut `width` dan `height` dapat digunakan untuk menentukan dimensi pemutar video, dan atribut `controls` wajib disertakan agar pengguna dapat mengoperasikan pemutaran.

```html
<!-- HTML -->
<video width="640" height="360" controls>
  <source src="video-penjelasan.mp4" type="video/mp4" />
  <source src="video-penjelasan.webm" type="video/webm" />
  Browser Anda tidak mendukung pemutaran video HTML5.
</video>
```

**Contoh penerapan dalam halaman kursus online:**

```html
<!-- HTML -->
<section>
  <h2>Materi 3: Cara Kerja CSS Box Model</h2>

  <video width="800" controls poster="thumbnail/materi-3.jpg">
    <source src="video/materi-3-box-model.mp4" type="video/mp4" />
    <source src="video/materi-3-box-model.webm" type="video/webm" />
    Browser Anda tidak mendukung pemutaran video HTML5. Silakan
    <a href="video/materi-3-box-model.mp4">unduh video</a> untuk ditonton secara
    lokal.
  </video>

  <p>
    Video ini menjelaskan konsep Box Model dalam CSS, termasuk padding, border,
    margin, dan cara menghitung lebar total sebuah elemen.
  </p>
</section>
```

---

### 4. Atribut Tambahan untuk `<audio>` dan `<video>`

Selain `controls`, terdapat beberapa atribut tambahan yang dapat diterapkan pada tag `<audio>` maupun `<video>` untuk mengatur perilaku pemutaran:

| Atribut    | Berlaku Pada  | Fungsi                                                                       |
| ---------- | ------------- | ---------------------------------------------------------------------------- |
| `autoplay` | Audio & Video | Media diputar secara otomatis saat halaman selesai dimuat                    |
| `muted`    | Audio & Video | Media diputar dalam kondisi dimatikan suaranya (volume 0)                    |
| `loop`     | Audio & Video | Media diputar berulang secara terus-menerus setelah selesai                  |
| `poster`   | Video saja    | Menentukan gambar yang ditampilkan sebelum video diputar (seperti thumbnail) |

> **Catatan penting mengenai `autoplay`:** Browser modern seperti Chrome dan Firefox secara bawaan akan memblokir pemutaran otomatis media yang memiliki suara. Untuk menggunakan `autoplay` secara efektif, kombinasikan dengan atribut `muted`. Pemutaran otomatis dengan suara umumnya hanya diizinkan jika pengguna sebelumnya telah berinteraksi dengan halaman tersebut.

**Contoh — Video latar yang diputar otomatis (seperti pada halaman utama website):**

```html
<!-- HTML -->

<!-- Video latar: autoplay, tanpa suara, berulang, tanpa kontrol -->
<video src="video/latar-halaman-utama.mp4" autoplay muted loop width="100%">
  Browser Anda tidak mendukung pemutaran video HTML5.
</video>
```

**Contoh — Perbandingan penggunaan berbagai atribut:**

```html
<!-- HTML -->

<!-- Video dengan kontrol lengkap dan thumbnail -->
<h3>Video dengan Kontrol</h3>
<video width="640" controls poster="thumbnail/intro.jpg">
  <source src="video/intro.mp4" type="video/mp4" />
</video>

<!-- Audio yang diputar otomatis dan berulang (cocok untuk musik latar) -->
<h3>Musik Latar (diputar otomatis, berulang, tanpa suara)</h3>
<audio autoplay muted loop>
  <source src="audio/musik-latar.mp3" type="audio/mpeg" />
</audio>

<!-- Video yang diputar otomatis, berulang, dengan thumbnail -->
<h3>Video Promo (diputar otomatis, berulang)</h3>
<video autoplay muted loop poster="thumbnail/promo.jpg" width="100%">
  <source src="video/promo.mp4" type="video/mp4" />
</video>
```

---

### Kesimpulan

Tag `<img>`, `<audio>`, dan `<video>` memungkinkan konten multimedia disajikan langsung di dalam halaman HTML tanpa memerlukan plugin atau teknologi pihak ketiga. Kunci penggunaan yang baik adalah selalu menyertakan atribut `alt` pada gambar untuk keperluan aksesibilitas, menyediakan beberapa format file sebagai alternatif untuk kompatibilitas lintas browser, dan memahami kapan penggunaan `autoplay` sesuai dengan konteks halaman.

**Ringkasan Elemen:**

| Tag        | Jenis Tag   | Fungsi                                               |
| ---------- | ----------- | ---------------------------------------------------- |
| `<img>`    | Tunggal     | Menampilkan gambar                                   |
| `<audio>`  | Berpasangan | Memutar file audio                                   |
| `<video>`  | Berpasangan | Menampilkan dan memutar file video                   |
| `<source>` | Tunggal     | Menyediakan sumber file alternatif untuk audio/video |

**Ringkasan Atribut:**

| Atribut    | Digunakan Pada       | Fungsi                                            |
| ---------- | -------------------- | ------------------------------------------------- |
| `src`      | `<img>`              | Menentukan alamat file gambar                     |
| `alt`      | `<img>`              | Teks alternatif jika gambar gagal dimuat          |
| `width`    | `<img>`, `<video>`   | Menentukan lebar elemen dalam piksel              |
| `height`   | `<img>`, `<video>`   | Menentukan tinggi elemen dalam piksel             |
| `controls` | `<audio>`, `<video>` | Menampilkan antarmuka kontrol pemutaran media     |
| `autoplay` | `<audio>`, `<video>` | Memutar media secara otomatis saat halaman dimuat |
| `muted`    | `<audio>`, `<video>` | Menonaktifkan suara saat media diputar            |
| `loop`     | `<audio>`, `<video>` | Mengulang pemutaran media secara terus-menerus    |
| `poster`   | `<video>`            | Menentukan gambar thumbnail sebelum video diputar |

**Panduan Pemilihan Atribut Media:**

| Kebutuhan                                       | Atribut yang Digunakan                        |
| ----------------------------------------------- | --------------------------------------------- |
| Menampilkan kontrol play/pause/volume           | `controls`                                    |
| Video latar yang diputar otomatis tanpa suara   | `autoplay muted loop`                         |
| Menampilkan gambar sebelum video diputar        | `poster="path/thumbnail.jpg"`                 |
| Kompatibilitas lintas browser untuk audio/video | Beberapa tag `<source>` dengan format berbeda |
| Gambar yang dapat diakses oleh screen reader    | `alt="deskripsi gambar"`                      |
