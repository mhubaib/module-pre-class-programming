# Bab 6: Percabangan (Control Flow)

## Tujuan Pembelajaran

- Memahami konsep percabangan sebagai cara membelokkan alur eksekusi program.
- Menulis logika `if`, `else if`, dan `else` berdasarkan kondisi tertentu.
- Menguasai seleksi nilai menggunakan struktur `switch/case`.
- Memahami konsep nilai _Truthy_ dan _Falsy_ dalam evaluasi kondisi JavaScript.

---

## Materi Utama

Secara default, JavaScript membaca dan mengeksekusi kode dari baris pertama hingga baris terakhir secara berurutan, seperti aliran air dari atas ke bawah. Namun dalam program nyata, kita sering perlu membuat keputusan: "Jika pengguna belum mengisi formulir, jangan izinkan data disimpan."

Di sinilah peran **Control Flow** — mekanisme yang memungkinkan program mengambil jalur eksekusi yang berbeda berdasarkan kondisi tertentu.

---

### 1. Struktur Kondisional: `if`, `else if`, dan `else`

Perintah `if` memeriksa apakah sebuah kondisi bernilai `true`. Jika ya, blok kode di dalamnya akan dieksekusi. Jika tidak, blok tersebut dilewati.

#### A. `if` — Kondisi Tunggal

```javascript
let sisaBensin = 10;

if (sisaBensin < 20) {
  console.log("Peringatan: Bahan bakar hampir habis, segera isi ulang.");
}
// Output: Peringatan: Bahan bakar hampir habis, segera isi ulang.
```

Jika `sisaBensin` bernilai 25 atau lebih, blok di dalam `if` tidak akan dieksekusi dan program melanjutkan ke baris berikutnya.

#### B. `if...else` — Dua Alternatif

`else` menyediakan blok kode alternatif yang dieksekusi ketika kondisi `if` tidak terpenuhi.

```javascript
let nilaiUjian = 60;

if (nilaiUjian >= 75) {
  console.log("Selamat, kamu lulus!");
} else {
  console.log("Kamu perlu mengikuti ujian remedial.");
}
// Output: Kamu perlu mengikuti ujian remedial.
```

#### C. `if...else if...else` — Banyak Alternatif

Ketika ada lebih dari dua kemungkinan, gunakan `else if` untuk menambahkan kondisi tambahan.

```javascript
let lampu = "kuning";

if (lampu === "merah") {
  console.log("Berhenti.");
} else if (lampu === "kuning") {
  console.log("Bersiap, kurangi kecepatan.");
} else if (lampu === "hijau") {
  console.log("Jalan.");
} else {
  console.log("Warna lampu tidak dikenali.");
}
// Output: Bersiap, kurangi kecepatan.
```

JavaScript memeriksa kondisi dari atas ke bawah secara berurutan. Begitu satu kondisi terpenuhi, blok tersebut dieksekusi dan seluruh sisa kondisi `else if` maupun `else` dilewati.

**Contoh lengkap — Sistem penilaian:**

```javascript
let nilai = 82;
let predikat;

if (nilai >= 90) {
  predikat = "A";
} else if (nilai >= 80) {
  predikat = "B";
} else if (nilai >= 70) {
  predikat = "C";
} else if (nilai >= 60) {
  predikat = "D";
} else {
  predikat = "E";
}

console.log("Nilai  :", nilai); // Output: Nilai  : 82
console.log("Predikat:", predikat); // Output: Predikat: B
```

---

### 2. Seleksi Nilai Tetap: `switch / case`

Ketika kamu perlu membandingkan sebuah variabel dengan banyak kemungkinan nilai yang tetap dan spesifik, `switch` menawarkan struktur yang lebih rapi dibandingkan deretan `else if`.

```javascript
let hariKe = 3;

switch (hariKe) {
  case 1:
    console.log("Senin");
    break;
  case 2:
    console.log("Selasa");
    break;
  case 3:
    console.log("Rabu");
    break;
  case 4:
    console.log("Kamis");
    break;
  case 5:
    console.log("Jumat");
    break;
  default:
    console.log("Hari tidak valid.");
}
// Output: Rabu
```

**Cara kerja `switch`:**

1. Nilai dalam `switch(...)` dibandingkan dengan setiap `case` menggunakan perbandingan ketat (`===`).
2. Ketika kecocokan ditemukan, blok kode di bawah `case` tersebut dieksekusi.
3. Perintah `break` menghentikan eksekusi dan keluar dari blok `switch`.
4. `default` adalah blok yang dieksekusi jika tidak ada `case` yang cocok — setara dengan `else`.

**Peringatan — _Fall-through_:**

Jika `break` tidak ditulis, eksekusi akan berlanjut ke `case` berikutnya secara otomatis, meskipun nilainya tidak cocok. Perilaku ini disebut _fall-through_ dan umumnya merupakan sumber bug.

```javascript
let hari = 2;

switch (hari) {
  case 1:
    console.log("Senin");
  // break tidak ditulis!
  case 2:
    console.log("Selasa");
  // break tidak ditulis!
  case 3:
    console.log("Rabu");
    break;
}
// Output:
// Selasa
// Rabu   ← ikut tereksekusi karena tidak ada break di case 2
```

Namun, _fall-through_ terkadang dimanfaatkan secara sengaja untuk mengelompokkan beberapa `case` dengan perilaku yang sama:

```javascript
let bulan = 4;

switch (bulan) {
  case 4:
  case 6:
  case 9:
  case 11:
    console.log("Bulan ini memiliki 30 hari.");
    break;
  case 2:
    console.log("Bulan ini memiliki 28 atau 29 hari.");
    break;
  default:
    console.log("Bulan ini memiliki 31 hari.");
}
// Output: Bulan ini memiliki 30 hari.
```

**Perbandingan `if...else if` vs `switch`:**

|                       | `if...else if`                                      | `switch`                                                          |
| --------------------- | --------------------------------------------------- | ----------------------------------------------------------------- |
| Cocok untuk           | Kondisi dengan rentang nilai atau ekspresi kompleks | Perbandingan satu variabel dengan nilai-nilai tetap yang spesifik |
| Operator perbandingan | Bebas (`>`, `<`, `===`, dll.)                       | Hanya `===` (ketat)                                               |
| Keterbacaan           | Bisa panjang jika banyak kondisi                    | Lebih rapi untuk banyak nilai tetap                               |

---

### 3. Truthy dan Falsy

Dalam kondisi `if`, JavaScript tidak hanya menerima nilai Boolean (`true`/`false`) — ia akan mengevaluasi nilai apa pun dan menentukan apakah nilai tersebut dianggap "benar" atau "salah".

- **Truthy**: Nilai yang dianggap `true` oleh JavaScript saat dievaluasi sebagai kondisi.
- **Falsy**: Nilai yang dianggap `false` oleh JavaScript saat dievaluasi sebagai kondisi.

**Daftar nilai Falsy (hanya 6):**

```javascript
false; // Boolean false
0; // Angka nol
(""); // String kosong
null; // Nilai null
undefined; // Variabel yang belum diberi nilai
NaN; // Not a Number
```

**Semua nilai lainnya adalah Truthy**, termasuk:

```javascript
true          // Boolean true
1             // Angka selain 0 (termasuk negatif)
"halo"        // String yang tidak kosong
[]            // Array kosong sekalipun
{}            // Object kosong sekalipun
```

**Contoh — Falsy dalam kondisi `if`:**

```javascript
let namaPengguna = ""; // String kosong — Falsy

if (namaPengguna) {
  console.log("Halo,", namaPengguna);
} else {
  console.log("Nama pengguna belum diisi."); // Ini yang dieksekusi
}
// Output: Nama pengguna belum diisi.
```

**Contoh — Truthy dalam kondisi `if`:**

```javascript
let dataPengguna = { nama: "Budi", umur: 25 }; // Object — Truthy

if (dataPengguna) {
  console.log("Data ditemukan:", dataPengguna.nama); // Ini yang dieksekusi
}
// Output: Data ditemukan: Budi
```

**Penerapan praktis — Validasi input:**

```javascript
function prosesFormulir(namaInput, emailInput) {
  if (!namaInput) {
    console.log("Error: Nama tidak boleh kosong.");
    return;
  }

  if (!emailInput) {
    console.log("Error: Email tidak boleh kosong.");
    return;
  }

  console.log("Formulir berhasil dikirim untuk:", namaInput);
}

prosesFormulir("", "budi@email.com");
// Output: Error: Nama tidak boleh kosong.

prosesFormulir("Budi", "");
// Output: Error: Email tidak boleh kosong.

prosesFormulir("Budi", "budi@email.com");
// Output: Formulir berhasil dikirim untuk: Budi
```

---

### Kesimpulan

Percabangan adalah mekanisme fundamental yang memungkinkan program berperilaku secara dinamis berdasarkan kondisi yang berbeda. Dengan menguasai `if...else`, `switch`, dan konsep Truthy/Falsy, kamu memiliki kontrol penuh atas alur eksekusi program — fondasi yang diperlukan untuk membangun logika yang lebih kompleks.

**Ringkasan:**

| Konsep    | Kegunaan                                                                         |
| --------- | -------------------------------------------------------------------------------- |
| `if`      | Mengeksekusi blok kode jika kondisi bernilai `true`                              |
| `else`    | Blok alternatif jika kondisi `if` tidak terpenuhi                                |
| `else if` | Menambahkan kondisi tambahan di antara `if` dan `else`                           |
| `switch`  | Membandingkan satu variabel dengan banyak nilai tetap                            |
| `break`   | Menghentikan eksekusi di dalam blok `switch`                                     |
| `default` | Blok fallback di `switch` jika tidak ada `case` yang cocok                       |
| Truthy    | Nilai yang dianggap `true` saat dievaluasi sebagai kondisi                       |
| Falsy     | Enam nilai yang dianggap `false`: `false`, `0`, `""`, `null`, `undefined`, `NaN` |
