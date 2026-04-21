# Bab 7: Hyperlink

## Tujuan Pembelajaran

- Memahami konsep dasar Hyperlink sebagai inti dari "World Wide Web".
- Mampu membuat link menggunakan tag `<a>`.
- Membedakan penggunaan _Absolute Path_ (URL lengkap) dan _Relative Path_ (URL lokal).
- Mengetahui cara membuat link terbuka di tab baru.

## Materi Utama

Bayangkan internet tanpa kemampuan berpindah dari satu halaman ke halaman lain hanya dengan sekali "klik". Pasti sangat membosankan, bukan? Fitur magis yang menghubungkan miliaran halaman web di seluruh dunia ini bernama **Hyperlink** (atau sering kita sebut "link" saja).

Sesuai namanya, Hyperlink adalah teks atau gambar ajaib yang jika ditekan akan membawa kita berpindah (melompat) ke lokasi lain. Lokasi ini bisa berupa halaman yang berbeda di website yang sama, halaman di website orang lain, atau bahkan bagian bawah dari halaman yang sedang kita baca.

### 1. Mengenal Tag Anchor (`<a>`)

Di HTML, Hyperlink dibuat menggunakan tag `<a>` (kependekan dari **Anchor** atau jangkar). Tag ini **wajib** dipasangkan dengan atribut `href` (Hypertext Reference) agar bisa berfungsi. Jika atribut `href` tidak ada, teks di dalam tag `<a>` hanya akan terlihat seperti teks biasa tanpa sihir apa-apa.

**Analogi Pintu Doraemon:**
Tag `<a>` adalah Pintu Kemana Saja milik Doraemon. Namun, pintu itu tidak akan tahu harus mengantarkanmu ke mana jika kamu tidak mensetting tujuannya lewat tombol koordinat rahasia. Nah, atribut `href` inilah tombol koordinat pengatur tujuan tersebut.

**Sintaks Dasar:**

```html
<a href="URL_TUJUAN">Teks yang bisa diklik oleh user</a>
```

Contoh nyata:

```html
<p>
  Silakan kunjungi <a href="https://google.com">Google</a> untuk mencari
  informasi.
</p>
```

Secara otomatis, browser akan mengubah kata "Google" menjadi berwarna biru (atau ungu jika sudah pernah dikunjungi) serta memberikan garis bawah (_underline_).

### 2. Absolute Path vs Relative Path

Sebagai Web Developer, kamu harus jeli menentukan jenis alamat pada atribut `href`. Ada dua jenis alamat (path) yang selalu kita gunakan:

**A. Absolute Path (Alamat Lengkap / Mutlak)**
Digunakan ketika kamu ingin menumpang kapal menuju pulau orang lain (mengarah ke website eksternal). Syaratnya, kamu harus menuliskan URL lengkap beserta protokolnya (seperti `https://` atau `http://`).
Analogi: Mengirim paket ke luar kota (Butuh Provinsi, Kota, Kecamatan, Jalan, RT/RW).

```html
<a href="https://youtube.com">Buka YouTube</a>
<a href="https://id.wikipedia.org/wiki/HTML"
  >Membaca Sejarah HTML di Wikipedia</a
>
```

**B. Relative Path (Alamat Lokal / Relatif)**
Digunakan ketika kamu ingin berpindah ruangan di dalam rumahmu sendiri (mengarah ke file HTML lain yang ada di dalam **komputermu/foldermu** sendiri). Di sini, kamu tidak perlu repot menulis `https://`. Cukup tulis nama filenya saja.
Analogi: Kamu sedang di Ruang Tamu, lalu menyuruh adikmu, "Tolong ambilkan minum di _Dapur_." Kamu tak perlu menyebutkan alamat lengkap provinsi dan RT/RW rumahmu lagi.

Contoh struktur di foldermu:

- `index.html` (Kamu saat ini di sini)
- `tentang-saya.html`
- `kontak.html`

Maka kode di dalam `index.html` untuk memanggil halaman kontak adalah:

```html
<a href="kontak.html">Hubungi Saya (Berpindah Halaman)</a>
<a href="tentang-saya.html">Profil Penulis</a>
```

### 3. Membuka Link di Tab Baru (Atribut `target`)

Pernahkah kamu mengeklik sebuah berita, tapi berita tersebut malah terbuka di tab baru sehingga halaman aslimu tidak tertutup?
Untuk melakukan trik ini, kita membutuhkan atribut tambahan bernama `target` dengan nilai `_blank`.

```html
<a href="https://instagram.com" target="_blank"
  >Lompat ke Instagram tanpa menutup web ini!</a
>
```

Atribut `target="_blank"` sangat disarankan dipakai jika kamu memberikan link ke website **orang lain**, supaya pengunjung tidak benar-benar "kabur" meninggalkan websitemu sendiri.

### 4. Link yang Mengarah ke Email dan Telepon

Kehebatan atribut `href` ternyata tak terbatas pada alamat website saja. Kamu bisa menyulap teks menjadi jembatan instan untuk memanggil aplikasi Email dan aplikasi Telepon di HP pengunjung!

- **Link Email (mailto):**
  Akan otomatis membuka aplikasi email (Gmail/Outlook) dengan tujuan alamat yang sudah terisi.

  ```html
  <a href="mailto:presiden@negara.com">Kirim email pengaduan ke Presiden</a>
  ```

- **Link Telepon (tel):**
  Jika diklik via HP, akan langsung melempar angka ke menu Panggilan (Dialer).
  ```html
  <a href="tel:+6281234567890">Telepon Darurat Kami di Sini</a>
  ```
