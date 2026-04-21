# Bab 31: CSS Pseudo Elements

## Tujuan Pembelajaran

- Membedakan antara Pseudo-Class (status) dan Pseudo-Element (bagian fisik buatan).
- Menguasai penggunaan titik dua ganda (`::`).
- Memanipulasi tipografi tingkat lanjut lewat `::first-letter` dan `::selection`.
- Mengenal sihir menciptakan elemen palsu tanpa HTML menggunakan `::before` dan `::after`.

## Materi Utama

Jika Pseudo-**Class** di Bab 30 bercerita tentang "Status Keadaan" (seperti sedang disentuh mouse), maka Pseudo-**Element** adalah ilmu untuk memanipulasi atau menciptakan **Bagian Spesifik Fisik** dari suatu elemen teksi/kotak yang tadinya murni.

Ciri khas penulisan Pseudo-Element yang disepakati standar modern adalah menggunakan **titik dua ganda (`::`)** (Tujuannya agar tidak tertukar dengan Pseudo-Class).

### 1. Manipulasi Estetika Sebagian Tulisan

Pernah lihat novel atau buku dongeng kuno di mana huruf PERTAMA pada paragraf pertama di sebuah bab itu dicetak sangat raksasa nan indah? Atau bagaimana cara mengubah warna background stabilo saat teks disorot (di-blok) pakai mouse oleh pengunjung?

```css
/* Sihir 1: Memperbesar huruf pertama khusus di paragraf (Efek Drop-Cap) */
p::first-letter {
  font-size: 300%;
  color: maroon;
  font-weight: bold;
}

/* Sihir 2: Mengubah warna default highlight saat teks di-blok/select oleh mouse (Biasanya warnanya biru kaku) */
p::selection {
  background-color: yellow; /* Blok jadi stabilo kuning */
  color: red; /* Teks yang diblok jadi merah */
}
```

### 2. Sihir Penciptaan Hantu: `::before` dan `::after`

Ini adalah sihir paling mutakhir (dan sangat sering ditanyakan saat interview kerja _Dunia Web Dev_).

Keduanya digunakan untuk **menyisipkan konten palsu/bayangan** tepat _SEBELUM_ atau _SESUDAH_ konten asli milik elemen HTML berjalan, TANPA KITA PERLU repot menulis tag HTML baru di file aslinya!

Ini sangat sering merubah ikon pemanis, efek centang, dan ornamen hiasan.

**Aturan Emas Mutlak:**
Saat memakai `::before` atau `::after`, kamu **WAJIB MENULIS** properti yang namanya `content: "";`. Tanpa baris sakti content (meskipun isinya kosong melompong pakai tanda kutip), elemen palsu tersebut tidak akan sudi nongol di layar.

**Contoh 1: Menyisipkan Teks Pemanis**

```css
/* Menambahkan kata sapaan hantu di depan semua nama elemen H1 */
h1::before {
  content: "Halo Bapak/Ibu ";
  color: grey;
}
/* Jika HTML aslinya <h1>Budi</h1>, maka yang tampil di layar adalah: Halo Bapak/Ibu Budi */
```

**Contoh 2: Membuat Balok Hiasan Dekoratif Kosong (Dewa Styling)**

```css
/* Kita punya kotak judul biasa */
h2 {
  position: relative;
}

/* Kita hire asisten hantu `::after` untuk bikin garis bawah pemanis tebal pendek ala Web Modern */
h2::after {
  content: ""; /* Isinya sengaja dikosongin, karena kita mau ngegambar kotak */
  position: absolute;
  bottom: -5px; /* Nempel dibawah h2 */
  left: 0;
  width: 50px; /* Panjang garisnya 50px aja */
  height: 4px; /* Tinggi tebelnya 4px */
  background-color: green; /* Warna garis hiasannya hijau */
}
```

**Analogi Asisten Ghaib Khusus (Tangan Kanan):**
Pseudo-Element `::before` dan `::after` ibaratnya kamu mengangkat dua Jin asisten pendamping pribadi di kanan dan kirimu. Saat si Tuan Boss (Elemen Utama) berjalan, si asisten Jin kiri (`::before`) tugasnya membawakan spanduk kecil di depan, dan Jin kanan (`::after`) tugasnya nyapu buntut di belakang bawa mahkota. Walau mereka terlihat nyata, di catatan Dukcapil (Dokumen HTML), nama Jin ini tidak pernah tercatat lahir. Murni cuman ilusi dari CSS!
