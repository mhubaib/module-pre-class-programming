# Bab 64: Pengenalan & Setup GitHub

## Tujuan Pembelajaran

- Memahami fungsi GitHub sebagai platform kolaborasi kode berbasis cloud.
- Mampu membuat akun GitHub dan mengenal antarmuka dasarnya.
- Mampu menghubungkan Git lokal di komputer dengan akun GitHub.

---

## Materi Utama

Jika Git (Bab 60) adalah alat untuk mencatat versi kode di komputermu sendiri, maka **GitHub** adalah platform berbasis web tempat kode tersebut disimpan secara online, dibagikan, dan dikerjakan bersama. Di sinilah jutaan pengembang di seluruh dunia menyimpan proyek, berkolaborasi, dan memamerkan hasil pekerjaan mereka.

---

### 1. Mengapa Kita Butuh GitHub?

Git yang sudah kita pelajari di bab-bab sebelumnya bekerja sepenuhnya secara lokal — seluruh riwayat tersimpan di dalam folder `.git` di komputermu. Ini berarti jika komputermu rusak atau hilang, seluruh riwayat proyek ikut hilang.

GitHub menyelesaikan masalah ini sekaligus membuka kemampuan tambahan:

- **Cadangan Online**: Kode dan seluruh riwayat commitmu tersimpan di server GitHub, aman dari kerusakan perangkat keras.
- **Portofolio**: Akun GitHub yang aktif dengan proyek-proyek yang rapi adalah salah satu hal pertama yang dilihat oleh rekruter dan perusahaan teknologi saat menilai calon pengembang.
- **Kolaborasi Tim**: Beberapa pengembang dapat bekerja pada proyek yang sama secara bersamaan — masing-masing dari komputernya sendiri — dan menggabungkan hasilnya dengan terstruktur.
- **Open Source**: Kamu dapat melihat, mempelajari, dan berkontribusi pada proyek-proyek nyata yang digunakan oleh jutaan orang di seluruh dunia.

---

### 2. Membuat Akun GitHub

Langkah-langkah membuat akun:

1. Buka [github.com](https://github.com/) di browser.
2. Klik tombol **Sign up** dan ikuti proses pendaftaran menggunakan alamat email aktif.
3. Pilih username yang profesional — ini akan menjadi bagian dari URL profilmu (contoh: `github.com/budisantoso`).
4. Selesaikan verifikasi dan konfirmasi email.

> **Catatan:** Gunakan alamat email yang sama dengan yang sudah kamu daftarkan di konfigurasi Git lokal (`git config --global user.email`) agar riwayat commit terhubung dengan benar ke akunmu.

---

### 3. Mengenal Antarmuka GitHub

Setelah masuk ke akun GitHub, terdapat beberapa elemen antarmuka yang penting untuk dipahami:

| Elemen | Lokasi | Fungsi |
|---|---|---|
| **Dashboard** | Halaman utama setelah login | Menampilkan aktivitas terbaru dan repositori yang kamu ikuti |
| **Profile** | Klik foto profil → Your profile | Halaman publik yang menampilkan proyekmu kepada orang lain |
| **Repositories** | Tab di halaman profil | Daftar seluruh repositori milikmu |
| **New (+ ikon)** | Pojok kanan atas | Tombol untuk membuat repositori baru |
| **Explore** | Menu atas | Temukan proyek dan pengembang lain di GitHub |

---

### 4. Mengenal Repository

**Repository** (sering disingkat *repo*) adalah tempat penyimpanan proyek di GitHub. Sebuah repositori berisi seluruh file proyek beserta riwayat perubahannya — sama seperti folder proyek di komputermu, namun tersimpan di server GitHub dan dapat diakses dari mana saja.

Setiap repositori memiliki beberapa informasi utama:

| Informasi | Penjelasan |
|---|---|
| **Nama** | Identitas repositori, misalnya `belajar-frontend` |
| **Visibilitas** | **Public** (dapat dilihat siapa saja) atau **Private** (hanya kamu dan kolaborator) |
| **Branch utama** | Branch `main` yang menjadi versi resmi proyek |
| **README** | File `README.md` yang menjelaskan isi dan tujuan proyek |
| **Commits** | Riwayat seluruh perubahan yang pernah dilakukan |

---

### 5. Membuat Repository Pertama

1. Klik tombol **New** (ikon `+`) di pojok kanan atas halaman GitHub.
2. Isi formulir pembuatan repositori:
   - **Repository name**: `belajar-frontend`
   - **Description** *(opsional)*: Deskripsi singkat tentang proyekmu
   - **Visibility**: Pilih **Public** agar dapat dilihat oleh siapa saja
   - **Initialize this repository**: Untuk saat ini, **jangan dicentang** — kita akan menghubungkan repositori ini dengan folder lokal yang sudah ada.
3. Klik **Create repository**.

Setelah repositori dibuat, GitHub akan menampilkan halaman instruksi berisi perintah-perintah yang perlu dijalankan di terminal untuk menghubungkan folder lokal ke repositori tersebut. Kita akan menggunakannya di langkah berikutnya.

---

### 6. Menghubungkan Git Lokal ke GitHub

Untuk dapat mengirim kode dari komputermu ke GitHub, terdapat dua hal yang perlu disiapkan: identitas Git dan metode autentikasi.

#### A. Verifikasi Konfigurasi Identitas

Pastikan identitas Git lokalmu sudah dikonfigurasi dengan email yang sama dengan akun GitHub:

```bash
git config --global user.name "Nama Lengkapmu"
git config --global user.email "email-github@kamu.com"

# Verifikasi
git config --list
# Output:
# user.name=Nama Lengkapmu
# user.email=email-github@kamu.com
```

#### B. Autentikasi ke GitHub

GitHub tidak lagi mengizinkan penggunaan kata sandi untuk operasi melalui terminal. Terdapat dua metode autentikasi yang didukung:

**Metode 1 — Personal Access Token (PAT):** Token yang dibuat di pengaturan akun GitHub, digunakan sebagai pengganti kata sandi saat terminal memintanya. Cocok untuk pemula.

Langkah membuat PAT:
1. Masuk ke GitHub → klik foto profil → **Settings**.
2. Gulir ke bawah → klik **Developer settings** → **Personal access tokens** → **Tokens (classic)**.
3. Klik **Generate new token**, beri nama, dan centang izin **repo**.
4. Salin token yang dihasilkan dan simpan di tempat yang aman — token ini hanya ditampilkan sekali.

**Metode 2 — SSH Key:** Metode yang lebih aman dan nyaman untuk penggunaan jangka panjang karena tidak memerlukan input token setiap saat. Direkomendasikan setelah kamu mulai bekerja secara rutin dengan GitHub.

> **Untuk pemula:** Metode termudah adalah menggunakan **GitHub Desktop** — aplikasi resmi GitHub yang menangani seluruh proses autentikasi secara otomatis melalui antarmuka grafis. Kamu dapat mengunduhnya di [desktop.github.com](https://desktop.github.com/).

---

### 7. Menghubungkan Folder Lokal ke Repository GitHub

Setelah repositori dibuat di GitHub dan autentikasi siap, berikut cara menghubungkan folder proyek lokalmu:

```bash
# 1. Pastikan kamu berada di dalam folder proyek yang sudah diinisialisasi Git
cd ~/Dokumen/belajar-frontend
git status
# On branch main

# 2. Tambahkan URL repositori GitHub sebagai "remote" bernama "origin"
git remote add origin https://github.com/username-kamu/belajar-frontend.git

# 3. Verifikasi bahwa remote sudah terdaftar
git remote -v
# Output:
# origin  https://github.com/username-kamu/belajar-frontend.git (fetch)
# origin  https://github.com/username-kamu/belajar-frontend.git (push)

# 4. Kirim seluruh commit lokal ke GitHub (akan dibahas lebih lanjut di Bab 65)
git push -u origin main
```

> **Catatan:** Perintah `git push` untuk mengirim kode ke GitHub akan dibahas secara lengkap di Bab 65. Langkah di atas cukup untuk memahami bahwa `git remote add` adalah cara Git "mengenal" alamat repositori di GitHub.

---

### Kesimpulan

GitHub adalah komponen yang melengkapi Git — jika Git mencatat seluruh riwayat perubahan secara lokal, GitHub menyimpannya secara online sekaligus membuka kemampuan kolaborasi, backup, dan berbagi karya kepada dunia. Memiliki akun GitHub yang aktif dengan proyek-proyek yang terdokumentasi dengan baik adalah salah satu aset terpenting sebagai seorang pengembang web.

Di bab berikutnya, kita akan mempraktikkan cara mengirimkan kode dari komputer lokal ke repositori GitHub menggunakan `git push`, serta cara mengambil pembaruan terbaru dari GitHub ke komputer lokal menggunakan `git pull`.

**Ringkasan:**

| Konsep / Perintah | Penjelasan |
|---|---|
| Repository (Repo) | Folder proyek yang tersimpan di GitHub beserta seluruh riwayat commitnya |
| Public / Private | Visibilitas repositori — dapat diakses publik atau hanya oleh pemilik |
| `git remote add origin URL` | Mendaftarkan alamat repositori GitHub ke proyek Git lokal |
| `git remote -v` | Menampilkan daftar remote yang terdaftar |
| PAT | Personal Access Token — pengganti kata sandi untuk autentikasi ke GitHub via terminal |
| SSH Key | Metode autentikasi yang lebih aman untuk penggunaan jangka panjang |
