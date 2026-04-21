# Bab 53: JS Events

## Tujuan Pembelajaran
- Memahami konsep *Event* sebagai alat pendeteksi interaksi pengguna.
- Mampu mendengarkan dan merespons aksi (*Event Listener*) seperti klik, ketikan keyboard, dan pengiriman formulir.
- Membaca dan memanfaatkan data dari *Event Object*.
- Menguasai fungsi `preventDefault()` untuk membatalkan sifat *refresh* bawaan dari browser.

## Materi Utama

Di Bab 52, kita telah berhasil memanipulasi elemen DOM. Namun, kapan kita mengeksekusi manipulasi tersebut? Tentu saja kita menjalankannya ketika terjadi suatu **Kejadian (Event)**, misalnya "Saat tombol ditekan", "Saat mouse digeser", atau "Saat tombol *Enter* di-klik".

Dalam JavaScript, kita memasang sebuah "Sensor Pendengar" pada sebuah elemen HTML untuk bereaksi ketika pengunjung melakukan suatu tindakan.

### 1. Memasang Sensor (Event Listener)

Alat pendeteksi utama di JavaScript modern bernama `addEventListener()`. Fungsi ini membutuhkan dua bahan (argumen) mutlak:
1. **Nama Event**: Jenis kejadian apa yang mau ditunggu? (Misal: `'click'`, `'mouseenter'`, `'keydown'`).
2. **Fungsi Tanggapan (Callback)**: Sebuah instruksi fungsi yang hanya akan dijalankan manakala kejadian tersebut benar-benar berlansung.

```javascript
// 1. Tangkap dulu elemen tombolnya
const tombolBeli = document.querySelector("#btn-beli");

// 2. Pasang sensor 'click' pada tombol tersebut
tombolBeli.addEventListener('click', function() {
    // Kode di dalam blok ini HANYA JALAN saat tombol selesai diklik
    alert("Terima kasih sudah membeli produk kami!");
    tombolBeli.textContent = "Sudah Dibeli"; // Merubah teks tombolnya langsung
});
```
*(Gaya modern: Programmer sering mengganti function biasa di atas menggunakan Arrow Function `=>` seperti yang kita pelajari di Bab 45).*

### 2. Macam-Macam Event Populer

Selain `'click'`, ada puluhan jenis event di luar sana. Berikut yang paling laris digunakan:
- `'input'` : Mendeteksi setiap jari menekan satu per satu abjad saat mengetik di dalam kolom inputan.
- `'mouseenter'` & `'mouseleave'` : Mirip seperti `:hover` di CSS, mendeteksi kursor mouse masuk atau keluar dari area suatu elemen.
- `'keydown'` & `'keyup'` : Mendeteksi tusukan jari pada *keyboard* laptop (Biasanya digunakan untuk mengecek apakah *Enter* ditekan).
- `'submit'` : Sensor yang ditaruh di tag `<form>`, mendeteksi aktifitas formulir pendaftaran saat akan dikirim ke server.

### 3. Membedah Data Kejadian (Event Object)

Setiap kali sebuah *event* benar-benar terjadi dan memicu fungsi berjalan, JavaScript diam-diam membawakan bingkisan raport kejadian dan memberikannya ke parameter pertama fungsi tanggapanmu. Bingkisan ini lazimnya diberi nama parameter huruf **`e`** atau **`event`**.

Di dalam bingkisan (Object) tersebut, terdapat kumpulan informasi berharga, seperti kordinat piksel mouse, atau jenis tombol keyboard apa yang baru saja ditekan.

```html
<!-- Anggap ada kolom input HTML seperti ini -->
<input type="text" id="kolom-nama" placeholder="Ketik nama anda">
```

```javascript
const kolomNama = document.querySelector("#kolom-nama");

// Kita pasang sensor 'input' dan sediakan lubang parameter 'e' untuk menangkap raportnya
kolomNama.addEventListener('input', function(e) {
    // Kita bisa mengekstrak huruf per huruf yang baru saja diketik user menggunakan e.target.value
    let hurufSedangDiketik = e.target.value; 
    
    console.log("Kamu sedang mengetik: " + hurufSedangDiketik);
});
```

### 4. Mematikan Sifat Bawaan Kuno (`e.preventDefault()`)

Ini adalah trik yang paling krusial untuk membuat sebuah halaman *Single Page Application* (website interaktif yang tak pernah kedip/memuat ulang layarnya).

Tag HTML bawaan kuno selalu merepotkan. Contohnya saja:
- Elemen tautan `<a href>` jika ditekan bawaannya selalu ingin melempar pindah ke halaman baru.
- Elemen `<form>` jika diklik Submit, sifat bawaan dari alam sananya adalah memaksa halamannya memuat ulang (*refresh* keras) untuk melempar data.

Di era modern, kita memproses data murni di balik layar sehingga aktivitas memuat ulang (*refresh* halaman) ini sangat dibenci dan haram terjadi. Gunakan mantera `e.preventDefault()` untuk melucuti dan membatalkan sifat-sifat bawaan menjengkelkan dari HTML tersebut.

```javascript
const formulirLogin = document.querySelector("#form-login");

formulirLogin.addEventListener('submit', function(e) {
    // MANTERA SAKTI: Hentikan sifat reload halaman bawaan formulir ini!
    e.preventDefault(); 
    
    console.log("Formulir sukses sedang diproses di balik layar tanpa refresh!");
    
    // Disini tempatmu mengambil data (e.target.value) dan melemparnya diam-diam ke server...
});
```

Hanya menguasai Bab 52 (DOM) dan Bab 53 (Events) dengan kokoh ini, secara prinsip logika kamu sudah memiliki kompetensi mentah untuk mulai membangun logika kerangka kerja React.js atau Vue.js modern!
