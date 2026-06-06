# Bab 13: Scope, Hoisting, & Closure

## Tujuan Pembelajaran

- Memahami `Scope` sebagai batasan wilayah di mana sebuah variabel dapat diakses.
- Mengetahui fenomena `Hoisting` dan dampaknya terhadap urutan eksekusi kode.
- Memahami konsep `Closure` dan bagaimana sebuah fungsi mengingat lingkup tempat ia dibuat.

---

## Materi Utama

Scope, Hoisting, dan Closure adalah tiga konsep inti JavaScript yang sering menjadi topik dalam wawancara teknis pengembang. Memahami ketiganya akan memberikan gambaran yang jelas tentang cara kerja JavaScript di balik layar.

---

### 1. Scope (Cakupan Wilayah Akses)

**Scope** menentukan di mana sebuah variabel dapat diakses dalam kode. Variabel yang dideklarasikan di satu tempat tidak selalu dapat diakses dari tempat lain.

JavaScript memiliki tiga jenis scope:

#### A. Global Scope

Variabel yang dideklarasikan di luar fungsi atau blok mana pun berada di **Global Scope**. Variabel ini dapat diakses dari mana saja dalam program.

```javascript
const pajakPPN = 11; // Global Scope

function hitungHarga(harga) {
  // Variabel pajakPPN dari Global Scope dapat diakses di sini
  const pajak = harga * (pajakPPN / 100);
  return harga + pajak;
}

console.log(hitungHarga(100000)); // Output: 111000
console.log(pajakPPN); // Output: 11 — dapat diakses di mana saja
```

#### B. Local Scope (Function Scope)

Variabel yang dideklarasikan di dalam sebuah fungsi hanya dapat diakses dari dalam fungsi tersebut. Variabel ini tidak terlihat dari luar.

```javascript
function prosesLogin() {
  const tokenSesi = "abc123xyz"; // Local Scope — hanya ada di dalam fungsi ini
  console.log("Token:", tokenSesi); // Output: Token: abc123xyz
}

prosesLogin();
console.log(tokenSesi);
// ReferenceError: tokenSesi is not defined
// Variabel ini tidak ada di luar fungsi prosesLogin
```

#### C. Block Scope

Variabel yang dideklarasikan menggunakan `let` atau `const` di dalam blok `{}` hanya dapat diakses di dalam blok tersebut — termasuk blok `if`, `for`, dan `while`.

```javascript
if (true) {
  let pesanDalam = "Saya ada di dalam blok if";
  console.log(pesanDalam); // Output: Saya ada di dalam blok if
}
console.log(pesanDalam);
// ReferenceError: pesanDalam is not defined

// Contoh dengan for loop
for (let i = 0; i < 3; i++) {
  // variabel i hanya ada di dalam blok for
}
console.log(i);
// ReferenceError: i is not defined
```

> **Catatan:** Variabel yang dideklarasikan dengan `var` tidak memiliki block scope — ia hanya mengenal global scope dan function scope. Inilah salah satu alasan `var` tidak lagi direkomendasikan.

**Ilustrasi Scope bertingkat:**

```javascript
const nama = "Global"; // Global Scope

function luarFungsi() {
  const nama = "Luar"; // Function Scope — menutupi variabel global di dalam fungsi ini

  function dalamFungsi() {
    const nama = "Dalam"; // Function Scope — menutupi variabel luar di dalam fungsi ini
    console.log(nama); // Output: "Dalam"
  }

  dalamFungsi();
  console.log(nama); // Output: "Luar"
}

luarFungsi();
console.log(nama); // Output: "Global"
```

Ketika sebuah variabel diakses, JavaScript mencarinya dari scope terdekat ke yang terluar. Prinsip ini disebut **Scope Chain**.

---

### 2. Hoisting (Pengangkatan Deklarasi)

**Hoisting** adalah perilaku JavaScript di mana deklarasi fungsi dan variabel secara otomatis "diangkat" ke bagian atas scope-nya sebelum kode dieksekusi. Ini terjadi pada tahap awal saat mesin JavaScript membaca seluruh kode.

#### A. Hoisting pada Function Declaration

Function Declaration sepenuhnya di-hoist — fungsi dapat dipanggil bahkan sebelum baris deklarasinya.

```javascript
// Dipanggil sebelum dideklarasikan
sapaUser(); // Output: Halo, Pengguna!

// Deklarasi fungsi ada di bawah
function sapaUser() {
  console.log("Halo, Pengguna!");
}
```

Ini berfungsi karena JavaScript mengangkat seluruh isi fungsi ke atas sebelum menjalankan kode.

#### B. Hoisting pada `var`

Variabel `var` juga di-hoist, namun hanya **deklarasinya** saja — bukan nilainya. Nilai variabel tetap `undefined` hingga baris penugasannya dieksekusi.

```javascript
console.log(warna); // Output: undefined — deklarasi diangkat, tapi nilai belum ada
var warna = "biru";
console.log(warna); // Output: "biru"
```

Perilaku ini sering menjadi sumber bug yang sulit dilacak karena variabel tampak "sudah ada" namun nilainya masih `undefined`.

#### C. `let` dan `const` Tidak Di-Hoist

Berbeda dengan `var`, variabel `let` dan `const` **tidak dapat diakses** sebelum baris deklarasinya meskipun secara teknis deklarasinya diproses. Mengaksesnya sebelum dideklarasikan akan menghasilkan `ReferenceError`.

```javascript
console.log(kota);
// ReferenceError: Cannot access 'kota' before initialization
const kota = "Jakarta";
```

Inilah alasan utama mengapa `let` dan `const` direkomendasikan — perilakunya lebih dapat diprediksi dan mencegah bug akibat hoisting.

**Perbandingan perilaku hoisting:**

|                                  | `var`                  | `let` / `const`               | Function Declaration |
| -------------------------------- | ---------------------- | ----------------------------- | -------------------- |
| Deklarasi di-hoist?              | Ya                     | Ya (tapi tidak dapat diakses) | Ya                   |
| Nilai di-hoist?                  | Tidak (`undefined`)    | Tidak                         | Ya (seluruh fungsi)  |
| Dapat diakses sebelum deklarasi? | Ya (nilai `undefined`) | Tidak (ReferenceError)        | Ya                   |

---

### 3. Closure (Fungsi yang Mengingat Lingkungannya)

**Closure** adalah kemampuan sebuah fungsi untuk mengingat dan mengakses variabel dari lingkup (scope) tempat fungsi tersebut dibuat, bahkan setelah fungsi luar selesai dieksekusi.

Konsep ini terjadi secara otomatis ketika sebuah fungsi didefinisikan di dalam fungsi lain.

```javascript
function buatPenghitung() {
  let hitungan = 0; // Variabel di scope luar

  // Fungsi dalam — memiliki akses ke variabel "hitungan"
  return function tambah() {
    hitungan++;
    console.log("Hitungan saat ini:", hitungan);
  };
}

const penghitung = buatPenghitung();
// Fungsi buatPenghitung() selesai dieksekusi, namun "hitungan" tetap diingat

penghitung(); // Output: Hitungan saat ini: 1
penghitung(); // Output: Hitungan saat ini: 2
penghitung(); // Output: Hitungan saat ini: 3
```

Setiap kali `penghitung()` dipanggil, ia mengakses dan memperbarui variabel `hitungan` yang tetap diingat melalui closure — meskipun `buatPenghitung()` sudah selesai dieksekusi.

**Contoh praktis — Simulasi rekening bank:**

```javascript
function buatRekening(saldoAwal) {
  let saldo = saldoAwal; // Variabel privat — tidak dapat diakses dari luar

  return {
    setor(jumlah) {
      saldo += jumlah;
      console.log("Setoran berhasil. Saldo:", saldo);
    },
    tarik(jumlah) {
      if (jumlah > saldo) {
        console.log("Saldo tidak mencukupi.");
        return;
      }
      saldo -= jumlah;
      console.log("Penarikan berhasil. Saldo:", saldo);
    },
    cekSaldo() {
      console.log("Saldo saat ini:", saldo);
    },
  };
}

const rekeningBudi = buatRekening(1000000);

rekeningBudi.cekSaldo(); // Output: Saldo saat ini: 1000000
rekeningBudi.setor(500000); // Output: Setoran berhasil. Saldo: 1500000
rekeningBudi.tarik(200000); // Output: Penarikan berhasil. Saldo: 1300000

// Variabel "saldo" tidak dapat diakses langsung dari luar
console.log(rekeningBudi.saldo); // Output: undefined — terlindungi oleh closure
```

Dalam contoh di atas, closure digunakan untuk menciptakan **data privat** — variabel `saldo` hanya dapat diakses dan dimodifikasi melalui method yang disediakan, tidak bisa diubah secara langsung dari luar.

**Setiap pemanggilan fungsi luar membuat closure yang independen:**

```javascript
const rekeningAni = buatRekening(500000);
const rekeningBudi = buatRekening(2000000);

rekeningAni.setor(100000);
// Output: Setoran berhasil. Saldo: 600000

rekeningBudi.tarik(500000);
// Output: Penarikan berhasil. Saldo: 1500000

// Kedua rekening memiliki variabel "saldo" yang sepenuhnya terpisah
rekeningAni.cekSaldo(); // Output: Saldo saat ini: 600000
rekeningBudi.cekSaldo(); // Output: Saldo saat ini: 1500000
```

---

### Kesimpulan

Ketiga konsep ini saling berkaitan dan membentuk landasan cara JavaScript mengelola variabel dan eksekusi kode. Scope menentukan di mana variabel dapat diakses; Hoisting menjelaskan urutan pemrosesan deklarasi; dan Closure memungkinkan fungsi mempertahankan akses ke variabel dari lingkup tempat ia dibuat.

**Ringkasan:**

| Konsep                 | Penjelasan                                                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| Global Scope           | Variabel yang dapat diakses dari mana saja dalam program                                    |
| Local/Function Scope   | Variabel yang hanya dapat diakses di dalam fungsi tempat ia dideklarasikan                  |
| Block Scope            | Variabel `let`/`const` yang hanya dapat diakses di dalam blok `{}` tempat ia dideklarasikan |
| Scope Chain            | Mekanisme JavaScript mencari variabel dari scope terdekat ke terluar                        |
| Hoisting               | Pengangkatan deklarasi fungsi dan variabel ke bagian atas scope sebelum eksekusi            |
| `var` hoisting         | Deklarasi diangkat, nilai tetap `undefined` hingga baris penugasan dieksekusi               |
| `let`/`const` hoisting | Tidak dapat diakses sebelum dideklarasikan (ReferenceError)                                 |
| Closure                | Kemampuan fungsi mengingat dan mengakses variabel dari scope tempat ia dibuat               |
