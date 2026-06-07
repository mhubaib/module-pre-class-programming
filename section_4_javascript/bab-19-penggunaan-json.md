# Bab 19: Penggunaan JSON

## Tujuan Pembelajaran

- Memahami pengertian JSON sebagai format pertukaran data universal.
- Membedakan format JSON dari Object JavaScript biasa.
- Menguasai `JSON.stringify()` dan `JSON.parse()` sebagai alat konversi data.

---

## Materi Utama

Dalam pengembangan web modern, aplikasi Front-End pada suatu saat perlu berkomunikasi dengan Server Back-End untuk mengirim atau menerima data. Namun, server mungkin dibangun menggunakan bahasa pemrograman lain seperti Python, PHP, atau Go. Bahasa-bahasa tersebut tidak mengenal struktur Object JavaScript secara langsung.

Solusinya adalah menggunakan format pertukaran data yang dapat dipahami oleh semua bahasa pemrograman. Format yang paling umum digunakan saat ini adalah **JSON**.

---

### 1. Apa itu JSON?

**JSON** (JavaScript Object Notation) adalah format teks untuk merepresentasikan data terstruktur. Meskipun namanya mengandung "JavaScript", JSON bukan bagian eksklusif dari JavaScript — ia adalah format teks universal yang dapat dibaca dan dihasilkan oleh hampir semua bahasa pemrograman.

Karena JSON pada dasarnya adalah teks (_String_), data dalam format ini dapat dikirimkan melalui jaringan internet, disimpan ke file, dan dibaca kembali oleh sistem mana pun.

**Contoh file JSON:**

```json
{
  "nama": "Budi Santoso",
  "umur": 28,
  "aktif": true,
  "alamat": {
    "kota": "Jakarta",
    "kodePos": "10110"
  },
  "hobi": ["membaca", "coding", "hiking"]
}
```

---

### 2. Perbedaan Object JavaScript dan JSON

Meskipun tampilannya mirip, JSON memiliki aturan penulisan yang lebih ketat dibandingkan Object JavaScript.

| Aspek                   | Object JavaScript                             | JSON                                           |
| ----------------------- | --------------------------------------------- | ---------------------------------------------- |
| Penulisan key           | Bebas: `nama` atau `"nama"`                   | Wajib kutip ganda: `"nama"`                    |
| Penulisan nilai string  | Kutip tunggal atau ganda: `'teks'` / `"teks"` | Hanya kutip ganda: `"teks"`                    |
| Method / fungsi         | Diizinkan                                     | Tidak diizinkan                                |
| `undefined`             | Diizinkan                                     | Tidak diizinkan                                |
| `Date` object           | Diizinkan                                     | Tidak diizinkan (disimpan sebagai string)      |
| Komentar                | Diizinkan                                     | Tidak diizinkan                                |
| Tipe data yang didukung | Semua tipe JS                                 | String, Number, Boolean, Array, Object, `null` |

**Contoh perbandingan:**

```javascript
// Object JavaScript — penulisan lebih longgar
const penggunJS = {
  nama: "Asep", // key tanpa kutip, value kutip tunggal
  umur: 20,
  tampilkan: function () {
    // method diizinkan
    return this.nama;
  },
};

// JSON — aturan penulisan ketat
// {
//   "nama": "Asep",        key dan value wajib kutip ganda
//   "umur": 20             tidak ada method
// }
```

---

### 3. `JSON.stringify()` — Mengonversi Object ke JSON String

Sebelum mengirimkan data ke server, Object JavaScript harus diubah terlebih dahulu menjadi teks JSON. Gunakan `JSON.stringify()` untuk ini.

```javascript
const keranjang = {
  produk: "Sampo",
  harga: 15000,
  terbayar: false,
};

const jsonString = JSON.stringify(keranjang);
console.log(jsonString);
// Output: '{"produk":"Sampo","harga":15000,"terbayar":false}'

console.log(typeof jsonString); // Output: "string"
```

**Efek pada tipe data yang tidak didukung JSON:**

```javascript
const data = {
  nama: "Budi",
  metode: function () {
    return "halo";
  }, // fungsi dihapus
  tanggal: new Date("2026-01-01"), // dikonversi ke string ISO
  kosong: undefined, // dihapus
  nilaiNull: null, // dipertahankan
};

console.log(JSON.stringify(data));
// Output: '{"nama":"Budi","tanggal":"2026-01-01T00:00:00.000Z","nilaiNull":null}'
// Perhatikan: metode dan undefined tidak muncul dalam hasil
```

**Memformat output JSON agar mudah dibaca:**

`JSON.stringify()` menerima argumen kedua dan ketiga untuk memformat output:

```javascript
const pengguna = {
  nama: "Ani",
  email: "ani@email.com",
  premium: true,
};

// Argumen ketiga: jumlah spasi untuk indentasi
console.log(JSON.stringify(pengguna, null, 2));
// Output:
// {
//   "nama": "Ani",
//   "email": "ani@email.com",
//   "premium": true
// }
```

---

### 4. `JSON.parse()` — Mengonversi JSON String ke Object

Saat menerima data dari server, data tersebut biasanya berbentuk teks JSON. Gunakan `JSON.parse()` untuk mengubahnya kembali menjadi Object JavaScript yang dapat dimanipulasi.

```javascript
const jsonDariServer = '{"nama":"Budi","lulusUjian":true,"nilai":92}';

// Sebelum di-parse — masih berupa string
console.log(typeof jsonDariServer); // Output: "string"
console.log(jsonDariServer.nama); // Output: undefined — tidak bisa diakses

// Setelah di-parse — menjadi Object JavaScript
const data = JSON.parse(jsonDariServer);

console.log(typeof data); // Output: "object"
console.log(data.nama); // Output: "Budi"
console.log(data.lulusUjian); // Output: true
console.log(data.nilai); // Output: 92
```

**Contoh dengan data bersarang (nested):**

```javascript
const jsonProduk = `{
  "nama": "Laptop Gaming",
  "harga": 15000000,
  "spesifikasi": {
    "RAM": "16GB",
    "storage": "512GB SSD"
  },
  "tersedia": true
}`;

const produk = JSON.parse(jsonProduk);

console.log(produk.nama); // Output: "Laptop Gaming"
console.log(produk.spesifikasi.RAM); // Output: "16GB"
console.log(produk.harga.toLocaleString()); // Output: "15.000.000"
```

---

### 5. Menangani Error pada `JSON.parse()`

Jika teks yang diberikan ke `JSON.parse()` bukan format JSON yang valid, program akan melempar error. Selalu gunakan `try...catch` untuk menangani kemungkinan ini.

```javascript
function parseAman(teks) {
  try {
    const data = JSON.parse(teks);
    return { sukses: true, data };
  } catch (error) {
    return {
      sukses: false,
      pesan: "Format JSON tidak valid: " + error.message,
    };
  }
}

console.log(parseAman('{"nama":"Budi"}'));
// Output: { sukses: true, data: { nama: "Budi" } }

console.log(parseAman("{nama: Budi}"));
// Output: { sukses: false, pesan: "Format JSON tidak valid: ..." }
// Gagal karena key tidak dikutip dan value tidak dikutip
```

---

### 6. Simulasi Lengkap — Alur Kirim dan Terima Data

Berikut simulasi alur komunikasi data antara Front-End dan Back-End menggunakan JSON:

```javascript
// === SISI FRONT-END: Menyiapkan data untuk dikirim ke server ===

const dataFormulir = {
  nama: "Budi Santoso",
  email: "budi@email.com",
  langganan: true,
};

// Konversi ke JSON String sebelum dikirim
const dataKirim = JSON.stringify(dataFormulir);
console.log("Data yang dikirim:", dataKirim);
// Output: '{"nama":"Budi Santoso","email":"budi@email.com","langganan":true}'

// === SISI BACK-END (simulasi): Server memproses dan mengirimkan respons ===

const responDariServer =
  '{"status":"berhasil","id":1042,"pesan":"Pendaftaran berhasil!"}';

// === SISI FRONT-END: Menerima dan memproses respons ===

const respon = JSON.parse(responDariServer);
console.log("Status  :", respon.status); // Output: berhasil
console.log("ID User :", respon.id); // Output: 1042
console.log("Pesan   :", respon.pesan); // Output: Pendaftaran berhasil!
```

---

### Kesimpulan

JSON adalah fondasi komunikasi data antara aplikasi Front-End dan Back-End. Memahami cara mengonversi data menggunakan `JSON.stringify()` dan `JSON.parse()` adalah prasyarat sebelum mempelajari komunikasi dengan server menggunakan Fetch API yang akan dibahas di bab berikutnya.

**Ringkasan:**

| Konsep                | Penjelasan                                                                                 |
| --------------------- | ------------------------------------------------------------------------------------------ |
| JSON                  | Format teks universal untuk merepresentasikan data terstruktur                             |
| `JSON.stringify(obj)` | Mengonversi Object JavaScript menjadi teks JSON (String)                                   |
| `JSON.parse(str)`     | Mengonversi teks JSON menjadi Object JavaScript                                            |
| Aturan JSON           | Key dan nilai string wajib kutip ganda; tidak mendukung fungsi, `undefined`, atau komentar |
| `try...catch`         | Digunakan untuk menangani error saat `JSON.parse()` menerima teks tidak valid              |
