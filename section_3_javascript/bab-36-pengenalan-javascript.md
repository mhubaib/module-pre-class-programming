# Bab 36: Pengenalan JavaScript

## Tujuan Pembelajaran
- Memahami pengertian dan fungsi utama JavaScript dalam pengembangan web.
- Memahami perbedaan peran antara HTML, CSS, dan JavaScript.
- Mengenal di mana saja kode JavaScript dapat dijalankan.
- Mengetahui sekilas sejarah dan peran ECMAScript (ES).

## Materi Utama

Setelah mempelajari kerangka website (HTML) dan desain kosmetiknya (CSS), kita tiba pada komponen ketiga yang paling penting dalam pengembangan web modern: **JavaScript**. 

HTML dan CSS adalah bahasa *markup* dan *style*, yang berarti mereka hanya mendeskripsikan "apa" dan "bagaimana" sesuatu terlihat. Mereka berdua bersifat statis (diam). Untuk membuat website tersebut "hidup" dan bisa diajak berinteraksi, kita memerlukan sebuah bahasa pemrograman yang memiliki logika. Itulah tugas JavaScript.

### 1. Apa itu JavaScript?

JavaScript (sering disingkat JS) adalah bahasa pemrograman tingkat tinggi yang awalnya diciptakan untuk membuat halaman web menjadi interaktif. 

Dengan JavaScript, kamu bisa:
- Membuat tombol memunculkan *pop-up* peringatan ketika diklik.
- Memvalidasi isi formulir (misalnya memastikan format email sudah benar sebelum dikirim).
- Mengambil data dari server eksternal tanpa harus memuat ulang (*refresh*) halaman web (konsep AJAX).
- Membuat animasi kompleks, galeri gambar yang bisa di-geser (*carousel*), hingga game 2 Dimensi.

**Analogi Pembangunan:**
- **HTML** adalah tulang punggung dan struktur ruangan bangunan.
- **CSS** adalah cat dinding, desain interior, dan ornamen yang membuatnya indah.
- **JavaScript** adalah aliran listrik, pipa air, mesin elevator, dan tombol sakelar yang membuat bangunan tersebut berfungsi dan bisa digunakan.

### 2. Di mana JavaScript Dijalankan?

Pada awalnya, JavaScript hanya dirancang untuk dijalankan di dalam **Browser** (Chrome, Firefox, Safari). Browser memiliki mesin khusus (disebut *JavaScript Engine*, seperti V8 di Chrome) yang bertugas membaca kode JavaScript dan mengeksekusinya menjadi tindakan di layar layar pengunjung. Area ini disebut sebagai pengembangan **Front-End**.

Namun, pada tahun 2009, sebuah teknologi bernama **Node.js** diciptakan. Node.js adalah lingkungan (*environment*) yang memungkinkan JavaScript dijalankan secara langsung di sistem operasi komputer atau Server, tanpa memerlukan Browser. Berkat Node.js, JavaScript kini bisa digunakan untuk membuat sistem **Back-End** (koneksi ke database, membuat API, dll). 
Hal ini menjadikan JavaScript sebagai bahasa yang sangat kuat dan fleksibel, karena satu bahasa bisa digunakan untuk Front-End sekaligus Back-End.

### 3. ECMAScript (ES): Standar Bahasa JavaScript

Saat belajar JavaScript dari berbagai sumber di internet, kamu mungkin akan sering mendengar istilah seperti "ES6", "ES7", atau "ES2015". Apa maksudnya?

JavaScript adalah merek dagangnya, sedangkan **ECMAScript (ES)** adalah badan standarisasi bahasa pemrogramannya. ECMAScript bertugas membuat buku aturan teknis tentang bagaimana bahasa JavaScript seharusnya bekerja, agar kode yang ditulis di browser Chrome juga bisa berjalan normal di Firefox atau Safari.

- **ES6 / ES2015**: Ini adalah versi pembaruan paling revolusioner dalam sejarah JavaScript. Pembaruan ini dirilis pada tahun 2015 dan memperkenalkan banyak sintaks baru yang modern dan lebih rapi (seperti `let`, `const`, dan *arrow function*).
- Sejak 2015, ECMAScript merilis pembaruan kecil secara rutin setiap tahun (dinamai berdasarkan tahunnya, misal: ES2021, ES2022).

Dalam modul ini, kita akan mempelajari sintaks JavaScript modern standar ES6 ke atas, agar kode yang kamu hasilkan relevan dengan standar industri perangkat lunak saat ini.
