# Bab 4: Git Flow (Inisialisasi, Staging, Commit)

## Tujuan Pembelajaran

- Mampu mengaktifkan Git pada sebuah folder proyek menggunakan `git init`.
- Memahami konsep _Three States_ dalam Git (Working Directory, Staging Area, Repository).
- Mampu mencatat perubahan kode menggunakan perintah `git add` dan `git commit`.

---

## Materi Utama

Setelah berhasil memasang dan mengonfigurasi Git di Bab 3 yang lalu, sekarang kita akan masuk ke inti dari cara kerja Git sehari-hari. Menggunakan Git itu seperti mendokumentasikan proses pembangunan sebuah gedung: ada saatnya kamu meletakkan batu bata, dan ada saatnya kamu mengambil foto untuk mencatat kemajuan yang sudah dicapai.

---

### 1. Memulai Proyek Baru (`git init`)

Secara default, Git tidak mengawasi semua folder di komputermu. Kamu perlu secara eksplisit mengaktifkan Git pada folder proyek yang ingin dilacak perubahannya. Proses ini disebut **inisialisasi**.

```bash
# 1. Masuk ke folder proyek
cd ~/Dokumen/proyek-portfolio

# 2. Aktifkan Git di folder tersebut
git init
# Output:
# Initialized empty Git repository in /c/Users/NamaPengguna/Dokumen/proyek-portfolio/.git/
```

Setelah perintah ini dijalankan, Git akan membuat folder tersembunyi bernama `.git` di dalam direktori proyekmu. Folder inilah yang menjadi "otak" Git — tempat seluruh riwayat perubahan disimpan. Kamu tidak perlu membuka atau mengubah isi folder `.git` ini secara manual.

Untuk memverifikasi bahwa folder `.git` berhasil dibuat:

```bash
ls -a
# Output: .  ..  .git  index.html  css  js
```

> **Catatan:** Perintah `git init` hanya perlu dijalankan **satu kali** di awal pembuatan proyek. Setelah itu, Git akan terus mengawasi seluruh perubahan dalam folder tersebut secara otomatis.

---

### 2. Alur Kerja Tiga Tahapan (The Three States)

Git tidak mencatat perubahan secara otomatis setiap kali kamu mengetik. Setiap perubahan harus melewati tiga tahapan resmi sebelum benar-benar tersimpan dalam riwayat Git.

| Tahapan | Nama                   | Deskripsi                                                                                                             |
| ------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------- |
| 1       | **Working Directory**  | Area tempat kamu menulis dan mengubah kode. File di sini berstatus _Untracked_ (baru) atau _Modified_ (sudah diubah). |
| 2       | **Staging Area**       | Area tunggu. Tempat mengumpulkan file-file yang sudah siap untuk dicatat dalam versi berikutnya.                      |
| 3       | **Repository (Local)** | Tempat penyimpanan permanen. Setiap versi yang sudah di-_commit_ akan tersimpan di sini beserta seluruh riwayatnya.   |

**Analogi Belanja Online:**

1. **Working Directory** — Kamu memilih dan memasukkan produk ke keranjang belanja (menulis kode).
2. **Staging Area** — Kamu membawa keranjang ke meja kasir dan memilih produk mana yang akan dibayar (menentukan perubahan mana yang akan dicatat).
3. **Repository** — Kasir mencetak struk sebagai bukti transaksi resmi (perubahan tersimpan permanen dalam riwayat Git).

**Visualisasi alur:**

```
[ Working Directory ] --git add--> [ Staging Area ] --git commit--> [ Repository ]
     (kamu menulis)                  (siap dicatat)                  (tersimpan)
```

---

### 3. Mencatat Perubahan (Add & Commit)

Berikut adalah alur kerja lengkap yang akan kamu gunakan setiap kali ingin menyimpan kemajuan proyekmu.

#### Langkah 1 — Cek Status (`git status`)

Sebelum melakukan apa pun, gunakan `git status` untuk melihat kondisi terkini proyekmu: file mana yang baru ditambahkan, mana yang sudah diubah, dan mana yang sudah masuk ke Staging Area.

```bash
git status
# Output (contoh saat ada file baru yang belum dicatat):
#
# On branch main
#
# No commits yet
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#         index.html
#         css/style.css
#
# nothing added to commit but untracked files present
```

Istilah warna dan status yang umum muncul:

| Status      | Artinya                                               |
| ----------- | ----------------------------------------------------- |
| `Untracked` | File baru yang belum pernah dikenal oleh Git          |
| `Modified`  | File yang sudah dikenal Git dan baru saja diubah      |
| `Staged`    | File yang sudah masuk ke Staging Area, siap di-commit |

#### Langkah 2 — Masukkan ke Staging Area (`git add`)

Pilih file mana yang ingin kamu sertakan dalam versi yang akan dicatat.

```bash
# Memasukkan satu file tertentu
git add index.html

# Memasukkan beberapa file sekaligus
git add index.html css/style.css

# Memasukkan semua file yang berubah sekaligus
git add .
```

Setelah `git add`, jalankan `git status` lagi untuk memverifikasi bahwa file sudah masuk ke Staging Area:

```bash
git status
# Output:
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#         new file:   index.html
#         new file:   css/style.css
```

File yang berwarna hijau dan bertanda `new file` atau `modified` berarti sudah siap untuk di-commit.

#### Langkah 3 — Simpan Versi (`git commit`)

`git commit` adalah langkah akhir yang menyimpan semua file dari Staging Area ke dalam Repository secara permanen. Setiap commit **wajib disertai pesan** yang menjelaskan perubahan apa yang dilakukan.

```bash
git commit -m "Menambahkan halaman utama dan file CSS dasar"
# Output:
# [main (root-commit) a3f2c1d] Menambahkan halaman utama dan file CSS dasar
#  2 files changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 css/style.css
#  create mode 100644 index.html
```

**Panduan menulis pesan commit yang baik:**

| Kurang Baik              | Lebih Baik                                                         |
| ------------------------ | ------------------------------------------------------------------ |
| `git commit -m "update"` | `git commit -m "Memperbarui warna tombol pada halaman login"`      |
| `git commit -m "fix"`    | `git commit -m "Memperbaiki layout yang rusak di tampilan mobile"` |
| `git commit -m "asdfgh"` | `git commit -m "Menambahkan validasi form kontak"`                 |

> **Catatan:** Pesan commit yang jelas sangat penting ketika bekerja dalam tim. Anggota tim lain (atau dirimu sendiri di masa mendatang) harus bisa memahami apa yang diubah hanya dari membaca pesan commit tersebut, tanpa perlu melihat kodenya.

---

### 4. Melihat Riwayat Commit (`git log`)

Setelah beberapa kali melakukan commit, kamu dapat melihat seluruh riwayat perubahan menggunakan perintah `git log`.

```bash
git log
# Output:
# commit d4e5f6a7b8c9... (HEAD -> main)
# Author: Budi Santoso <budi@gmail.com>
# Date:   Thu Jun 4 10:30:00 2026 +0700
#
#     Menambahkan navigasi dan footer
#
# commit a3f2c1d2e3f4...
# Author: Budi Santoso <budi@gmail.com>
# Date:   Thu Jun 4 09:15:00 2026 +0700
#
#     Menambahkan halaman utama dan file CSS dasar
```

Untuk tampilan yang lebih ringkas, gunakan opsi `--oneline`:

```bash
git log --oneline
# Output:
# d4e5f6a (HEAD -> main) Menambahkan navigasi dan footer
# a3f2c1d Menambahkan halaman utama dan file CSS dasar
```

---

### 5. Simulasi Sesi Kerja Lengkap

Berikut adalah simulasi sesi kerja Git dari awal hingga tiga commit pertama:

```bash
# --- Persiapan Proyek ---
cd ~/Dokumen
mkdir proyek-portfolio
cd proyek-portfolio
git init
# Output: Initialized empty Git repository in .../proyek-portfolio/.git/

# --- Commit Pertama: Struktur awal ---
touch index.html
mkdir css js
touch css/style.css js/script.js

git status
# index.html, css/style.css, js/script.js → Untracked

git add .
git commit -m "Inisialisasi proyek: menambahkan struktur folder awal"

# --- Commit Kedua: Menambahkan konten ---
# (misalnya kamu mengisi index.html dengan kode HTML dasar)

git status
# index.html → Modified

git add index.html
git commit -m "Menambahkan struktur HTML dasar pada halaman utama"

# --- Commit Ketiga: Menambahkan gaya ---
# (misalnya kamu mengisi style.css)

git add css/style.css
git commit -m "Menambahkan gaya dasar: warna latar dan tipografi"

# --- Melihat riwayat ---
git log --oneline
# Output:
# c7d8e9f (HEAD -> main) Menambahkan gaya dasar: warna latar dan tipografi
# b5c6d7e Menambahkan struktur HTML dasar pada halaman utama
# a3f2c1d Inisialisasi proyek: menambahkan struktur folder awal
```

---

### Kesimpulan

Alur kerja Git yang baru saja dipelajari — `git init`, `git add`, dan `git commit` — adalah siklus yang akan kamu ulangi setiap hari selama berkarier sebagai pengembang web. Memahami tiga tahapan (Working Directory → Staging Area → Repository) adalah kunci untuk menggunakan Git dengan benar dan percaya diri.

**Ringkasan Perintah:**

| Perintah                | Fungsi                                                          |
| ----------------------- | --------------------------------------------------------------- |
| `git init`              | Mengaktifkan Git pada folder proyek (dijalankan sekali di awal) |
| `git status`            | Menampilkan status terkini seluruh file dalam proyek            |
| `git add nama-file`     | Memasukkan satu file tertentu ke Staging Area                   |
| `git add .`             | Memasukkan semua perubahan ke Staging Area                      |
| `git commit -m "pesan"` | Menyimpan perubahan dari Staging Area ke Repository             |
| `git log`               | Menampilkan riwayat seluruh commit secara lengkap               |
| `git log --oneline`     | Menampilkan riwayat commit secara ringkas                       |
