# Bab 60: Pengenalan VCS (Git) & Instalasi

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Memahami kegunaan Version Control System (VCS) dalam pengelolaan proyek.
- Mengenal Git sebagai alat pengelola versi yang paling populer.
- Mampu melakukan instalasi Git di Windows secara benar.
- Membedakan antara Git (alat lokal) dan GitHub (layanan online).

## 📚 Materi Utama

Pernahkah kamu menyimpan file tugas dengan nama `tugas_v1.doc`, `tugas_revisi.doc`, hingga `tugas_REVISI_FINAL_FIX.doc`? Cara manual ini sangat membingungkan. Dalam programming, kita menggunakan program cerdas yang disebut **Version Control System (VCS)**.

### 1. Apa itu Git?

**Git** adalah sistem *Version Control* yang membantu kita:
- **Mencatat Riwayat**: Git mencatat setiap perubahan yang kita buat (siapa, kapan, dan apa yang diubah).
- **Mesin Waktu**: Jika suatu hari kodemu mendadak *error*, kamu bisa mengembalikan file tersebut ke versi sebelumnya saat masih berjalan lancar.
- **Kerja Kolaborasi**: Tim yang besar bisa mengerjakan file yang sama tanpa takut saling menimpa data orang lain.

### 2. Git vs GitHub: Apa Bedanya?

Sering kali pemula menyangka keduanya sama, padahal berbeda:
- **Git** adalah **Kameranya**: Alat di komputermu sendiri untuk mengambil "foto" (mencatat versi) dari kodemu.
- **GitHub** adalah **Instagramnya**: Layanan di internet tempat kamu meng-*upload* kodemu agar bisa dilihat dan dikerjakan bersama tim lain.

### 3. Instalasi Git di Windows

Ikuti langkah praktis ini:
1. Unduh penginstal di situs resmi [git-scm.com](https://git-scm.com/).
2. Jalankan file `.exe`-nya.
3. Klik **Next** terus-menerus (gunakan pengaturan default).
4. Selesaikan sampai **Finish**.

**Cara Cek Keberhasilan:**
1. Klik kanan di folder mana saja, pilih **"Git Bash Here"**.
2. Ketikkan: `git --version`
3. Jika muncul angka versinya, berarti Git sudah terpasang dengan benar di laptopmu.
