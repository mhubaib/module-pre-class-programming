# Bab 26: CSS Border & Outline

## Tujuan Pembelajaran

- Mengetahui cara memberikan garis tepi (Border) pada elemen.
- Memahami tiga properti pembentuk Border (Width, Style, Color).
- Membedakan antara Border dan Outline.
- Mampu membulatkan sudut kotak menggunakan `border-radius`.

## Materi Utama

Setelah kita memahami _Padding_ (ruang di dalam) dan _Margin_ (ruang di luar), sekarang kita akan membahas dinding pemisahnya, yaitu **Border** dan saudara kembarnya **Outline**.

Memberikan pinggiran pada kotak sangat berguna untuk membedakan satu bagian dengan bagian lain, atau untuk membuat tombol yang menarik.

### 1. Mengenal Border (Garis Tepi)

**Border** adalah garis nyata yang mengelilingi Padding dan batas Content dari suatu elemen.

Menurut hukum _Box Model_, ketebalan Border akan menambah ukuran asli elemenmu, kecuali kamu sudah menggunakan mantra `box-sizing: border-box;` (ingat pelajaran Bab 22!).

Agar sebuah Border bisa muncul dan terlihat oleh mata, ia wajib memiliki minimal 3 komponen, yaitu:

1. **Ketebalan (Width)**: Seberapa tebal garisnya (misal: `1px`, `5px`, `thick`).
2. **Gaya (Style)**: Bentuk jenis garisnya (misal: garis lurus, putus-putus, titik-titik).
3. **Warna (Color)**: Warna tinta garisnya (misal: `red`, `#000000`).

```css
.kotak-peringatan {
  border-width: 2px;
  border-style: solid;
  border-color: red;
}
```

### 2. Jenis-jenis Gaya Garis (`border-style`)

Ada banyak bentuk garis yang disediakan CSS. Yang paling sering digunakan oleh programmer adalah:

- `solid`: Garis lurus tegas biasa (paling populer).
- `dashed`: Garis putus-putus.
- `dotted`: Garis titik-titik kecil.
- `double`: Garis ganda (dua garis sejajar).
- `none`: Menghilangkan border (sering dipakai untuk me-reset bawaan tabel atau tombol).

### 3. Penulisan Singkat Border (Shorthand)

Menulis 3 baris kode untuk satu garis itu membuang waktu. Oleh karena itu, kita selalu menggunakan penulisan singkat (shorthand). Urutannya bebas, tapi yang paling umum adalah: **[Ketebalan] [Gaya] [Warna]**.

```css
.tombol-keren {
  border: 3px solid blue; /* Lebih hemat dan efisien! */
}
```

Sama seperti Padding dan Margin, kamu juga bisa mengatur border di sisi tertentu saja:

- `border-top: 1px solid black;`
- `border-bottom: 5px dashed green;`

### 4. Membulatkan Sudut Kotak: `border-radius`

Di era desain web modern, bentuk kotak yang ujung-ujungnya tajam siku-siku sudah mulai ditinggalkan. Desain kekinian cenderung menyukai pinggiran yang tumpul atau melengkung (seperti bentuk tombol di iPhone atau aplikasi Android).

Untuk menumpulkan sudut secara ajaib, gunakan `border-radius`.

```css
.kartu-kredit {
  background-color: navy;
  /* Sudut akan terpotong melengkung sebanyak 10 pixel */
  border-radius: 10px;
}

.foto-profil {
  width: 200px;
  height: 200px;
  /* Trik rahasia: 50% akan membuat kotak sempurna menjadi LINGKARAN PENUH! */
  border-radius: 50%;
}
```

### 5. Apa bedanya Border dan Outline?

Pernahkah kamu mengeklik sebuah kotak input di _form_ pendaftaran, lalu tiba-tiba muncul garis biru terang di luarnya yang menandakan kamu sedang mengetik di situ? Itu bukanlah Border, melainkan **Outline**.

**Perbedaan Utama:**

- **Letak**: `outline` berada di **LUAR** batas border (menumpuk di atas margin).
- **Ukuran**: `outline` **TIDAK PERNAH** merusak atau menambah ukuran layout kotak sama sekali. Dia seperti bayangan (hologram) yang tidak butuh ruang fisik.
- **Bentuk**: `outline` tidak bisa membulat mengikuti lengkungan `border-radius` (setidaknya di beberapa browser lama bentuknya akan tetap siku-siku).
- **Pengaturan Sisi**: `outline` tidak bisa diatur cuma di sisi atas/bawah saja. Dia harus full keliling kotak 4 sisi sekaligus.

**Cara Penulisan Outline (Sama dengan Border):**

```css
input:focus {
  outline: 2px solid lightblue;
}
```

**Analogi Pagar Rumah:**
Jika elemenmu adalah sebuah Rumah, maka **Border** adalah pagar bata permanen yang mengelilingi halamanmu. Pagar bata itu butuh semen, makan tempat, dan kokoh (mempengaruhi ukuran rumahmu).
Sedangkan **Outline** adalah garis pita polisi kuning (Police Line) yang ditarik cepat di sekeliling rumahmu. Pita itu tidak makan tempat, gampang dipasang-lepas, dan bisa ditarik tembus menimpa pohon tetangga tanpa minta izin (tidak merusak layout).
