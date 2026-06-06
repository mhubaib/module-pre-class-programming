# Bab 11: Iterable & Non-Iterable

## Tujuan Pembelajaran

- Memahami konsep Iterable dan Non-Iterable dalam struktur data JavaScript.
- Mengetahui penggunaan perulangan `for...of` untuk tipe data Iterable.
- Mengetahui penggunaan perulangan `for...in` untuk mengiterasi properti Object.

---

## Materi Utama

Dalam JavaScript, tidak semua tipe data dapat diiterasi (disisir satu per satu). Kemampuan ini menentukan metode perulangan mana yang tepat digunakan untuk memproses sebuah data.

---

### 1. Iterable — Data yang Dapat Disisir Berurutan

**Iterable** adalah tipe data yang elemennya dapat diakses satu per satu secara berurutan. Tipe data ini memiliki konsep "urutan" yang memungkinkan mesin perulangan mengetahui elemen mana yang harus diproses berikutnya.

Tipe data Iterable yang paling umum digunakan:

| Tipe Data  | Contoh            | Cara Iterasi                               |
| ---------- | ----------------- | ------------------------------------------ |
| **String** | `"Jakarta"`       | Karakter demi karakter: `J`, `a`, `k`, ... |
| **Array**  | `["Budi", "Ani"]` | Elemen demi elemen: `"Budi"`, `"Ani"`      |
| **Map**    | `new Map()`       | Pasangan key-value satu per satu           |
| **Set**    | `new Set()`       | Nilai unik satu per satu                   |

#### Perulangan `for...of`

Tipe data Iterable dapat diproses menggunakan `for...of` — cara yang lebih ringkas dibandingkan `for` konvensional karena tidak memerlukan variabel penghitung indeks.

```javascript
// Menyisir String karakter per karakter
const kota = "JAKARTA";

for (let huruf of kota) {
  console.log(huruf);
}
// Output:
// J
// A
// K
// A
// R
// T
// A
```

```javascript
// Menyisir Array elemen per elemen
const daftarBelanja = ["Beras", "Telur", "Minyak"];

for (let barang of daftarBelanja) {
  console.log("Membeli:", barang);
}
// Output:
// Membeli: Beras
// Membeli: Telur
// Membeli: Minyak
```

**Perbandingan `for` konvensional vs `for...of`:**

```javascript
const buah = ["Apel", "Jeruk", "Mangga"];

// for konvensional — perlu mengelola variabel indeks secara manual
for (let i = 0; i < buah.length; i++) {
  console.log(buah[i]);
}

// for...of — lebih ringkas, tidak perlu indeks
for (let item of buah) {
  console.log(item);
}

// Keduanya menghasilkan output yang sama:
// Apel
// Jeruk
// Mangga
```

Gunakan `for...of` ketika kamu hanya perlu nilai elemennya. Gunakan `for` konvensional ketika kamu juga memerlukan nomor indeks setiap elemen.

**Contoh lengkap — Menghitung total nilai:**

```javascript
const nilaiUjian = [85, 92, 78, 90, 88];
let total = 0;

for (let nilai of nilaiUjian) {
  total += nilai;
}

const rataRata = total / nilaiUjian.length;
console.log("Total   :", total); // Output: Total   : 433
console.log("Rata-rata:", rataRata); // Output: Rata-rata: 86.6
```

---

### 2. Non-Iterable — Data yang Tidak Dapat Disisir

**Non-Iterable** adalah tipe data yang tidak memiliki konsep urutan internal, sehingga tidak dapat diproses menggunakan `for...of`.

| Tipe Data       | Alasan Tidak Dapat Diiterasi                                                  |
| --------------- | ----------------------------------------------------------------------------- |
| **Number**      | Angka seperti `4500` adalah satu nilai tunggal, bukan kumpulan                |
| **Boolean**     | `true` atau `false` adalah status, bukan kumpulan elemen                      |
| **Object `{}`** | Meskipun memiliki banyak properti, Object tidak memiliki urutan indeks bawaan |

```javascript
// Mencoba for...of pada Number — akan menghasilkan error
const angka = 100;
for (let digit of angka) {
  // TypeError: angka is not iterable
  console.log(digit);
}
```

---

### 3. Mengiterasi Object dengan `for...in`

Karena Object bukan Iterable, `for...of` tidak dapat digunakan. JavaScript menyediakan `for...in` khusus untuk mengiterasi **kunci (key)** dari sebuah Object.

```javascript
const profilKaryawan = {
  nama: "Dono",
  umur: 30,
  pekerjaan: "Programmer",
};

for (let kunci in profilKaryawan) {
  console.log(kunci + ":", profilKaryawan[kunci]);
}
// Output:
// nama: Dono
// umur: 30
// pekerjaan: Programmer
```

`for...in` memberikan nama kunci di setiap iterasi, yang kemudian dapat digunakan dengan Bracket Notation (`object[kunci]`) untuk mengakses nilainya.

**Contoh — Mencetak semua properti secara dinamis:**

```javascript
const spesifikasiLaptop = {
  merek: "ASUS",
  prosesor: "Intel Core i7",
  RAM: "16GB",
  storage: "512GB SSD",
  harga: 15000000,
};

console.log("=== Spesifikasi Laptop ===");
for (let spek in spesifikasiLaptop) {
  console.log("-", spek + ":", spesifikasiLaptop[spek]);
}
// Output:
// === Spesifikasi Laptop ===
// - merek: ASUS
// - prosesor: Intel Core i7
// - RAM: 16GB
// - storage: 512GB SSD
// - harga: 15000000
```

> **Catatan:** `for...in` juga dapat digunakan pada Array, namun hasilnya adalah indeks (`"0"`, `"1"`, `"2"`) bukan nilainya. Untuk Array, `for...of` atau `for` konvensional lebih tepat digunakan.

---

### 4. Perbandingan `for...of` vs `for...in`

|                   | `for...of`                                   | `for...in`                                   |
| ----------------- | -------------------------------------------- | -------------------------------------------- |
| Digunakan untuk   | Tipe data Iterable (Array, String, Map, Set) | Object                                       |
| Yang diiterasi    | **Nilai** elemen                             | **Kunci (key)** properti                     |
| Mendukung Array?  | Ya — menghasilkan nilai elemen               | Ya — menghasilkan indeks (sebaiknya hindari) |
| Mendukung Object? | Tidak — akan menghasilkan error              | Ya                                           |

**Contoh perbandingan langsung:**

```javascript
const data = ["alpha", "beta", "gamma"];

// for...of — menghasilkan nilai
for (let nilai of data) {
  console.log(nilai); // alpha, beta, gamma
}

// for...in — menghasilkan indeks
for (let indeks in data) {
  console.log(indeks); // "0", "1", "2"
}
```

---

### Kesimpulan

Memahami perbedaan Iterable dan Non-Iterable menentukan metode perulangan yang tepat untuk setiap situasi. Menggunakan metode yang salah — misalnya `for...of` pada Object — akan menghasilkan error yang sulit didiagnosis.

**Panduan cepat:**

| Jika ingin mengiterasi...        | Gunakan                            |
| -------------------------------- | ---------------------------------- |
| Elemen Array                     | `for...of` atau `for` konvensional |
| Karakter dalam String            | `for...of`                         |
| Kunci properti Object            | `for...in`                         |
| Elemen Array dengan akses indeks | `for` konvensional                 |
