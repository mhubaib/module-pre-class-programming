# Bab 20: Mengatur Width & Height Element

## Tujuan Pembelajaran

- Memahami properti `width` dan `height` untuk mengatur dimensi elemen.
- Mampu membedakan satuan pixel (px) dan persentase (%).
- Mengenal properti pembatas ukuran (max-width, min-width, dll).
- Memahami perilaku dimensi pada elemen Block vs Inline.

## Materi Utama

Semua elemen di dalam website pada dasarnya adalah sebuah "kotak". Agar website terlihat rapi, kita harus bisa mengendalikan seberapa lebar dan seberapa tinggi kotak-kotak tersebut.

### 1. Mengatur Lebar dan Tinggi (Width & Height)

Untuk menentukan dimensi, kita menggunakan dua properti ini:

- **`width`**: Mengatur lebar (mendatar).
- **`height`**: Mengatur tinggi (tegak).

```css
.kotak-iklan {
  width: 300px;
  height: 250px;
  background-color: yellow;
}
```

### 2. Satuan Ukuran: Statis vs Relatif

Ini adalah bagian paling penting agar websitemu tidak berantakan saat dibuka di layar HP.

- **Pixel (px)**: Satuan statis/tetap. Ukurannya akan selalu sama, tidak peduli layarnya besar atau kecil.
- **Persentase (%)**: Satuan relatif. Ukurannya akan menyesuaikan dengan lebar wadah induknya (parent).

**Analogi Baju dan Ukuran:**

- **Pixel** ibarat baju ukuran **S** yang kaku. Jika dipakai orang besar, bajunya akan sesak atau tidak muat.
- **Persentase** ibarat baju **Oversize** yang elastis. Jika dipakai orang besar, dia melar. Jika dipakai orang kecil, dia mengecil mengikuti bentuk badannya.

Di dunia modern, penggunaan **persentase** sangat disarankan untuk lebar (`width`) agar website otomatis rapi di layar HP yang sempit (Responsive Design).

### 3. Properti Pembatas (Min & Max)

Terkadang, kita ingin sebuah kotak bisa melar mengikuti layar, tapi tidak mau dia melar sampai terlalu lebar karena akan terlihat jelek. Gunakanlah pembatas:

- **`max-width`**: "Boleh melar, tapi jangan lebih dari angka ini ya!".
- **`min-width`**: "Boleh mengecil, tapi jangan lebih kecil dari angka ini!".

```css
.artikel {
  width: 100%; /* Coba penuhi layar */
  max-width: 800px; /* Tapi kalau layarnya raksasa, berhenti di 800px saja */
}
```

### 4. Perhatian: Elemen Inline

Ingat materi Bab 13? Elemen **Inline** (seperti `<a>` atau `<span>`) tidak bisa diatur lebar dan tingginya secara langsung. Dia akan bebal dan menghiraukan kode CSS-mu.
Agar bisa diatur ukurannya, elemen tersebut harus diubah dulu sifatnya menjadi **Block** atau **Inline-Block** (ini akan kita bahas lebih dalam di bab Display nanti).

### 5. Satuan Layar (vh & vw)

Ada satuan keren lainnya di CSS modern:

- **vw (Viewport Width)**: Berdasarkan lebar layar browser (100vw = lebar total layar).
- **vh (Viewport Height)**: Berdasarkan tinggi layar browser (100vh = tinggi total layar).

Ini sangat berguna jika kamu ingin membuat bagian "Hero" atau pembuka website yang tingginya persis memenuhi seluruh layar laptop pengunjung saat pertama kali dibuka.

```css
.header-hero {
  width: 100%;
  height: 100vh; /* Tinggi pas satu layar penuh */
}
```

**Analogi Penjahit:**
Mengatur `width` dan `height` ibarat menjadi seorang penjahit. Kamu harus menentukan berapa centimeter kain yang dibutuhkan. Jika kamu salah ukur, bajunya (website) bisa kebesaran (melebar keluar layar) atau kekecilan sampai tidak terlihat.
