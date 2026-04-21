# Bab 18: Error - error di CSS

## Tujuan Pembelajaran

- Mengenali kesalahan-kesalahan umum yang sering dilakukan pemula saat menulis CSS.
- Mampu melakukan debugging sederhana menggunakan Browser Developer Tools.
- Memahami konsep "Cascading" dan "Specificity" untuk mendeteksi konflik kode.

## Materi Utama

Menulis CSS terkadang bisa membuat frustrasi. Kamu sudah mengetik kode dengan benar, tapi warna tulisannya tidak berubah. Kamu ingin menggeser kotak ke tengah, tapi ia malah diam di pojok. Jangan panik! Bahkan programmer profesional pun sering mengalami hal ini.

Bab ini akan membantumu mendeteksi "penyakit" umum pada kode CSS-mu dan cara menyembuhkannya.

### 1. Kesalahan Penulisan (Typo & Syntax Error)

Ini adalah penyebab 90% masalah bagi pemula. CSS sangat sensitif terhadap tanda baca.

- **Lupa Titik Koma (`;`)**: Jika kamu lupa menutup satu baris instruksi dengan `;`, maka instruksi di bawahnya akan dianggap sebagai bagian dari baris sebelumnya. Hasilnya? Seluruh blok kode tersebut akan diabaikan oleh browser.
- **Salah Ketik Nama Properti**: Menulis `collor` (double 'l') alih-alih `color`, atau `background-colorr`. Browser tidak akan memberi tahu ada error, ia hanya akan mengabaikan kode yang tidak ia kenali.
- **Lupa Simbol Selektor**: Ingin memanggil Class tapi lupa tanda titik (`.`), atau ingin memanggil ID tapi lupa tanda pagar (`#`).

### 2. Masalah Jalur File (Path Error)

Jika kamu menggunakan **External CSS**, pastikan link di HTML-mu sudah benar.

- Apakah nama filenya persis sama? (Ingat: `Style.css` beda dengan `style.css`).
- Apakah filenya ada di folder yang sama? Jika CSS-mu ada di dalam folder bernama `css`, maka panggilannya harus `<link href="css/style.css">`.

### 3. Konsep Cascading (Urutan Menang)

Pernahkah kamu bertanya-tanya mengapa CSS disebut **Cascading** Style Sheets? "Cascading" artinya air terjun atau berurutan.

Jika ada dua aturan CSS yang menargetkan elemen yang sama, aturan yang **paling bawah** (yang ditulis terakhir) biasanya akan menang dan menimpa aturan yang di atasnya.

```css
p {
  color: red;
}

/* Kode di bawah ini yang akan menang karena ditulis terakhir */
p {
  color: blue;
}
```

### 4. Specificity (Siapa yang Lebih Spesifik?)

Selain urutan, browser juga melihat "siapa yang lebih berkuasa". Ada kasta atau tingkatan kekuatan selektor:

1. **ID Selector (#)**: Paling kuat (Kasta Raja).
2. **Class Selector (.)**: Menengah (Kasta Bangsawan).
3. **Element Selector**: Paling lemah (Kasta Rakyat).

**Contoh Kasus:**
Jika kamu punya paragraf dengan ID `teks-biru` tapi kamu mengaturnya di CSS seperti ini:

```css
#teks-biru {
  color: blue;
} /* Raja bilang biru */
p {
  color: red;
} /* Rakyat bilang merah */
```

Maka teks tersebut akan tetap berwarna **biru**, meskipun aturan merah ditulis di bawah. Karena ID jauh lebih kuat daripada Element.

### 5. Senjata Rahasia: Inspect Element

Jika kodemu tidak jalan, jangan hanya menatap layar editor. Gunakan **Browser Developer Tools**:

1. Buka website latihanmu di Chrome.
2. Klik kanan pada elemen yang bermasalah -> pilih **Inspect**.
3. Lihat panel di sebelah kanan pada bagian **Styles**.

Di sana kamu bisa melihat:

- Apakah kodemu terbaca oleh browser?
- Apakah ada tanda seru kuning atau kode yang dicoret? (Jika dicoret, artinya kodemu kalah perang oleh aturan lain/Specificity).
- Kamu bahkan bisa mencoba mengganti warna atau ukuran secara langsung di situ untuk melihat perubahan instan sebelum memperbaikinya di file `.css`.

**Analogi Dokter:**
Menghadapi error CSS ibarat menjadi dokter. Kamu tidak bisa menebak penyakit hanya dengan melihat pasien dari jauh. Kamu harus melakukan "rontgen" menggunakan _Inspect Element_ untuk melihat apa yang sebenarnya terjadi di dalam "tulang" kode tersebut.
