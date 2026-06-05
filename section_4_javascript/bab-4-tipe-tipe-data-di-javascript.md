# Bab 4: Tipe-tipe Data di JavaScript

## Tujuan Pembelajaran

- Mengenali fungsi utama tipe data dalam mengelola informasi.
- Membedakan tipe data Primitif (String, Number, Boolean, Undefined, Null) dan Non-Primitif (Object, Array).
- Menggunakan operator `typeof` untuk memeriksa tipe data sebuah variabel secara dinamis.

---

## Materi Utama

JavaScript memiliki berbagai jenis nilai yang dapat disimpan dan diproses, yang dikenal sebagai **Tipe Data**. Tanpa informasi tipe data, komputer tidak akan tahu bahwa angka `5` dapat dijumlahkan, sementara teks `"A"` hanya dapat ditampilkan.

Salah satu karakteristik unik JavaScript adalah sistem **_Dynamic Typing_** — sebuah variabel dapat diisi dengan tipe data apa pun, dan bahkan dapat diubah tipenya sewaktu-waktu tanpa menghasilkan error. JavaScript akan menyesuaikan diri secara otomatis.

```javascript
// JavaScript menerima perubahan tipe data tanpa error
let data = 42; // awalnya Number
data = "empat puluh"; // diubah menjadi String — JavaScript tidak keberatan
data = true; // diubah lagi menjadi Boolean
```

Tipe data dibagi menjadi dua kelompok: **Primitif** dan **Non-Primitif**.

---

### 1. Tipe Data Primitif

Tipe data primitif menyimpan **satu nilai tunggal** dalam sebuah variabel.

#### A. String (Teks)

Digunakan untuk menyimpan teks atau kalimat. Nilai String harus diapit oleh tanda kutip tunggal (`''`), kutip ganda (`""`), atau _backtick_ (` `` `).

```javascript
let namaSiswa = "Budi Hartono";
let kotaTinggal = "Bandung";
const keterangan = `Siswa tinggal di ${kotaTinggal}`; // Template literal dengan backtick

// Perhatikan: angka dalam kutip adalah String, bukan Number
const hargaTampil = "Rp 150.000"; // Ini teks, tidak bisa dihitung secara matematis
```

> **Catatan:** _Backtick_ (`` ` ``) memiliki kemampuan tambahan bernama _Template Literal_ — memungkinkan penyisipan nilai variabel langsung ke dalam teks menggunakan `${}`.

#### B. Number (Angka)

Digunakan untuk menyimpan angka bulat, negatif, maupun desimal. Penulisannya **tidak** menggunakan tanda kutip. Untuk angka desimal, gunakan titik (`.`), bukan koma.

```javascript
let umur = 25;
let suhuAir = -7;
const nilaiPhi = 3.14;
let persentase = 98.6;
```

**Nilai Number khusus yang perlu diketahui:**

```javascript
console.log(10 / 0); // Output: Infinity
console.log("abc" * 2); // Output: NaN (Not a Number — hasil operasi yang tidak valid)
```

#### C. Boolean (Logika)

Boolean hanya memiliki dua kemungkinan nilai: **`true`** (benar) dan **`false`** (salah). Tipe ini sangat sering digunakan untuk menyimpan status atau kondisi.

```javascript
let sudahLogin = false;
let lampiNyala = true;
let formTerkirim = false;

// Boolean juga dihasilkan dari operasi perbandingan
console.log(10 > 5); // Output: true
console.log(3 === 7); // Output: false
```

#### D. Undefined (Belum Didefinisikan)

Terjadi ketika sebuah variabel dideklarasikan namun **belum diberi nilai**. JavaScript secara otomatis mengisi variabel tersebut dengan `undefined`.

```javascript
let namaAnak;
console.log(namaAnak); // Output: undefined
console.log(typeof namaAnak); // Output: "undefined"
```

#### E. Null (Kosong yang Disengaja)

`null` adalah nilai yang secara **sengaja** ditetapkan oleh programmer untuk menyatakan bahwa sebuah variabel saat ini tidak memiliki nilai. Berbeda dari `undefined` yang terjadi secara otomatis, `null` adalah keputusan eksplisit.

```javascript
let dataPengguna = null; // Sengaja dikosongkan karena data belum dimuat

// Setelah data dimuat dari server, baru diisi nilainya
dataPengguna = { nama: "Budi", umur: 25 };
```

**Perbedaan `undefined` vs `null`:**

|          | `undefined`                        | `null`                                      |
| -------- | ---------------------------------- | ------------------------------------------- |
| Penyebab | Otomatis oleh JavaScript           | Disengaja oleh programmer                   |
| Artinya  | Variabel belum pernah diberi nilai | Variabel sengaja dikosongkan                |
| `typeof` | `"undefined"`                      | `"object"` _(perilaku historis JavaScript)_ |

---

### 2. Tipe Data Non-Primitif

Tipe data non-primitif digunakan untuk menyimpan **kumpulan nilai** dalam satu variabel.

#### A. Array (Daftar Berurutan)

Digunakan untuk menyimpan daftar beberapa nilai secara berurutan dalam satu variabel. Ditulis menggunakan **kurung siku `[]`**, dengan setiap nilai dipisahkan oleh koma.

```javascript
let daftarBuah = ["Apel", "Jeruk", "Mangga"];
let nilaiUjian = [90, 85, 88, 100];
let campuran = ["Budi", 25, true]; // Array bisa menyimpan tipe data berbeda
```

Setiap nilai dalam array dapat diakses menggunakan **indeks** yang dimulai dari angka `0`:

```javascript
console.log(daftarBuah[0]); // Output: "Apel"    ← indeks ke-0
console.log(daftarBuah[1]); // Output: "Jeruk"   ← indeks ke-1
console.log(daftarBuah[2]); // Output: "Mangga"  ← indeks ke-2
```

#### B. Object (Data Terstruktur)

Digunakan ketika sebuah entitas memiliki beberapa atribut yang terkait satu sama lain — misalnya data pengguna yang memiliki nama, umur, dan alamat. Ditulis menggunakan **kurung kurawal `{}`** dengan format `kunci: nilai`.

```javascript
let dataUser = {
  namaLengkap: "Joko Anwar",
  umur: 28,
  alamat: "Sleman",
  sudahLogin: true,
};
```

Nilai dalam object dapat diakses menggunakan **notasi titik** (`.`) atau **notasi kurung siku**:

```javascript
console.log(dataUser.namaLengkap); // Output: "Joko Anwar"
console.log(dataUser.umur); // Output: 28
console.log(dataUser["alamat"]); // Output: "Sleman"
```

---

### 3. Memeriksa Tipe Data (`typeof`)

Karena JavaScript bersifat dinamis, kadang kamu perlu memastikan tipe data dari sebuah variabel, terutama ketika bekerja dengan data yang datang dari luar (misalnya dari input pengguna atau server). Gunakan operator `typeof` untuk memeriksanya.

```javascript
let umur = 50;
let tahun = "2025";
let aktif = true;
let data;

console.log(typeof umur); // Output: "number"
console.log(typeof tahun); // Output: "string"
console.log(typeof aktif); // Output: "boolean"
console.log(typeof data); // Output: "undefined"
```

**Mengapa `"2025"` bertipe String, bukan Number?**

```javascript
let tahun = "2025";
// Meskipun isinya tampak seperti angka,
// karena diapit tanda kutip, JavaScript memperlakukannya sebagai teks.

console.log(typeof tahun); // Output: "string"
console.log(tahun + 1); // Output: "20251"  ← penggabungan teks, bukan penjumlahan!

let tahunAngka = 2025;
console.log(tahunAngka + 1); // Output: 2026  ← penjumlahan matematika yang benar
```

**Contoh penggunaan `typeof` dalam program:**

```javascript
function tampilkanInfo(nilai) {
  console.log("Nilai  :", nilai);
  console.log("Tipe   :", typeof nilai);
}

tampilkanInfo(42); // Nilai: 42      | Tipe: number
tampilkanInfo("Halo"); // Nilai: Halo    | Tipe: string
tampilkanInfo(true); // Nilai: true    | Tipe: boolean
tampilkanInfo([1, 2, 3]); // Nilai: [1,2,3] | Tipe: object
tampilkanInfo({ nama: "X" }); // Nilai: {nama:X}| Tipe: object
```

---

### Kesimpulan

Memahami tipe data adalah fondasi yang diperlukan untuk menulis logika program yang benar. Banyak bug dalam JavaScript terjadi karena ketidaktahuan tentang tipe data — misalnya menjumlahkan angka yang tidak sengaja tersimpan sebagai String, atau mengakses properti dari variabel yang bernilai `null`.

**Ringkasan Tipe Data:**

| Tipe Data   | Kelompok     | Contoh Nilai                          |
| ----------- | ------------ | ------------------------------------- |
| `String`    | Primitif     | `"Halo"`, `'Budi'`, `` `Teks` ``      |
| `Number`    | Primitif     | `25`, `-7`, `3.14`, `NaN`, `Infinity` |
| `Boolean`   | Primitif     | `true`, `false`                       |
| `Undefined` | Primitif     | `undefined` (otomatis)                |
| `Null`      | Primitif     | `null` (disengaja)                    |
| `Array`     | Non-Primitif | `["Apel", "Jeruk"]`, `[1, 2, 3]`      |
| `Object`    | Non-Primitif | `{ nama: "Budi", umur: 25 }`          |
