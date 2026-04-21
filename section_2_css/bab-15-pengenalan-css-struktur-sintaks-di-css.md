# Bab 15: Pengenalan CSS & Struktur Sintaks di CSS

## Tujuan Pembelajaran

- Memahami pengertian CSS dan perannya dalam mempercantik halaman web.
- Mengetahui struktur sintaks dasar CSS (Selector, Property, dan Value).
- Memahami fungsi tanda kurung kurawal `{}` dan titik koma `;` dalam penulisan CSS.

## Materi Utama

Setelah kita belajar membuat fondasi dan struktur bangunan menggunakan HTML di Bagian 1, sekarang saatnya kita belajar menjadi seorang arsitek sekaligus desainer interior. Selamat datang di dunia **CSS!**

### 1. Apa itu CSS?

CSS adalah singkatan dari **Cascading Style Sheets**. Jika HTML bertugas menentukan **APA** yang tampil di layar (teks, gambar, tombol), maka CSS bertugas menentukan **BAGAIMANA** tampilan tersebut terlihat oleh mata (warna, ukuran, posisi, hingga animasi).

Tanpa CSS, halaman web hanyalah deretan teks kaku berwarna hitam di atas latar putih. Dengan CSS, kita bisa mengubah sebuah halaman web yang "biasa saja" menjadi terlihat profesional, premium, dan sangat menarik.

**Analogi Arsitektur Bangunan:**

- **HTML:** Adalah bata, semen, dan tulang besi. Ia membangun rangka rumah, jendela, dan pintu. Tanpa HTML, rumah tidak berdiri.
- **CSS:** Adalah cat tembok, motif keramik lantai, desain lampu gantung, dan ornamen taman. Ia tidak membangun rangka, tapi ia membuat rumah tersebut layak huni dan indah dipandang.

### 2. Struktur Sintaks Dasar CSS

Menulis kode CSS berbeda dengan menulis HTML. CSS tidak menggunakan "Tag" yang berpasangan. CSS menggunakan aturan (rules) yang terdiri dari tiga komponen utama: **Selector, Property, dan Value.**

Perhatikan contoh kode berikut:

```css
h1 {
  color: blue;
  font-size: 24px;
}
```

Mari kita bedah anatominya:

- **Selector (Siapa yang ingin dihias?):** Dalam contoh di atas, `h1` adalah selector. Kita memberi tahu browser: "Cari semua tag `<h1>` yang ada di HTML".
- **Property (Apanya yang mau diubah?):** Di dalam kurung kurawal, ada kata `color` dan `font-size`. Ini adalah atribut yang ingin kita modifikasi arsitekturnya.
- **Value (Mau diubah jadi apa?):** Di sebelah kanan tanda titik dua `:`, ada nilai `blue` dan `24px`. Inilah instruksi spesifiknya.

### 3. Aturan Penulisan (Tanda Baca)

Dalam CSS, tanda baca sangatlah sakral. Salah sedikit, desainmu tidak akan muncul.

1. **Kurung Kurawal `{ }`**: Digunakan untuk membungkus semua instruksi desain (Property & Value) untuk selector tersebut. Semua keajaiban terjadi di dalam kurung ini.
2. **Titik Dua `:`**: Digunakan untuk memisahkan antara _Property_ dan _Value_. Ibarat berkata: "Warna tulisan **adalah** Biru".
3. **Titik Koma `;`**: Digunakan untuk mengakhiri sebuah baris instruksi. Anggap saja ini sebagai "Tanda Titik" di sebuah kalimat. Jika kamu lupa menaruh `;`, browser akan bingung dan instruksi di bawahnya akan terbaca error.

**Tips Penulisan Rapi:**
Sebenarnya kamu bisa menulis CSS dalam satu baris panjang, tapi demi kerapihan dan kemudahan dibaca oleh rekan kerja atau dirimu sendiri di masa depan, sangat disarankan untuk menulis setiap property di baris yang baru.

```css
/* Penulisan yang BURUK (Sulit dibaca) */
p {
  color: red;
  text-align: center;
  font-family: script;
}

/* Penulisan yang BAIK (Rapi & Profesional) */
p {
  color: red;
  text-align: center;
  font-family: script;
}
```

Dengan memahami struktur sederhana ini, kamu sudah siap untuk mulai merancang desain website pertamamu!
