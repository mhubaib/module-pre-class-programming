# Bab 2: Sintaks, Statements, & Comments

## Tujuan Pembelajaran

- Memahami aturan dasar penulisan kode (sintaks) JavaScript.
- Membedakan perbedaan mendasar antara _Statement_ dan _Expression_.
- Menerapkan penulisan _Comments_ (komentar) untuk dokumentasi kode.

---

## Materi Utama

Pemrograman adalah cara kita memberikan serangkaian instruksi kepada komputer. Agar komputer (dalam hal ini _JavaScript Engine_ di browser) dapat memahami perintah kita, instruksi tersebut harus ditulis menggunakan tata bahasa yang baku dan konsisten. Tata bahasa baku dalam pemrograman disebut **Sintaks (Syntax)**.

---

### 1. Aturan Dasar Sintaks JavaScript

JavaScript memiliki beberapa aturan penulisan yang harus diikuti secara konsisten.

#### A. Bersifat _Case-Sensitive_

JavaScript membedakan antara huruf besar dan huruf kecil. Variabel bernama `nama`, `Nama`, dan `NAMA` akan dianggap sebagai tiga hal yang sepenuhnya berbeda.

```javascript
let nama = "Budi"; // variabel "nama"
let Nama = "Ani"; // variabel berbeda dari "nama"
let NAMA = "Citra"; // variabel berbeda dari keduanya

console.log(nama); // Output: Budi
console.log(Nama); // Output: Ani
console.log(NAMA); // Output: Citra
```

Kesalahan penulisan karena perbedaan huruf besar/kecil adalah salah satu penyebab error yang paling umum di kalangan pemula. Biasakan untuk selalu konsisten.

#### B. Penggunaan Titik Koma (`;`)

JavaScript menggunakan titik koma (`;`) di akhir baris untuk menandakan bahwa satu instruksi telah selesai — serupa dengan tanda titik di akhir kalimat dalam bahasa Indonesia.

```javascript
console.log("Halo Dunia");
console.log("Selamat belajar JavaScript!");
```

> **Catatan:** JavaScript modern memiliki fitur _Automatic Semicolon Insertion (ASI)_ yang secara otomatis menambahkan titik koma jika terlewat. Namun, untuk pemula yang sedang membangun kebiasaan menulis kode yang rapi, sangat disarankan untuk selalu menuliskan titik koma secara eksplisit guna menghindari bug yang sulit dilacak.

#### C. Konvensi Penulisan Nama (_Naming Convention_)

Selain aturan teknis, terdapat konvensi penulisan nama yang umum digunakan di JavaScript:

| Gaya Penulisan       | Contoh                          | Digunakan untuk     |
| -------------------- | ------------------------------- | ------------------- |
| **camelCase**        | `namaLengkap`, `totalHarga`     | Variabel dan fungsi |
| **PascalCase**       | `KeranjangBelanja`, `FormLogin` | Kelas (_class_)     |
| **UPPER_SNAKE_CASE** | `BATAS_MAKSIMUM`, `API_URL`     | Konstanta global    |

```javascript
// camelCase — variabel dan fungsi
let namaLengkap = "Budi Santoso";
function hitungTotal() {}

// UPPER_SNAKE_CASE — nilai konstanta yang tidak pernah berubah
const TARIF_PAJAK = 0.11;
const URL_API = "https://api.contoh.com";
```

---

### 2. Statement dan Expression

Dua istilah ini adalah fondasi cara berpikir dalam JavaScript. Memahami perbedaannya sejak awal akan memudahkan proses belajar selanjutnya.

#### A. Statement (Pernyataan)

_Statement_ adalah instruksi lengkap yang memerintahkan komputer untuk melakukan suatu tindakan. Statement tidak menghasilkan nilai yang bisa langsung digunakan di tempat lain — ia hanya menjalankan sebuah aksi.

```javascript
// Statement: membuat variabel
let umur = 20;

// Statement: percabangan logika
if (umur >= 18) {
  console.log("Sudah dewasa.");
}

// Statement: perulangan
for (let i = 0; i < 3; i++) {
  console.log("Pengulangan ke-" + i);
}
```

#### B. Expression (Ekspresi)

_Expression_ adalah potongan kode yang **menghasilkan sebuah nilai** setelah dievaluasi oleh komputer. Setiap expression selalu dapat disederhanakan menjadi satu nilai.

```javascript
// Expression aritmatika → menghasilkan nilai 15
5 + 10;

// Expression teks → menghasilkan string "halo budi"
"halo" + " " + "budi";

// Expression perbandingan → menghasilkan nilai true atau false
20 > 18;

// Expression pemanggilan fungsi → menghasilkan nilai kembalian fungsi
Math.max(10, 25);
```

**Hubungan Statement dan Expression:**

Dalam praktiknya, expression sering digunakan di dalam statement. Contoh di bawah adalah satu _statement_ yang berisi sebuah _expression_:

```javascript
// Statement: simpan nilai ke variabel
// Expression: "5 + 10" dievaluasi menjadi 15, lalu disimpan
let hasil = 5 + 10;

// Statement: tampilkan ke konsol
// Expression: "hasil * 2" dievaluasi menjadi 30
console.log(hasil * 2); // Output: 30
```

**Cara mudah membedakannya:**

- Jika potongan kode tersebut dapat menghasilkan sebuah nilai → itu adalah **Expression**.
- Jika potongan kode tersebut hanya menyuruh komputer melakukan sesuatu tanpa menghasilkan nilai secara langsung → itu adalah **Statement**.

---

### 3. Menulis Komentar (_Comments_)

Saat program berkembang menjadi ratusan atau ribuan baris kode, sangat mudah untuk lupa apa tujuan dari suatu blok kode — terutama setelah beberapa bulan tidak menyentuhnya.

**Komentar** adalah teks yang ditulis di dalam kode namun **sepenuhnya diabaikan** oleh JavaScript Engine saat kode dijalankan. Komentar ditulis semata-mata untuk dibaca oleh manusia sebagai catatan atau dokumentasi.

#### A. Komentar Satu Baris (`//`)

Gunakan dua garis miring (`//`). Semua teks di sebelah kanan simbol ini pada baris tersebut akan dianggap komentar.

```javascript
// Menghitung total harga setelah diskon 20%
let hargaAsli = 150000;
let diskon = hargaAsli * 0.2;
let hargaAkhir = hargaAsli - diskon;

console.log(hargaAkhir); // Output: 120000
```

#### B. Komentar Banyak Baris (`/* ... */`)

Gunakan `/*` untuk membuka dan `*/` untuk menutup. Berguna untuk menulis penjelasan yang lebih panjang, atau untuk menonaktifkan sementara blok kode saat proses pencarian _bug_ (_debugging_).

```javascript
/*
  Fungsi ini menghitung total pajak berdasarkan tarif yang berlaku.
  Tarif pajak saat ini: 11% (PPN sesuai regulasi 2022).
  
  Dibuat oleh : Hubaib
  Terakhir diperbarui : 2025
*/
let pajak = harga * 0.11;

/*
  Blok kode di bawah dinonaktifkan sementara selama proses debugging.
  Akan diaktifkan kembali setelah bug pada fungsi validasi diselesaikan.

  console.log("Data pengguna:", dataUser);
  kirimKeServer(dataUser);
*/
```

#### C. Panduan Menulis Komentar yang Baik

Komentar yang baik menjelaskan **mengapa** sesuatu ditulis seperti itu, bukan **apa** yang dilakukan kode tersebut. Kode yang ditulis dengan baik sudah cukup menjelaskan "apa"-nya sendiri.

```javascript
// Kurang informatif — hanya mengulangi apa yang sudah jelas dari kode
let total = harga * jumlah; // kalikan harga dengan jumlah

// Lebih informatif — menjelaskan alasan di balik keputusan teknis
// Harga dikalikan 1.11 karena sudah termasuk PPN 11%
let totalDenganPajak = harga * 1.11;
```

---

### Kesimpulan

Sintaks, statement, expression, dan komentar adalah fondasi dari setiap kode JavaScript yang kamu tulis. Menguasai aturan-aturan dasar ini sejak awal akan membuat proses belajar di topik yang lebih kompleks — seperti fungsi, kondisi, dan perulangan — menjadi jauh lebih mudah.

**Ringkasan:**

| Konsep           | Penjelasan                                                                            |
| ---------------- | ------------------------------------------------------------------------------------- |
| Sintaks          | Aturan tata bahasa yang harus diikuti agar kode dapat dipahami oleh JavaScript Engine |
| Case-Sensitive   | JavaScript membedakan huruf besar dan huruf kecil                                     |
| Titik koma (`;`) | Menandai akhir dari satu instruksi                                                    |
| camelCase        | Konvensi penulisan nama variabel dan fungsi di JavaScript                             |
| Statement        | Instruksi lengkap yang memerintahkan komputer melakukan sebuah tindakan               |
| Expression       | Potongan kode yang menghasilkan sebuah nilai                                          |
| Komentar `//`    | Komentar satu baris, diabaikan oleh JavaScript Engine                                 |
| Komentar `/* */` | Komentar banyak baris, diabaikan oleh JavaScript Engine                               |
