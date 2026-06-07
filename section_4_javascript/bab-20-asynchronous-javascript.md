# Bab 20: Asynchronous JavaScript

## Tujuan Pembelajaran

- Membedakan paradigma eksekusi _Synchronous_ dan _Asynchronous_.
- Memahami konsep Promise sebagai wadah nilai yang akan tersedia di masa mendatang.
- Menguasai sintaks `async` / `await` untuk menulis kode asinkron yang mudah dibaca.
- Menangani error pada operasi asinkron menggunakan `try...catch`.

---

## Materi Utama

JavaScript adalah bahasa yang bersifat **Single-Threaded** — ia hanya dapat mengerjakan satu instruksi pada satu waktu, secara berurutan dari atas ke bawah. Dalam kondisi normal (disebut _Synchronous_), jika satu baris kode memerlukan waktu lama untuk selesai, seluruh program akan berhenti menunggu hingga baris tersebut selesai.

Ini menjadi masalah besar ketika program perlu menunggu operasi yang lambat seperti memuat data dari server, yang bisa memakan waktu beberapa detik. Layar aplikasi akan _freeze_ dan tidak merespons selama menunggu.

Solusinya adalah **Asynchronous JavaScript** — mekanisme yang memungkinkan operasi yang lama diproses di latar belakang, sementara program tetap berjalan dan merespons interaksi pengguna.

---

### 1. Synchronous vs Asynchronous

**Synchronous** — setiap baris dieksekusi secara berurutan, baris berikutnya hanya dijalankan setelah baris sebelumnya selesai.

```javascript
console.log("Mulai");
console.log("Tengah");
console.log("Selesai");
// Output (berurutan):
// Mulai
// Tengah
// Selesai
```

**Asynchronous** — operasi yang lama dijalankan di latar belakang, dan baris berikutnya dapat terus dieksekusi tanpa menunggu.

`setTimeout()` adalah contoh sederhana operasi asinkron — ia menunda eksekusi sebuah fungsi tanpa memblokir program.

```javascript
console.log("1. Mulai memasak nasi...");

setTimeout(function () {
  console.log("2. Nasi sudah matang!");
}, 3000); // Dieksekusi setelah 3 detik

console.log("3. Sambil menunggu, goreng tempe...");

// Output (urutan tidak linear):
// 1. Mulai memasak nasi...
// 3. Sambil menunggu, goreng tempe...
// (3 detik kemudian...)
// 2. Nasi sudah matang!
```

Baris ke-3 dieksekusi sebelum baris ke-2 selesai — ini adalah inti dari asynchronous.

---

### 2. Promise

**Promise** adalah objek yang merepresentasikan nilai yang akan tersedia di masa mendatang — biasanya hasil dari operasi asinkron seperti permintaan data ke server.

Sebuah Promise memiliki tiga kemungkinan status:

| Status        | Keterangan                                         |
| ------------- | -------------------------------------------------- |
| **Pending**   | Operasi sedang berjalan, hasil belum tersedia      |
| **Fulfilled** | Operasi berhasil, nilai tersedia                   |
| **Rejected**  | Operasi gagal (error jaringan, server error, dll.) |

**Membuat Promise:**

```javascript
const janji = new Promise(function (resolve, reject) {
  const berhasil = true;

  if (berhasil) {
    resolve("Data berhasil dimuat."); // Fulfilled
  } else {
    reject("Terjadi kesalahan koneksi."); // Rejected
  }
});
```

**Mengonsumsi Promise dengan `.then()` dan `.catch()`:**

```javascript
janji
  .then(function (hasil) {
    console.log("Berhasil:", hasil);
    // Output: Berhasil: Data berhasil dimuat.
  })
  .catch(function (error) {
    console.log("Gagal:", error);
  })
  .finally(function () {
    console.log("Selesai — baik berhasil maupun gagal.");
  });
```

**Contoh Promise dengan simulasi penundaan:**

```javascript
function ambilDataPengguna(id) {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      if (id > 0) {
        resolve({ id: id, nama: "Budi Santoso", email: "budi@email.com" });
      } else {
        reject("ID pengguna tidak valid.");
      }
    }, 2000); // Simulasi waktu tunggu 2 detik
  });
}

ambilDataPengguna(1)
  .then(function (pengguna) {
    console.log("Data diterima:", pengguna.nama);
  })
  .catch(function (error) {
    console.log("Error:", error);
  });
```

---

### 3. `async` / `await`

Sintaks `async/await` yang diperkenalkan pada ES2017 adalah cara yang lebih bersih dan mudah dibaca untuk bekerja dengan Promise. Alih-alih merantai `.then()` dan `.catch()`, kamu dapat menulis kode asinkron seolah-olah ia bersifat synchronous.

**Dua aturan utama:**

1. **`async`** ditulis sebelum kata kunci `function` — menandai bahwa fungsi tersebut bersifat asinkron dan selalu mengembalikan Promise.
2. **`await`** hanya dapat digunakan di dalam fungsi `async` — ia menghentikan eksekusi hingga Promise di depannya selesai (fulfilled atau rejected).

```javascript
// Fungsi yang mengembalikan Promise (simulasi mengambil data)
function ambilData() {
  return new Promise(function (resolve) {
    setTimeout(function () {
      resolve({ nama: "Budi", nilai: 95 });
    }, 2000);
  });
}

// Menggunakan async/await
async function tampilkanData() {
  console.log("Mengambil data...");

  const data = await ambilData(); // Menunggu hingga Promise selesai

  // Baris ini baru dieksekusi setelah data tersedia
  console.log("Nama :", data.nama);
  console.log("Nilai:", data.nilai);
}

tampilkanData();
// Output:
// Mengambil data...
// (2 detik kemudian...)
// Nama : Budi
// Nilai: 95
```

**Perbandingan `.then()` vs `async/await`:**

```javascript
// Dengan .then() — bersarang dan sulit dibaca saat kompleks
function tampilkanDenganThen() {
  ambilDataPengguna(1)
    .then(function (pengguna) {
      return ambilPostinganUser(pengguna.id);
    })
    .then(function (postingan) {
      console.log("Postingan:", postingan);
    })
    .catch(function (error) {
      console.log("Error:", error);
    });
}

// Dengan async/await — lebih linear dan mudah dibaca
async function tampilkanDenganAwait() {
  const pengguna = await ambilDataPengguna(1);
  const postingan = await ambilPostinganUser(pengguna.id);
  console.log("Postingan:", postingan);
}
```

---

### 4. Menangani Error dengan `try...catch`

Saat menggunakan `async/await`, gunakan `try...catch` untuk menangani error yang terjadi ketika Promise ditolak (rejected).

```javascript
async function muatProfilPengguna(id) {
  try {
    const pengguna = await ambilDataPengguna(id);
    console.log("Profil berhasil dimuat:", pengguna.nama);
    return pengguna;
  } catch (error) {
    console.log("Gagal memuat profil:", error);
    return null;
  } finally {
    console.log("Proses selesai.");
  }
}

muatProfilPengguna(1); // Berhasil
muatProfilPengguna(-1); // Akan menangkap error
```

---

### 5. Menjalankan Beberapa Promise Secara Paralel

Jika kamu memiliki beberapa operasi asinkron yang tidak saling bergantung, jalankan keduanya secara bersamaan menggunakan `Promise.all()` untuk menghemat waktu.

```javascript
function ambilDataProduk() {
  return new Promise((resolve) =>
    setTimeout(() => resolve(["Sepatu", "Baju"]), 1000),
  );
}

function ambilDataPengguna(id) {
  return new Promise((resolve) =>
    setTimeout(() => resolve({ id, nama: "Budi" }), 1500),
  );
}

// Berurutan — total waktu tunggu 2.5 detik (1 + 1.5)
async function berurutan() {
  const produk = await ambilDataProduk();
  const pengguna = await ambilDataPengguna(1);
  console.log(produk, pengguna);
}

// Paralel — total waktu tunggu 1.5 detik (menunggu yang terlama)
async function paralel() {
  const [produk, pengguna] = await Promise.all([
    ambilDataProduk(),
    ambilDataPengguna(1),
  ]);
  console.log(produk, pengguna);
}
```

**Method `Promise` yang umum digunakan:**

| Method                      | Perilaku                                                       |
| --------------------------- | -------------------------------------------------------------- |
| `Promise.all([...])`        | Menunggu semua Promise selesai. Gagal jika salah satu ditolak. |
| `Promise.allSettled([...])` | Menunggu semua selesai tanpa peduli berhasil atau gagal.       |
| `Promise.race([...])`       | Mengembalikan hasil dari Promise yang pertama kali selesai.    |
| `Promise.any([...])`        | Mengembalikan hasil dari Promise yang pertama kali berhasil.   |

---

### 6. Simulasi Lengkap — Memuat dan Menampilkan Data Pengguna

```javascript
// Simulasi fungsi pengambil data (meniru perilaku Fetch API)
function ambilPengguna(id) {
  return new Promise(function (resolve, reject) {
    setTimeout(function () {
      const database = {
        1: {
          id: 1,
          nama: "Budi Santoso",
          email: "budi@email.com",
          premium: true,
        },
        2: {
          id: 2,
          nama: "Ani Rahayu",
          email: "ani@email.com",
          premium: false,
        },
      };

      const pengguna = database[id];
      if (pengguna) {
        resolve(pengguna);
      } else {
        reject("Pengguna dengan ID " + id + " tidak ditemukan.");
      }
    }, 1500);
  });
}

async function tampilkanProfilPengguna(id) {
  console.log("Memuat profil pengguna ID:", id);

  try {
    const pengguna = await ambilPengguna(id);

    console.log("---");
    console.log("Nama   :", pengguna.nama);
    console.log("Email  :", pengguna.email);
    console.log("Status :", pengguna.premium ? "Premium" : "Reguler");
  } catch (error) {
    console.log("Error:", error);
  }
}

tampilkanProfilPengguna(1);
// Output:
// Memuat profil pengguna ID: 1
// (1.5 detik kemudian...)
// ---
// Nama   : Budi Santoso
// Email  : budi@email.com
// Status : Premium

tampilkanProfilPengguna(99);
// Output:
// Memuat profil pengguna ID: 99
// Error: Pengguna dengan ID 99 tidak ditemukan.
```

---

### Kesimpulan

Asynchronous JavaScript adalah konsep fundamental yang harus dikuasai sebelum bekerja dengan data dari server. Dengan memahami Promise dan sintaks `async/await`, kamu dapat menulis kode yang menangani operasi waktu-tidak-pasti dengan cara yang terstruktur, mudah dibaca, dan tidak memblokir antarmuka pengguna.

Pemahaman materi ini adalah prasyarat langsung untuk mempelajari Fetch API di bab berikutnya.

**Ringkasan:**

| Konsep                 | Penjelasan                                                                    |
| ---------------------- | ----------------------------------------------------------------------------- |
| Synchronous            | Kode dieksekusi berurutan; baris berikutnya menunggu baris sebelumnya selesai |
| Asynchronous           | Operasi lama dijalankan di latar belakang; program tidak diblokir             |
| Promise                | Objek yang merepresentasikan nilai yang akan tersedia di masa mendatang       |
| `.then()` / `.catch()` | Cara mengonsumsi Promise menggunakan chaining                                 |
| `async`                | Menandai fungsi sebagai asinkron; fungsi selalu mengembalikan Promise         |
| `await`                | Menghentikan eksekusi di dalam fungsi `async` hingga Promise selesai          |
| `try...catch`          | Menangani error pada operasi `async/await`                                    |
| `Promise.all()`        | Menjalankan beberapa Promise secara paralel dan menunggu semua selesai        |
