# Bab 39: Tipe-tipe Data di JavaScript

## Tujuan Pembelajaran
- Mengenali fungsi utama tipe data dalam mengelola informasi.
- Membedakan tipe data Primitif (String, Number, Boolean, Undefined, Null) dan Non-Primitif (Object, Array).
- Menggunakan perintah `typeof` untuk mengecek jenis suatu variabel aslinya secara dinamis.

## Materi Utama

JavaScript memiliki jenis wujud informasi yang bisa ia kenali, yang disebut dengan **Tipe Data**. Tanpa mengetahui tipe datanya, komputer tidak akan mengerti bahwa angka `5` bisa dijumlahkan, sementara huruf `"A"` hanya bisa ditampilkan. 

Uniknya, sistem tipe data Javascript sangat **Dinamis (Dynamic Typing)**. Artinya, sebuah kotak laci variabel bisa awalnya diisi dengan angka bulat, lalu selang sepuluh detik kemudian ditimpa dengan teks huruf alfabet tanpa membuat sistem memunculkan galat marah (Error). Komputer Javascript akan beradaptasi paham secara instan.

Tipe Data dipisahkan menjadi dua kasta: **Primitif (Asli Sederhana)** dan **Non-Primitif (Kompleks/Majemuk)**.

### 1. Tipe Data Primitif

Ini ibarat menyumpankan 1 wujud satuan informasi dasar ke dalam kotak variabel.

**A. String (Teks/Huruf)**
Digunakan untuk menyimpan huruf teks atau kalimat utuh. Tandanya adalah kamu mutlak harus **mengurung** teks tersebut menggunakan tanda kutip tunggal (`''`), kutip ganda (`""`), atau *backtick* (``` `` ```).
```javascript
let namaSiswa = "Budi Hartono";
let kotaTinggal = 'Bandung';
const dompetDigital = "Rp 150.000"; // Teks, bukan angka mutlak untuk perhitungan kalkulator
```

**B. Number (Angka)**
Menyimpan angka bilangan bulat, minus, maupun hitungan angka desimal (koma). Penulisannya **TIDAK dikurung** dengan kutip sama sekali. (Catatan dunia komputer, untuk membuat "koma", kita wajib memakai simbol Titik `.` karena bahasa acuan koding standar internasional memihak aturan Inggis).
```javascript
let umur = 25; 
let suhuAir = -7;
const nilaiPhi = 3.14; // Angka Desimal
```

**C. Boolean (Logika Benar / Salah)**
Tipe data ini sangat ringan, ia hanya merekam dua sifat kepastian mutlak yang saklek: **`true`** (Benar) dan **`false`** (Salah).
Sering dipakai untuk mencatat indikator stempel status.
```javascript
let sudahMenikah = false;
let sakelarLampuNyala = true;
```

**D. Undefined (Belum Ditentukan)**
Terjadi murni ketika sebuah laci nama variabel dipesan diciptakan namun **belum diisikan nilai sekecil apapun** kedalamnya.
```javascript
let namaAnak; 
console.log(namaAnak); // Hasil layarnya adalah: undefined (Data belum terdefinisi).
```

**E. Null (Kosong yang Disengaja)**
Walau statusnya mirip menganga seperti fungsi di atasnya, ia sangat berbeda fungsi secara takdirnya. `null` adalah keadaan dimana programmer **secara sadar kemauannya** mendeklarasikan mengosongkan melompongkan bak variabel. (Bukan terjadi tidak sengaja kayak `undefined`).

### 2. Tipe Data Non-Primitif

Tipe ini berfungsi meletakkan gerombolan banyak nilai informasi dasar merangkap ke dalam 1 slot variabel yang sama rapinya.

**A. Array (Daftar Kumpulan)**
Dipakai jika kau butuh meletakkan deretan rak sepatu kumpulan banyak data berurutan. Format kurungnya mutlak memakai **Kurung Siku `[]`**.
```javascript
let daftarBuah = ["Apel", "Jeruk", "Mangga"];
let deretUjian = [90, 85, 88, 100];
```

**B. Object (Data Lengkap Strukturnya)**
Digunakan saat satu benda itu memiliki berbagai identitas mendetail yang terkait nama sifatnya sendiri-sendiri (Contoh: Biodata Manusia, Detail Barang Tokopedia). Format kurungnya memakai pasangan **Kurung Kurawal `{}`**.
```javascript
// Sebuah wadah laci Object yang punya property nama, umur, pekerjaan.
let dataKtpUser = {
    namaLengkap: "Joko Anwar",
    umurPengguna: 28,
    alamat: "Sleman"
};
```

### 3. Cek Asal Usul Tipe (Fitur `typeof`)

Karena Javascript sanggup mengubah nilai wujud seenaknya (dinamis), kamu barangkali kelak bingung pas membaca sistem, "Variabel ini aselinya didalemnya nyimpen String atau Number sik?". Tanyalah jurus sakti utilitas pengeceknya dengan mantera: `typeof`.

```javascript
let umur = 50;
console.log(typeof umur); // Browser komputer membalas info: "number"

let tahun = "2025";
console.log(typeof tahun); // Browser berbunyi melapor: "string".  
// Walau wujudnya mirip bilangan tahun, tapi akibat dipenjara dalam jeruji kutip "", maka statusnya di mata mesin dianggap huruf huruf Teks murni yang tak bisa diikutsertakan ke dalam pertambahan matmatika silang sembarangan.
```
