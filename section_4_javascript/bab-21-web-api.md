# Bab 21: Web API

## Tujuan Pembelajaran

- Memahami konsep Web API sebagai antarmuka bawaan browser yang dapat diakses melalui JavaScript.
- Menguasai Fetch API untuk komunikasi data dengan server.
- Memanfaatkan Web Storage API untuk menyimpan data di browser.
- Menggunakan Geolocation API untuk mengakses posisi pengguna.
- Mengenal History API untuk mengelola navigasi halaman.
- Mengenal API-API browser lainnya yang umum digunakan.

---

## Materi Utama

**Web API** adalah sekumpulan antarmuka yang disediakan oleh browser kepada JavaScript, memungkinkan kode kita berinteraksi dengan fitur-fitur browser maupun server eksternal. Sebagian besar fitur canggih dalam aplikasi web modern — menyimpan data offline, mengetahui lokasi pengguna, hingga berkomunikasi dengan server — semuanya berjalan melalui Web API.

---

### 1. Fetch API — Mengambil Data dari Server

Fetch API adalah antarmuka modern untuk mengirim permintaan jaringan ke server. Karena melibatkan komunikasi melalui internet, Fetch bersifat asinkron dan mengembalikan Promise.

**Mengambil data (GET request):**

```javascript
async function ambilArtikel(id) {
  try {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts/${id}`,
    );

    if (!response.ok) {
      throw new Error("Permintaan gagal. Status: " + response.status);
    }

    const artikel = await response.json();
    console.log(artikel.title);
  } catch (error) {
    console.log("Error:", error.message);
  }
}

ambilArtikel(1);
```

**Mengirim data (POST request):**

```javascript
async function kirimPostingan(data) {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(data),
    });

    const hasil = await response.json();
    console.log("ID baru:", hasil.id);
  } catch (error) {
    console.log("Gagal:", error.message);
  }
}

kirimPostingan({ title: "Judul Baru", body: "Isi artikel", userId: 1 });
```

**Menampilkan data ke DOM:**

```html
<!-- HTML -->
<ul id="daftar-pengguna"></ul>
```

```javascript
async function tampilkanPengguna() {
  const daftar = document.getElementById("daftar-pengguna");
  daftar.textContent = "Memuat data...";

  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");
    if (!response.ok) throw new Error("Gagal memuat.");
    const pengguna = await response.json();

    daftar.innerHTML = "";
    pengguna.forEach((user) => {
      const item = document.createElement("li");
      item.innerHTML = `<strong>${user.name}</strong> — ${user.email}`;
      daftar.appendChild(item);
    });
  } catch (error) {
    daftar.textContent = "Error: " + error.message;
  }
}

tampilkanPengguna();
```

**Metode HTTP yang didukung:**

| Method   | Fungsi                              |
| -------- | ----------------------------------- |
| `GET`    | Mengambil data (default)            |
| `POST`   | Mengirimkan data baru               |
| `PUT`    | Memperbarui data secara keseluruhan |
| `PATCH`  | Memperbarui sebagian data           |
| `DELETE` | Menghapus data                      |

---

### 2. Web Storage API — Menyimpan Data di Browser

Web Storage API menyediakan dua mekanisme penyimpanan data di sisi browser: **localStorage** dan **sessionStorage**. Keduanya menyimpan data dalam format teks (String).

|                 | `localStorage`                         | `sessionStorage`                 |
| --------------- | -------------------------------------- | -------------------------------- |
| Masa simpan     | Permanen (sampai dihapus manual)       | Hanya selama tab/browser terbuka |
| Kapasitas       | ~5–10 MB                               | ~5 MB                            |
| Cakupan         | Semua tab dalam domain yang sama       | Hanya tab saat ini               |
| Penggunaan umum | Preferensi pengguna, tema, token login | Data sementara per sesi          |

**Method yang tersedia:**

```javascript
// Menyimpan data
localStorage.setItem("kunci", "nilai");

// Membaca data
const nilai = localStorage.getItem("kunci");

// Menghapus satu item
localStorage.removeItem("kunci");

// Menghapus semua item
localStorage.clear();

// Cek jumlah item tersimpan
console.log(localStorage.length);
```

**Menyimpan Object (wajib dikonversi ke JSON String):**

```javascript
const pengaturan = {
  tema: "gelap",
  bahasa: "id",
  notif: true,
};

// Simpan
localStorage.setItem("pengaturan", JSON.stringify(pengaturan));

// Baca kembali
const tersimpan = localStorage.getItem("pengaturan");
const data = JSON.parse(tersimpan);
console.log(data.tema); // Output: "gelap"
```

**Contoh lengkap — Menyimpan preferensi tema:**

```javascript
function simpanTema(tema) {
  localStorage.setItem("tema", tema);
  terapkanTema(tema);
}

function terapkanTema(tema) {
  document.body.classList.toggle("mode-gelap", tema === "gelap");
}

function muatTema() {
  const temaTersimpan = localStorage.getItem("tema") || "terang";
  terapkanTema(temaTersimpan);
}

// Saat halaman pertama kali dimuat
muatTema();

// Saat pengguna mengganti tema
document.getElementById("tombol-tema").addEventListener("click", () => {
  const temaSaat ini = localStorage.getItem("tema") || "terang";
  simpanTema(temaSekarang === "terang" ? "gelap" : "terang");
});
```

**sessionStorage** digunakan dengan cara yang sama, cukup ganti `localStorage` dengan `sessionStorage`:

```javascript
// Simpan data sementara selama sesi berlangsung
sessionStorage.setItem("langkahFormulir", "2");
const langkah = sessionStorage.getItem("langkahFormulir");
```

---

### 3. Geolocation API — Mengakses Lokasi Pengguna

Geolocation API memungkinkan aplikasi web mengakses informasi posisi geografis perangkat pengguna (koordinat lintang dan bujur). Browser akan meminta izin kepada pengguna sebelum informasi ini dapat diakses.

**Mendapatkan posisi sekali:**

```javascript
function dapatkanLokasi() {
  if (!navigator.geolocation) {
    console.log("Geolocation tidak didukung browser ini.");
    return;
  }

  navigator.geolocation.getCurrentPosition(
    function (posisi) {
      // Berhasil mendapatkan lokasi
      const lat = posisi.coords.latitude;
      const lng = posisi.coords.longitude;
      const akur = posisi.coords.accuracy;

      console.log("Lintang :", lat);
      console.log("Bujur   :", lng);
      console.log("Akurasi :", akur, "meter");
    },
    function (error) {
      // Gagal (izin ditolak, timeout, dll.)
      console.log("Gagal mendapatkan lokasi:", error.message);
    },
    {
      enableHighAccuracy: true, // Gunakan GPS jika tersedia
      timeout: 5000, // Batas waktu 5 detik
      maximumAge: 0, // Jangan gunakan cache lokasi
    },
  );
}

dapatkanLokasi();
```

**Memantau pergerakan secara real-time:**

```javascript
const idPemantau = navigator.geolocation.watchPosition(
  function (posisi) {
    console.log(
      "Posisi diperbarui:",
      posisi.coords.latitude,
      posisi.coords.longitude,
    );
  },
  function (error) {
    console.log("Error:", error.message);
  },
);

// Menghentikan pemantauan
navigator.geolocation.clearWatch(idPemantau);
```

**Contoh — Menampilkan lokasi di halaman:**

```html
<!-- HTML -->
<button id="tombol-lokasi">Dapatkan Lokasi Saya</button>
<p id="hasil-lokasi"></p>
```

```javascript
document.getElementById("tombol-lokasi").addEventListener("click", () => {
  const hasil = document.getElementById("hasil-lokasi");
  hasil.textContent = "Mendeteksi lokasi...";

  navigator.geolocation.getCurrentPosition(
    (posisi) => {
      const lat = posisi.coords.latitude.toFixed(6);
      const lng = posisi.coords.longitude.toFixed(6);
      hasil.textContent = `Lokasi Anda: ${lat}, ${lng}`;

      // Buka Google Maps dengan koordinat tersebut
      const urlMaps = `https://www.google.com/maps?q=${lat},${lng}`;
      hasil.innerHTML += ` <a href="${urlMaps}" target="_blank">Lihat di Maps</a>`;
    },
    (error) => {
      hasil.textContent = "Izin lokasi ditolak atau terjadi kesalahan.";
    },
  );
});
```

---

### 4. History API — Mengelola Navigasi Halaman

History API memungkinkan JavaScript memanipulasi riwayat navigasi browser — menambahkan entri baru, mengubah URL yang tampil di address bar, atau merespons tombol _Back_ dan _Forward_ tanpa perlu memuat ulang halaman. Inilah yang memungkinkan Single Page Application (SPA) bekerja.

**Method utama History API:**

```javascript
// Menambahkan entri baru ke riwayat (URL berubah tanpa reload)
history.pushState({ halaman: "profil" }, "Profil", "/profil");

// Mengganti entri saat ini (tanpa menambah entri baru)
history.replaceState({ halaman: "beranda" }, "Beranda", "/");

// Navigasi mundur (sama seperti tombol Back)
history.back();

// Navigasi maju (sama seperti tombol Forward)
history.forward();

// Navigasi ke entri tertentu (negatif = mundur, positif = maju)
history.go(-2); // Mundur 2 langkah
history.go(1); // Maju 1 langkah
```

**Mendeteksi navigasi dengan `popstate`:**

Event `popstate` dilepaskan saat pengguna menekan tombol Back atau Forward browser.

```javascript
window.addEventListener("popstate", function (event) {
  console.log("Navigasi ke:", event.state);
  // Render halaman sesuai event.state
  renderHalaman(event.state);
});

function renderHalaman(state) {
  const konten = document.getElementById("konten");
  if (state && state.halaman === "profil") {
    konten.innerHTML = "<h1>Halaman Profil</h1>";
  } else {
    konten.innerHTML = "<h1>Halaman Beranda</h1>";
  }
}
```

**Contoh — Navigasi SPA sederhana:**

```html
<!-- HTML -->
<nav>
  <a class="nav-link" href="#" data-halaman="beranda">Beranda</a>
  <a class="nav-link" href="#" data-halaman="produk">Produk</a>
  <a class="nav-link" href="#" data-halaman="kontak">Kontak</a>
</nav>
<main id="konten"></main>
```

```javascript
const halaman = {
  beranda: "<h1>Beranda</h1><p>Selamat datang!</p>",
  produk: "<h1>Produk</h1><p>Daftar produk kami.</p>",
  kontak: "<h1>Kontak</h1><p>Hubungi kami di sini.</p>",
};

function navigasiKe(namaHalaman) {
  document.getElementById("konten").innerHTML = halaman[namaHalaman];
  history.pushState({ halaman: namaHalaman }, namaHalaman, "/" + namaHalaman);
}

document.querySelectorAll(".nav-link").forEach((link) => {
  link.addEventListener("click", (e) => {
    e.preventDefault();
    navigasiKe(e.target.dataset.halaman);
  });
});

window.addEventListener("popstate", (e) => {
  const namaHalaman = e.state ? e.state.halaman : "beranda";
  document.getElementById("konten").innerHTML = halaman[namaHalaman];
});

// Muat halaman awal
navigasiKe("beranda");
```

---

### 5. Clipboard API — Menyalin dan Menempel Teks

Clipboard API memungkinkan JavaScript membaca dan menulis konten clipboard pengguna secara terprogram.

```javascript
// Menyalin teks ke clipboard
async function salinTeks(teks) {
  try {
    await navigator.clipboard.writeText(teks);
    console.log("Teks berhasil disalin.");
  } catch (error) {
    console.log("Gagal menyalin:", error.message);
  }
}

// Membaca teks dari clipboard
async function bacaClipboard() {
  try {
    const teks = await navigator.clipboard.readText();
    console.log("Isi clipboard:", teks);
  } catch (error) {
    console.log("Akses clipboard ditolak:", error.message);
  }
}
```

**Contoh — Tombol "Salin Kode":**

```html
<!-- HTML -->
<code id="kode-contoh">npm install react</code>
<button id="tombol-salin">Salin</button>
```

```javascript
document.getElementById("tombol-salin").addEventListener("click", async () => {
  const teks = document.getElementById("kode-contoh").textContent;
  const tombol = document.getElementById("tombol-salin");

  await navigator.clipboard.writeText(teks);
  tombol.textContent = "Tersalin!";
  setTimeout(() => {
    tombol.textContent = "Salin";
  }, 2000);
});
```

---

### 6. Intersection Observer API — Mendeteksi Visibilitas Elemen

Intersection Observer API memberitahu JavaScript ketika sebuah elemen masuk atau keluar dari area tampilan (viewport). Sangat berguna untuk fitur _lazy loading_ gambar atau animasi saat elemen terlihat.

```javascript
const pengamat = new IntersectionObserver(
  function (entries) {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        // Elemen sedang terlihat di layar
        entry.target.classList.add("terlihat");
      }
    });
  },
  {
    threshold: 0.1, // Trigger saat 10% elemen terlihat
  },
);

// Pantau semua elemen dengan class "animasi-masuk"
document.querySelectorAll(".animasi-masuk").forEach((el) => {
  pengamat.observe(el);
});
```

---

### Kesimpulan

Browser menyediakan berbagai Web API yang sangat powerful, memungkinkan JavaScript berinteraksi dengan hampir semua aspek browser dan perangkat pengguna. Pemahaman Web API adalah yang membedakan pengembang yang hanya bisa membuat halaman statis dari yang mampu membangun aplikasi web yang sungguh-sungguh dinamis dan interaktif.

**Ringkasan Web API yang Dipelajari:**

| API                           | Fungsi Utama                                                 |
| ----------------------------- | ------------------------------------------------------------ |
| **Fetch API**                 | Komunikasi data dengan server (GET, POST, dll.)              |
| **Web Storage API**           | Menyimpan data di browser (`localStorage`, `sessionStorage`) |
| **Geolocation API**           | Mengakses koordinat lokasi geografis pengguna                |
| **History API**               | Mengelola navigasi URL tanpa reload halaman                  |
| **Clipboard API**             | Membaca dan menulis konten clipboard                         |
| **Intersection Observer API** | Mendeteksi visibilitas elemen di viewport                    |
