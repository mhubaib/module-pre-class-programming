# Bab 62: Git History Commit

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Mampu melihat daftar riwayat perubahan menggunakan `git log`.
- Memahami cara membaca informasi *Commit Hash*, Penulis, dan Tanggal.
- Mengenal cara menampilkan log yang lebih ringkas dan mudah dibaca.

## 📚 Materi Utama

Keunggulan utama Git adalah kemampuannya untuk menoleh ke belakang. Jika kamu lupa apa saja yang sudah kamu kerjakan kemarin, atau siapa yang merusak sebuah fungsi di kode, Git punya catatannya.

### 1. Melihat Riwayat (`git log`)

Ketikkan `git log` di terminal. Kamu akan melihat daftar panjang berisi:
- **Commit Hash**: Kode unik (seperti KTP) untuk setiap versi, misalnya `a1b2c3d...`.
- **Author**: Nama dan email orang yang melakukan perubahan.
- **Date**: Kapan perubahan itu dibuat.
- **Commit Message**: Pesan penjelasan yang kamu tulis saat melakukan commit.

### 2. Log yang Lebih Rapi

Jika proyekmu sudah memiliki ratusan commit, `git log` biasa akan terasa sangat sesak dan sulit dibaca. Untuk itu, programmer sering menggunakan "jalan pintas" agar log terlihat hanya satu baris per versi:

```bash
git log --oneline
```
Perintah ini akan menampilkan daftar versi yang sangat ringkas, hanya berisi 7 digit pertama *hash* dan pesan commit-nya saja. Sangat rapi!

### 3. Mencari Tahu Siapa Pelakunya (`git blame`)

Pernahkah kamu menemukan baris kode yang *error* dan ingin tahu siapa yang mengetiknya?
```bash
git blame nama-file.html
```
Git akan menampilkan setiap baris di file tersebut lengkap dengan nama orang yang terakhir kali mengubah baris itu. (Gunakan ini untuk belajar atau diskusi, bukan untuk menyalahkan teman ya! 😄)

### 4. Membandingkan Perubahan (`git diff`)

Sebelum kamu melakukan `git add`, kamu bisa melihat perbedaan antara kode yang sekarang dengan versi sebelumnya:
```bash
git diff
```
Baris yang kamu tambahkan akan berwarna **hijau (+)** dan baris yang kamu hapus/ubah akan berwarna **merah (-)**.

Dengan menguasai cara melihat riwayat ini, kamu tidak akan pernah merasa "tersesat" saat mengerjakan proyek besar. Kamu selalu tahu apa yang terjadi di masa lalu.