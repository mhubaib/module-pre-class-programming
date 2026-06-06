# Bab 9: JavaScript Function

## Tujuan Pembelajaran

- Memahami konsep Function sebagai blok kode yang dapat digunakan kembali.
- Menguasai anatomi Function: deklarasi, parameter, argumen, dan `return`.
- Mengenal variasi penulisan fungsi: Function Expression dan Arrow Function.

---

## Materi Utama

Saat membangun program yang kompleks, kamu mungkin menemukan situasi di mana logika yang sama perlu dijalankan di beberapa tempat yang berbeda. Menyalin dan menempelkan kode yang sama berulang kali melanggar prinsip dasar pemrograman yang disebut **DRY — _Don't Repeat Yourself_**.

Solusinya adalah **Function** (Fungsi) — sebuah blok kode yang diberi nama, dapat dipanggil kapan saja dan sebanyak yang dibutuhkan, tanpa perlu menuliskan ulang logikanya.

**Analogi:**

Bayangkan sebuah fungsi seperti mesin blender. Kamu merakitnya sekali, lalu tinggal memasukkan bahan (input), dan mesin secara otomatis mengolahnya menjadi hasil (output). Kamu tidak perlu merakit ulang mesinnya setiap kali ingin membuat jus.

---

### 1. Deklarasi dan Pemanggilan Fungsi

Untuk membuat fungsi, gunakan kata kunci `function`, diikuti nama fungsi, tanda kurung `()`, dan blok kode dalam kurung kurawal `{}`.

```javascript
// 1. Mendefinisikan fungsi
function tampilkanSambutan() {
  console.log("Selamat datang! Silakan selesaikan proses pembayaran.");
}

// 2. Memanggil fungsi
tampilkanSambutan();
// Output: Selamat datang! Silakan selesaikan proses pembayaran.
```

Fungsi tidak akan dieksekusi hanya karena sudah didefinisikan. Ia harus **dipanggil** secara eksplisit menggunakan nama fungsi diikuti tanda kurung `()`.

```javascript
// Fungsi dapat dipanggil berkali-kali
tampilkanSambutan(); // Dipanggil pertama kali
tampilkanSambutan(); // Dipanggil kedua kali
tampilkanSambutan(); // Dipanggil ketiga kali
// Ketiganya mencetak output yang sama tanpa menulis ulang logika
```

---

### 2. Parameter dan Argumen

Fungsi yang hanya menghasilkan output tetap kurang fleksibel. Agar fungsi dapat bekerja dengan data yang berbeda-beda, gunakan **Parameter**.

- **Parameter**: Nama variabel yang dideklarasikan di dalam tanda kurung fungsi sebagai "pintu masuk" data.
- **Argumen**: Nilai nyata yang diberikan ke fungsi saat dipanggil.

```javascript
// "namaDepan" dan "namaBelakang" adalah parameter
function sapa(namaDepan, namaBelakang) {
  console.log("Halo,", namaDepan, namaBelakang + "!");
}

// "Budi" dan "Santoso" adalah argumen
sapa("Budi", "Santoso"); // Output: Halo, Budi Santoso!
sapa("Ani", "Rahayu"); // Output: Halo, Ani Rahayu!
```

**Parameter dengan nilai default:**

Jika argumen tidak diberikan saat pemanggilan, kamu dapat mendefinisikan nilai default untuk parameter:

```javascript
function hitungDiskon(harga, persentase = 10) {
  return harga - (harga * persentase) / 100;
}

console.log(hitungDiskon(100000, 20)); // Output: 80000 — menggunakan persentase 20
console.log(hitungDiskon(100000)); // Output: 90000 — menggunakan default 10
```

**Contoh lengkap — Fungsi dengan beberapa parameter:**

```javascript
function tampilkanProduk(nama, harga, stok) {
  console.log("Produk :", nama);
  console.log("Harga  : Rp", harga);
  console.log("Stok   :", stok, "unit");
  console.log("---");
}

tampilkanProduk("Sepatu Lari", 350000, 25);
tampilkanProduk("Kaos Polos", 85000, 100);
// Output:
// Produk : Sepatu Lari
// Harga  : Rp 350000
// Stok   : 25 unit
// ---
// Produk : Kaos Polos
// Harga  : Rp 85000
// Stok   : 100 unit
// ---
```

---

### 3. Mengembalikan Nilai: `return`

Sejauh ini, fungsi hanya mencetak output ke konsol. Namun dalam banyak kasus, kita perlu fungsi untuk **mengembalikan nilai** yang dapat disimpan ke variabel atau digunakan dalam ekspresi lain.

Gunakan perintah `return` untuk mengembalikan nilai dari dalam fungsi.

```javascript
function hitungDiskon(harga) {
  let potongan = harga * 0.5;
  return potongan; // Nilai ini dikembalikan ke pemanggil fungsi
}

// Nilai kembalian ditangkap dalam variabel
let hargaSetelahDiskon = hitungDiskon(50000);
console.log(hargaSetelahDiskon); // Output: 25000

// Atau langsung digunakan dalam ekspresi
console.log("Total:", hitungDiskon(80000) + hitungDiskon(60000)); // Output: Total: 70000
```

**Perilaku penting `return`:**

Begitu `return` dieksekusi, fungsi langsung berhenti. Kode setelah `return` tidak akan pernah dijalankan.

```javascript
function cekUmur(umur) {
  if (umur < 18) {
    return "Belum memenuhi syarat.";
    // Baris di bawah ini tidak akan pernah dieksekusi
    console.log("Ini tidak akan muncul.");
  }
  return "Memenuhi syarat.";
}

console.log(cekUmur(15)); // Output: Belum memenuhi syarat.
console.log(cekUmur(20)); // Output: Memenuhi syarat.
```

**Perbedaan fungsi dengan dan tanpa `return`:**

```javascript
// Tanpa return — hanya mencetak, tidak bisa digunakan lebih lanjut
function cetakTotal(a, b) {
  console.log(a + b);
}
let hasil = cetakTotal(3, 4); // Mencetak 7
console.log(hasil); // Output: undefined — tidak ada nilai yang dikembalikan

// Dengan return — nilai dapat disimpan dan digunakan kembali
function hitungTotal(a, b) {
  return a + b;
}
let total = hitungTotal(3, 4);
console.log(total); // Output: 7
console.log(total * 2); // Output: 14 — dapat digunakan dalam operasi lain
```

---

### 4. Function Expression

Selain menggunakan deklarasi `function`, kamu juga dapat mendefinisikan fungsi dan menyimpannya dalam sebuah variabel. Ini disebut **Function Expression**.

```javascript
// Function Expression — fungsi disimpan dalam variabel
const hitungLuasPersegiPanjang = function (panjang, lebar) {
  return panjang * lebar;
};

console.log(hitungLuasPersegiPanjang(5, 3)); // Output: 15
```

**Perbedaan antara Function Declaration dan Function Expression:**

|                                        | Function Declaration  | Function Expression                              |
| -------------------------------------- | --------------------- | ------------------------------------------------ |
| Sintaks                                | `function nama() {}`  | `const nama = function() {}`                     |
| Dapat dipanggil sebelum didefinisikan? | Ya (_hoisting_)       | Tidak                                            |
| Penggunaan umum                        | Fungsi utama dan umum | Fungsi yang diberikan sebagai nilai atau argumen |

---

### 5. Arrow Function (ES6)

Diperkenalkan pada ES6 (2015), **Arrow Function** adalah cara penulisan fungsi yang lebih ringkas menggunakan simbol panah `=>`.

**Konversi dari Function Expression ke Arrow Function:**

```javascript
// Function Expression (cara lama)
const kali = function (x, y) {
  return x * y;
};

// Arrow Function (cara modern)
const kali = (x, y) => {
  return x * y;
};

// Arrow Function ringkas — jika hanya satu ekspresi, kurung kurawal dan return dapat dihilangkan
const kali = (x, y) => x * y;

console.log(kali(3, 4)); // Output: 12
```

**Variasi penulisan Arrow Function:**

```javascript
// Tanpa parameter
const salam = () => "Halo!";
console.log(salam()); // Output: Halo!

// Satu parameter — tanda kurung boleh dihilangkan
const kuadrat = (n) => n * n;
console.log(kuadrat(5)); // Output: 25

// Dua parameter atau lebih — tanda kurung wajib ada
const tambah = (a, b) => a + b;
console.log(tambah(3, 7)); // Output: 10

// Lebih dari satu baris — kurung kurawal dan return diperlukan kembali
const hitungPPN = (harga) => {
  const tarif = 0.11;
  const pajak = harga * tarif;
  return harga + pajak;
};
console.log(hitungPPN(100000)); // Output: 111000
```

> **Catatan:** Arrow Function sangat umum digunakan dalam pengembangan modern, terutama dalam framework seperti React. Biasakan diri dengan sintaks ini karena akan sering dijumpai dalam kode JavaScript profesional.

---

### 6. Simulasi Lengkap — Sistem Kalkulator Belanja

Berikut contoh program yang menggabungkan seluruh konsep function yang telah dipelajari:

```javascript
// Fungsi-fungsi pembantu
const hitungSubtotal = (harga, jumlah) => harga * jumlah;
const hitungPPN = (subtotal, tarif = 0.11) => subtotal * tarif;
const hitungTotal = (subtotal, pajak) => subtotal + pajak;

function cetakStruk(namaProduk, harga, jumlah) {
  const subtotal = hitungSubtotal(harga, jumlah);
  const pajak = hitungPPN(subtotal);
  const total = hitungTotal(subtotal, pajak);

  console.log("================================");
  console.log("Produk    :", namaProduk);
  console.log("Harga     : Rp", harga);
  console.log("Jumlah    :", jumlah);
  console.log("Subtotal  : Rp", subtotal);
  console.log("PPN (11%) : Rp", pajak);
  console.log("Total     : Rp", total);
  console.log("================================");
}

cetakStruk("Sepatu Lari", 350000, 2);
// Output:
// ================================
// Produk    : Sepatu Lari
// Harga     : Rp 350000
// Jumlah    : 2
// Subtotal  : Rp 700000
// PPN (11%) : Rp 77000
// Total     : Rp 777000
// ================================
```

---

### Kesimpulan

Function adalah salah satu konsep terpenting dalam JavaScript. Dengan membungkus logika ke dalam fungsi, kamu dapat membangun program yang lebih terstruktur, mudah dibaca, dan mudah dipelihara. Arrow Function memperkuat kemampuan ini dengan sintaks yang lebih ringkas dan modern.

**Ringkasan:**

| Konsep               | Penjelasan                                                                 |
| -------------------- | -------------------------------------------------------------------------- |
| Function Declaration | Mendefinisikan fungsi dengan kata kunci `function`                         |
| Function Expression  | Menyimpan fungsi ke dalam variabel                                         |
| Arrow Function       | Penulisan fungsi ringkas menggunakan `=>` (ES6)                            |
| Parameter            | Variabel penerima data yang didefinisikan saat deklarasi fungsi            |
| Argumen              | Nilai nyata yang diberikan saat fungsi dipanggil                           |
| `return`             | Mengembalikan nilai dari fungsi ke pemanggil; menghentikan eksekusi fungsi |
| Nilai default        | Nilai parameter yang digunakan jika argumen tidak diberikan                |
