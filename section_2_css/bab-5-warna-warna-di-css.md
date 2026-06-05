# Bab 19: Warna-warna di CSS

## Tujuan Pembelajaran

- Mengenal berbagai format sistem pewarnaan di CSS (Nama, HEX, RGB, HSL).
- Mampu memberikan warna pada teks dan latar belakang elemen.
- Memahami konsep transparansi (Opacity) menggunakan RGBA.

## Materi Utama

Warna adalah nyawa dari sebuah desain. Di HTML kita hanya mengenal warna dasar seperti `red` atau `blue`, tapi di CSS, kita punya jutaan kombinasi warna yang bisa kita gunakan untuk menyihir pengunjung website.

### 1. Nama Warna (Color Names)

Cara termudah adalah menggunakan nama warna dalam bahasa Inggris. Ada sekitar 140 nama warna standar yang dikenali semua browser (seperti `SkyBlue`, `Tomato`, `SlateGrey`).

```css
h1 {
  color: Tomato;
}
```

### 2. Format HEX (Hexadecimal)

Ini adalah format yang paling sering digunakan oleh desainer profesional. Terdiri dari tanda pagar (`#`) diikuti oleh 6 karakter (kombinasi angka 0-9 dan huruf A-F).

- Contoh: `#FF0000` (Merah), `#00FF00` (Hijau), `#0000FF` (Biru).
- Putih murni adalah `#FFFFFF` dan Hitam murni adalah `#000000`.

**Analogi Kode Rahasia:**
Bayangkan HEX adalah "resep rahasia" yang sangat spesifik. Jika kamu minta "warna merah" ke toko cat, kamu mungkin dapat merah yang berbeda-beda. Tapi jika kamu memberikan kode `#FF5733`, kamu akan mendapatkan warna merah jingga yang persis sama di mana pun kamu berada.

### 3. Format RGB dan RGBA

RGB adalah singkatan dari **Red, Green, Blue**. Di sini kita mencampurkan tiga warna primer cahaya tersebut dengan rentang angka 0 sampai 255.

```css
p {
  /* Campuran: Merah penuh, Hijau setengah, Biru nol */
  color: rgb(255, 127, 0);
}
```

**Konsep Transparansi (RGBA):**
Jika kamu ingin warnanya agak tembus pandang (transparan), gunakan `rgba`. Huruf `a` (Alpha) memiliki rentang dari **0** (hilang total) sampai **1** (pekat/tidak transparan).

```css
div {
  background-color: rgba(0, 0, 0, 0.5); /* Hitam transparan 50% */
}
```

### 4. Format HSL (Hue, Saturation, Lightness)

Ini adalah format yang paling manusiawi dan mudah dipahami untuk memodifikasi warna secara manual.

- **Hue (Warna)**: Dari 0 sampai 360 (bayangkan lingkaran warna). 0 adalah merah, 120 hijau, 240 biru.
- **Saturation (Kepekatan)**: 0% berarti warnanya pudar (abu-abu), 100% berarti warnanya sangat mencolok.
- **Lightness (Kecerahan)**: 0% hitam gelap, 50% normal, 100% putih terang.

```css
button {
  background-color: hsl(120, 100%, 50%); /* Hijau terang yang segar */
}
```

### 5. Di mana kita meletakkan warna?

Ada dua tempat utama penggunaan properti warna:

1. **`color`**: Mengubah warna **teks atau tulisan**.
2. **`background-color`**: Mengubah warna **kotak latar belakang** sebuah elemen.

**Tips Memilih Warna:**
Jangan asal pilih warna yang mencolok mata (seperti kuning terang di atas putih). Gunakan alat bantu seperti **Adobe Color** atau **Coolors.co** untuk mencari kombinasi warna yang harmonis dan enak dipandang (palet warna).

**Analogi Melukis:**
Belajar sistem warna CSS ibarat belajar mencampur cat di palet lukis. Kamu bisa pakai cat instan yang sudah ada namanya (Color Names), atau mencampurkan sendiri tetes demi tetes tinta Merah, Hijau, dan Biru (RGB) sampai mendapatkan warna impianmu.
