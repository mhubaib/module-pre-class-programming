# Bab 2: Tag, Element, dan Atribut dalam HTML

## Tujuan Pembelajaran

- Mengetahui perbedaan mendasar antara Tag, Element, dan Atribut pada kode HTML.
- Mampu menulis sintaks HTML dasar tanpa bingung membedakan istilah-istilah di atas.
- Mengenal fungsi Atribut dan cara penulisannya yang benar.

## Materi Utama

Satu-satunya cara HTML berkomunikasi dengan Web Browser adalah menggunakan **"Tanda"**. Dalam kacamata HTML, tulisan tidak sekadar tulisan. Tulisan harus "dibungkus" oleh tanda tertentu agar browser tahu maksudnya.
Secara teknis, bahasa HTML dibangun dari tiga unsur utama pembentuk anatominya: **Tag, Element, dan Atribut.**

### 1. Tag (Tanda atau Label)

Tag adalah instruksi berupa tanda khusus penanda awal dan akhir. Tag bertugas memberitahu browser: _"Tolong tampilkan teks di bagian ini sebagai paragraf, dan bagian yang itu sebagai judul besar."_
Setiap kali kamu menulis tag HTML, ia wajib dibungkus dengan tanda kurung siku pembuka `<` dan penutup `>`.

Konsep dasar Tag selalu berpasangan: ada **Tag Pembuka** (Opening Tag) dan **Tag Penutup** (Closing Tag). Perbedaannya, tag penutup wajib diimbuhi **garis miring/slash (`/`)** setelah kurung siku pertama.

**Contoh:**

- `<p>` adalah tag pembuka untuk Paragraf.
- `</p>` adalah tag penutup untuk Paragraf.
- `<h1>` adalah tag pembuka untuk Judul Besar (Heading 1).
- `</h1>` adalah tag penutup.

**Pengecualian (Tag Tunggal):**
Tidak semua benda di dunia nyata punya akhir. Begitu juga di HTML, ada tag yang tidak punya penutup, dinamakan **Self-Closing Tag**. Biasanya ini dipakai untuk hal yang tidak membungkus teks, melainkan menyisipkan _sebuah objek_.
Contoh:

- `<br>` (Break), untuk menyisipkan jeda baris baru (seperti tombol Enter).
- `<img>` (Image), untuk menyisipkan gambar.

### 2. Element (Elemen Utuh)

Seringkali programmer pemula terbalik-balik menyebut Tag sebagai Element dan Element sebagai Tag.

**Analogi Kardus Paket:**
Bayangkan kamu sedang mengirim paket berisi TV melalui kurir SiCepat.

- **Tag Pembuka:** Label stiker bertuliskan "Fragile / Mudah Pecah" di bagian atas kardus.
- **Konten:** TV layar datar yang ada di dalamnya.
- **Tag Penutup:** Selotip besar/Label segel di bagian bawah kardus.

Nah, **Element** adalah KESELURUHAN paket tersebut: Kardus yang ditempeli label secara utuh beserta TV di dalamnya!

Dalam kacamata kode:

```html
<p>Halo, ini adalah sebuah paragraf!</p>
```

Penjelasan Anatomi:

- `<p>` = Tag Pembuka
- `Halo, ini adalah sebuah paragraf!` = Konten / Isi
- `</p>` = Tag Penutup
  **Kesatuan dari ujung `<p>` sampai menabrak ujung `</p>` itulah yang dinamakan HTML ELEMENT.** Jika seseorang berkata, _"Tolong hapus Element Paragraf tersebut,"_ artinya kamu harus menghapus tag pembuka, isinya, dan tag penutupnya sekaligus.

### 3. Atribut (Attribute / Informasi Ekstra)

Terkadang, sekadar label kardus "Fragile" tidak cukup. Kurir perlu tahu, _"Ke mana kardus ini harus dikirim? Berapa beratnya?"_ Di sinilah **Atribut** berperan.

Atribut adalah penyedia informasi tambahan atau modifikasi yang disematkan **khusus di dalam Tag Pembuka** (tidak pernah ditulis di Tag Penutup).

Aturan dasar penulisan Atribut:

1. Ditulis di dalam kurung siku Tag Pembuka, dipisahkan dengan spasi.
2. Formasi penulisannya selalu berpasangan: `nama_atribut="nilai_atribut"`.
3. Gunakan tanda sama dengan (`=`) dan bungkus nilai menggunakan tanda kutip ganda (`" "`).

**Contoh Kasus Atribut:**

_Kasus 1: Atribut pada Elemen Link (Tautan)_

```html
<a href="https://google.com">Ayo buka Google</a>
```

- `<a ...>` = Tag pembuka `a` (Anchor, pembuat teks bisa diklik).
- `href` = Nama atribut (Singkatan Hypertext Reference, tempat menyimpan URL tujuan).
- `"https://google.com"` = Nilai dari atribut tersebut.

_Kasus 2: Atribut pada Elemen Gambar (Tag Tunggal)_

```html
<img src="foto-kucing.jpg" alt="Gambar Kucing Anggora sedang tidur" />
```

- `<img>` = Tag penyisip gambar.
- `src` = Atribut Source (Sumber). Di sinilah browser tahu gambar bernama `foto-kucing.jpg` yang harus ditampilkan.
- `alt` = Atribut Alternative Text. Sebuah teks cadangan. Jika koneksi internet pengguna sangat lambat dan `foto-kucing.jpg` gagal dimuat, teks "Gambar Kucing Anggora sedang tidur"-lah yang akan muncul di layar. Atribut `alt` ini juga krusial bagi penyandang tunanetra yang berselancar di internet menggunakan aplikasi pembaca layar otomatis (Screen Reader).

Sebuah tag bisa memiliki satu atribut, banyak atribut sekaligus (dipisahkan spasi antar atribut), atau tidak sama sekali.
