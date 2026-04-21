# Bab 54: Modularisasi JavaScript

## Tujuan Pembelajaran
- Memahami perlunya pemecahan file logika yang panjang menjadi modul terpisah (*Separation of Concerns*).
- Membukakan koneksi antar file menggunakan aturan *Export* dan *Import*.
- Memahami perbedaan jalur suplai data: *Named Export* versus *Default Export*.
- Menyesuaikan struktur pemasangan modul pada dokumen HTML.

## Materi Utama

Ketika aplikasi webmu semakin besar dan kompleks, menaruh seluruh kode JavaScript (ribuan baris berisi fungsi, variabel, dom manipulasi) ke dalam satu buah file `script.js` adalah awal dari bencana (*Spaghetti Code*). File akan terasa berat dibaca, kusut untuk dicari kerusakannya, dan sangat rentan mengalami bentrok (*conflict* nama variabel ganda).

Solusinya adalah pendekatan **Modularisasi**: Mencacah satu file raksasa menjadi potongan beberapa kepingan file-file kecil yang spesifik (Disebut Modul) di mana tiap file bertanggung jawab atas 1 fungsi terfokus saja. (Misalnya: satu modul khusus menangani perhitungan harga keranjang belanja, satu modul lagi untuk pengaturan tema gelap/terang).

Fitur memilah potong file ini (dikenal sebagai **ES6 Modules**) menjadi basis tumpuan di industri nyata pembuatan aplikasi yang besar.

### 1. Konsep Alur Export & Import

Jika kita memotong-motong fungsi ke dalam beberapa file berbeda, bagaimana mereka bisa disatukan kembali saat halaman dijalankan?
- Fungsi yang bersedia diizinkan untuk dikirim dan dipakai di luar tempat kelahirannya, harus diselipkan penanda stempel izin keluar: **`export`**.
- File lain yang membutuhkan fungsi tersebut harus menarik data/menjemputnya dari jembatan penyambung bernama: **`import`**.

Terdapat dua tipe mode perizinan bongkar-muat (*Export*):

### 2. Named Export (Eksport Identitas Terperinci)

Metode ini lazim dipakai manakala di dalam satu file kecil tersebut, ada **banyak** fungsi kecil-kecil yang berbeda yang ingin dikirimkan semua ke luar ruangan. Data yang dijemput nantinya wajib dikurung dengan kurung kurawal `{}` beserta nama persis yang identik (*case-sensitive*).

**File Sumber: `matematika.js`**
```javascript
// Kita menempelkan stempel export pada dua fungsi sekaligus

export function hitungPajak(harga) {
    return harga * 0.11;
}

export function potongDiskon(harga) {
    return harga - 10000;
}
```

**File Penerima: `app-utama.js`**
```javascript
// Kita tarik nama persis fungsi tadi dikurung kurawal dari rumah asalnya!
import { hitungPajak, potongDiskon } from './matematika.js';

let hargaBayar = 50000;
let hasilPajaknya = hitungPajak(hargaBayar);

console.log(hasilPajaknya); // Fungsi sukses berjalan melintasi file
```

### 3. Default Export (Mengekspor Sang Raja Utama File)

Pola ini sangat populer apabila 1 file modul memang sengaja diciptakan sepenuhnya murni cuma untuk mewadahi dan melaksanakan **1 Tugas/Fungsi Utama** secara penuh tiada duanya.
Karena ia penguasa satu-satunya dari file tersebut, penarikannya nanti bebas, tanpa kurung kurawal, dan bebas diberi nama alias julukan apa saja.

**File Sumber: `LoginSistem.js`**
```javascript
// Nama fungsi tidak terlalu penting, karena ia menggunakan stempel Mutlak Bebas "default"
export default function lakukanLoginAman() {
    console.log("Sistem login diaktifkan...");
}

// Catatan: Hanya boleh ada maksimal 1 `export default` saja dalam satu kandang file (karena ia rajanya)!
```

**File Penerima: `app-utama.js`**
```javascript
// Karena sifat penarikannya bebas kurung kurawal, kita bisa langsung namain ajaib fungsi tersebut sesuka hati!
import PanggilSistemKeamananMasuk from './LoginSistem.js';

// Menjalankan rajanya file LoginSistem!
PanggilSistemKeamananMasuk(); 
```

*(Di framework modern seperti React, pola struktur Default Export dipakai gencar untuk mengisolasi setiap Komponen Tampilan Visual UI agar mandiri, misal: File modul Tombol sendiri, file modul Bilah Navigasi sendiri).*

### 4. Aktivasi Modul di Rumah Induk HTML

Karena ekosistem modul ES6 melibatkan bongkar lalu lintas data di belakang tanah secara otomatis meminta izin jaringan ke sana ke mari ke file lain, sistem keamananan kuno di HTML tidak akan percaya, sehingga akan menutup (memblokir) *Import* tersebut untuk melindungi dari serangan bahaya.

Kita wajib dengan sadar menitipkan sertifikat izin lencana keikutsertaan di dalam pemanggilan Skrip utama HTML-nya dengan atribut pamungkas penutup `type="module"`.

**Di dalam file HTML (`index.html`)**
```html
<body>
    <h1>Program Kasir Toko Modular</h1>
    
    <!-- INGAT! File penarik pusatnya dipasangkan lencana khusus 'module' agar bisa menyerap sistem tarikan file anaknya! -->
    <script type="module" src="./app-utama.js"></script>
</body>
```

*(Sebagai pengingat keselamatan: Di beberapa browser, agar fitur lalu-lintas file `module` lokal antar rakitanmu ini berjalan nyata, sering kali dituntut kamu harus menjalankan file indeksmu dengan bantuan Server Lokal - seperangkat *Live Server* dari plugin VSCode - dan bukannya menklik buka klik dua kali polosan semata ke Browser).*
