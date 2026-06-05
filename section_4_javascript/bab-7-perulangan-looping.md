# Bab 7: Perulangan (Looping)

## Tujuan Pembelajaran

- Memahami konsep otomasi perulangan tugas dalam pemrograman.
- Menguasai struktur perulangan `for` untuk jumlah iterasi yang sudah diketahui.
- Menguasai cara kerja perulangan `while` dan `do...while` untuk jumlah iterasi yang belum diketahui.
- Mengetahui cara menghentikan dan melewati iterasi menggunakan `break` dan `continue`.

---

## Materi Utama

Salah satu alasan komputer diciptakan adalah untuk mengerjakan tugas berulang dengan cepat dan konsisten. Di JavaScript, mekanisme ini disebut **Looping** (Perulangan) atau Iterasi.

Bayangkan kamu perlu mencetak teks "Halo Dunia" sebanyak 100 kali. Menulis `console.log` secara manual 100 kali jelas bukan pendekatan yang tepat. Dengan _looping_, kamu cukup menulis instruksi tersebut satu kali dan membiarkan mesin mengulanginya sebanyak yang dibutuhkan.

---

### 1. Perulangan dengan Jumlah Pasti: `for`

Gunakan `for` ketika **jumlah iterasi sudah diketahui** sejak awal. Strukturnya terdiri dari tiga bagian yang dipisahkan titik koma (`;`) di dalam tanda kurung:

```
for (inisialisasi; kondisi; increment/decrement) {
  // kode yang diulang
}
```

| Bagian                  | Fungsi                                                                                |
| ----------------------- | ------------------------------------------------------------------------------------- |
| **Inisialisasi**        | Mendeklarasikan dan memberi nilai awal pada variabel penghitung                       |
| **Kondisi**             | Diperiksa sebelum setiap iterasi; perulangan berhenti ketika kondisi bernilai `false` |
| **Increment/Decrement** | Mengubah nilai penghitung setelah setiap iterasi                                      |

```javascript
for (let i = 1; i <= 5; i++) {
  console.log("Antrean ke-" + i);
}
// Output:
// Antrean ke-1
// Antrean ke-2
// Antrean ke-3
// Antrean ke-4
// Antrean ke-5
```

**Urutan eksekusi `for`:**

```
1. Inisialisasi dijalankan sekali (let i = 1)
2. Kondisi diperiksa (i <= 5) → jika true, lanjutkan
3. Blok kode dieksekusi
4. Increment dijalankan (i++)
5. Kembali ke langkah 2
```

**Contoh — Menghitung mundur:**

```javascript
for (let i = 5; i >= 1; i--) {
  console.log(i);
}
console.log("Mulai!");
// Output: 5, 4, 3, 2, 1, Mulai!
```

**Contoh — Menjumlahkan angka 1 sampai 10:**

```javascript
let total = 0;

for (let i = 1; i <= 10; i++) {
  total += i;
}

console.log("Total:", total); // Output: Total: 55
```

**Contoh — Mengakses elemen array:**

```javascript
const buah = ["Apel", "Jeruk", "Mangga", "Anggur"];

for (let i = 0; i < buah.length; i++) {
  console.log(i + 1 + ".", buah[i]);
}
// Output:
// 1. Apel
// 2. Jeruk
// 3. Mangga
// 4. Anggur
```

---

### 2. Perulangan Bersyarat: `while`

Gunakan `while` ketika **jumlah iterasi belum diketahui** sejak awal. Perulangan akan terus berjalan selama kondisinya bernilai `true`, dan berhenti begitu kondisi menjadi `false`.

```javascript
let saldo = 15000;

while (saldo > 0) {
  console.log("Saldo saat ini: Rp", saldo);
  saldo -= 5000; // Dikurangi setiap iterasi
}
console.log("Saldo habis.");
// Output:
// Saldo saat ini: Rp 15000
// Saldo saat ini: Rp 10000
// Saldo saat ini: Rp 5000
// Saldo habis.
```

> **Peringatan — Infinite Loop:** Pastikan ada mekanisme di dalam blok `while` yang pada akhirnya akan membuat kondisi menjadi `false`. Jika kondisi tidak pernah berubah, perulangan akan berjalan selamanya (_infinite loop_) dan dapat menyebabkan browser atau aplikasi tidak merespons.

```javascript
// Contoh infinite loop — JANGAN dijalankan
let x = 1;
while (x > 0) {
  console.log(x);
  // x tidak pernah berubah → kondisi selalu true → loop tidak berhenti
}
```

**Contoh lengkap — Menebak angka:**

```javascript
let angkaRahasia = 7;
let tebakan = 0;
let percobaan = 0;

while (tebakan !== angkaRahasia) {
  percobaan++;
  tebakan = Math.floor(Math.random() * 10) + 1; // Angka acak 1-10
  console.log("Percobaan ke-" + percobaan + ": menebak angka", tebakan);
}

console.log(
  "Berhasil menebak angka",
  angkaRahasia,
  "dalam",
  percobaan,
  "percobaan.",
);
```

---

### 3. Eksekusi Minimal Satu Kali: `do...while`

`do...while` mirip dengan `while`, namun dengan satu perbedaan penting: **blok kode dieksekusi terlebih dahulu, baru kondisinya diperiksa**. Ini menjamin blok kode dijalankan setidaknya satu kali, terlepas dari apakah kondisinya `true` atau `false`.

```javascript
let angka = 10;

do {
  console.log("Nilai angka:", angka);
  angka--;
} while (angka > 0);
```

**Perbedaan `while` vs `do...while`:**

```javascript
// while — kondisi diperiksa SEBELUM eksekusi
let a = 0;
while (a > 5) {
  console.log("while dijalankan"); // Tidak pernah dieksekusi
}

// do...while — blok dijalankan SEBELUM kondisi diperiksa
let b = 0;
do {
  console.log("do...while dijalankan"); // Dieksekusi satu kali meskipun b > 5 adalah false
} while (b > 5);
// Output: do...while dijalankan
```

**Contoh penggunaan nyata — Konfirmasi pengguna:**

```javascript
let konfirmasi;

do {
  konfirmasi = prompt("Ketik 'ya' untuk melanjutkan:");
} while (konfirmasi !== "ya");

console.log("Pengguna telah mengkonfirmasi. Melanjutkan proses...");
```

`do...while` tepat digunakan di sini karena pertanyaan harus ditampilkan setidaknya satu kali sebelum kondisi jawaban bisa diperiksa.

---

### 4. Menghentikan Perulangan: `break`

Perintah `break` menghentikan perulangan secara langsung, terlepas dari kondisi yang sedang berjalan. Program kemudian melanjutkan eksekusi ke baris setelah blok perulangan.

```javascript
for (let i = 1; i <= 100; i++) {
  if (i === 10) {
    console.log(
      "Target ditemukan pada posisi ke-" + i + ". Pencarian dihentikan.",
    );
    break;
  }
  console.log("Memeriksa posisi ke-" + i);
}
// Output:
// Memeriksa posisi ke-1
// Memeriksa posisi ke-2
// ... (hingga ke-9)
// Target ditemukan pada posisi ke-10. Pencarian dihentikan.
```

Tanpa `break`, perulangan di atas akan terus berjalan hingga `i` mencapai 100, meskipun target sudah ditemukan di iterasi ke-10.

---

### 5. Melewati Iterasi Tertentu: `continue`

Perintah `continue` melewati sisa kode dalam iterasi saat ini dan langsung melanjutkan ke iterasi berikutnya. Berbeda dengan `break` yang menghentikan seluruh perulangan, `continue` hanya melewati satu iterasi.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i % 2 === 0) {
    continue; // Lewati angka genap
  }
  console.log(i);
}
// Output: 1, 3, 5, 7, 9 — hanya angka ganjil yang dicetak
```

**Contoh — Memfilter data array:**

```javascript
const nilai = [85, -5, 92, -10, 78, 60];

console.log("Nilai valid:");
for (let i = 0; i < nilai.length; i++) {
  if (nilai[i] < 0) {
    continue; // Lewati nilai negatif
  }
  console.log("-", nilai[i]);
}
// Output:
// Nilai valid:
// - 85
// - 92
// - 78
// - 60
```

**Perbandingan `break` vs `continue`:**

|                    | `break`                                         | `continue`                        |
| ------------------ | ----------------------------------------------- | --------------------------------- |
| Efek               | Menghentikan **seluruh** perulangan             | Melewati **satu iterasi** saja    |
| Program setelahnya | Melanjutkan ke baris setelah blok `for`/`while` | Melanjutkan ke iterasi berikutnya |

---

### 6. Simulasi Lengkap — Kombinasi Looping

Berikut contoh program yang menggabungkan beberapa konsep perulangan:

```javascript
const daftarNilai = [78, 45, 92, -3, 88, 55, 100, 0, 67];
let jumlah = 0;
let valid = 0;
let invalid = 0;

for (let i = 0; i < daftarNilai.length; i++) {
  const nilai = daftarNilai[i];

  // Lewati nilai yang tidak valid (di luar rentang 0–100)
  if (nilai < 0 || nilai > 100) {
    console.log("Nilai tidak valid dilewati:", nilai);
    invalid++;
    continue;
  }

  jumlah += nilai;
  valid++;
}

const rataRata = jumlah / valid;

console.log("---");
console.log("Total data    :", daftarNilai.length);
console.log("Data valid    :", valid);
console.log("Data tidak valid:", invalid);
console.log("Rata-rata     :", rataRata.toFixed(2));
// Output:
// Nilai tidak valid dilewati: -3
// ---
// Total data    : 9
// Data valid    : 8
// Data tidak valid: 1
// Rata-rata     : 65.63
```

---

### Kesimpulan

Perulangan adalah salah satu mekanisme paling fundamental dalam pemrograman. Dengan menguasai `for`, `while`, dan `do...while`, serta memahami kapan menggunakan `break` dan `continue`, kamu dapat mengotomasi hampir semua tugas berulang dengan kode yang ringkas dan efisien.

**Ringkasan:**

| Konsep          | Kapan Digunakan                                                               |
| --------------- | ----------------------------------------------------------------------------- |
| `for`           | Jumlah iterasi sudah diketahui                                                |
| `while`         | Jumlah iterasi belum diketahui, kondisi diperiksa di awal                     |
| `do...while`    | Blok kode harus dijalankan minimal satu kali sebelum kondisi diperiksa        |
| `break`         | Menghentikan seluruh perulangan secara langsung                               |
| `continue`      | Melewati satu iterasi dan melanjutkan ke iterasi berikutnya                   |
| _Infinite loop_ | Kondisi yang harus dihindari: kondisi perulangan tidak pernah menjadi `false` |
