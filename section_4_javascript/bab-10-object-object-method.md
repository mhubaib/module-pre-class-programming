# Bab 10: Object & Object Method

## Tujuan Pembelajaran

- Memahami konsep Object sebagai struktur data untuk mengelompokkan informasi yang saling berkaitan.
- Membaca dan memodifikasi properti dalam sebuah Object menggunakan Dot Notation dan Bracket Notation.
- Membedakan antara properti (data) dan method (fungsi) di dalam sebuah Object.
- Memahami kata kunci `this` dalam konteks Object.

---

## Materi Utama

Jika Array adalah daftar berurutan yang diakses melalui nomor indeks, maka **Object** adalah struktur data yang menyimpan informasi terkait suatu entitas secara lengkap dan terorganisir — seperti Kartu Tanda Penduduk yang memuat nama, alamat, tanggal lahir, dan informasi lainnya dalam satu dokumen.

Object digunakan ketika kamu perlu merepresentasikan sesuatu yang memiliki banyak atribut berbeda, misalnya data pengguna, produk di toko online, atau karakter dalam sebuah permainan.

---

### 1. Membuat Object

Object ditulis menggunakan **kurung kurawal `{}`**. Setiap data di dalamnya disusun dalam format `key: value` (kunci: nilai), dipisahkan oleh koma.

```javascript
const profilPengguna = {
  nama: "Budi Santoso",
  umur: 28,
  email: "budi@email.com",
  sudahLogin: true,
};
```

- `nama`, `umur`, `email`, `sudahLogin` disebut **Key** (kunci) atau **Properti**.
- `"Budi Santoso"`, `28`, `"budi@email.com"`, `true` disebut **Value** (nilai).

Aturan penamaan key mengikuti aturan penamaan variabel — menggunakan camelCase dan tidak boleh diawali angka. Namun, jika nama key mengandung spasi atau karakter khusus, harus diapit tanda kutip:

```javascript
const konfigurasi = {
  versiAplikasi: "1.0.0",
  "nama-lengkap": "Budi Santoso", // key dengan tanda hubung wajib dikutip
};
```

---

### 2. Mengakses dan Memodifikasi Properti

#### A. Dot Notation

Cara yang paling umum digunakan. Tulis nama object, titik, lalu nama properti.

```javascript
const mobilImpian = {
  merek: "Toyota",
  model: "Supra",
  tahunKeluaran: 2024,
  warna: "Silver",
};

// Membaca properti
console.log(mobilImpian.merek); // Output: "Toyota"
console.log(mobilImpian.tahunKeluaran); // Output: 2024

// Mengubah nilai properti
mobilImpian.warna = "Hitam Matte";
console.log(mobilImpian.warna); // Output: "Hitam Matte"

// Menambahkan properti baru
mobilImpian.harga = 850000000;
console.log(mobilImpian.harga); // Output: 850000000
```

#### B. Bracket Notation

Digunakan ketika nama properti dinamis (disimpan dalam variabel), atau ketika nama properti mengandung karakter yang tidak valid untuk dot notation.

```javascript
// Membaca properti menggunakan string
console.log(mobilImpian["model"]); // Output: "Supra"

// Membaca properti menggunakan variabel — berguna ketika nama properti ditentukan secara dinamis
let namaProperti = "merek";
console.log(mobilImpian[namaProperti]); // Output: "Toyota"

// Properti dengan tanda hubung — wajib menggunakan bracket notation
const konfigurasi = { "nama-aplikasi": "TokoBuku" };
console.log(konfigurasi["nama-aplikasi"]); // Output: "TokoBuku"
```

**Kapan menggunakan masing-masing:**

|                                      | Dot Notation   | Bracket Notation      |
| ------------------------------------ | -------------- | --------------------- |
| Sintaks                              | `obj.properti` | `obj["properti"]`     |
| Nama properti dinamis                | Tidak bisa     | Bisa                  |
| Nama properti dengan karakter khusus | Tidak bisa     | Bisa                  |
| Keterbacaan                          | Lebih bersih   | Sedikit lebih verbose |

---

### 3. Menghapus dan Memeriksa Properti

#### Menghapus properti dengan `delete`

```javascript
const pengguna = {
  nama: "Ani",
  email: "ani@email.com",
  token: "abc123xyz",
};

// Hapus properti sensitif sebelum mengirim data ke tampilan
delete pengguna.token;
console.log(pengguna);
// Output: { nama: "Ani", email: "ani@email.com" }
```

#### Memeriksa keberadaan properti dengan `in`

```javascript
const produk = {
  nama: "Sepatu Lari",
  harga: 350000,
};

console.log("nama" in produk); // Output: true
console.log("diskon" in produk); // Output: false
```

---

### 4. Object Method

Object tidak hanya dapat menyimpan data — ia juga dapat menyimpan **fungsi**. Fungsi yang berada di dalam Object disebut **Method**.

```javascript
const ksatria = {
  nama: "Bima",
  nyawa: 100,
  level: 5,

  // Method — fungsi yang menjadi bagian dari object
  serang: function () {
    console.log(this.nama + " menyerang dengan pedang!");
  },

  terkenaSerangan: function (damage) {
    this.nyawa -= damage;
    console.log(this.nama + " terkena serangan! Nyawa tersisa:", this.nyawa);
  },

  tampilkanStatus: function () {
    console.log("=== Status Karakter ===");
    console.log("Nama  :", this.nama);
    console.log("Nyawa :", this.nyawa);
    console.log("Level :", this.level);
  },
};

// Memanggil method
ksatria.serang();
// Output: Bima menyerang dengan pedang!

ksatria.terkenaSerangan(25);
// Output: Bima terkena serangan! Nyawa tersisa: 75

ksatria.tampilkanStatus();
// Output:
// === Status Karakter ===
// Nama  : Bima
// Nyawa : 75
// Level : 5
```

Method dapat ditulis menggunakan sintaks yang lebih ringkas (ES6):

```javascript
const ksatria = {
  nama: "Bima",
  nyawa: 100,

  // Sintaks method ringkas — tanpa kata kunci "function"
  serang() {
    console.log(this.nama + " menyerang!");
  },

  terkenaSerangan(damage) {
    this.nyawa -= damage;
  },
};
```

---

### 5. Kata Kunci `this`

Di dalam sebuah method, kata kunci `this` merujuk pada **object yang memiliki method tersebut**. Ini memungkinkan method mengakses atau memodifikasi properti lain dalam object yang sama.

```javascript
const rekeningBank = {
  pemilik: "Budi Santoso",
  saldo: 1000000,

  setor(jumlah) {
    this.saldo += jumlah;
    console.log("Setoran berhasil. Saldo sekarang: Rp", this.saldo);
  },

  tarik(jumlah) {
    if (jumlah > this.saldo) {
      console.log("Saldo tidak mencukupi.");
      return;
    }
    this.saldo -= jumlah;
    console.log("Penarikan berhasil. Saldo sekarang: Rp", this.saldo);
  },

  cekSaldo() {
    console.log(
      "Saldo rekening atas nama",
      this.pemilik + ":",
      "Rp",
      this.saldo,
    );
  },
};

rekeningBank.cekSaldo();
// Output: Saldo rekening atas nama Budi Santoso: Rp 1000000

rekeningBank.setor(500000);
// Output: Setoran berhasil. Saldo sekarang: Rp 1500000

rekeningBank.tarik(200000);
// Output: Penarikan berhasil. Saldo sekarang: Rp 1300000

rekeningBank.tarik(2000000);
// Output: Saldo tidak mencukupi.
```

---

### 6. Iterasi Properti Object

Untuk mengakses seluruh properti dalam sebuah object secara berurutan, gunakan perulangan `for...in`:

```javascript
const produk = {
  nama: "Laptop Gaming",
  merek: "ASUS",
  harga: 15000000,
  stok: 10,
};

for (let key in produk) {
  console.log(key + ":", produk[key]);
}
// Output:
// nama: Laptop Gaming
// merek: ASUS
// harga: 15000000
// stok: 10
```

Selain itu, terdapat tiga method bawaan Object yang berguna untuk mendapatkan daftar kunci, nilai, atau keduanya:

```javascript
console.log(Object.keys(produk));
// Output: ["nama", "merek", "harga", "stok"]

console.log(Object.values(produk));
// Output: ["Laptop Gaming", "ASUS", 15000000, 10]

console.log(Object.entries(produk));
// Output: [["nama", "Laptop Gaming"], ["merek", "ASUS"], ...]
```

---

### Kesimpulan

Object adalah struktur data yang fundamental dalam JavaScript. Hampir semua data kompleks — dari respons API hingga komponen antarmuka — direpresentasikan sebagai Object. Memahami cara membuat, mengakses, memodifikasi, dan mendefinisikan method dalam Object adalah keterampilan inti yang akan digunakan di setiap aspek pengembangan web.

**Ringkasan:**

| Konsep            | Penjelasan                                                                       |
| ----------------- | -------------------------------------------------------------------------------- |
| Object            | Struktur data `key: value` untuk merepresentasikan entitas dengan banyak atribut |
| Properti          | Data yang tersimpan dalam Object (key dan value-nya)                             |
| Dot Notation      | Cara akses properti: `object.properti`                                           |
| Bracket Notation  | Cara akses properti dinamis: `object["properti"]`                                |
| Method            | Fungsi yang didefinisikan di dalam Object                                        |
| `this`            | Kata kunci yang merujuk pada Object pemilik method                               |
| `delete`          | Menghapus sebuah properti dari Object                                            |
| `for...in`        | Perulangan untuk mengiterasi seluruh properti Object                             |
| `Object.keys()`   | Mengembalikan array berisi seluruh kunci Object                                  |
| `Object.values()` | Mengembalikan array berisi seluruh nilai Object                                  |
