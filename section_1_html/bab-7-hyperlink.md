# Bab 7: Hyperlink

## Tujuan Pembelajaran

- Memahami konsep dasar Hyperlink sebagai fondasi dari konektivitas World Wide Web.
- Membuat tautan menggunakan tag `<a>` beserta atribut `href`.
- Membedakan penggunaan _Absolute Path_ (URL lengkap) dan _Relative Path_ (URL lokal).
- Menerapkan atribut `target` untuk membuka tautan di tab baru.
- Membuat tautan yang mengarah ke alamat email dan nomor telepon.

---

## Materi Utama

Internet pada dasarnya adalah kumpulan miliaran halaman yang saling terhubung satu sama lain. Kemampuan untuk berpindah dari satu halaman ke halaman lain hanya dengan satu klik adalah fitur yang menjadi inti dari World Wide Web. Fitur tersebut dikenal sebagai **Hyperlink**, atau dalam percakapan sehari-hari sering disebut sebagai _link_ (tautan).

Hyperlink memungkinkan pengguna untuk berpindah ke halaman lain di website yang sama, mengunjungi website eksternal, atau bahkan melompat ke bagian tertentu dalam halaman yang sedang dibaca.

---

### 1. Mengenal Tag Anchor (`<a>`)

Di HTML, Hyperlink dibuat menggunakan tag `<a>` — singkatan dari **Anchor** (jangkar). Tag ini wajib disertai atribut `href` (_Hypertext Reference_) yang berisi alamat tujuan dari tautan tersebut. Tanpa atribut `href`, teks di dalam tag `<a>` hanya ditampilkan seperti teks biasa tanpa fungsi tautan.

**Sintaks dasar:**

```html
<a href="URL_TUJUAN">Teks yang dapat diklik</a>
```

Secara bawaan, browser akan menampilkan tautan dengan warna biru dan garis bawah. Tautan yang sudah pernah dikunjungi umumnya berubah warna menjadi ungu.

**Contoh dasar:**

```html
<!-- HTML -->
<p>
  Silakan kunjungi <a href="https://www.google.com">Google</a> untuk mencari
  informasi lebih lanjut.
</p>
```

**Contoh penerapan dalam navigasi halaman:**

```html
<!-- HTML -->
<nav>
  <a href="index.html">Beranda</a> | <a href="tentang.html">Tentang</a> |
  <a href="portofolio.html">Portofolio</a> |
  <a href="kontak.html">Kontak</a>
</nav>

<h1>Selamat Datang di Website Saya</h1>
<p>
  Temukan informasi lengkap tentang layanan kami di halaman
  <a href="tentang.html">Tentang</a>, atau langsung hubungi kami melalui halaman
  <a href="kontak.html">Kontak</a>.
</p>
```

---

### 2. Absolute Path vs Relative Path

Nilai atribut `href` dapat menggunakan dua jenis format alamat tergantung pada tujuan tautan: alamat lengkap (_absolute path_) atau alamat relatif terhadap lokasi file saat ini (_relative path_).

#### A. Absolute Path (Alamat Lengkap)

Digunakan untuk mengarahkan pengguna ke halaman di luar website yang sedang dikerjakan — misalnya ke website eksternal. Alamat harus ditulis secara lengkap, termasuk protokolnya (`https://` atau `http://`).

```html
<!-- HTML -->
<a href="https://www.youtube.com">Buka YouTube</a>
<a href="https://id.wikipedia.org/wiki/HTML">Sejarah HTML di Wikipedia</a>
```

**Analogi:** Absolute path seperti menulis alamat pengiriman paket secara lengkap — nama jalan, nomor rumah, kelurahan, kecamatan, kota, dan kode pos — agar kurir dari mana pun dapat menemukan tujuan yang tepat.

**Contoh penerapan dalam artikel:**

```html
<!-- HTML -->
<h2>Referensi Belajar</h2>
<p>Berikut adalah sumber referensi yang direkomendasikan:</p>
<ul>
  <li>
    <a href="https://developer.mozilla.org">MDN Web Docs</a> — dokumentasi resmi
    HTML, CSS, dan JavaScript
  </li>
  <li>
    <a href="https://www.w3schools.com">W3Schools</a> — panduan interaktif untuk
    pemula
  </li>
  <li>
    <a href="https://css-tricks.com">CSS-Tricks</a> — artikel dan teknik CSS
    lanjutan
  </li>
</ul>
```

#### B. Relative Path (Alamat Lokal)

Digunakan untuk berpindah antar halaman di dalam website atau folder yang sama. Tidak perlu menuliskan protokol atau domain — cukup nama file atau jalur relatif dari lokasi file saat ini.

Contoh struktur folder:

```
/website-saya/
├── index.html
├── tentang.html
├── kontak.html
└── artikel/
    └── belajar-html.html
```

Tautan di dalam `index.html` yang mengarah ke halaman lain di folder yang sama:

```html
<!-- HTML — di dalam index.html -->
<a href="tentang.html">Tentang Kami</a>
<a href="kontak.html">Hubungi Kami</a>
```

Tautan di dalam `index.html` yang mengarah ke file di dalam subfolder:

```html
<!-- HTML — di dalam index.html -->
<a href="artikel/belajar-html.html">Baca: Belajar HTML dari Nol</a>
```

Tautan di dalam `artikel/belajar-html.html` yang kembali ke halaman utama:

```html
<!-- HTML — di dalam artikel/belajar-html.html -->
<a href="../index.html">← Kembali ke Beranda</a>
<!-- Tanda "../" berarti naik satu tingkat ke folder induk -->
```

**Analogi:** Relative path seperti memberikan petunjuk arah dari posisi saat ini — "belok kiri, lalu masuk pintu kedua" — tanpa perlu menyebutkan alamat lengkap dari awal.

---

### 3. Membuka Tautan di Tab Baru (`target`)

Secara bawaan, tautan akan membuka halaman tujuan di tab yang sama, sehingga halaman sebelumnya tertutup. Untuk membuka tautan di tab baru, tambahkan atribut `target` dengan nilai `_blank`.

```html
<!-- HTML -->
<a href="https://www.instagram.com" target="_blank">Kunjungi Instagram</a>
```

Atribut `target="_blank"` sangat disarankan digunakan saat membuat tautan yang mengarah ke website eksternal, agar pengguna tidak meninggalkan website yang sedang mereka kunjungi.

**Contoh penerapan — tautan internal vs eksternal:**

```html
<!-- HTML -->
<h2>Sumber Bacaan Lanjutan</h2>

<!-- Tautan internal: dibuka di tab yang sama -->
<p>
  Baca juga artikel kami tentang
  <a href="artikel/css-dasar.html">CSS Dasar untuk Pemula</a>.
</p>

<!-- Tautan eksternal: dibuka di tab baru -->
<p>
  Untuk referensi resmi, kunjungi
  <a href="https://developer.mozilla.org" target="_blank">MDN Web Docs</a>.
</p>
```

---

### 4. Tautan ke Alamat Email dan Nomor Telepon

Atribut `href` tidak terbatas pada alamat halaman web. HTML juga mendukung protokol khusus untuk membuka aplikasi email dan aplikasi panggilan telepon secara langsung.

#### Tautan Email (`mailto:`)

Ketika diklik, browser akan membuka aplikasi email bawaan perangkat (seperti Gmail atau Outlook) dengan kolom penerima yang sudah terisi secara otomatis.

```html
<!-- HTML -->
<a href="mailto:info@namawebsite.com">Kirim Email kepada Kami</a>
```

Parameter tambahan juga dapat disertakan dalam format `mailto:`:

```html
<!-- HTML: dengan subjek dan isi pesan yang sudah terisi otomatis -->
<a
  href="mailto:info@namawebsite.com?subject=Pertanyaan%20Layanan&body=Halo%2C%20saya%20ingin%20bertanya%20tentang..."
>
  Kirim Email dengan Subjek Otomatis
</a>
```

#### Tautan Telepon (`tel:`)

Ketika diklik di perangkat mobile, browser akan membuka aplikasi panggilan telepon dengan nomor yang sudah terisi. Nomor telepon ditulis dalam format internasional (diawali dengan kode negara).

```html
<!-- HTML -->
<a href="tel:+6281234567890">Hubungi Kami: +62 812-3456-7890</a>
```

**Contoh penerapan — Bagian kontak di halaman website:**

```html
<!-- HTML -->
<section>
  <h2>Hubungi Kami</h2>
  <p>
    Untuk pertanyaan dan informasi lebih lanjut, silakan menghubungi kami
    melalui salah satu saluran berikut:
  </p>
  <ul>
    <li>
      Email:
      <a href="mailto:halo@namawebsite.com">halo@namawebsite.com</a>
    </li>
    <li>
      Telepon:
      <a href="tel:+622112345678">+62 21 1234-5678</a>
      (Senin–Jumat, 09.00–17.00 WIB)
    </li>
    <li>
      Website resmi:
      <a href="https://www.namawebsite.com" target="_blank">
        www.namawebsite.com
      </a>
    </li>
  </ul>
</section>
```

---

### Kesimpulan

Tag `<a>` adalah elemen yang menjadikan halaman web saling terhubung. Dengan memahami perbedaan antara absolute path dan relative path, serta mengetahui kapan menggunakan atribut `target="_blank"`, tautan dapat dibuat dengan tepat sesuai konteks penggunaannya. Selain itu, protokol `mailto:` dan `tel:` memperluas fungsi tautan tidak hanya untuk berpindah halaman, tetapi juga untuk memulai komunikasi langsung dengan pengguna.

**Ringkasan Elemen dan Atribut:**

| Elemen / Atribut  | Fungsi                                                    |
| ----------------- | --------------------------------------------------------- |
| `<a>`             | Membuat tautan (_hyperlink_)                              |
| `href`            | Menentukan alamat tujuan tautan                           |
| `target="_blank"` | Membuka tautan di tab baru                                |
| `mailto:`         | Membuka aplikasi email dengan penerima yang sudah terisi  |
| `tel:`            | Membuka aplikasi panggilan dengan nomor yang sudah terisi |

**Panduan Pemilihan Jenis Path:**

| Kebutuhan                                           | Jenis Path yang Digunakan                  |
| --------------------------------------------------- | ------------------------------------------ |
| Mengarah ke website eksternal                       | Absolute Path (`https://...`)              |
| Berpindah ke halaman lain di folder yang sama       | Relative Path (`nama-file.html`)           |
| Berpindah ke halaman di dalam subfolder             | Relative Path (`subfolder/nama-file.html`) |
| Kembali ke folder induk                             | Relative Path (`../nama-file.html`)        |
| Tautan ke website eksternal agar tab tidak tertutup | Absolute Path + `target="_blank"`          |
| Membuka aplikasi email                              | `href="mailto:alamat@email.com"`           |
| Membuka aplikasi telepon                            | `href="tel:+6281234567890"`                |
