# Bab 14: Date Object

## Tujuan Pembelajaran

- Memahami kegunaan Date Object dalam JavaScript untuk manajemen waktu.
- Mampu membuat objek tanggal untuk waktu saat ini maupun waktu spesifik.
- Mampu mengekstrak dan memformat komponen tanggal menggunakan _Date Methods_.
- Mengenal Setter Methods untuk memodifikasi nilai tanggal.

---

## Materi Utama

Dalam membangun aplikasi, informasi waktu hampir selalu diperlukan — kapan pengguna mendaftar, kapan batas pembayaran, berapa lama sejak unggahan terakhir. JavaScript menyediakan **Date Object** sebagai alat bawaan untuk membuat, mengakses, dan memanipulasi data waktu.

---

### 1. Membuat Date Object

Untuk membuat objek tanggal, gunakan kata kunci `new Date()` dengan huruf `D` kapital.

#### A. Waktu Saat Ini

```javascript
const sekarang = new Date();
console.log(sekarang);
// Output: Wed Jun 04 2026 14:30:00 GMT+0700 (Western Indonesia Time)
// Format mentah ini belum siap ditampilkan langsung ke antarmuka — perlu diekstrak lebih lanjut
```

#### B. Waktu Spesifik

```javascript
// Format: new Date(tahun, indeksBulan, tanggal, jam, menit, detik)
// Penting: indeks bulan dimulai dari 0 (Januari = 0, Desember = 11)
const hariKemerdekaan = new Date(1945, 7, 17, 10, 0, 0);
// Bulan 7 = Agustus (bukan Juli)
console.log(hariKemerdekaan);
// Output: Fri Aug 17 1945 10:00:00

// Alternatif — menggunakan format string ISO (lebih mudah dibaca)
const peluncuran = new Date("2026-01-15");
console.log(peluncuran);
// Output: Thu Jan 15 2026 00:00:00
```

> **Perhatian — Indeks Bulan Dimulai dari 0:** Ini adalah salah satu sumber kebingungan yang paling umum di JavaScript. Januari = `0`, Februari = `1`, ..., Desember = `11`. Selalu tambahkan `1` saat menampilkan nomor bulan ke pengguna.

---

### 2. Getter Methods — Mengekstrak Komponen Tanggal

Format mentah dari `new Date()` tidak layak ditampilkan langsung ke antarmuka. Gunakan Getter Methods untuk mengekstrak nilai tertentu.

| Method           | Mengembalikan                | Rentang Nilai              |
| ---------------- | ---------------------------- | -------------------------- |
| `.getFullYear()` | Tahun (4 digit)              | misalnya `2026`            |
| `.getMonth()`    | Indeks bulan                 | `0` (Jan) – `11` (Des)     |
| `.getDate()`     | Tanggal dalam bulan          | `1` – `31`                 |
| `.getDay()`      | Indeks hari dalam seminggu   | `0` (Minggu) – `6` (Sabtu) |
| `.getHours()`    | Jam                          | `0` – `23`                 |
| `.getMinutes()`  | Menit                        | `0` – `59`                 |
| `.getSeconds()`  | Detik                        | `0` – `59`                 |
| `.getTime()`     | Millisecond sejak 1 Jan 1970 | Angka besar (timestamp)    |

```javascript
const sekarang = new Date();

const tahun = sekarang.getFullYear();
const bulan = sekarang.getMonth() + 1; // +1 karena indeks dimulai dari 0
const tanggal = sekarang.getDate();
const jam = sekarang.getHours();
const menit = sekarang.getMinutes();

console.log("Tanggal:", tanggal + "-" + bulan + "-" + tahun);
// Output: Tanggal: 4-6-2026

console.log("Waktu:", jam + ":" + menit);
// Output: Waktu: 14:30
```

**Contoh — Menampilkan nama hari:**

```javascript
const namaHari = [
  "Minggu",
  "Senin",
  "Selasa",
  "Rabu",
  "Kamis",
  "Jumat",
  "Sabtu",
];
const namaBulan = [
  "Januari",
  "Februari",
  "Maret",
  "April",
  "Mei",
  "Juni",
  "Juli",
  "Agustus",
  "September",
  "Oktober",
  "November",
  "Desember",
];

const sekarang = new Date();
const hari = namaHari[sekarang.getDay()];
const tgl = sekarang.getDate();
const bln = namaBulan[sekarang.getMonth()];
const thn = sekarang.getFullYear();

console.log(hari + ", " + tgl + " " + bln + " " + thn);
// Output: Kamis, 4 Juni 2026
```

---

### 3. Memformat Tanggal untuk Ditampilkan

JavaScript menyediakan beberapa cara untuk memformat tanggal menjadi teks yang dapat dibaca.

#### A. Manual dengan Getter Methods

Cara yang paling fleksibel karena kamu bisa mengatur format sesuai kebutuhan:

```javascript
function formatTanggal(date) {
  const tgl = String(date.getDate()).padStart(2, "0");
  const bln = String(date.getMonth() + 1).padStart(2, "0");
  const thn = date.getFullYear();
  return tgl + "/" + bln + "/" + thn;
}

const fakturDibuat = new Date();
console.log("Tanggal Faktur:", formatTanggal(fakturDibuat));
// Output: Tanggal Faktur: 04/06/2026
```

#### B. Menggunakan `toLocaleDateString()`

Method bawaan untuk memformat tanggal sesuai lokal tertentu:

```javascript
const tanggal = new Date("2026-06-04");

console.log(tanggal.toLocaleDateString("id-ID"));
// Output: 4/6/2026

console.log(
  tanggal.toLocaleDateString("id-ID", {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
  }),
);
// Output: Kamis, 4 Juni 2026
```

---

### 4. Setter Methods — Memodifikasi Tanggal

Selain membaca nilai, Date Object juga memiliki Setter Methods untuk mengubah komponen tanggal.

| Method                | Fungsi                       |
| --------------------- | ---------------------------- |
| `.setFullYear(tahun)` | Mengubah tahun               |
| `.setMonth(bulan)`    | Mengubah bulan (indeks 0–11) |
| `.setDate(tanggal)`   | Mengubah tanggal             |
| `.setHours(jam)`      | Mengubah jam                 |

```javascript
const batasTagihan = new Date();

// Tetapkan tanggal jatuh tempo ke tanggal 30 bulan ini
batasTagihan.setDate(30);

const tgl = batasTagihan.getDate();
const bln = batasTagihan.getMonth() + 1;
const thn = batasTagihan.getFullYear();

console.log("Batas Pembayaran: " + tgl + "/" + bln + "/" + thn);
// Output: Batas Pembayaran: 30/6/2026
```

---

### 5. Perbandingan dan Selisih Waktu

Date Object menyimpan waktu sebagai **timestamp** — jumlah millisecond sejak 1 Januari 1970. Ini memungkinkan perbandingan dan perhitungan selisih antar tanggal.

```javascript
const tanggalMulai = new Date("2026-01-01");
const tanggalAkhir = new Date("2026-06-04");

// Hitung selisih dalam millisecond
const selisihMs = tanggalAkhir - tanggalMulai;

// Konversi ke hari
const selisihHari = Math.floor(selisihMs / (1000 * 60 * 60 * 24));
console.log("Selisih:", selisihHari, "hari");
// Output: Selisih: 154 hari
```

**Contoh — Menghitung hari menuju suatu tanggal:**

```javascript
function hitungHariMenuju(targetTanggal) {
  const sekarang = new Date();
  const target = new Date(targetTanggal);
  const selisihMs = target - sekarang;

  if (selisihMs < 0) {
    return "Tanggal sudah terlewat.";
  }

  const hari = Math.ceil(selisihMs / (1000 * 60 * 60 * 24));
  return hari + " hari lagi";
}

console.log(hitungHariMenuju("2026-12-31")); // Output: (jumlah hari menuju akhir tahun)
console.log(hitungHariMenuju("2025-01-01")); // Output: Tanggal sudah terlewat.
```

---

### 6. Catatan tentang Library Tanggal Pihak Ketiga

Meskipun Date Object sudah memadai untuk kebutuhan dasar, ia memiliki beberapa keterbatasan yang dikenal di kalangan pengembang:

- Indeks bulan yang dimulai dari 0 sering memicu bug.
- Parsing format tanggal dari string tidak konsisten di semua browser.
- Tidak ada dukungan bawaan untuk format yang ramah pengguna seperti "2 hari yang lalu".
- Penanganan zona waktu (_timezone_) cukup kompleks untuk kasus lintas negara.

Untuk proyek yang memerlukan manajemen tanggal yang lebih kompleks, pengembang biasanya menggunakan library pihak ketiga:

| Library      | Keunggulan                              |
| ------------ | --------------------------------------- |
| **date-fns** | Ringan, modular, banyak fungsi utilitas |
| **Luxon**    | Dukungan timezone yang kuat, API modern |
| **Day.js**   | Sangat ringan, API mirip Moment.js      |

---

### Kesimpulan

Date Object adalah alat bawaan JavaScript untuk bekerja dengan waktu. Dengan memahami cara membuat objek tanggal, mengekstrak komponen, memformatnya untuk ditampilkan, dan menghitung selisih antar tanggal, kamu dapat menangani sebagian besar kebutuhan manajemen waktu dalam aplikasi web.

**Ringkasan:**

| Konsep / Method               | Fungsi                                                     |
| ----------------------------- | ---------------------------------------------------------- |
| `new Date()`                  | Membuat objek tanggal untuk waktu saat ini                 |
| `new Date(tahun, bulan, tgl)` | Membuat objek tanggal spesifik (bulan dimulai dari 0)      |
| `.getFullYear()`              | Mengambil tahun                                            |
| `.getMonth()`                 | Mengambil indeks bulan (0–11), tambahkan +1 untuk tampilan |
| `.getDate()`                  | Mengambil tanggal dalam bulan                              |
| `.getDay()`                   | Mengambil indeks hari dalam seminggu (0 = Minggu)          |
| `.getTime()`                  | Mengambil timestamp (ms sejak 1 Jan 1970)                  |
| `.setDate(n)`                 | Mengubah tanggal                                           |
| `.toLocaleDateString()`       | Memformat tanggal sesuai lokal                             |
