# Bab 16: JS DOM (Manipulasi DOM & DOM API)

## Tujuan Pembelajaran

- Memahami konsep Document Object Model (DOM) sebagai jembatan antara HTML dan JavaScript.
- Menguasai cara menyeleksi elemen HTML menggunakan DOM API (`querySelector`, `getElementById`).
- Mampu mengubah isi teks, gaya (_style_), dan kelas (_class_) dari sebuah elemen.
- Memahami cara menciptakan dan menyisipkan elemen baru secara dinamis ke halaman web.

---

## Materi Utama

Sejauh ini, kita menjalankan kode JavaScript dan melihat hasilnya di Console browser. Sekarang, saatnya JavaScript mulai menyentuh dan memanipulasi elemen-elemen HTML yang terlihat langsung oleh pengunjung — judul, paragraf, tombol, dan lainnya.

Ilmu untuk memanipulasi elemen HTML menggunakan JavaScript disebut **Manipulasi DOM**.

---

### 1. Apa itu DOM?

**DOM (Document Object Model)** adalah representasi struktur halaman HTML dalam bentuk pohon objek yang dibuat oleh browser di dalam memorinya. Setiap elemen HTML menjadi sebuah node dalam pohon tersebut, dengan `document` sebagai akar utamanya.

```
document
└── <html>
    ├── <head>
    │   └── <title>
    └── <body>
        ├── <h1>
        ├── <p>
        └── <div>
            ├── <button>
            └── <span>
```

Melalui objek `document` inilah JavaScript dapat membaca, mengubah, menambah, atau menghapus elemen HTML secara dinamis tanpa perlu memuat ulang halaman.

---

### 2. Menyeleksi Elemen HTML

Langkah pertama sebelum memanipulasi elemen adalah menemukannya. JavaScript menyediakan beberapa method untuk ini.

#### A. `getElementById(id)`

Mengembalikan satu elemen yang memiliki atribut `id` yang sesuai.

```html
<!-- HTML -->
<h1 id="judul-utama">Selamat Datang</h1>
```

```javascript
const judulUtama = document.getElementById("judul-utama");
console.log(judulUtama); // Output: <h1 id="judul-utama">Selamat Datang</h1>
```

#### B. `querySelector(selektor)` dan `querySelectorAll(selektor)`

Cara yang paling fleksibel dan direkomendasikan. Menggunakan sintaks selektor CSS yang sudah dipelajari.

- `querySelector` — Mengembalikan **satu** elemen pertama yang cocok.
- `querySelectorAll` — Mengembalikan **semua** elemen yang cocok dalam bentuk `NodeList`.

```javascript
// Menyeleksi satu elemen berdasarkan class
const tombolMasuk = document.querySelector(".btn-login");

// Menyeleksi satu elemen berdasarkan id
const formLogin = document.querySelector("#form-login");

// Menyeleksi satu elemen berdasarkan tag
const judulPertama = document.querySelector("h1");

// Menyeleksi semua paragraf di halaman
const semuaParagraf = document.querySelectorAll("p");

// Menyeleksi semua item dengan class tertentu
const semuaTombol = document.querySelectorAll(".btn");
```

**Iterasi hasil `querySelectorAll`:**

```javascript
const semuaParagraf = document.querySelectorAll("p");

semuaParagraf.forEach(function (paragraf) {
  paragraf.style.color = "gray";
});
```

**Perbandingan metode seleksi:**

| Method                    | Mencari Berdasarkan  | Mengembalikan                         |
| ------------------------- | -------------------- | ------------------------------------- |
| `getElementById("id")`    | Atribut `id`         | Satu elemen atau `null`               |
| `querySelector(".class")` | Selektor CSS apa pun | Elemen pertama yang cocok atau `null` |
| `querySelectorAll("p")`   | Selektor CSS apa pun | `NodeList` semua elemen yang cocok    |

---

### 3. Memanipulasi Konten Elemen

#### A. Mengubah Teks: `textContent` dan `innerHTML`

```html
<!-- HTML -->
<p id="status">Menunggu...</p>
```

```javascript
const status = document.querySelector("#status");

// textContent — hanya mengubah teks biasa
// Tag HTML yang disisipkan akan ditampilkan sebagai teks literal, bukan dirender
status.textContent = "Kamu sudah logout.";

// innerHTML — mengubah teks sekaligus merender tag HTML di dalamnya
status.innerHTML = "Status: <strong>Aktif</strong>";
```

> **Panduan keamanan:** Gunakan `textContent` untuk menampilkan data yang berasal dari input pengguna. Menggunakan `innerHTML` dengan data tidak terpercaya dapat membuka celah keamanan (_Cross-Site Scripting / XSS_). Gunakan `innerHTML` hanya untuk konten yang kamu kendalikan sendiri.

#### B. Membaca dan Mengubah Atribut

```javascript
const gambar = document.querySelector("img");

// Membaca atribut
console.log(gambar.getAttribute("src")); // Output: "foto.jpg"
console.log(gambar.getAttribute("alt")); // Output: "Deskripsi foto"

// Mengubah atribut
gambar.setAttribute("src", "foto-baru.jpg");
gambar.setAttribute("alt", "Foto produk terbaru");
```

---

### 4. Memanipulasi Gaya (Style)

#### A. Mengubah Style Secara Langsung

Properti CSS ditulis dalam format camelCase (contoh: `background-color` → `backgroundColor`).

```javascript
const kotakPeringatan = document.querySelector(".alert");

kotakPeringatan.style.backgroundColor = "red";
kotakPeringatan.style.color = "white";
kotakPeringatan.style.padding = "12px 16px";
kotakPeringatan.style.display = "none"; // Menyembunyikan elemen
```

#### B. Mengelola Class CSS (`classList`)

Pendekatan yang lebih direkomendasikan adalah menambah atau menghapus class CSS, lalu mendefinisikan gayanya di file CSS. Ini memisahkan tanggung jawab antara JavaScript (logika) dan CSS (tampilan).

```javascript
const tombolMenu = document.querySelector(".menu-toggle");
const navigasi = document.querySelector(".navigasi");

// Menambahkan class
navigasi.classList.add("terbuka");

// Menghapus class
navigasi.classList.remove("tersembunyi");

// Toggle — menambahkan class jika belum ada, menghapusnya jika sudah ada
tombolMenu.classList.toggle("aktif");

// Memeriksa apakah sebuah class ada
if (navigasi.classList.contains("terbuka")) {
  console.log("Menu sedang terbuka.");
}
```

**Contoh lengkap — Tombol toggle mode gelap:**

```html
<!-- HTML -->
<button id="toggle-tema">Ganti Tema</button>
<body id="halaman">
  ...
</body>
```

```javascript
const tombol = document.querySelector("#toggle-tema");
const halaman = document.querySelector("#halaman");

tombol.addEventListener("click", function () {
  halaman.classList.toggle("mode-gelap");

  const temaAktif = halaman.classList.contains("mode-gelap")
    ? "Gelap"
    : "Terang";
  tombol.textContent = "Tema: " + temaAktif;
});
```

```css
/* CSS */
.mode-gelap {
  background-color: #1a1a1a;
  color: #f0f0f0;
}
```

---

### 5. Menciptakan dan Menyisipkan Elemen Baru

Untuk menambahkan elemen yang sebelumnya tidak ada di HTML — misalnya notifikasi baru atau item daftar dari server — ikuti tiga langkah ini:

1. Buat elemen baru dengan `document.createElement(tag)`.
2. Isi konten dan atributnya.
3. Sisipkan ke dalam elemen induk.

```javascript
// 1. Buat elemen <li> baru
const itemBaru = document.createElement("li");

// 2. Isi kontennya
itemBaru.textContent = "Pesan baru dari Budi";
itemBaru.classList.add("item-pesan");

// 3. Temukan elemen induk dan sisipkan
const daftarPesan = document.querySelector("#daftar-pesan");
daftarPesan.appendChild(itemBaru); // Disisipkan sebagai anak terakhir
```

**Metode penyisipan lainnya:**

```javascript
const wadah = document.querySelector(".wadah");
const elemenBaru = document.createElement("p");
elemenBaru.textContent = "Paragraf baru";

// Sisipkan sebelum elemen pertama di dalam wadah
wadah.prepend(elemenBaru);

// Sisipkan setelah elemen tertentu
const acuan = document.querySelector(".acuan");
acuan.after(elemenBaru);

// Menghapus elemen dari DOM
const elemenDihapus = document.querySelector(".pesan-lama");
elemenDihapus.remove();
```

**Contoh lengkap — Membuat daftar dinamis:**

```html
<!-- HTML -->
<ul id="daftar-tugas"></ul>
```

```javascript
const tugas = ["Belajar JavaScript", "Membuat proyek", "Review kode"];
const daftarTugas = document.querySelector("#daftar-tugas");

tugas.forEach(function (namaTugas) {
  const item = document.createElement("li");
  item.textContent = namaTugas;
  daftarTugas.appendChild(item);
});

// Hasil HTML yang dihasilkan:
// <ul id="daftar-tugas">
//   <li>Belajar JavaScript</li>
//   <li>Membuat proyek</li>
//   <li>Review kode</li>
// </ul>
```

---

### Kesimpulan

Manipulasi DOM adalah kemampuan inti yang mengubah halaman web statis menjadi aplikasi yang dinamis dan interaktif. Dengan menguasai cara menyeleksi elemen, mengubah kontennya, mengelola class CSS, dan menciptakan elemen baru, kamu memiliki fondasi untuk membangun antarmuka yang merespons aksi pengguna secara real-time.

**Ringkasan:**

| Konsep / Method                   | Fungsi                                                   |
| --------------------------------- | -------------------------------------------------------- |
| `document.getElementById(id)`     | Menyeleksi satu elemen berdasarkan atribut `id`          |
| `document.querySelector(css)`     | Menyeleksi elemen pertama yang cocok dengan selektor CSS |
| `document.querySelectorAll(css)`  | Menyeleksi semua elemen yang cocok                       |
| `element.textContent`             | Membaca atau mengubah teks (tanpa HTML)                  |
| `element.innerHTML`               | Membaca atau mengubah konten termasuk tag HTML           |
| `element.setAttribute(attr, val)` | Mengubah nilai atribut elemen                            |
| `element.style.properti`          | Mengubah gaya CSS secara langsung (inline)               |
| `element.classList.add(cls)`      | Menambahkan class CSS                                    |
| `element.classList.remove(cls)`   | Menghapus class CSS                                      |
| `element.classList.toggle(cls)`   | Menambah/menghapus class secara bergantian               |
| `element.classList.contains(cls)` | Memeriksa apakah class ada                               |
| `document.createElement(tag)`     | Membuat elemen HTML baru                                 |
| `parent.appendChild(child)`       | Menyisipkan elemen sebagai anak terakhir                 |
| `element.remove()`                | Menghapus elemen dari DOM                                |
