# Bab 15: Destructuring, Spread Operator, & Rest Parameter

## Tujuan Pembelajaran

- Menguasai _Destructuring_ untuk mengekstrak nilai dari Array dan Object secara ringkas.
- Mampu menduplikasi dan menggabungkan Array/Object menggunakan _Spread Operator_.
- Memahami kegunaan _Rest Parameter_ untuk menampung argumen dalam jumlah yang tidak tetap.

---

## Materi Utama

Bab ini memperkenalkan tiga fitur ES6 yang sangat sering digunakan dalam pengembangan JavaScript modern — terutama dalam framework seperti React dan Vue. Ketiganya dirancang untuk membuat kode lebih ringkas, mudah dibaca, dan lebih ekspresif.

---

### 1. Destructuring Assignment

**Destructuring** adalah cara mengekstrak nilai dari Array atau Object dan langsung menyimpannya ke dalam variabel dalam satu baris kode.

#### A. Object Destructuring

```javascript
// Cara lama — satu variabel per baris
const hero = {
  nama: "GatotKaca",
  kelas: "Tank",
  nyawa: 5000,
};

const nama = hero.nama;
const nyawa = hero.nyawa;

// Cara modern — Object Destructuring
const { nama, nyawa } = hero;

console.log(nama); // Output: "GatotKaca"
console.log(nyawa); // Output: 5000
```

**Destructuring dengan nama variabel berbeda:**

Jika kamu ingin menyimpan nilai ke variabel dengan nama berbeda dari key-nya:

```javascript
const pengguna = {
  namaLengkap: "Budi Santoso",
  emailAkun: "budi@email.com",
};

const { namaLengkap: nama, emailAkun: email } = pengguna;

console.log(nama); // Output: "Budi Santoso"
console.log(email); // Output: "budi@email.com"
```

**Destructuring dengan nilai default:**

```javascript
const produk = {
  nama: "Sepatu Lari",
  harga: 350000,
};

// "stok" tidak ada di object, maka menggunakan nilai default 0
const { nama, harga, stok = 0 } = produk;

console.log(nama); // Output: "Sepatu Lari"
console.log(stok); // Output: 0
```

**Destructuring pada parameter fungsi:**

```javascript
// Tanpa destructuring
function tampilkanPengguna(pengguna) {
  console.log(pengguna.nama, "-", pengguna.email);
}

// Dengan destructuring langsung di parameter
function tampilkanPengguna({ nama, email }) {
  console.log(nama, "-", email);
}

tampilkanPengguna({ nama: "Ani", email: "ani@email.com" });
// Output: Ani - ani@email.com
```

#### B. Array Destructuring

Nilai array diekstrak berdasarkan urutan indeks:

```javascript
const buah = ["Apel", "Jeruk", "Mangga", "Anggur"];

// Mengekstrak dua elemen pertama
const [pertama, kedua] = buah;

console.log(pertama); // Output: "Apel"
console.log(kedua); // Output: "Jeruk"
```

**Melewati elemen tertentu dengan koma kosong:**

```javascript
const nilai = [85, 92, 78, 95];

// Ambil elemen pertama dan ketiga, lewati yang kedua
const [pertama, , ketiga] = nilai;

console.log(pertama); // Output: 85
console.log(ketiga); // Output: 78
```

**Contoh praktis — Menukar nilai dua variabel:**

```javascript
let a = 10;
let b = 20;

// Cara lama memerlukan variabel sementara
// let temp = a; a = b; b = temp;

// Dengan array destructuring — lebih ringkas
[a, b] = [b, a];

console.log(a); // Output: 20
console.log(b); // Output: 10
```

---

### 2. Spread Operator (`...`)

**Spread Operator** ditulis sebagai tiga titik (`...`) dan berfungsi untuk "menyebarkan" elemen Array atau properti Object ke dalam konteks yang baru.

#### A. Menyalin Array

```javascript
const timA = ["Asep", "Budi"];
const timASalinan = [...timA]; // Salinan independen

// Mengubah salinan tidak memengaruhi array asli
timASalinan.push("Citra");

console.log(timA); // Output: ["Asep", "Budi"] — tidak berubah
console.log(timASalinan); // Output: ["Asep", "Budi", "Citra"]
```

> **Catatan:** Menyalin array dengan `const salinan = array` tidak membuat salinan baru — keduanya menunjuk ke data yang sama. Gunakan spread operator untuk membuat salinan yang benar-benar independen.

#### B. Menggabungkan Array

```javascript
const timA = ["Asep", "Budi"];
const timB = ["Citra", "Deni"];

const timGabungan = [...timA, ...timB];
console.log(timGabungan);
// Output: ["Asep", "Budi", "Citra", "Deni"]

// Menambahkan elemen baru di tengah
const timLengkap = [...timA, "Eko", ...timB];
console.log(timLengkap);
// Output: ["Asep", "Budi", "Eko", "Citra", "Deni"]
```

#### C. Menyalin dan Menggabungkan Object

```javascript
const dataKendaraan = { ban: 4, stir: 1 };
const mesin = { silinder: "V8", bahan_bakar: "Pertamax" };

// Menggabungkan dua object
const mobilBalap = {
  ...dataKendaraan,
  ...mesin,
  warna: "Merah",
};

console.log(mobilBalap);
// Output: { ban: 4, stir: 1, silinder: "V8", bahan_bakar: "Pertamax", warna: "Merah" }
```

**Menyalin dan menimpa properti tertentu:**

```javascript
const penggunaLama = {
  nama: "Budi",
  email: "budi@email.com",
  kota: "Jakarta",
};

// Buat salinan dengan kota yang diperbarui
const penggunaBaru = {
  ...penggunaLama,
  kota: "Bandung", // Menimpa nilai kota dari penggunaan spread
};

console.log(penggunaBaru);
// Output: { nama: "Budi", email: "budi@email.com", kota: "Bandung" }
console.log(penggunalama.kota); // Output: "Jakarta" — data asli tidak berubah
```

#### D. Spread dalam Pemanggilan Fungsi

```javascript
const angka = [3, 1, 7, 2, 9, 4];

// Meneruskan elemen array sebagai argumen terpisah
const tertinggi = Math.max(...angka);
const terendah = Math.min(...angka);

console.log(tertinggi); // Output: 9
console.log(terendah); // Output: 1
```

---

### 3. Rest Parameter (`...`)

**Rest Parameter** menggunakan simbol yang sama (`...`) dengan Spread Operator, namun fungsinya berlawanan — alih-alih menyebarkan data ke luar, Rest Parameter **mengumpulkan** sejumlah argumen yang tidak tetap menjadi sebuah Array di dalam fungsi.

```javascript
function checkout(...barang) {
  console.log("Jumlah item:", barang.length);
  console.log("Daftar belanja:", barang);
}

checkout("Minyak", "Telur", "Mie");
// Output: Jumlah item: 3
// Output: Daftar belanja: ["Minyak", "Telur", "Mie"]

checkout("Buku");
// Output: Jumlah item: 1
// Output: Daftar belanja: ["Buku"]

checkout("A", "B", "C", "D", "E");
// Output: Jumlah item: 5
// Output: Daftar belanja: ["A", "B", "C", "D", "E"]
```

**Kombinasi parameter tetap dan Rest Parameter:**

```javascript
function buatPesanan(namaPemesan, ...daftarMenu) {
  console.log("Pemesan  :", namaPemesan);
  console.log("Menu     :", daftarMenu.join(", "));
  console.log("Total item:", daftarMenu.length);
}

buatPesanan("Budi", "Nasi Goreng", "Es Teh", "Pisang Goreng");
// Output:
// Pemesan  : Budi
// Menu     : Nasi Goreng, Es Teh, Pisang Goreng
// Total item: 3
```

> **Aturan penting:** Rest Parameter harus selalu menjadi parameter **terakhir** dalam daftar parameter fungsi.

---

### 4. Perbedaan Spread vs Rest

Keduanya menggunakan simbol `...` namun digunakan dalam konteks yang berbeda:

|               | Spread Operator                                  | Rest Parameter                              |
| ------------- | ------------------------------------------------ | ------------------------------------------- |
| **Posisi**    | Di luar fungsi, saat pemanggilan                 | Di dalam definisi fungsi, di parameter      |
| **Arah data** | Menyebarkan Array/Object menjadi elemen terpisah | Mengumpulkan argumen terpisah menjadi Array |
| **Contoh**    | `Math.max(...angka)`                             | `function f(...args) {}`                    |

```javascript
const angka = [1, 2, 3];

// Spread — menyebarkan array saat memanggil fungsi
console.log(Math.max(...angka)); // Sama dengan Math.max(1, 2, 3)

// Rest — mengumpulkan argumen saat mendefinisikan fungsi
function jumlahkan(...nums) {
  return nums.reduce((total, n) => total + n, 0);
}
console.log(jumlahkan(1, 2, 3, 4, 5)); // Output: 15
```

---

### Kesimpulan

Destructuring, Spread Operator, dan Rest Parameter adalah fitur ES6 yang secara signifikan menyederhanakan penulisan kode JavaScript modern. Ketiga fitur ini sangat umum dijumpai dalam kode produksi, terutama saat bekerja dengan framework front-end seperti React dan Vue.

**Ringkasan:**

| Fitur                | Simbol                 | Fungsi                                      |
| -------------------- | ---------------------- | ------------------------------------------- |
| Object Destructuring | `const { key } = obj`  | Mengekstrak properti object ke variabel     |
| Array Destructuring  | `const [a, b] = arr`   | Mengekstrak elemen array berdasarkan urutan |
| Spread (Array)       | `[...arr]`             | Menyalin atau menggabungkan array           |
| Spread (Object)      | `{...obj}`             | Menyalin atau menggabungkan object          |
| Spread (Fungsi)      | `fn(...arr)`           | Meneruskan elemen array sebagai argumen     |
| Rest Parameter       | `function fn(...args)` | Mengumpulkan argumen menjadi array          |
