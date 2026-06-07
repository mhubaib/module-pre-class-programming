# Bab 18: Modularisasi JavaScript

## Tujuan Pembelajaran

- Memahami konsep modularisasi sebagai solusi pengelolaan kode yang besar (_Separation of Concerns_).
- Menghubungkan antar file menggunakan `export` dan `import`.
- Membedakan _Named Export_ dan _Default Export_ beserta cara penggunaannya.
- Mengaktifkan sistem modul ES6 pada dokumen HTML.

---

## Materi Utama

Ketika aplikasi webmu semakin besar, menaruh seluruh kode JavaScript ke dalam satu file `script.js` menjadi masalah — file menjadi sulit dibaca, sulit diperbaiki, dan rentan terhadap konflik nama variabel (_Spaghetti Code_).

Solusinya adalah **Modularisasi**: memecah satu file besar menjadi beberapa file kecil yang masing-masing bertanggung jawab atas satu fungsi spesifik. Pendekatan ini dikenal sebagai **ES6 Modules** dan menjadi standar dalam pengembangan aplikasi web modern.

---

### 1. Konsep Export dan Import

Agar fungsi atau variabel yang didefinisikan di satu file dapat digunakan di file lain, diperlukan dua mekanisme:

- **`export`** — Menandai bahwa sebuah fungsi, variabel, atau class tersedia untuk digunakan oleh file lain.
- **`import`** — Mengambil fungsi, variabel, atau class dari file lain untuk digunakan di file saat ini.

```
[ matematika.js ]  --export-->  [ app.js ]
                   <--import--
```

Terdapat dua jenis export: **Named Export** dan **Default Export**.

---

### 2. Named Export

Gunakan Named Export ketika sebuah file memiliki **lebih dari satu** fungsi atau nilai yang ingin diekspor. Saat mengimpornya, nama harus ditulis persis sama (case-sensitive) dan diapit kurung kurawal `{}`.

**File sumber: `matematika.js`**

```javascript
// Setiap fungsi yang diberi kata kunci "export" dapat digunakan di file lain
export function hitungPajak(harga) {
  return harga * 0.11;
}

export function hitungDiskon(harga, persen) {
  return harga - (harga * persen) / 100;
}

export const TARIF_PAJAK = 0.11;
```

**File penerima: `app.js`**

```javascript
// Nama harus persis sama dengan yang diekspor
import { hitungPajak, hitungDiskon, TARIF_PAJAK } from "./matematika.js";

const harga = 100000;
const pajak = hitungPajak(harga);
const akhir = hitungDiskon(harga + pajak, 10);

console.log("Harga awal :", harga);
console.log("Pajak (11%):", pajak);
console.log("Setelah diskon 10%:", akhir);
```

**Mengimpor dengan alias:**

Jika nama yang diekspor terlalu panjang atau berkonflik dengan variabel lain, kamu dapat memberi alias menggunakan kata kunci `as`:

```javascript
import { hitungPajak as hitung, hitungDiskon as diskon } from "./matematika.js";

const pajak = hitung(50000);
const akhir = diskon(50000, 20);
```

**Mengimpor seluruh isi file sekaligus:**

```javascript
import * as Matematika from "./matematika.js";

console.log(Matematika.hitungPajak(100000)); // Output: 11000
console.log(Matematika.TARIF_PAJAK); // Output: 0.11
```

---

### 3. Default Export

Gunakan Default Export ketika sebuah file memang dirancang untuk mengekspor **satu hal utama** saja. Keuntungannya: saat mengimport, tidak perlu kurung kurawal, dan dapat diberi nama apa saja.

Setiap file hanya boleh memiliki **satu** `export default`.

**File sumber: `loginSistem.js`**

```javascript
// Fungsi utama file ini diekspor sebagai default
export default function prosesLogin(email, password) {
  if (!email || !password) {
    return { sukses: false, pesan: "Email dan password wajib diisi." };
  }
  return { sukses: true, pesan: "Login berhasil untuk " + email };
}
```

**File penerima: `app.js`**

```javascript
// Tanpa kurung kurawal, dan nama bebas ditentukan saat import
import login from "./loginSistem.js";

const hasil = login("budi@email.com", "rahasia123");
console.log(hasil.pesan); // Output: Login berhasil untuk budi@email.com
```

**Kombinasi Named Export dan Default Export dalam satu file:**

```javascript
// utils.js
export default function formatRupiah(angka) {
  return "Rp " + angka.toLocaleString("id-ID");
}

export function formatTanggal(date) {
  return date.toLocaleDateString("id-ID");
}

export const VERSI_APLIKASI = "1.0.0";
```

```javascript
// app.js
import formatRupiah, { formatTanggal, VERSI_APLIKASI } from "./utils.js";

console.log(formatRupiah(150000)); // Output: Rp 150.000
console.log(VERSI_APLIKASI); // Output: 1.0.0
```

**Perbandingan Named vs Default Export:**

|                            | Named Export                       | Default Export                      |
| -------------------------- | ---------------------------------- | ----------------------------------- |
| Jumlah per file            | Tidak terbatas                     | Hanya satu                          |
| Sintaks export             | `export function nama() {}`        | `export default function() {}`      |
| Sintaks import             | `import { nama } from "./file.js"` | `import namaBebas from "./file.js"` |
| Kurung kurawal saat import | Wajib                              | Tidak perlu                         |
| Nama saat import           | Harus sama persis                  | Bebas ditentukan                    |

---

### 4. Mengaktifkan Modul di HTML

Karena ES6 Modules bekerja dengan memuat file secara dinamis melalui protokol jaringan, tag `<script>` biasa tidak cukup. Kamu perlu menambahkan atribut `type="module"` pada tag script yang menjadi titik masuk aplikasimu.

```html
<!-- index.html -->
<body>
  <h1>Aplikasi Kasir</h1>

  <!-- Atribut type="module" wajib ada agar sistem import/export bekerja -->
  <script type="module" src="./app.js"></script>
</body>
```

**Perbedaan script biasa vs script modul:**

|                              | `<script src="...">` | `<script type="module" src="...">` |
| ---------------------------- | -------------------- | ---------------------------------- |
| Mendukung `import`/`export`? | Tidak                | Ya                                 |
| Scope variabel               | Global               | Lokal per file                     |
| Eksekusi                     | Sinkron              | Ditangguhkan hingga DOM selesai    |
| `this` di tingkat atas       | `window`             | `undefined`                        |

> **Catatan penting:** ES6 Modules tidak dapat dijalankan langsung dengan membuka file HTML di browser (`file://`). File harus dilayani melalui server lokal. Di VSCode, gunakan ekstensi **Live Server** untuk menjalankan server lokal secara otomatis.

---

### 5. Struktur Proyek dengan Modularisasi

Berikut contoh struktur folder proyek yang terorganisir menggunakan modularisasi:

```
proyek-kasir/
├── index.html
├── css/
│   └── style.css
└── js/
    ├── app.js           ← File utama (titik masuk)
    ├── kalkulasi.js     ← Modul perhitungan harga
    ├── tampilan.js      ← Modul manipulasi DOM
    └── validasi.js      ← Modul validasi input
```

**`kalkulasi.js`:**

```javascript
export function hitungSubtotal(harga, jumlah) {
  return harga * jumlah;
}

export function hitungPajak(subtotal) {
  return subtotal * 0.11;
}

export function hitungTotal(subtotal, pajak) {
  return subtotal + pajak;
}
```

**`validasi.js`:**

```javascript
export function validasiInput(nilai, label) {
  if (!nilai || nilai.trim() === "") {
    return label + " tidak boleh kosong.";
  }
  return null;
}
```

**`app.js`:**

```javascript
import { hitungSubtotal, hitungPajak, hitungTotal } from "./kalkulasi.js";
import { validasiInput } from "./validasi.js";

const harga = 75000;
const jumlah = 3;

const subtotal = hitungSubtotal(harga, jumlah);
const pajak = hitungPajak(subtotal);
const total = hitungTotal(subtotal, pajak);

console.log("Subtotal :", subtotal); // Output: 225000
console.log("Pajak    :", pajak); // Output: 24750
console.log("Total    :", total); // Output: 249750

const pesanError = validasiInput("", "Nama produk");
if (pesanError) {
  console.log(pesanError); // Output: Nama produk tidak boleh kosong.
}
```

---

### Kesimpulan

Modularisasi adalah praktik wajib dalam pengembangan JavaScript skala besar. Dengan memecah kode ke dalam modul-modul yang terfokus, kode menjadi lebih mudah dibaca, diuji, dan dipelihara. Pemahaman tentang Named Export dan Default Export juga menjadi prasyarat penting sebelum belajar framework seperti React atau Vue, karena keduanya menggunakan sistem modul ES6 secara intensif.

**Ringkasan:**

| Konsep          | Penjelasan                                                                                |
| --------------- | ----------------------------------------------------------------------------------------- |
| Modularisasi    | Memecah kode ke dalam file-file kecil yang masing-masing memiliki tanggung jawab spesifik |
| `export`        | Menandai fungsi atau variabel agar dapat digunakan di file lain                           |
| `import`        | Mengambil fungsi atau variabel dari file lain                                             |
| Named Export    | Mengekspor banyak hal dari satu file; import menggunakan `{}`                             |
| Default Export  | Mengekspor satu hal utama per file; import bebas nama tanpa `{}`                          |
| `import ... as` | Memberi alias pada sesuatu yang diimport                                                  |
| `import * as`   | Mengimport seluruh isi file sekaligus dalam satu namespace                                |
| `type="module"` | Atribut wajib pada tag `<script>` untuk mengaktifkan sistem modul                         |
