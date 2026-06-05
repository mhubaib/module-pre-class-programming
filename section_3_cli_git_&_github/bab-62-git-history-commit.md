# Bab 62: Git History & Commit

## Tujuan Pembelajaran

- Mampu melihat daftar riwayat perubahan menggunakan `git log`.
- Memahami cara membaca informasi *Commit Hash*, penulis, dan tanggal.
- Mengenal cara menampilkan log yang lebih ringkas dan mudah dibaca.
- Mampu membandingkan perubahan kode menggunakan `git diff`.
- Mengenal perintah `git blame` untuk menelusuri asal-usul sebuah baris kode.

---

## Materi Utama

Salah satu keunggulan utama Git adalah kemampuannya untuk menyimpan seluruh riwayat perubahan proyek. Jika kamu lupa apa yang sudah dikerjakan kemarin, ingin mengetahui kapan sebuah bug pertama kali muncul, atau perlu melihat detail perubahan tertentu — semua informasi tersebut dapat diakses melalui perintah-perintah yang akan dibahas di modul ini.

---

### 1. Melihat Riwayat Commit (`git log`)

Perintah `git log` menampilkan seluruh riwayat commit dalam proyek, diurutkan dari yang paling baru hingga yang paling lama.

```bash
git log
# Output:
#
# commit d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3  ← Commit Hash
# Author: Budi Santoso <budi@gmail.com>             ← Identitas pembuat
# Date:   Thu Jun 4 14:22:00 2026 +0700             ← Waktu commit
#
#     Menambahkan navigasi dan footer                ← Pesan commit
#
# commit a3f2c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6a7b8
# Author: Budi Santoso <budi@gmail.com>
# Date:   Thu Jun 4 09:15:00 2026 +0700
#
#     Inisialisasi proyek: menambahkan struktur folder awal
```

Setiap entri dalam `git log` memuat empat informasi:

| Informasi | Penjelasan |
|---|---|
| **Commit Hash** | Kode unik sepanjang 40 karakter yang mengidentifikasi setiap commit, seperti nomor identitas untuk setiap versi |
| **Author** | Nama dan alamat email orang yang membuat commit tersebut |
| **Date** | Tanggal dan waktu commit dibuat, beserta zona waktunya |
| **Pesan Commit** | Keterangan yang ditulis oleh pembuat commit untuk menjelaskan perubahan yang dilakukan |

Untuk keluar dari tampilan `git log` yang panjang, tekan tombol **`q`**.

---

### 2. Tampilan Log yang Lebih Ringkas

Ketika proyek sudah memiliki banyak commit, tampilan `git log` biasa bisa terasa padat dan sulit ditelusuri. Terdapat beberapa opsi untuk menampilkan riwayat dengan cara yang lebih ringkas.

**`git log --oneline`** — Satu baris per commit:

```bash
git log --oneline
# Output:
# d4e5f6a (HEAD -> main) Menambahkan navigasi dan footer
# b5c6d7e Menambahkan gaya dasar: warna latar dan tipografi
# a3f2c1d Inisialisasi proyek: menambahkan struktur folder awal
```

Opsi `--oneline` menampilkan hanya 7 karakter pertama dari commit hash dan pesan commitnya. Ini sudah cukup untuk mengidentifikasi setiap commit karena 7 karakter pertama hampir selalu unik dalam satu proyek.

**Opsi tambahan yang berguna:**

| Perintah | Fungsi |
|---|---|
| `git log --oneline` | Satu baris per commit (hash pendek + pesan) |
| `git log --oneline -5` | Menampilkan hanya 5 commit terakhir |
| `git log --oneline --author="Budi"` | Menampilkan commit dari satu orang tertentu |
| `git log --oneline --since="2 days ago"` | Menampilkan commit dalam dua hari terakhir |
| `git log --stat` | Menampilkan daftar file yang berubah di setiap commit |

**Contoh — Menampilkan 3 commit terakhir:**

```bash
git log --oneline -3
# Output:
# d4e5f6a (HEAD -> main) Menambahkan navigasi dan footer
# b5c6d7e Menambahkan gaya dasar: warna latar dan tipografi
# a3f2c1d Inisialisasi proyek: menambahkan struktur folder awal
```

---

### 3. Membandingkan Perubahan (`git diff`)

Sebelum menjalankan `git add`, kamu bisa melihat secara detail apa saja yang berubah dalam file yang sudah dimodifikasi menggunakan `git diff`.

```bash
git diff
```

Cara membaca output `git diff`:

- Baris yang diawali tanda **`+`** (berwarna hijau) adalah baris yang **baru ditambahkan**.
- Baris yang diawali tanda **`-`** (berwarna merah) adalah baris yang **dihapus atau digantikan**.
- Baris tanpa tanda adalah baris yang tidak berubah, ditampilkan sebagai konteks.

**Contoh output:**

```bash
git diff
# Output:
#
# diff --git a/css/style.css b/css/style.css
# --- a/css/style.css     ← versi lama
# +++ b/css/style.css     ← versi baru
#
# @@ -1,5 +1,8 @@
#  body {
# -  background-color: white;     ← baris lama yang diganti
# +  background-color: #f0f2f5;   ← baris baru penggantinya
# +  font-family: sans-serif;     ← baris baru yang ditambahkan
#    margin: 0;
#    padding: 0;
#  }
```

**Variasi perintah `git diff`:**

| Perintah | Fungsi |
|---|---|
| `git diff` | Menampilkan perubahan yang belum masuk Staging Area |
| `git diff --staged` | Menampilkan perubahan yang sudah masuk Staging Area (sudah `git add`) |
| `git diff nama-file.css` | Menampilkan perubahan hanya pada satu file tertentu |

> **Kebiasaan yang baik:** Jalankan `git diff` sebelum `git add` untuk memastikan perubahan yang akan dicatat sudah sesuai dengan yang dimaksud.

---

### 4. Menelusuri Asal-Usul Baris Kode (`git blame`)

`git blame` menampilkan isi sebuah file baris per baris, disertai informasi commit hash, nama pembuat, dan waktu terakhir kali setiap baris tersebut diubah.

```bash
git blame index.html
# Output:
#
# a3f2c1d (Budi Santoso  2026-06-04 09:15:00) <!DOCTYPE html>
# a3f2c1d (Budi Santoso  2026-06-04 09:15:00) <html lang="id">
# b5c6d7e (Ani Rahayu    2026-06-04 11:30:00) <head>
# b5c6d7e (Ani Rahayu    2026-06-04 11:30:00)   <meta charset="UTF-8">
# d4e5f6a (Budi Santoso  2026-06-04 14:22:00)   <title>Portofolio</title>
```

Perintah ini berguna untuk:
- Memahami konteks sebuah perubahan — siapa yang membuatnya dan kapan.
- Menelusuri kapan sebuah bug pertama kali dimasukkan ke dalam kode.
- Memahami bagian kode yang tidak kamu tulis sendiri sebelum mengubahnya.

> **Catatan:** Gunakan `git blame` sebagai alat untuk memahami dan berdiskusi tentang kode, bukan untuk mencari kesalahan rekan tim.

---

### 5. Simulasi Sesi Penelusuran Riwayat

Berikut adalah contoh sesi lengkap menelusuri riwayat proyek menggunakan perintah-perintah yang telah dipelajari:

```bash
# Situasi: kamu kembali ke proyek setelah beberapa hari
# dan ingin mengetahui apa yang sudah terjadi

# 1. Lihat ringkasan seluruh riwayat
git log --oneline
# d4e5f6a (HEAD -> main) Memperbaiki tampilan navigasi di mobile
# c3d4e5f Menambahkan halaman tentang kami
# b5c6d7e Menambahkan gaya dasar: warna latar dan tipografi
# a3f2c1d Inisialisasi proyek: menambahkan struktur folder awal

# 2. Ingin tahu detail perubahan di commit tertentu
git log --stat
# commit d4e5f6a...
#  css/style.css | 8 +++++---
#  index.html    | 3 ++-
#  2 files changed, 8 insertions(+), 3 deletions(-)

# 3. Kamu mengubah style.css dan ingin cek apa yang berubah
#    sebelum memasukkannya ke Staging Area
git diff css/style.css
# (menampilkan perubahan spesifik pada file tersebut)

# 4. Setelah puas, masukkan ke Staging dan commit
git add css/style.css
git diff --staged    # verifikasi sekali lagi sebelum commit
git commit -m "Menyesuaikan ukuran font pada tampilan mobile"

# 5. Verifikasi commit baru sudah masuk ke riwayat
git log --oneline -3
# e5f6a7b (HEAD -> main) Menyesuaikan ukuran font pada tampilan mobile
# d4e5f6a Memperbaiki tampilan navigasi di mobile
# c3d4e5f Menambahkan halaman tentang kami
```

---

### Kesimpulan

Kemampuan menelusuri riwayat adalah salah satu fitur paling berharga dari Git. Dengan menguasai `git log`, `git diff`, dan `git blame`, kamu selalu memiliki visibilitas penuh atas apa yang terjadi dalam proyekmu — baik yang kamu kerjakan sendiri maupun bersama tim.

**Ringkasan Perintah:**

| Perintah | Fungsi |
|---|---|
| `git log` | Menampilkan seluruh riwayat commit secara lengkap |
| `git log --oneline` | Menampilkan riwayat commit secara ringkas (satu baris per commit) |
| `git log --oneline -N` | Menampilkan N commit terakhir saja |
| `git log --stat` | Menampilkan daftar file yang berubah di setiap commit |
| `git diff` | Menampilkan perubahan yang belum masuk Staging Area |
| `git diff --staged` | Menampilkan perubahan yang sudah masuk Staging Area |
| `git blame nama-file` | Menampilkan siapa yang terakhir mengubah setiap baris di sebuah file |
