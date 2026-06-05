# Bab 3: Variable di JavaScript

## Tujuan Pembelajaran

- Memahami konsep dasar variabel sebagai wadah penyimpan data.
- Mengetahui cara mendeklarasikan variabel dengan sintaks modern (`let` dan `const`).
- Memahami alasan mengapa penggunaan `var` sudah banyak ditinggalkan.
- Mengikuti aturan dan standar penamaan variabel (_camelCase_).

---

## Materi Utama

Dalam memproses informasi, sebuah program perlu tempat untuk "mengingat" sebuah data sementara waktu sebelum data tersebut digunakan dalam perhitungan atau ditampilkan ke layar. Tempat penyimpanan data sementara di dalam memori komputer ini dinamakan **Variabel**.

**Analogi Kotak Laci:**

Bayangkan variabel sebagai sebuah kotak laci. Kamu menempelkan label di depan laci tersebut, misalnya "Koleksi Kemeja", lalu memasukkan beberapa kemeja ke dalamnya. Kapan pun kamu membutuhkan kemeja, kamu tidak perlu mencari di seluruh lemari — cukup buka laci berlabel "Koleksi Kemeja" dan isinya tersedia.

Dalam pemrograman, "Koleksi Kemeja" adalah **nama variabel**, dan kemeja-kemeja di dalamnya adalah **datanya**.

---

### 1. Mendeklarasikan Variabel: `let` dan `const`

Hingga tahun 2015, JavaScript hanya memiliki satu cara membuat variabel, yaitu menggunakan kata kunci `var`. Namun, `var` memiliki beberapa perilaku yang tidak konsisten dan sering memicu bug di program yang besar.

Pada pembaruan ES6 (2015), lahirlah dua kata kunci baru: **`let`** dan **`const`**. Keduanya inilah yang digunakan dalam penulisan kode JavaScript modern.

#### A. `let` — Variabel yang Dapat Diubah

Gunakan `let` jika nilai variabel tersebut **berpotensi berubah** di kemudian hari.

```javascript
// Membuat variabel "skorPemain" dengan nilai awal 0
let skorPemain = 0;

// Nilai diperbarui di ronde berikutnya
// Tidak perlu menulis "let" lagi — cukup sebut nama variabelnya
skorPemain = 50;

console.log(skorPemain); // Output: 50
```

**Contoh penggunaan `let` yang umum:**

```javascript
let namaLengkap = "Budi Santoso";
namaLengkap = "Budi S."; // Diizinkan — nama bisa diperbarui

let jumlahItem = 0;
jumlahItem = jumlahItem + 1; // Diizinkan — nilai bertambah
console.log(jumlahItem); // Output: 1
```

#### B. `const` — Variabel yang Tidak Dapat Diubah

Gunakan `const` untuk variabel yang nilainya bersifat tetap dan **tidak boleh diubah** setelah dideklarasikan pertama kali. Jika kamu mencoba mengubah nilainya, JavaScript akan langsung menampilkan error dan menghentikan program.

```javascript
// Membuat konstanta nilai phi
const nilaiPhi = 3.14;

// Mencoba mengubah nilainya
nilaiPhi = 3.15;
// Error: Assignment to constant variable.
// Program berhenti — nilai konstan tidak boleh ditimpa.
```

**Contoh penggunaan `const` yang umum:**

```javascript
const namaAplikasi = "TokoBuku";
const TARIF_PAJAK = 0.11;
const URL_API = "https://api.contoh.com/v1";

// Semua nilai di atas tidak akan pernah berubah sepanjang program berjalan
```

#### C. Kapan Menggunakan `let` vs `const`?

Panduan praktis yang digunakan di industri:

> **Selalu mulai dengan `const`.** Jika di kemudian hari logika programmu membutuhkan nilai tersebut untuk berubah, barulah ubah menjadi `let`.

Pendekatan ini menciptakan kebiasaan yang lebih aman karena mencegah perubahan nilai yang tidak disengaja.

```javascript
// Mulai dengan const
const harga = 50000;
const jumlah = 3;
const total = harga * jumlah;

console.log(total); // Output: 150000

// Jika nanti harga perlu berubah, ubah ke let:
let hargaDinamis = 50000;
hargaDinamis = 45000; // Diskon diterapkan
```

---

### 2. Mengapa `var` Sudah Ditinggalkan?

Untuk memahami alasan `var` tidak lagi direkomendasikan, perlu dipahami dua perilaku `var` yang berpotensi memicu bug:

**A. Tidak memiliki _block scope_:**

Variabel `var` tidak terbatas pada blok kode `{}` tempat ia dideklarasikan — ia dapat diakses dari luar blok tersebut, yang sering menyebabkan nilai yang tidak terduga.

```javascript
// Dengan var — berperilaku tidak terduga
if (true) {
  var pesanVar = "Halo dari var";
}
console.log(pesanVar); // Output: "Halo dari var"
// Variabel bocor ke luar blok if!

// Dengan let — berperilaku sesuai harapan
if (true) {
  let pesanLet = "Halo dari let";
}
console.log(pesanLet); // Error: pesanLet is not defined
// Variabel terbatas di dalam blok if, seperti yang diharapkan
```

**B. Dapat dideklarasikan ulang tanpa error:**

`var` mengizinkan pembuatan variabel dengan nama yang sama dua kali tanpa peringatan, yang dapat menimpa data secara tidak sengaja.

```javascript
// Dengan var — tidak ada peringatan meskipun nama sama
var email = "budi@email.com";
var email = "ani@email.com"; // Tidak ada error — nilai lama tertimpa diam-diam

// Dengan let — langsung error jika nama sudah digunakan
let email = "budi@email.com";
let email = "ani@email.com"; // Error: Identifier 'email' has already been declared
```

---

### 3. Aturan Penamaan Variabel

Penamaan variabel di JavaScript mengikuti aturan teknis dan konvensi yang perlu dipatuhi.

**Aturan teknis (wajib diikuti):**

| Aturan                                             | Contoh Salah       | Contoh Benar         |
| -------------------------------------------------- | ------------------ | -------------------- |
| Tidak boleh diawali angka                          | `let 1nama`        | `let nama1`          |
| Tidak boleh mengandung spasi                       | `let nama lengkap` | `let namaLengkap`    |
| Tidak boleh menggunakan simbol kecuali `_` dan `$` | `let nama-user`    | `let namaUser`       |
| Tidak boleh menggunakan kata kunci JavaScript      | `let const = 5`    | `let nilaiTetap = 5` |

**Kata kunci yang tidak boleh digunakan sebagai nama variabel** (contoh sebagian): `let`, `const`, `var`, `function`, `if`, `else`, `for`, `while`, `return`, `class`, `new`, `this`.

**Konvensi penamaan (sangat direkomendasikan):**

Gunakan **camelCase** untuk penamaan variabel dan fungsi di JavaScript — huruf pertama kata pertama ditulis kecil, dan huruf pertama setiap kata berikutnya ditulis kapital.

```javascript
// camelCase — standar untuk variabel dan fungsi
let namaLengkap = "Budi Santoso";
let totalHargaAkhir = 150000;
let jumlahItemDiKeranjang = 3;

// Hindari singkatan yang tidak jelas
let x = "Budi"; // Kurang baik — tidak menjelaskan apa isinya
let namaPengguna = "Budi"; // Lebih baik — langsung terbaca tujuannya
```

> **Prinsip penting:** Nama variabel yang baik adalah nama yang dapat dibaca dan dipahami orang lain (atau dirimu sendiri di masa mendatang) tanpa perlu penjelasan tambahan. `namaLengkap` jauh lebih informatif daripada `nl` atau `x`.

---

### 4. Contoh Lengkap — Variabel dalam Program Sederhana

Berikut adalah contoh penggunaan variabel `let` dan `const` dalam sebuah program kecil yang menghitung total belanja:

```javascript
// Informasi produk — tidak akan berubah, gunakan const
const namaProduk = "Sepatu Lari";
const hargaSatuan = 350000;
const TARIF_PAJAK = 0.11;

// Data transaksi — bisa berubah, gunakan let
let jumlahDibeli = 2;
let totalSebelumPajak = hargaSatuan * jumlahDibeli;
let pajak = totalSebelumPajak * TARIF_PAJAK;
let totalAkhir = totalSebelumPajak + pajak;

console.log("Produk     :", namaProduk);
console.log("Harga      : Rp", hargaSatuan);
console.log("Jumlah     :", jumlahDibeli);
console.log("Subtotal   : Rp", totalSebelumPajak);
console.log("Pajak (11%): Rp", pajak);
console.log("Total      : Rp", totalAkhir);

// Output:
// Produk     : Sepatu Lari
// Harga      : Rp 350000
// Jumlah     : 2
// Subtotal   : Rp 700000
// Pajak (11%): Rp 77000
// Total      : Rp 777000
```

---

### Kesimpulan

Variabel adalah salah satu konsep paling fundamental dalam pemrograman. Memilih antara `let` dan `const` dengan tepat, serta menamai variabel dengan jelas, adalah kebiasaan yang membedakan kode yang mudah dipelihara dari kode yang sulit dipahami.

**Ringkasan:**

| Konsep        | Penjelasan                                                                                     |
| ------------- | ---------------------------------------------------------------------------------------------- |
| Variabel      | Wadah untuk menyimpan data sementara di dalam memori program                                   |
| `let`         | Variabel yang nilainya dapat diubah setelah dideklarasikan                                     |
| `const`       | Variabel yang nilainya tetap dan tidak dapat diubah                                            |
| `var`         | Kata kunci lama yang tidak lagi direkomendasikan                                               |
| camelCase     | Konvensi penamaan variabel: `namaLengkap`, `totalHarga`                                        |
| _Block scope_ | Variabel `let` dan `const` hanya dapat diakses di dalam blok `{}` tempat mereka dideklarasikan |
