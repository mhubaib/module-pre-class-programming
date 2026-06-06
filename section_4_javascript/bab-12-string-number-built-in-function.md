# Bab 12: String & Number Built-in Function

## Tujuan Pembelajaran

- Menguasai fungsi bawaan (_Built-in Methods_) untuk memproses data String.
- Menggunakan metode String untuk mencari kata, mengubah casing, memotong, dan memformat teks.
- Menguasai fungsi bawaan untuk memproses dan memformat data Number.
- Mampu mengonversi String ke Number menggunakan `parseInt` dan `parseFloat`.

---

## Materi Utama

Sama seperti Array yang memiliki method bawaan seperti `.push()` dan `.length`, tipe data **String** dan **Number** juga dilengkapi dengan sejumlah method bawaan yang siap digunakan untuk berbagai operasi umum.

---

### 1. String Methods

Penguasaan String methods sangat penting karena hampir semua data yang diterima dari input pengguna — seperti kolom formulir, kotak pencarian, atau parameter URL — berbentuk String.

#### A. Mengubah Casing

```javascript
let sapaan = "Hai Apa Kabar Kawan!";

console.log(sapaan.toUpperCase()); // Output: "HAI APA KABAR KAWAN!"
console.log(sapaan.toLowerCase()); // Output: "hai apa kabar kawan!"
```

**Penggunaan umum:**

```javascript
// Normalisasi email agar tidak case-sensitive saat disimpan ke database
const emailInput = "Budi.Santoso@Gmail.COM";
const emailNormal = emailInput.toLowerCase();
console.log(emailNormal); // Output: "budi.santoso@gmail.com"

// Membandingkan dua string tanpa mempedulikan huruf besar/kecil
const a = "Jakarta";
const b = "JAKARTA";
console.log(a.toLowerCase() === b.toLowerCase()); // Output: true
```

#### B. Mencari Teks

**`.includes(kata)`** — Memeriksa apakah sebuah substring ada di dalam string. Mengembalikan `true` atau `false`.

```javascript
const judul = "Harga Beras Melonjak Tajam";

console.log(judul.includes("Beras")); // Output: true
console.log(judul.includes("Cuaca")); // Output: false

// Penggunaan praktis — validasi isi teks
if (judul.includes("Melonjak")) {
  console.log("Artikel berisi kata 'Melonjak'.");
}
```

**`.indexOf(kata)`** — Mengembalikan indeks posisi pertama kali substring ditemukan. Mengembalikan `-1` jika tidak ditemukan.

```javascript
const kalimat = "Harga Beras Melonjak";

console.log(kalimat.indexOf("Beras")); // Output: 6
console.log(kalimat.indexOf("Melonjak")); // Output: 12
console.log(kalimat.indexOf("Cuaca")); // Output: -1
```

**`.startsWith(kata)` dan `.endsWith(kata)`** — Memeriksa apakah string dimulai atau diakhiri dengan kata tertentu.

```javascript
const url = "https://www.contoh.com";

console.log(url.startsWith("https")); // Output: true
console.log(url.endsWith(".com")); // Output: true
console.log(url.startsWith("http://")); // Output: false
```

#### C. Memotong dan Mengekstrak Teks

**`.slice(mulai, akhir)`** — Mengekstrak bagian dari string dari indeks `mulai` hingga sebelum indeks `akhir`. Tidak mengubah string aslinya.

```javascript
const teks = "Mangga Apel Anggur";

console.log(teks.slice(7, 11)); // Output: "Apel"
console.log(teks.slice(0, 6)); // Output: "Mangga"
console.log(teks.slice(-6)); // Output: "Anggur" — indeks negatif dihitung dari akhir
```

**`.substring(mulai, akhir)`** — Mirip dengan `.slice()`, namun tidak mendukung indeks negatif.

```javascript
const nama = "Budi Santoso";
console.log(nama.substring(5)); // Output: "Santoso"
```

#### D. Menghapus Spasi

**`.trim()`** — Menghapus spasi di awal dan akhir string. Sangat berguna untuk membersihkan input pengguna.

```javascript
const inputKotor = "   budi@email.com   ";
const inputBersih = inputKotor.trim();
console.log(inputBersih); // Output: "budi@email.com"
console.log(inputBersih.length); // Output: 14 — tanpa spasi di ujung
```

#### E. Mengganti Teks

**`.replace(lama, baru)`** — Mengganti kemunculan pertama dari sebuah substring.

**`.replaceAll(lama, baru)`** — Mengganti semua kemunculan dari sebuah substring.

```javascript
const kalimat = "Saya suka kopi. Kopi adalah minuman favorit saya.";

console.log(kalimat.replace("kopi", "teh"));
// Output: "Saya suka teh. Kopi adalah minuman favorit saya." — hanya yang pertama

console.log(kalimat.replaceAll("kopi", "teh"));
// Output: "Saya suka teh. teh adalah minuman favorit saya." — semua diganti
```

#### F. Memecah String Menjadi Array

**`.split(pemisah)`** — Memecah string menjadi array berdasarkan karakter pemisah yang ditentukan.

```javascript
const tanggal = "2026-06-15";
const bagian = tanggal.split("-");
console.log(bagian); // Output: ["2026", "06", "15"]

const kalimat = "apel,jeruk,mangga";
const buah = kalimat.split(",");
console.log(buah); // Output: ["apel", "jeruk", "mangga"]
```

#### G. Mendapatkan Panjang String

**`.length`** — Mengembalikan jumlah karakter dalam string (termasuk spasi).

```javascript
const kata = "JavaScript";
console.log(kata.length); // Output: 10

// Validasi panjang password
const password = "abc";
if (password.length < 8) {
  console.log("Password terlalu pendek. Minimal 8 karakter.");
}
```

---

### 2. Number Methods

#### A. Membatasi Angka Desimal: `.toFixed(n)`

Membulatkan angka hingga `n` digit di belakang koma, dan mengembalikan hasilnya sebagai **String**.

```javascript
const harga = 50000.41928;

console.log(harga.toFixed(2)); // Output: "50000.42"
console.log(harga.toFixed(0)); // Output: "50000"
console.log(harga.toFixed(4)); // Output: "50000.4193"
```

**Penggunaan praktis — Menampilkan harga di struk:**

```javascript
const subtotal = 157333.3333;
const pajak = subtotal * 0.11;
const total = subtotal + pajak;

console.log("Subtotal : Rp", subtotal.toFixed(2)); // Output: Rp 157333.33
console.log("Pajak    : Rp", pajak.toFixed(2)); // Output: Rp 17306.67
console.log("Total    : Rp", total.toFixed(2)); // Output: Rp 174640.00
```

> **Catatan:** `.toFixed()` mengembalikan String, bukan Number. Jika hasil tersebut perlu digunakan dalam operasi matematika berikutnya, konversi kembali ke Number menggunakan `parseFloat()`.

#### B. Mengonversi String ke Number

Saat data diterima dari input pengguna atau file eksternal, angka sering kali berbentuk String. Menggunakan String dalam operasi matematika dapat menghasilkan perilaku yang tidak terduga.

```javascript
// Masalah: angka sebagai String
const inputHarga = "150";
console.log(inputHarga + 2); // Output: "1502" — penggabungan String, bukan penjumlahan!
console.log(typeof inputHarga); // Output: "string"
```

**`parseInt(string)`** — Mengonversi String menjadi bilangan bulat (_integer_).

```javascript
const tagihan = "500";
const admin = 250;

const tagihanAngka = parseInt(tagihan);
console.log(tagihanAngka + admin); // Output: 750 — penjumlahan yang benar
console.log(typeof tagihanAngka); // Output: "number"

// parseInt mengabaikan karakter non-angka di belakang
console.log(parseInt("42px")); // Output: 42
console.log(parseInt("3.99")); // Output: 3  — bagian desimal dipotong
```

**`parseFloat(string)`** — Mengonversi String menjadi bilangan desimal.

```javascript
const diskon = "12.5";
const hargaAwal = 100000;

const diskonAngka = parseFloat(diskon);
const hargaAkhir = hargaAwal - (hargaAwal * diskonAngka) / 100;
console.log(hargaAkhir); // Output: 87500
```

**`Number(string)`** — Cara alternatif untuk mengonversi String ke Number. Lebih ketat dari `parseInt` dan `parseFloat`.

```javascript
console.log(Number("42")); // Output: 42
console.log(Number("3.14")); // Output: 3.14
console.log(Number("42px")); // Output: NaN — tidak dapat dikonversi
console.log(Number("")); // Output: 0
```

**Perbandingan metode konversi:**

| Metode                  | Input       | Output | Catatan                                  |
| ----------------------- | ----------- | ------ | ---------------------------------------- |
| `parseInt("42px")`      | `"42px"`    | `42`   | Mengabaikan karakter di belakang angka   |
| `parseFloat("3.14abc")` | `"3.14abc"` | `3.14` | Mengabaikan karakter di belakang desimal |
| `Number("42px")`        | `"42px"`    | `NaN`  | Gagal jika ada karakter non-angka        |
| `Number("")`            | `""`        | `0`    | String kosong dikonversi ke 0            |

---

### 3. Simulasi Lengkap — Pemrosesan Data Formulir

Berikut contoh penggunaan berbagai String dan Number method dalam satu alur pemrosesan data:

```javascript
// Data yang diterima dari formulir pendaftaran (semuanya masih String)
const inputNama = "  budi santoso  ";
const inputEmail = "Budi.Santoso@GMAIL.COM";
const inputHarga = "75000.50";
const inputKupon = "DISKON20";

// Bersihkan dan normalisasi data
const namaBersih = inputNama.trim();
const namaTampil = namaBersih
  .split(" ")
  .map((kata) => kata.charAt(0).toUpperCase() + kata.slice(1))
  .join(" ");
const emailNormal = inputEmail.toLowerCase();
const hargaAngka = parseFloat(inputHarga);

// Proses logika bisnis
const punyaKupon = inputKupon.includes("DISKON");
const persenDiskon = punyaKupon
  ? parseInt(inputKupon.replace("DISKON", ""))
  : 0;
const hargaAkhir = hargaAngka - (hargaAngka * persenDiskon) / 100;

// Tampilkan hasil
console.log("Nama    :", namaTampil);
console.log("Email   :", emailNormal);
console.log("Harga   : Rp", hargaAngka.toFixed(2));
console.log("Diskon  :", persenDiskon + "%");
console.log("Total   : Rp", hargaAkhir.toFixed(2));

// Output:
// Nama    : Budi Santoso
// Email   : budi.santoso@gmail.com
// Harga   : Rp 75000.50
// Diskon  : 20%
// Total   : Rp 60000.40
```

---

### Kesimpulan

String dan Number methods adalah alat-alat praktis yang sangat sering digunakan dalam pengembangan web sehari-hari — mulai dari memvalidasi input pengguna, memformat tampilan harga, hingga membersihkan data sebelum dikirim ke server.

**Ringkasan String Methods:**

| Method                    | Fungsi                                              |
| ------------------------- | --------------------------------------------------- |
| `.toUpperCase()`          | Mengubah seluruh teks menjadi huruf kapital         |
| `.toLowerCase()`          | Mengubah seluruh teks menjadi huruf kecil           |
| `.includes(kata)`         | Memeriksa apakah substring ada (`true`/`false`)     |
| `.indexOf(kata)`          | Mencari posisi indeks pertama substring             |
| `.startsWith(kata)`       | Memeriksa apakah teks dimulai dengan kata tertentu  |
| `.endsWith(kata)`         | Memeriksa apakah teks diakhiri dengan kata tertentu |
| `.slice(i, j)`            | Mengekstrak bagian teks                             |
| `.trim()`                 | Menghapus spasi di awal dan akhir                   |
| `.replace(lama, baru)`    | Mengganti kemunculan pertama substring              |
| `.replaceAll(lama, baru)` | Mengganti semua kemunculan substring                |
| `.split(pemisah)`         | Memecah string menjadi array                        |
| `.length`                 | Mengembalikan panjang string                        |

**Ringkasan Number Methods:**

| Method            | Fungsi                                                |
| ----------------- | ----------------------------------------------------- |
| `.toFixed(n)`     | Membulatkan ke `n` digit desimal, hasil berupa String |
| `parseInt(str)`   | Mengonversi String ke bilangan bulat                  |
| `parseFloat(str)` | Mengonversi String ke bilangan desimal                |
| `Number(str)`     | Mengonversi String ke Number (ketat)                  |
