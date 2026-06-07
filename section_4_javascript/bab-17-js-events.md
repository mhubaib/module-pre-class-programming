# Bab 17: JS Events

## Tujuan Pembelajaran

- Memahami konsep _Event_ sebagai mekanisme pendeteksi interaksi pengguna.
- Mampu memasang dan merespons _Event Listener_ untuk berbagai jenis aksi pengguna.
- Membaca dan memanfaatkan data dari _Event Object_.
- Menguasai `preventDefault()` untuk mencegah perilaku bawaan browser.

---

## Materi Utama

Pada Bab 16 kita telah berhasil memanipulasi elemen DOM. Namun, manipulasi tersebut idealnya tidak berjalan otomatis begitu halaman dimuat — melainkan dipicu oleh aksi pengguna: klik tombol, ketikan di kolom input, atau pengiriman formulir.

Mekanisme untuk mendeteksi dan merespons aksi pengguna ini disebut **Event Handling**.

---

### 1. Memasang Event Listener

Method utama untuk mendeteksi event adalah `addEventListener()`. Method ini dipasang pada sebuah elemen dan menerima dua argumen:

1. **Nama event** — jenis aksi yang ingin dideteksi, misalnya `"click"`.
2. **Callback function** — fungsi yang akan dijalankan saat event tersebut terjadi.

```javascript
const tombolBeli = document.querySelector("#btn-beli");

tombolBeli.addEventListener("click", function () {
  alert("Terima kasih telah melakukan pembelian!");
  tombolBeli.textContent = "Sudah Dibeli";
});
```

Fungsi callback juga dapat ditulis menggunakan Arrow Function:

```javascript
tombolBeli.addEventListener("click", () => {
  tombolBeli.textContent = "Sudah Dibeli";
  tombolBeli.disabled = true;
});
```

---

### 2. Jenis-Jenis Event yang Umum Digunakan

#### A. Event Mouse

| Event        | Kapan Terpicu                              |
| ------------ | ------------------------------------------ |
| `click`      | Saat elemen diklik (tekan dan lepas)       |
| `dblclick`   | Saat elemen diklik dua kali berturut-turut |
| `mouseenter` | Saat kursor memasuki area elemen           |
| `mouseleave` | Saat kursor meninggalkan area elemen       |
| `mousemove`  | Setiap kali kursor bergerak di atas elemen |

```javascript
const kartu = document.querySelector(".kartu-produk");

kartu.addEventListener("mouseenter", () => {
  kartu.style.boxShadow = "0 8px 16px rgba(0,0,0,0.2)";
});

kartu.addEventListener("mouseleave", () => {
  kartu.style.boxShadow = "none";
});
```

#### B. Event Keyboard

| Event     | Kapan Terpicu                |
| --------- | ---------------------------- |
| `keydown` | Saat tombol keyboard ditekan |
| `keyup`   | Saat tombol keyboard dilepas |

```javascript
const kolomPencarian = document.querySelector("#kolom-cari");

kolomPencarian.addEventListener("keydown", (e) => {
  // Jalankan pencarian saat tombol Enter ditekan
  if (e.key === "Enter") {
    console.log("Mencari:", kolomPencarian.value);
  }
});
```

#### C. Event Form

| Event    | Kapan Terpicu                                        |
| -------- | ---------------------------------------------------- |
| `input`  | Setiap kali nilai input berubah (real-time)          |
| `change` | Saat nilai input berubah dan elemen kehilangan fokus |
| `submit` | Saat formulir dikirimkan                             |
| `focus`  | Saat elemen mendapat fokus                           |
| `blur`   | Saat elemen kehilangan fokus                         |

```javascript
const kolomEmail = document.querySelector("#email");

kolomEmail.addEventListener("input", (e) => {
  const nilai = e.target.value;
  if (!nilai.includes("@")) {
    kolomEmail.style.borderColor = "red";
  } else {
    kolomEmail.style.borderColor = "green";
  }
});
```

#### D. Event Halaman

| Event              | Kapan Terpicu                                                |
| ------------------ | ------------------------------------------------------------ |
| `load`             | Saat seluruh halaman selesai dimuat                          |
| `DOMContentLoaded` | Saat struktur DOM selesai dibangun (lebih cepat dari `load`) |
| `scroll`           | Saat halaman atau elemen di-scroll                           |
| `resize`           | Saat ukuran jendela browser berubah                          |

```javascript
document.addEventListener("DOMContentLoaded", () => {
  console.log("DOM siap. JavaScript dapat mengakses elemen HTML.");
});
```

---

### 3. Event Object

Setiap kali sebuah event terjadi, JavaScript secara otomatis membuat **Event Object** yang berisi informasi lengkap tentang kejadian tersebut. Object ini diteruskan ke callback function sebagai argumen pertama, biasanya diberi nama `e` atau `event`.

```javascript
const tombol = document.querySelector("#tombol");

tombol.addEventListener("click", function (e) {
  console.log("Tipe event    :", e.type); // Output: "click"
  console.log("Elemen target :", e.target); // Output: <button id="tombol">
  console.log("Posisi X mouse:", e.clientX); // Koordinat X kursor
  console.log("Posisi Y mouse:", e.clientY); // Koordinat Y kursor
});
```

**Properti Event Object yang umum digunakan:**

| Properti / Method         | Keterangan                                           |
| ------------------------- | ---------------------------------------------------- |
| `e.type`                  | Nama event yang terjadi (`"click"`, `"input"`, dll.) |
| `e.target`                | Elemen yang memicu event                             |
| `e.target.value`          | Nilai input pada elemen form                         |
| `e.key`                   | Nama tombol keyboard yang ditekan                    |
| `e.clientX` / `e.clientY` | Koordinat kursor saat event terjadi                  |
| `e.preventDefault()`      | Mencegah perilaku bawaan browser                     |

**Membaca nilai input secara real-time:**

```html
<!-- HTML -->
<input type="text" id="kolom-nama" placeholder="Ketik nama Anda" />
<p id="pratinjau"></p>
```

```javascript
const kolomNama = document.querySelector("#kolom-nama");
const pratinjau = document.querySelector("#pratinjau");

kolomNama.addEventListener("input", (e) => {
  pratinjau.textContent = "Halo, " + e.target.value + "!";
});
```

---

### 4. `preventDefault()` — Mencegah Perilaku Bawaan Browser

Beberapa elemen HTML memiliki perilaku bawaan yang terjadi saat di-interaksi:

- Elemen `<a href="...">` akan berpindah halaman saat diklik.
- Elemen `<form>` akan memuat ulang (_refresh_) halaman saat formulir dikirimkan.

Dalam pengembangan web modern, kita sering perlu mencegah perilaku ini agar dapat memproses data secara dinamis di JavaScript tanpa reload halaman. Gunakan `e.preventDefault()` untuk itu.

```javascript
// Mencegah tautan berpindah halaman
const tautan = document.querySelector("#tautan-lihat");

tautan.addEventListener("click", (e) => {
  e.preventDefault(); // Tautan tidak akan berpindah halaman
  console.log("Konten ditampilkan secara dinamis tanpa berpindah halaman.");
});
```

```javascript
// Mencegah formulir me-refresh halaman
const formLogin = document.querySelector("#form-login");

formLogin.addEventListener("submit", (e) => {
  e.preventDefault(); // Halaman tidak akan di-refresh

  const email = document.querySelector("#email").value;
  const password = document.querySelector("#password").value;

  console.log("Memproses login untuk:", email);
  // Data dapat dikirim ke server menggunakan fetch() tanpa reload halaman
});
```

---

### 5. Event Delegation

Ketika kamu memiliki banyak elemen yang perlu didengarkan, memasang `addEventListener` pada setiap elemen secara individual tidak efisien. **Event Delegation** adalah teknik memasang satu `addEventListener` pada elemen induk, lalu memeriksa `e.target` untuk menentukan elemen mana yang diklik.

```html
<!-- HTML: daftar tombol yang jumlahnya bisa bertambah secara dinamis -->
<ul id="daftar-menu">
  <li>Beranda</li>
  <li>Produk</li>
  <li>Tentang</li>
</ul>
```

```javascript
const daftarMenu = document.querySelector("#daftar-menu");

// Satu listener untuk semua <li> di dalamnya
daftarMenu.addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Menu yang dipilih:", e.target.textContent);
    e.target.classList.toggle("aktif");
  }
});
```

Teknik ini juga bekerja untuk elemen yang ditambahkan secara dinamis setelah halaman dimuat — karena listener dipasang di induk, bukan di setiap elemen anak.

---

### 6. Simulasi Lengkap — Formulir Pendaftaran Interaktif

Berikut contoh yang menggabungkan seluruh konsep event yang telah dipelajari:

```html
<!-- HTML -->
<form id="form-daftar">
  <input type="text" id="nama" placeholder="Nama lengkap" />
  <input type="email" id="email" placeholder="Alamat email" />
  <input type="password" id="sandi" placeholder="Kata sandi" />
  <button type="submit">Daftar</button>
  <p id="pesan-status"></p>
</form>
```

```javascript
const form = document.querySelector("#form-daftar");
const pesan = document.querySelector("#pesan-status");
const inputSandi = document.querySelector("#sandi");

// Validasi real-time — tampilkan peringatan jika kata sandi terlalu pendek
inputSandi.addEventListener("input", (e) => {
  if (e.target.value.length < 8) {
    inputSandi.style.borderColor = "red";
    pesan.textContent = "Kata sandi minimal 8 karakter.";
    pesan.style.color = "red";
  } else {
    inputSandi.style.borderColor = "green";
    pesan.textContent = "";
  }
});

// Proses pengiriman formulir tanpa reload halaman
form.addEventListener("submit", (e) => {
  e.preventDefault();

  const nama = document.querySelector("#nama").value.trim();
  const email = document.querySelector("#email").value.trim();
  const sandi = document.querySelector("#sandi").value;

  if (!nama || !email || !sandi) {
    pesan.textContent = "Semua kolom wajib diisi.";
    pesan.style.color = "red";
    return;
  }

  if (sandi.length < 8) {
    pesan.textContent = "Kata sandi terlalu pendek.";
    pesan.style.color = "red";
    return;
  }

  pesan.textContent = "Pendaftaran berhasil! Selamat datang, " + nama + ".";
  pesan.style.color = "green";
  form.reset();
});
```

---

### Kesimpulan

Event Handling adalah jembatan antara DOM dan interaksi pengguna. Dengan menguasai `addEventListener`, Event Object, `preventDefault()`, dan Event Delegation, kamu dapat membangun antarmuka yang sepenuhnya responsif terhadap aksi pengguna — tanpa memuat ulang halaman.

**Ringkasan:**

| Konsep / Method                     | Fungsi                                                               |
| ----------------------------------- | -------------------------------------------------------------------- |
| `addEventListener(event, callback)` | Memasang pendengar event pada elemen                                 |
| `e.type`                            | Nama event yang terpicu                                              |
| `e.target`                          | Elemen yang memicu event                                             |
| `e.target.value`                    | Nilai input dari elemen form                                         |
| `e.key`                             | Tombol keyboard yang ditekan                                         |
| `e.preventDefault()`                | Mencegah perilaku bawaan browser                                     |
| Event Delegation                    | Teknik memasang satu listener pada induk untuk menangani banyak anak |
| `"click"`                           | Event klik mouse                                                     |
| `"input"`                           | Event perubahan nilai input secara real-time                         |
| `"submit"`                          | Event pengiriman formulir                                            |
| `"keydown"`                         | Event penekanan tombol keyboard                                      |
| `"DOMContentLoaded"`                | Event ketika DOM selesai dibangun                                    |
