# Bab 30: CSS Pseudo Classes

## Tujuan Pembelajaran

- Memahami konsep Pseudo-Class sebagai "Status/Keadaan" sesaat dari sebuah elemen.
- Menguasai properti interaktif seperti `:hover`, `:active`, dan `:focus`.
- Mampu menyeleksi anak elemen spesifik menggunakan `:nth-child` dan `:first-child`.

## Materi Utama

Sejauh ini, kita mewarnai sebuah tombol secara permanen. Tombol berwarna biru, ya akan terus biru. Tetapi, bagaimana cara kita membuat tombol tersebut "menyala" atau berubah warna hanya ketika kursor mouse menyentuhnya?

Di sinilah kita memanggil ilmu **Pseudo-Class** (Kelas Semu).

### 1. Apa itu Pseudo-Class?

Pseudo-class digunakan untuk memberikan gaya pada sebuah elemen hanya ketika elemen tersebut berada dalam **keadaan atau status tertentu**.

Penulisannya sangat khas, yaitu menempelkan tanda titik dua tunggal (`:`) setelah nama selektor utama tanpa spasi.

### 2. Status Interaksi Pengguna (Interactive States)

Ini adalah kelompok pseudo-class yang bereaksi terhadap respon fisik dari pengguna (mouse atau sentuhan).

- **`:hover` (Disentuh Mouse)**: Keadaan saat anak panah (kursor) mouse melayang di atas elemen, tapi belum diklik. Sangat sering dipakai untuk membuat tombol yang terasa _"hidup"_.
- **`:active` (Sedang Ditekan)**: Momen sepersekian detik ketika klik kiri mouse sedang dalam posisi ditekan tahan pada elemen tersebut.
- **`:focus` (Jadi Perhatian)**: Status saat sebuah elemen sedang "aktif/menyala" karena baru saja diklik atau diakses menggunakan tombol TAB di keyboard (Sering dipakai pada kotak input form).

```css
/* Gaya tombol saat normal diam */
.tombol-beli {
  background-color: blue;
  color: white;
}

/* Saat mouse mampir di atas tombol (belum klik) */
.tombol-beli:hover {
  background-color: darkblue; /* Berubah jadi biru gelap */
  cursor: pointer; /* Ubah panah mouse jadi gambar tangan menunjuk */
}

/* Saat tombol sedang ditekan keras (klik kiri tahan) */
.tombol-beli:active {
  background-color: red; /* Sedetik jadi merah */
}

/* Saat kotak input form sedang di-klik siap diketik */
.kotak-nge-chat:focus {
  background-color: lightyellow;
  border: 3px solid orange;
}
```

**Analogi Bunglon:**
Elemen HTML pada dasarnya adalah bunglon. Saat diam di dahan, ia berwarna hijau (normal css). Namun saat ia merasa didekati pemangsa (kursor `hover`), ia otomatis mengubah warna kulitnya menjadi coklat.

### 3. Status Urutan Silsilah (Tree-Structural States)

Lalu, bagaimana jika kamu punya 10 baris di dalam tabel HTML, dan kamu hanya ingin mewarnai baris nomer 1 saja, atau mewarnai selang-seling genap-ganjil tanpa harus memberi ID satu-satu?

Gunakan kelompok pseudo-class logika matematika silsilah ini!

- **`:first-child`**: Menargetkan anak sulung (urutan pertama mutlak).
- **`:last-child`**: Menargetkan anak bungsung (urutan terakhir mutlak).
- **`:nth-child(angka/rumus)`**: Menargetkan urutan persis sesuai angka yang kamu kirim, atau pakai rumus canggih.

```css
/* Mewarnai paragraf urutan pertama menjadi tebal */
p:first-child {
  font-weight: bold;
}

/* Mewarnai baris ketiga (urutan ke-3) persis di tabel */
tr:nth-child(3) {
  background-color: gray;
}

/* Trik Dewa: Mewarnai selang-seling (Zebra Cross) genap ganjil! */
tr:nth-child(even) {
  background-color: white;
} /* Untuk urutan 2,4,6... */
tr:nth-child(odd) {
  background-color: lightblue;
} /* Untuk urutan 1,3,5... */
```

### Kesimpulan

Pseudo-Class adalah jalan pintas CSS agar kita tidak perlu menumpuk puluhan teks nama `class="baru"` di dokumen HTML hanya untuk mengubah visual sesaat. Biarkan CSS yang pintar melacak keadaan status (interaksi dan urutan) dan mengaplikasikan kosmetiknya secara gaib otomatis.
