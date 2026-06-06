# Bab 8: Array & Array Method

## Tujuan Pembelajaran

- Mengingat kembali konsep dasar tipe data Array sebagai struktur data kumpulan.
- Menguasai teknik membaca, mengakses, dan mengubah elemen Array menggunakan indeks.
- Mengenal dan menggunakan _Built-in Array Methods_ seperti `push`, `pop`, `shift`, `unshift`, `splice`, `slice`, dan `indexOf`.

---

## Materi Utama

Array adalah struktur data yang mampu menyimpan banyak nilai dalam satu variabel. Tanpa Array, menyimpan data 50 mahasiswa berarti membuat 50 variabel terpisah — pendekatan yang tidak praktis dan sulit dikelola.

```javascript
// Tanpa Array — tidak praktis
let siswa1 = "Budi";
let siswa2 = "Asep";
let siswa3 = "Joko";
// ... hingga siswa50

// Dengan Array — ringkas dan mudah dikelola
let siswa = ["Budi", "Asep", "Joko", "Dewi", "Rina"];
```

---

### 1. Struktur Array dan Akses Elemen via Indeks

Array ditulis menggunakan kurung siku `[]`, dengan setiap elemen dipisahkan oleh koma.

```javascript
let barangTas = ["Buku", "Pulpen", "Laptop", "Dompet"];
```

**Aturan penting — Indeks dimulai dari 0:**

Elemen pertama dalam array berada di indeks `0`, bukan `1`. Ini adalah konvensi yang berlaku di hampir semua bahasa pemrograman.

```
Nilai :  "Buku"  "Pulpen"  "Laptop"  "Dompet"
Indeks:    0        1         2         3
```

**Mengakses elemen:**

```javascript
console.log(barangTas[0]); // Output: "Buku"
console.log(barangTas[2]); // Output: "Laptop"
console.log(barangTas[3]); // Output: "Dompet"

// Mengakses indeks yang tidak ada
console.log(barangTas[10]); // Output: undefined
```

**Mengubah nilai elemen:**

```javascript
barangTas[2] = "Kotak Makan";
console.log(barangTas);
// Output: ["Buku", "Pulpen", "Kotak Makan", "Dompet"]
```

**Mengakses elemen terakhir tanpa tahu panjang array:**

```javascript
let panjang = barangTas.length;
console.log(barangTas[panjang - 1]); // Output: "Dompet" — selalu elemen terakhir
```

---

### 2. Mengetahui Panjang Array: `.length`

Properti `.length` mengembalikan jumlah total elemen dalam sebuah array.

```javascript
let peserta = ["Dani", "Yanto", "Gilang"];
console.log(peserta.length); // Output: 3
```

`.length` sangat sering digunakan bersama perulangan `for` untuk mengakses seluruh elemen array:

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

### 3. Menambahkan Elemen

#### `.push(nilai)` — Menambahkan di akhir

```javascript
let namaBulan = ["Januari", "Februari", "Maret"];

namaBulan.push("April");
console.log(namaBulan);
// Output: ["Januari", "Februari", "Maret", "April"]

// push() juga mengembalikan panjang array setelah penambahan
let panjangBaru = namaBulan.push("Mei");
console.log(panjangBaru); // Output: 5
```

#### `.unshift(nilai)` — Menambahkan di awal

```javascript
let namaBulan = ["Februari", "Maret"];

namaBulan.unshift("Januari");
console.log(namaBulan);
// Output: ["Januari", "Februari", "Maret"]
```

---

### 4. Menghapus Elemen

#### `.pop()` — Menghapus elemen terakhir

`.pop()` menghapus elemen terakhir dari array dan mengembalikan nilai yang dihapus tersebut.

```javascript
let daftarObat = ["Paracetamol", "Amoxicillin", "Vitamin C"];

let dihapus = daftarObat.pop();
console.log(dihapus); // Output: "Vitamin C"
console.log(daftarObat); // Output: ["Paracetamol", "Amoxicillin"]
```

#### `.shift()` — Menghapus elemen pertama

`.shift()` menghapus elemen pertama (indeks 0) dan menggeser seluruh elemen lainnya maju satu posisi.

```javascript
let antrian = ["Budi", "Ani", "Citra"];

let dilayani = antrian.shift();
console.log(dilayani); // Output: "Budi"
console.log(antrian); // Output: ["Ani", "Citra"]
```

**Ringkasan metode menambah dan menghapus:**

| Method            | Posisi | Aksi                               |
| ----------------- | ------ | ---------------------------------- |
| `.push(nilai)`    | Akhir  | Menambahkan elemen                 |
| `.unshift(nilai)` | Awal   | Menambahkan elemen                 |
| `.pop()`          | Akhir  | Menghapus dan mengembalikan elemen |
| `.shift()`        | Awal   | Menghapus dan mengembalikan elemen |

---

### 5. Metode Lanjutan yang Umum Digunakan

#### `.indexOf(nilai)` — Mencari posisi elemen

Mengembalikan indeks pertama dari elemen yang dicari. Mengembalikan `-1` jika elemen tidak ditemukan.

```javascript
const warna = ["merah", "hijau", "biru", "hijau"];

console.log(warna.indexOf("biru")); // Output: 2
console.log(warna.indexOf("hijau")); // Output: 1 — hanya indeks pertama
console.log(warna.indexOf("kuning")); // Output: -1 — tidak ditemukan
```

#### `.includes(nilai)` — Memeriksa keberadaan elemen

Mengembalikan `true` jika elemen ditemukan, `false` jika tidak.

```javascript
const izinAkses = ["admin", "editor", "viewer"];

console.log(izinAkses.includes("admin")); // Output: true
console.log(izinAkses.includes("superuser")); // Output: false

// Penggunaan praktis dalam kondisi if
const rolePengguna = "editor";
if (izinAkses.includes(rolePengguna)) {
  console.log("Akses diberikan.");
} else {
  console.log("Akses ditolak.");
}
// Output: Akses diberikan.
```

#### `.splice(mulai, jumlahHapus, ...tambah)` — Menyisip dan menghapus di posisi tertentu

`.splice()` adalah metode yang fleksibel untuk menghapus, menyisipkan, atau mengganti elemen di posisi tertentu.

```javascript
let kota = ["Jakarta", "Bandung", "Surabaya", "Medan"];

// Menghapus 1 elemen mulai dari indeks 1
let dihapus = kota.splice(1, 1);
console.log(dihapus); // Output: ["Bandung"]
console.log(kota); // Output: ["Jakarta", "Surabaya", "Medan"]

// Menyisipkan elemen di posisi tertentu tanpa menghapus
kota.splice(1, 0, "Yogyakarta");
console.log(kota); // Output: ["Jakarta", "Yogyakarta", "Surabaya", "Medan"]

// Mengganti elemen
kota.splice(2, 1, "Semarang");
console.log(kota); // Output: ["Jakarta", "Yogyakarta", "Semarang", "Medan"]
```

#### `.slice(mulai, akhir)` — Mengambil sebagian array

`.slice()` mengembalikan salinan sebagian array dari indeks `mulai` hingga sebelum indeks `akhir`, **tanpa mengubah array aslinya**.

```javascript
const angka = [10, 20, 30, 40, 50];

console.log(angka.slice(1, 4)); // Output: [20, 30, 40] — indeks 1 sampai sebelum 4
console.log(angka.slice(2)); // Output: [30, 40, 50] — dari indeks 2 hingga akhir
console.log(angka.slice(-2)); // Output: [40, 50] — dua elemen terakhir
console.log(angka); // Output: [10, 20, 30, 40, 50] — array asli tidak berubah
```

---

### 6. Simulasi Lengkap — Sistem Antrian

Berikut contoh program yang menggabungkan berbagai array method dalam satu alur kerja:

```javascript
// Sistem antrian sederhana
let antrian = [];

// Pengguna mendaftar — ditambahkan ke akhir antrian
antrian.push("Budi");
antrian.push("Ani");
antrian.push("Citra");
antrian.push("Dedi");
console.log("Antrian awal:", antrian);
// Output: Antrian awal: ["Budi", "Ani", "Citra", "Dedi"]

// Melayani pengguna pertama
let dilayani = antrian.shift();
console.log("Sedang dilayani:", dilayani);
console.log("Sisa antrian:", antrian);
// Output: Sedang dilayani: Budi
// Output: Sisa antrian: ["Ani", "Citra", "Dedi"]

// Pengguna prioritas masuk di depan antrian
antrian.unshift("Eka (Prioritas)");
console.log("Setelah sisipan prioritas:", antrian);
// Output: Setelah sisipan prioritas: ["Eka (Prioritas)", "Ani", "Citra", "Dedi"]

// Cek apakah seseorang ada dalam antrian
console.log("Apakah Ani ada?", antrian.includes("Ani")); // Output: true
console.log("Apakah Budi ada?", antrian.includes("Budi")); // Output: false

// Tampilkan seluruh antrian dengan nomor urut
console.log("--- Daftar Antrian ---");
for (let i = 0; i < antrian.length; i++) {
  console.log(i + 1 + ".", antrian[i]);
}
// Output:
// --- Daftar Antrian ---
// 1. Eka (Prioritas)
// 2. Ani
// 3. Citra
// 4. Dedi
```

---

### Kesimpulan

Array adalah struktur data yang akan kamu gunakan di hampir setiap program JavaScript. Memahami cara mengakses elemen via indeks dan menguasai method bawaan array adalah keterampilan fundamental yang diperlukan untuk mengolah dan memanipulasi kumpulan data secara efisien.

**Ringkasan Method Array:**

| Method             | Fungsi                                        | Mengubah Array Asli? |
| ------------------ | --------------------------------------------- | -------------------- |
| `.length`          | Mengembalikan jumlah elemen                   | Tidak (properti)     |
| `.push(nilai)`     | Menambahkan elemen di akhir                   | Ya                   |
| `.unshift(nilai)`  | Menambahkan elemen di awal                    | Ya                   |
| `.pop()`           | Menghapus dan mengembalikan elemen terakhir   | Ya                   |
| `.shift()`         | Menghapus dan mengembalikan elemen pertama    | Ya                   |
| `.indexOf(nilai)`  | Mencari indeks elemen pertama yang cocok      | Tidak                |
| `.includes(nilai)` | Memeriksa apakah elemen ada dalam array       | Tidak                |
| `.splice(i, n)`    | Menghapus, menyisipkan, atau mengganti elemen | Ya                   |
| `.slice(i, j)`     | Mengembalikan salinan sebagian array          | Tidak                |
