# Bab 5: Text & Format Teks di HTML

## Tujuan Pembelajaran

- Mengenali berbagai elemen pemformatan teks yang tersedia di HTML.
- Memahami perbedaan antara elemen yang bersifat visual dan elemen yang memiliki makna semantik.
- Menerapkan elemen pemformatan teks seperti tebal, miring, stabilo, coretan, dan lainnya pada konten halaman web.

---

## Materi Utama

Dalam aplikasi pengolah kata seperti Microsoft Word, pengguna dapat menerapkan format _Bold_ (tebal), _Italic_ (miring), atau _Underline_ (garis bawah) untuk memberikan penekanan pada teks tertentu. HTML menyediakan kemampuan serupa melalui elemen-elemen pemformatan teks yang dapat digunakan langsung tanpa memerlukan CSS.

---

### 1. Menebalkan Teks: `<b>` vs `<strong>`

Terdapat dua elemen yang menghasilkan tampilan teks tebal, namun dengan tujuan yang berbeda:

| Elemen     | Tampilan Visual | Makna Semantik                                         |
| ---------- | --------------- | ------------------------------------------------------ |
| `<b>`      | Teks tebal      | Tidak ada — hanya bersifat visual                      |
| `<strong>` | Teks tebal      | Menyatakan bahwa teks memiliki kepentingan yang tinggi |

Perbedaan semantik ini berdampak pada aksesibilitas: aplikasi pembaca layar (_screen reader_) yang digunakan oleh pengguna dengan keterbatasan penglihatan akan membacakan teks di dalam `<strong>` dengan penekanan intonasi yang lebih kuat, sedangkan `<b>` diperlakukan sama seperti teks biasa.

**Panduan penggunaan:**

- Gunakan `<b>` jika tujuannya hanya mempertebal teks secara visual tanpa kandungan makna khusus.
- Gunakan `<strong>` jika teks tersebut memang memiliki tingkat kepentingan yang tinggi — misalnya peringatan, instruksi krusial, atau istilah kunci.

```html
<!-- HTML -->
<p>
  Belajar HTML itu <b>mudah</b> dan sangat <strong>penting</strong> untuk masa
  depan.
</p>

<p>
  <strong>Perhatian:</strong> Simpan pekerjaan Anda sebelum menutup aplikasi.
</p>
```

**Contoh penerapan dalam konten nyata:**

```html
<!-- HTML -->
<h2>Panduan Instalasi</h2>
<p>
  Sebelum memulai, pastikan perangkat Anda memiliki koneksi internet yang
  stabil.
  <strong>Jangan matikan perangkat selama proses instalasi berlangsung</strong>,
  karena dapat menyebabkan kerusakan pada sistem.
</p>
<p>
  Versi yang direkomendasikan adalah <b>versi 3.2.1 (LTS)</b>, meskipun versi
  lain juga dapat digunakan.
</p>
```

---

### 2. Memiringkan Teks: `<i>` vs `<em>`

Sama seperti pasangan `<b>` dan `<strong>`, HTML menyediakan dua elemen untuk menghasilkan teks miring dengan tujuan yang berbeda:

| Elemen | Tampilan Visual | Makna Semantik                                                    |
| ------ | --------------- | ----------------------------------------------------------------- |
| `<i>`  | Teks miring     | Tidak ada — digunakan untuk istilah teknis, asing, atau idiomatis |
| `<em>` | Teks miring     | Menyatakan penekanan (_emphasis_) pada kata atau frasa tersebut   |

**Panduan penggunaan:**

- Gunakan `<i>` untuk menandai istilah asing, nama ilmiah, judul karya, atau istilah teknis yang lazim dicetak miring.
- Gunakan `<em>` jika kata atau frasa tersebut perlu mendapat penekanan makna dalam kalimat — mirip dengan cara seseorang menekankan kata tertentu saat berbicara.

```html
<!-- HTML -->
<p>Kucing peliharaanku berjenis <i>Felis catus</i>.</p>
<p>Tolong dengarkan, kamu <em>harus</em> belajar setiap hari secara rutin!</p>
```

**Contoh penerapan dalam konten nyata:**

```html
<!-- HTML -->
<h2>Artikel: Kebiasaan Produktif</h2>
<p>
  Konsep <i>deep work</i> yang dipopulerkan oleh Cal Newport menekankan
  pentingnya fokus tanpa gangguan dalam menyelesaikan pekerjaan bernilai tinggi.
</p>
<p>
  Kunci utamanya bukan seberapa lama kamu bekerja, melainkan seberapa
  <em>fokus</em> kamu selama bekerja.
</p>
```

---

### 3. Elemen Pemformatan Teks Lainnya

HTML menyediakan sejumlah elemen tambahan untuk kebutuhan pemformatan teks yang lebih spesifik. Berikut elemen-elemen yang paling sering digunakan:

#### `<mark>` — Sorotan Teks

Menampilkan teks dengan latar berwarna kuning (seperti efek stabilo), digunakan untuk menyoroti informasi yang perlu mendapat perhatian khusus dari pembaca.

```html
<!-- HTML -->
<p>Jangan lupa membawa <mark>KTP asli</mark> saat menghadiri ujian besok.</p>
```

**Contoh penerapan — Hasil pencarian dengan kata kunci yang disorot:**

```html
<!-- HTML -->
<h3>Hasil pencarian untuk: "HTML"</h3>
<p>
  <mark>HTML</mark> adalah singkatan dari HyperText Markup Language.
  <mark>HTML</mark> merupakan fondasi dari setiap halaman web yang ada di
  internet.
</p>
```

---

#### `<del>` — Teks Tercoret

Menampilkan teks dengan garis coretan di tengah (_strikethrough_). Secara semantik, `<del>` menyatakan bahwa teks tersebut telah dihapus atau tidak lagi berlaku.

```html
<!-- HTML -->
<p>Promo! Harga dari <del>Rp 100.000</del> kini hanya Rp 20.000.</p>
```

**Contoh penerapan — Kartu harga produk:**

```html
<!-- HTML -->
<div class="kartu-produk">
  <h3>Sepatu Olahraga Pro X</h3>
  <p>Harga normal: <del>Rp 850.000</del></p>
  <p>Harga promo: <ins>Rp 595.000</ins></p>
  <p><mark>Diskon 30% — Berlaku hingga akhir bulan</mark></p>
</div>
```

---

#### `<ins>` — Teks dengan Garis Bawah

Menampilkan teks dengan garis bawah (_underline_). Secara semantik, `<ins>` menyatakan bahwa teks tersebut merupakan tambahan atau pembaruan dari konten sebelumnya. Elemen ini sering digunakan berpasangan dengan `<del>`.

```html
<!-- HTML -->
<p>Jadwal diubah menjadi <ins>hari Minggu, 20 Juli 2025</ins>.</p>
```

**Contoh penerapan — Riwayat perubahan dokumen:**

```html
<!-- HTML -->
<h3>Catatan Perubahan Dokumen</h3>
<p>
  Lokasi kegiatan: <del>Gedung A, Lantai 3</del> <ins>Gedung B, Lantai 1</ins>
</p>
<p>Waktu mulai: <del>08.00 WIB</del> <ins>09.00 WIB</ins></p>
```

---

#### `<sub>` — Subscript (Teks Turun)

Menampilkan teks dalam ukuran lebih kecil dan posisi sedikit lebih rendah dari baris teks utama. Digunakan dalam penulisan rumus kimia, notasi matematika, atau referensi catatan kaki.

```html
<!-- HTML -->
<p>Rumus kimia air adalah H<sub>2</sub>O.</p>
<p>Glukosa memiliki rumus kimia C<sub>6</sub>H<sub>12</sub>O<sub>6</sub>.</p>
```

---

#### `<sup>` — Superscript (Teks Naik)

Menampilkan teks dalam ukuran lebih kecil dan posisi sedikit lebih tinggi dari baris teks utama. Digunakan dalam penulisan pangkat bilangan, notasi ilmiah, atau penanda referensi.

```html
<!-- HTML -->
<p>Luas persegi dengan sisi 5 cm adalah 5<sup>2</sup> = 25 cm<sup>2</sup>.</p>
<p>Kecepatan cahaya adalah sekitar 3 × 10<sup>8</sup> meter per detik.</p>
```

**Contoh penerapan `<sub>` dan `<sup>` dalam konten ilmiah:**

```html
<!-- HTML -->
<h2>Reaksi Kimia Dasar</h2>
<p>Pembakaran sempurna glukosa dalam tubuh mengikuti persamaan berikut:</p>
<p>
  C<sub>6</sub>H<sub>12</sub>O<sub>6</sub> + 6O<sub>2</sub> → 6CO<sub>2</sub> +
  6H<sub>2</sub>O + energi
</p>

<h2>Notasi Pangkat</h2>
<p>Nilai dari 2<sup>10</sup> adalah 1.024.</p>
<p>Massa bumi diperkirakan sekitar 5,97 × 10<sup>24</sup> kilogram.</p>
```

---

### Kesimpulan

Elemen pemformatan teks di HTML terbagi menjadi dua kategori: elemen yang bersifat **visual** (hanya mengubah tampilan) dan elemen yang bersifat **semantik** (mengubah tampilan sekaligus memberikan makna). Memilih elemen yang tepat sesuai konteks tidak hanya menghasilkan kode yang lebih bermakna, tetapi juga meningkatkan aksesibilitas dan keterbacaan halaman oleh mesin pencari.

**Panduan singkat penggunaan:**

- Perlu mempertebal teks dengan makna penting? → Gunakan **`<strong>`**.
- Perlu mempertebal teks hanya secara visual? → Gunakan **`<b>`**.
- Perlu memiringkan teks dengan penekanan makna? → Gunakan **`<em>`**.
- Perlu memiringkan teks istilah asing atau teknis? → Gunakan **`<i>`**.
- Perlu menyoroti teks seperti stabilo? → Gunakan **`<mark>`**.
- Perlu menampilkan teks yang dihapus atau tidak berlaku? → Gunakan **`<del>`**.
- Perlu menampilkan teks yang ditambahkan atau diperbarui? → Gunakan **`<ins>`**.
- Perlu menuliskan indeks bawah (rumus kimia, dsb.)? → Gunakan **`<sub>`**.
- Perlu menuliskan indeks atas (pangkat, notasi ilmiah, dsb.)? → Gunakan **`<sup>`**.

**Ringkasan Elemen:**

| Elemen     | Tampilan       | Kategori | Penggunaan Umum                                  |
| ---------- | -------------- | -------- | ------------------------------------------------ |
| `<b>`      | **Tebal**      | Visual   | Penekanan visual tanpa makna khusus              |
| `<strong>` | **Tebal**      | Semantik | Teks dengan tingkat kepentingan tinggi           |
| `<i>`      | _Miring_       | Visual   | Istilah asing, nama ilmiah, judul karya          |
| `<em>`     | _Miring_       | Semantik | Penekanan intonasi atau makna dalam kalimat      |
| `<mark>`   | Tersorot       | Visual   | Menyoroti informasi penting atau hasil pencarian |
| `<del>`    | ~~Tercoret~~   | Semantik | Teks yang dihapus atau tidak lagi berlaku        |
| `<ins>`    | Tergaris bawah | Semantik | Teks yang ditambahkan atau diperbarui            |
| `<sub>`    | Indeks bawah   | Visual   | Rumus kimia, notasi matematika bawah             |
| `<sup>`    | Indeks atas    | Visual   | Pangkat bilangan, notasi ilmiah                  |

**Panduan Pemilihan Elemen:**

| Kebutuhan                                        | Elemen yang Tepat |
| ------------------------------------------------ | ----------------- |
| Peringatan atau instruksi penting                | `<strong>`        |
| Nama spesies, istilah Latin, atau kata asing     | `<i>`             |
| Kata yang perlu ditekankan dalam konteks kalimat | `<em>`            |
| Kata kunci hasil pencarian yang disorot          | `<mark>`          |
| Harga lama yang sudah tidak berlaku              | `<del>`           |
| Harga baru atau informasi pengganti              | `<ins>`           |
| Rumus kimia seperti H₂O atau CO₂                 | `<sub>`           |
| Notasi pangkat seperti 10² atau 5³               | `<sup>`           |
