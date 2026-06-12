# Bab 2: Tag, Element, dan Atribut dalam HTML

## Tujuan Pembelajaran

- Memahami perbedaan mendasar antara Tag, Element, dan Atribut dalam HTML.
- Mampu menulis sintaks HTML dasar dengan pemahaman istilah yang tepat.
- Mengenal fungsi Atribut dan cara penulisannya yang benar.

---

## Materi Utama

HTML berkomunikasi dengan browser menggunakan tanda-tanda khusus yang disebut **tag**. Tulisan biasa tidak cukup untuk memberi tahu browser apakah sesuatu adalah judul, paragraf, tautan, atau gambar — semua itu perlu "dibungkus" oleh tag yang sesuai.

Bahasa HTML dibangun dari tiga unsur utama: **Tag**, **Element**, dan **Atribut**.

---

### 1. Tag

**Tag** adalah penanda instruksi yang memberi tahu browser bagaimana sebuah konten harus ditampilkan. Tag selalu ditulis di dalam tanda kurung siku `<` dan `>`.

Sebagian besar tag berpasangan: ada **Tag Pembuka** dan **Tag Penutup**. Tag penutup ditandai dengan garis miring (`/`) setelah tanda kurung siku pembuka.

```html
<p>← Tag Pembuka</p>
← Tag Penutup
```

**Contoh tag yang umum digunakan:**

| Tag Pembuka | Tag Penutup | Fungsi              |
| ----------- | ----------- | ------------------- |
| `<h1>`      | `</h1>`     | Judul utama halaman |
| `<h2>`      | `</h2>`     | Sub-judul           |
| `<p>`       | `</p>`      | Paragraf teks       |
| `<a>`       | `</a>`      | Tautan (link)       |
| `<div>`     | `</div>`    | Wadah blok umum     |
| `<span>`    | `</span>`   | Wadah inline umum   |

**Self-Closing Tag (Tag Tanpa Penutup):**

Beberapa tag tidak membungkus konten teks, melainkan menyisipkan objek. Tag ini tidak memiliki tag penutup dan disebut **Self-Closing Tag**.

```html
<br />
<!-- Jeda baris baru -->
<hr />
<!-- Garis horizontal pemisah -->
<img src="foto.jpg" alt="Foto" />
<!-- Gambar -->
<input type="text" />
<!-- Kolom input -->
<meta charset="UTF-8" />
<!-- Metadata -->
<link rel="stylesheet" href="style.css" />
<!-- Tautan file CSS -->
```

---

### 2. Element

**Element** adalah satu kesatuan utuh yang terdiri dari tag pembuka, konten di dalamnya, dan tag penutup. Jika tag adalah tanda, maka element adalah keseluruhan paket tersebut.

```html
<p>Halo, ini adalah sebuah paragraf!</p>
```

Anatomi element di atas:

| Bagian      | Teks                                | Keterangan             |
| ----------- | ----------------------------------- | ---------------------- |
| Tag Pembuka | `<p>`                               | Menandai awal element  |
| Konten      | `Halo, ini adalah sebuah paragraf!` | Isi yang ditampilkan   |
| Tag Penutup | `</p>`                              | Menandai akhir element |

**Keseluruhan tiga bagian tersebut — dari `<p>` hingga `</p>` — itulah yang disebut Element.**

**Element dapat bersarang (Nested Elements):**

Element boleh berada di dalam element lain. Element di dalamnya disebut **child element**, dan yang membungkusnya disebut **parent element**.

```html
<div>
  <h2>Judul Seksi</h2>
  <p>Ini adalah paragraf di dalam sebuah div.</p>
</div>
```

```html
<p>Teks ini memiliki kata yang <strong>ditebalkan</strong> di dalamnya.</p>
```

**Aturan penting:** Tag anak harus ditutup sebelum tag induknya ditutup.

```html
<!-- Benar — tag anak ditutup terlebih dahulu -->
<p><strong>Teks tebal</strong></p>

<!-- Salah — tag saling silang -->
<p><strong>Teks tebal</p></strong>
```

---

### 3. Atribut

**Atribut** adalah informasi tambahan yang disisipkan ke dalam tag pembuka untuk memodifikasi perilaku atau tampilan sebuah element.

**Aturan penulisan atribut:**

1. Ditulis di dalam tag pembuka, dipisahkan spasi dari nama tag.
2. Format penulisan: `nama-atribut="nilai"`.
3. Gunakan tanda sama dengan (`=`) dan apit nilai dengan tanda kutip ganda (`"`).
4. Atribut tidak ditulis di tag penutup.

```html
<tag nama-atribut="nilai">Konten</tag>
```

**Contoh — Atribut pada elemen tautan:**

```html
<a href="https://google.com">Buka Google</a>
```

- `href` — Atribut yang menyimpan URL tujuan tautan.
- `"https://google.com"` — Nilai dari atribut `href`.

**Contoh — Atribut pada elemen gambar:**

```html
<img src="foto-kucing.jpg" alt="Kucing Anggora sedang tidur" />
```

- `src` — Atribut Source, menentukan lokasi file gambar yang akan ditampilkan.
- `alt` — Atribut Alternative Text, teks yang ditampilkan jika gambar gagal dimuat. Juga digunakan oleh aplikasi pembaca layar (_screen reader_) untuk pengguna dengan gangguan penglihatan.

**Satu element dapat memiliki beberapa atribut sekaligus:**

```html
<a href="https://contoh.com" target="_blank" title="Buka di tab baru">
  Kunjungi Website
</a>
```

- `href` — URL tujuan.
- `target="_blank"` — Membuka tautan di tab baru.
- `title` — Teks tooltip yang muncul saat kursor diarahkan ke tautan.

**Contoh atribut lainnya yang umum digunakan:**

```html
<!-- Atribut id dan class untuk CSS/JavaScript -->
<div id="header-utama" class="container">...</div>

<!-- Atribut type dan placeholder pada input -->
<input type="email" placeholder="Masukkan email Anda" />

<!-- Atribut width dan height pada gambar -->
<img src="logo.png" alt="Logo" width="200" height="80" />

<!-- Atribut disabled pada tombol -->
<button disabled>Tidak Dapat Diklik</button>
```

---

### 4. Ringkasan Hubungan Ketiganya

```html
<a href="https://google.com">Buka Google</a>
```

```
┌─────────────────────────────────────────────────────┐
│                    ELEMENT                          │
│                                                     │
│  ┌──────────────────────┐                          │
│  │     TAG PEMBUKA       │     KONTEN     TAG PENUTUP│
│  │  <a href="...com">   │  Buka Google   </a>       │
│  │      ↑               │                           │
│  │   ATRIBUT            │                           │
│  └──────────────────────┘                          │
└─────────────────────────────────────────────────────┘
```

| Istilah     | Definisi                                             | Contoh                    |
| ----------- | ---------------------------------------------------- | ------------------------- |
| **Tag**     | Penanda instruksi dalam kurung siku                  | `<p>`, `</p>`, `<img>`    |
| **Atribut** | Informasi tambahan di dalam tag pembuka              | `href="..."`, `src="..."` |
| **Element** | Keseluruhan unit: tag pembuka + konten + tag penutup | `<p>Teks</p>`             |

---

### Kesimpulan

Memahami perbedaan antara Tag, Element, dan Atribut adalah fondasi untuk membaca dan menulis kode HTML dengan benar. Istilah-istilah ini akan terus muncul sepanjang pembelajaran HTML dan CSS, sehingga pemahaman yang tepat sejak awal akan menghindari kebingungan di kemudian hari.

**Ringkasan:**

| Konsep           | Penjelasan                                                    |
| ---------------- | ------------------------------------------------------------- |
| Tag              | Penanda dalam `< >` yang memberi instruksi ke browser         |
| Tag Pembuka      | `<nama>` — menandai awal element                              |
| Tag Penutup      | `</nama>` — menandai akhir element                            |
| Self-Closing Tag | Tag tanpa penutup: `<br>`, `<img>`, `<input>`                 |
| Element          | Kesatuan tag pembuka + konten + tag penutup                   |
| Nested Element   | Element di dalam element lain                                 |
| Atribut          | Informasi tambahan dalam format `nama="nilai"` di tag pembuka |
