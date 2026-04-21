# Bab 27: Teks, Format Teks, & Font di CSS

## Tujuan Pembelajaran

- Mampu memodifikasi bentuk dan arah teks (alignment, decoration, transform).
- Mengatur kerenggangan spasi antar huruf dan baris bacaan.
- Membedah properti `font` utama: Jenis Huruf, Ketebalan, dan Kemiringan.
- Memahami strategi pemanggilan Font Cadangan (Fallback Font).

## Materi Utama

Meskipun halaman websitemu sudah cantik bentuknya, tapi pada akhirnya yang dicari penonton adalah "Informasi" berupa teks tulisan.

Di HTML (Bab 5), kita sempat menyentuh sedikit cara menebalkan atau memiringkan dengan Tag `<b>` dan `<i>`. Namun, untuk urusan estetika Tipografi tingkat tinggi, CSS adalah sang Raja sejati.

### 1. Manipulasi Format Teks (`text-...`)

Keluarga properti pertama khusus bertugas memodifikasi cara teks tersebut direntangkan atau digambari coretan.

**A. Perataan Teks (`text-align`):**
Persis seperti fitur di Microsoft Word:

- `left` (merapat ke kiri - default)
- `right` (merapat ke kanan)
- `center` (tepat di tengah-tengah)
- `justify` (rata kanan-kiri seperti koran)

**B. Coretan Teks (`text-decoration`):**
Paling sering dipakai untuk menghilangkan garis bawah (underline) bawaan yang ada pada tag Link `<a>`, atau sekadar mencoret harga diskon.

- `underline` (garis bawah)
- `line-through` (dicoret tengah)
- `none` (menghapus kepolosan/default hiasan)

```css
/* Membuat link di artikel jadi bersih tanpa garis bawah */
a {
  text-decoration: none;
}
```

**C. Merubah Huruf Kapital (`text-transform`):**
Lupa mematikan tombol _Capslock_ saat ngetik? Santai, CSS bisa memperbaiki wujud akhirnya secara otomatis:

- `uppercase` (semuanya HURUF BESAR)
- `lowercase` (semuanya huruf kecil)
- `capitalize` (Hanya Huruf Pertama Di Tiap Kata Yang Besar)

### 2. Spasi dan Kerenggangan Bacaan

Desain teks yang sesak sangat menyakitkan mata. Kita bisa atur renggangnya:

- **`letter-spacing`**: Jarak antar satu huruf aksara dengan sebelahnya. (Misal `2px` akan membuat t e k s l e b i h l o n g g a r).
- **`line-height`**: Jarak spasial antar baris kalimat atas dan bawah. Normalnya browser memberi jarak 1.2, tapi untuk artikel bacaan panjang sangat sehat menaikkannya jadi `1.5` atau `1.6`.

### 3. Modifikasi Tipe Huruf (`font-...`)

Keluarga kedua bertugas memanipulasi tulang punggung sang huruf tersebut.

- **`font-size`**: Seberapa raksasa ukuran huruf tersebut (Bisa memakai `px`, `%`, `em`, atau `rem`).
- **`font-weight`**: Tingkat gemuknya karakter. Nilainya bisa berupa teks (`normal`, `bold`) atau angka ukur ketebalan (`400` untuk normal, `700` untuk tebal, `900` untuk ekstra gemuk).
- **`font-style`**: Ingin miring? Cukup isikan nilai `italic`.

### 4. Menentukan Ganti Baju Huruf (`font-family`)

Ini adalah properti paling vital untuk menyetel wajah keseluruhan _Brand_ websitemu.

Aturannya: Ketik nama Font utama yang paling kamu inginkan, lalu disusul dengan koma dan tuliskan nama font cadangan. Kenapa butuh cadangan? Karena kita tidak tahu apakah komputer si pengunjung meng-install varian font langka yang kita tuju tersebut.

```css
body {
  font-family: "Helvetica Neue", Arial, sans-serif;
}
```

**Analogi Ban Serep (Fallback Font):**

- Pilihan Pertama: "Helvetica Neue" (Tolong dong komputer, cari font ini yang cakep).
- Pilihan Kedua (Serep ke-1): "Arial" (Nah, misal gak ketemu Helvetica, tolong pakai Arial ya, mirip-mirip soalnya).
- Pilihan Terakhir (Serep Pamungkas): `sans-serif` (Waduh Arial juga gada? Ya udah pakai sembarang font botak/tanpa ekor aja deh yang ada di sistem laptop lu!).

Keluarga pamungkas bawaan (System Fonts) yang pasti selalu ada di browser:

1. `serif` = Tipe font klasik memiliki kait ekor lancip di kakinya (seperti Times New Roman).
2. `sans-serif` = Tipe font modern tanpa ekor atau bentuk tiang rapi (seperti Arial, Calibri).
3. `monospace` = Tipe mesin tik, jarak lebar lebarnya konsisten merata (Khas untuk ngebikin code program berjalan di terminal).
