# Bab 49: Scope, Hoisting, Closure

## Tujuan Pembelajaran
- Memahami `Scope` sebagai batasan wilayah di mana sebuah variabel bisa diakses.
- Mengetahui fenomena `Hoisting` yang terjadi pada saat kode JavaScript dievaluasi.
- Memahami konsep dasar `Closure` dan bagaimana sebuah fungsi mengingat tempat ia diciptakan.

## Materi Utama

Dalam mempelajari JavaScript, ada tiga konsep inti beruntun yang sering menjadi pertanyaan wajib saat *interview* kerja programmer: Scope, Hoisting, dan Closure. Memahami ketiganya akan membuatmu mengerti cara kerja mesin Javascript di belakang layar.

### 1. Scope (Cakupan Wilayah Akses)

Scope adalah hukum batas wilayah kerahasiaan. Di JavaScript, jika kamu menaruh variabel di dalam suatu pagar tertentu, variabel itu mungkin tidak bisa dilihat atau dipanggil oleh kode yang berada di luar pagar tersebut.

Ada dua jenis pagarisasi utama di JavaScript:

**A. Global Scope (Ruang Bebas Terbuka)**
Variabel yang dibuat bebas di luar fungsi apapun. Variabel ini bisa dibaca, diakses, dan diubah dari fungsi atau file mana saja di seluruh kodemu.
```javascript
let pajakNegara = 11; // Ini adalah Global Scope

function hitungHargaBeli() {
    // Mesin fungsi di dalam sini sukses leluasa mengintip dan memakai nilai pajakNegara dari luar
    console.log("Pajaknya adalah: " + pajakNegara); 
}
```

**B. Local/Block Scope (Kamar Tertutup)**
Sebaliknya, jika kamu membuat variabel di Jeroan/di dalam sebuah blok kurung kurawal `{}` (seperti fungsi, `if`, atau `for`), maka variabel itu murni hak milik mutlak ruangan itu saja. Kode di luar ruangan tak akan pernah sadar variabel itu eksis terbikin.

```javascript
function keamananAplikasi() {
    let passwordRahasia = "Budi123"; // Ini Local Scope
    console.log(passwordRahasia); // Berhasil tampil "Budi123"
}

keamananAplikasi();

// Saat kamu bermaksud memanggil password di ruang publik ini secara lancang:
console.log(passwordRahasia); 
// ERROR BESAR! Browser mengamuk tidak kenal karena passwordRahasia hanya hidup di bilik kamar fungsi keamananAplikasi.
```

### 2. Hoisting (Fenomena Variabel Melesat Terekam ke Atas)

Hoisting adalah kejadian ajaib murni bawaan Javascript: Mesin akan "membaca cepat (Scan)" duluan seluruh baris kodemu dari atas ke bawah sembari mencatat SEMUA deklarasi pembuatan fungsi dan variabel untuk diam-diam **"ditarik rekam melesat terbang diletakkan di atap memori teratas dokumen"**, SEBELUM mesin benar-benar menjalankan baris kodemu.

Akibat ajaibnya: Kita jadi bisa memanggil mengeksekusi fungsi di baris 1, BUKANNYA baris bawah, padahal rumus ketikan aseli fungsi itu baru kita ciptakan tuliskan di baris 100!

```javascript
// Baris 1: Memanggil fungsi secara ngawur walau belum di deklarasikan
sapaUser(); 

// ... baris ke 50 ...

// Baris 100: Pembentukan fungsi aselinya baru ada di sini
function sapaUser() {
    console.log("Halo Pelanggan!");
}

// Ajaibnya: Kodemu tidak Error. Malah sukses tercetak "Halo Pelanggan" duluan! 
// Karena fungsi di baris 100 tadi sudah kena sihir ditarik Hoisting duluan ke atap.
```

*(Pengecualian Mutlak: Perintah `let` dan `const` kebal / menolak di Hoisting. Inilah alasan utama kenapa syntax baru itu diciptakan JS modern guna memutus celah serampangan urutan kodingan programmer jaman purba `var` di versi jadul).*

### 3. Closure (Ingatan Lintas Waktu Sang Fungsi)

Closure adalah fenomena luar biasa di mana sebuah fungsi mesin di JavaScript itu ternyata punya **Ingatan Batin (Memori Perekam)**.

Definisi formal: Sebuah Fungsi Anak dijamin mutlak akan selalu mengingat dan bisa mengakses variabel apapun yang ada di rumah Fungsi Bapak tempat ia lahir dibesarkan, **Meskipun pada suatu saat nanti Fungsi Bapak tersebut sudah hancur lebur tuntas selesai dieksekusi mati masa penugasannya**.

```javascript
// Fungsi Bapak / Pembuat
function bikinMesinSaldo(saldoAwal) {
    let namaBank = "BCA"; 

    // Fungsi Anak yang hidup dan lahir di dalam perut fungsi Bapak
    return function ambilDuit(tarikan) {
        saldoAwal -= tarikan; 
        console.log("Kamu ngambil duit dari " + namaBank + ". Sisa duitmu: " + saldoAwal);
    }
}

// Kita jalanin Fungsi Bapak memodali awal tabungan 1 Juta. 
// Pas baris ini selesai diketik dieksekusi, statusnya fungsi bikinMesinSaldo harusnya sudah mati selesai dan musnah dihapus dari memori RAM komputer.
let mesinATM_Budi = bikinMesinSaldo(1000000);

// BUKTI KEAJAIBAN CLOSURE:
// Sebulan kemudian, kita mutlak baru mau jalanin tarik tunai:
mesinATM_Budi(200000); 

// TERCETAK HASILNYA NYALA NORMAL: "Kamu ngambil duit dari BCA. Sisa duitmu: 800000".
// LUAR BIASA! Padahal fungsi Bapak telah mati sebulan lalu, tapi si mesin anak secara magis masih setia MENGINGAT namaBank "BCA" dan modal 1 Juta aselinya!
// Inilah ilmu sihir Closure. Ingatan yang dibekukan batinnya terikat abadi.
```
