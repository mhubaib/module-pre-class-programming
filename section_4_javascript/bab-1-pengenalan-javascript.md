# Bab 1: Pengenalan JavaScript

## Tujuan Pembelajaran

- Memahami pengertian dan fungsi utama JavaScript dalam pengembangan web.
- Memahami perbedaan peran antara HTML, CSS, dan JavaScript.
- Mengenal di mana saja kode JavaScript dapat dijalankan.
- Mengetahui sekilas sejarah dan peran ECMAScript (ES).

---

## Materi Utama

Setelah mempelajari kerangka website (HTML) dan desain tampilannya (CSS), kita tiba pada komponen keempat yang paling penting dalam pengembangan web modern: **JavaScript**.

HTML dan CSS adalah bahasa _markup_ dan _style_, yang berarti mereka hanya mendeskripsikan "apa" dan "bagaimana" sesuatu terlihat. Keduanya bersifat statis. Untuk membuat website tersebut dapat merespons interaksi pengguna dan memiliki logika, kita memerlukan sebuah bahasa pemrograman. Itulah tugas JavaScript.

---

### 1. Apa itu JavaScript?

**JavaScript** (sering disingkat JS) adalah bahasa pemrograman tingkat tinggi yang awalnya diciptakan untuk membuat halaman web menjadi interaktif.

Dengan JavaScript, kamu bisa:

- Menampilkan pesan atau dialog ketika pengguna mengklik sebuah tombol.
- Memvalidasi isian formulir sebelum dikirim (misalnya memastikan format email sudah benar).
- Mengambil data dari server tanpa harus memuat ulang (_refresh_) halaman web.
- Membuat animasi, galeri gambar yang dapat digeser, hingga permainan berbasis browser.

**Analogi Pembangunan:**

- **HTML** adalah struktur dan denah ruangan sebuah bangunan.
- **CSS** adalah cat dinding, desain interior, dan ornamen yang membuatnya terlihat menarik.
- **JavaScript** adalah aliran listrik, pipa air, mesin elevator, dan tombol sakelar yang membuat bangunan tersebut berfungsi dan dapat digunakan.

**Contoh sederhana — JavaScript di browser:**

```html
<!-- HTML -->
<button id="tombol-sapa">Klik Saya</button>
<p id="pesan"></p>
```

```javascript
// JavaScript
const tombol = document.getElementById("tombol-sapa");
const pesan = document.getElementById("pesan");

tombol.addEventListener("click", function () {
  pesan.textContent = "Halo! Selamat datang di JavaScript.";
});
```

Ketika tombol diklik, teks akan muncul di paragraf di bawahnya — sesuatu yang tidak mungkin dilakukan oleh HTML atau CSS saja.

---

### 2. Di mana JavaScript Dijalankan?

#### A. Di Browser (Front-End)

Pada awalnya, JavaScript hanya dirancang untuk dijalankan di dalam **browser** (Chrome, Firefox, Safari). Browser memiliki mesin khusus yang disebut _JavaScript Engine_ — misalnya **V8** di Chrome — yang bertugas membaca dan mengeksekusi kode JavaScript menjadi tindakan nyata di layar pengguna.

Pengembangan yang berjalan di browser ini disebut sebagai pengembangan **Front-End**.

```
[ Kode JavaScript ] → [ JavaScript Engine di Browser ] → [ Tampilan di Layar ]
```

#### B. Di Server (Back-End)

Pada tahun 2009, teknologi bernama **Node.js** diciptakan. Node.js adalah lingkungan (_runtime environment_) yang memungkinkan JavaScript dijalankan langsung di sistem operasi komputer atau server, tanpa memerlukan browser.

Berkat Node.js, JavaScript kini dapat digunakan untuk:

- Membangun server dan API yang melayani permintaan dari browser.
- Mengakses dan mengelola database.
- Memproses file di sistem operasi.

Hal ini menjadikan JavaScript bahasa yang sangat fleksibel — satu bahasa dapat digunakan untuk pengembangan **Front-End** sekaligus **Back-End**.

**Perbandingan lingkungan eksekusi JavaScript:**

| Lingkungan | Platform                | Contoh Penggunaan                                 |
| ---------- | ----------------------- | ------------------------------------------------- |
| Browser    | Chrome, Firefox, Safari | Interaksi antarmuka, animasi, validasi form       |
| Node.js    | Komputer / Server       | API, database, otomatisasi, server-side rendering |

---

### 3. ECMAScript (ES): Standar Bahasa JavaScript

Saat mempelajari JavaScript dari berbagai sumber, kamu mungkin akan menemukan istilah seperti "ES6", "ES2015", atau "ES2022". Berikut penjelasannya:

**JavaScript** adalah nama merek dari bahasa pemrograman yang kita gunakan. **ECMAScript (ES)** adalah standar resmi yang mendefinisikan aturan teknis tentang bagaimana bahasa ini seharusnya bekerja — sehingga kode yang ditulis di Chrome juga berjalan dengan benar di Firefox, Safari, atau Edge.

**Versi-versi penting ECMAScript:**

| Versi             | Tahun        | Keterangan                                                                                                             |
| ----------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------- |
| ES5               | 2009         | Versi lama yang sudah sangat stabil; didukung oleh seluruh browser                                                     |
| **ES6 / ES2015**  | 2015         | Pembaruan terbesar dalam sejarah JavaScript; memperkenalkan `let`, `const`, _arrow function_, _class_, dan banyak lagi |
| ES2016 – sekarang | Setiap tahun | Pembaruan kecil yang ditambahkan secara rutin setiap tahun                                                             |

**ES6 / ES2015** adalah titik balik penting dalam perkembangan JavaScript. Sebelum ES6, kode JavaScript terkesan verbose dan kurang konsisten. Setelah ES6, bahasa ini menjadi jauh lebih modern, ringkas, dan mudah dibaca.

**Contoh perbandingan — Sebelum dan sesudah ES6:**

```javascript
// Sebelum ES6 (cara lama)
var nama = "Budi";
function sapa(nama) {
  return "Halo, " + nama + "!";
}

// Sesudah ES6 (cara modern)
const nama = "Budi";
const sapa = (nama) => `Halo, ${nama}!`;
```

Kedua blok kode di atas menghasilkan output yang sama, namun versi ES6 jauh lebih ringkas dan lebih mudah dibaca.

Dalam modul ini, seluruh materi ditulis menggunakan sintaks JavaScript modern standar ES6 ke atas, agar relevan dengan standar yang digunakan di industri pengembangan perangkat lunak saat ini.

---

### Kesimpulan

JavaScript adalah bahasa pemrograman yang melengkapi HTML dan CSS untuk membangun pengalaman web yang interaktif dan fungsional. Dengan memahami di mana JavaScript dijalankan dan standar penulisannya, kamu memiliki fondasi yang tepat untuk memulai perjalanan belajar JavaScript secara terstruktur.

**Ringkasan:**

| Konsep            | Penjelasan                                                        |
| ----------------- | ----------------------------------------------------------------- |
| JavaScript (JS)   | Bahasa pemrograman untuk membuat website interaktif               |
| JavaScript Engine | Mesin di dalam browser yang mengeksekusi kode JavaScript          |
| Node.js           | Lingkungan yang memungkinkan JavaScript berjalan di luar browser  |
| ECMAScript (ES)   | Standar resmi yang mendefinisikan aturan bahasa JavaScript        |
| ES6 / ES2015      | Versi pembaruan terbesar JavaScript; menjadi acuan sintaks modern |
| Front-End         | Pengembangan yang berjalan di sisi browser                        |
| Back-End          | Pengembangan yang berjalan di sisi server                         |
