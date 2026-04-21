# Bab 52: JS DOM (Manipulasi DOM & DOM API)

## Tujuan Pembelajaran
- Memahami konsep Document Object Model (DOM) sebagai jembatan antara HTML dan JavaScript.
- Menguasai cara menyeleksi elemen HTML manggunakan DOM API (`querySelector`, `getElementById`).
- Mampu mengubah isi teks, gaya (style), dan kelas (class) dari sebuah elemen.
- Memahami cara menciptakan dan menyisipkan elemen baru secara dinamis ke halaman web.

## Materi Utama

Sejauh ini, kita menjalankan kode JavaScript dan melihat hasilnya tersembunyi di balik layar (di dalam *Console Browser*). Sekarang, saatnya JavaScript keluar dari bilik layar hitam dan mulai menyentuh, merombak, dan memanipulasi elemen-elemen HTML (judul, paragraf, tombol) yang dilihat langsung oleh pengunjung web.

Ilmu untuk menyentuh elemen HTML menggunakan JavaScript ini disebut dengan **Manipulasi DOM**.

### 1. Apa itu DOM?

**DOM (Document Object Model)** adalah cara browser mengubah struktur teks HTML yang kamu tulis menjadi sebuah "Pohon Keluarga Berbentuk Object" di dalam memorinya. 

Ketika browser melihat tag `<body>`, ia akan membuat sebuah Object untuk merepresentasikannya. Semua elemen di dalam halamanmu dirangkai menjadi struktur objek yang bercabang dari satu induk tertinggi yang bernama `document`. Melalui objek `document` inilah JavaScript bisa memerintah, mengubah, atau menghapus elemen HTML.

### 2. Mengambil (Menyeleksi) Elemen HTML

Langkah pertama sebelum memanipulasi elemen adalah "menemukan/menangkap" elemen tersebut dari halaman. Kita bisa menggunakan beberapa alat pencari (Methods) bawaan dari `document`.

**A. Mencari Lewat ID Mutlak (`getElementById`)**
Menangkap satu elemen spesifik yang memiliki atribut `id` tertentu.
```html
<h1 id="judul-utama">Selamat Datang</h1>
```
```javascript
// Tangkap elemennya dan simpan ke dalam variabel
const elemenJudul = document.getElementById("judul-utama");
```

**B. Pencari Universal Modern (`querySelector` & `querySelectorAll`)**
Ini adalah cara yang paling direkomendasikan saat ini. Kamu bisa mencari elemen layaknya kamu sedang menulis penyeleksi CSS (Bab 16).
- `querySelector` : Hanya mengambil **satu** elemen pertama yang cocok.
- `querySelectorAll` : Mengambil **semua** elemen yang cocok dan menggabungkannya ke dalam sebuah kumpulan (seperti Array).

```javascript
// Mengambil tombol pertama yang punya class "btn-login"
const tombolMasuk = document.querySelector(".btn-login");

// Mengambil SEMUA paragraf <p> di dalam halaman
const semuaParagraf = document.querySelectorAll("p");
```

### 3. Memanipulasi Isi dan Kosmetik Elemen

Setelah elemen berhasil ditangkap ke dalam wadah variabel, kita bisa merombaknya semau kita!

**A. Mengubah Teks Isi (`textContent` dan `innerHTML`)**
```javascript
const teksStatus = document.querySelector("#status-user");

// Hanya mengubah teks biasa (Aman dari retasan)
teksStatus.textContent = "Kamu sudah Logout.";

// Menyisipkan teks BERSERTA tag HTML baru di dalamnya
teksStatus.innerHTML = "Status: <strong>Aktif</strong>";
```

**B. Mengubah Gaya Kosmetik Langsung (`style`)**
JavaScript juga bisa menimpa warna dan properti CSS secara langsung (Inline Edit). Penulisan nama properti yang dua kata diubah menjadi *Camel Case* (contoh: `background-color` menjadi `backgroundColor`).
```javascript
const kotakPeringatan = document.querySelector(".alert");

kotakPeringatan.style.backgroundColor = "red";
kotakPeringatan.style.display = "none"; // Menghilangkan kotak dari layar
```

**C. Mengelola Kelas CSS (`classList`)**
Daripada menulis *style* manual satu persatu dari JS yang merepotkan, lebih baik kita cukup menambah atau menghapus "Class" CSS dari elemen tersebut.
```javascript
const tombolMenu = document.querySelector(".menu");

// Menambahkan class "menu-terbuka"
tombolMenu.classList.add("menu-terbuka");

// Menghapus class "menu-sembunyi"
tombolMenu.classList.remove("menu-sembunyi");

// Menambah class jika belum ada, dan menghapusnya jika sudah ada (Sistem Saklar)
tombolMenu.classList.toggle("mode-gelap");
```

### 4. Menciptakan Elemen Baru dari Nol

Terkadang, kita ingin menambahkan elemen yang sebelumnya sama sekali tidak ada di file HTML (misalnya: membuat notifikasi *bubble chat* baru ketika ada pesan masuk).

Langkah-langkahnya: Buat elemennya -> Isi kontennya -> Sisipkan ke dalam halaman.
```javascript
// 1. Ciptakan elemen <li> kosong di memoriawang-awang
const kotakPesanBaru = document.createElement("li");

// 2. Isi teks di dalamnya
kotakPesanBaru.textContent = "Halo, pesan baru dari Budi!";

// 3. Cari wadah induk (parent) tempat kotak ini akan diletakkan
const daftarChat = document.querySelector("#list-pesan");

// 4. Sisipkan elemen baru ini ke bagian penutup (anak terakhir) dari si wadah induk
daftarChat.appendChild(kotakPesanBaru);
```

Dengan menguasai keempat fondasi DOM di atas, kamu secara resmi telah bisa membuat sebuah halaman web statis yang kaku menjadi halaman aplikasi yang dinamis dan hidup! Pintu menuju pembuatan aplikasi interaktif sudah terbuka lebar.
