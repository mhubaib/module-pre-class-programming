# Bab 64: Pengenalan & Setup Github

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Memahami fungsi GitHub sebagai platform kolaborasi kode berbasis awan (Cloud).
- Mampu membuat akun GitHub dan mengenal antarmuka dasarnya.
- Mampu menghubungkan Git lokal di komputer dengan akun GitHub.

## 📚 Materi Utama

Jika Git (Bab 60) adalah alat untuk mencatat versi di laptopmu sendiri, maka **GitHub** adalah "Rumah Sosmed" bagi kodemu. Di sinilah seluruh programmer di dunia memamerkan, menyimpan, dan bekerja sama membangun aplikasi raksasa.

### 1. Mengapa Kita Butuh GitHub?

- **Cadangan Aman**: Jika laptopmu hilang atau rusak, kodemu tetap aman tersimpan di server GitHub.
- **Portofolio**: Kamu bisa memamerkan hasil belajarmu kepada calon pemberi kerja atau HRD.
- **Kolaborasi**: Kamu bisa menarik kode temanmu, memperbaikinya, dan mengirimkannya kembali dengan sangat rapi.

### 2. Membuat Akun & Mengenal Repository

Langkah pertama:
1. Buka [github.com](https://github.com/).
2. Daftar menggunakan email aktifmu.
3. Setelah masuk, kamu akan mengenal istilah **Repository** (sering disebut *Repo*). Repo adalah "Folder Proyek" yang ada di GitHub.

### 3. Menghubungkan Git Lokal ke GitHub

Agar laptopmu bisa mengirim kode ke GitHub, kamu perlu memperkenalkan diri melalui Terminal (Git Bash).

**A. Mengatur Nama & Email**
```bash
git config --global user.name "Nama Lengkapmu"
git config --global user.email "email-github@kamu.com"
```

**B. Pengenalan Authentication**
Dulu kita menggunakan password, tapi sekarang GitHub mewajibkan penggunaan **Token (PAT)** atau **SSH Key**. 
- Untuk pemula, cara termudah adalah menggunakan **GitHub Desktop** atau mengikuti petunjuk *login* otomatis yang muncul di terminal saat pertama kali kamu melakukan "Push".

### 4. Membuat Repository Pertama

1. Klik tombol **New** (ikon +) di pojok kanan atas GitHub.
2. Beri nama: `belajar-frontend`.
3. Pilih **Public** agar bisa dilihat orang lain.
4. Klik **Create repository**.

Selamat! Kamu sekarang punya "kavling" tanah digital di internet untuk menyimpan kodemu. Di bab selanjutnya, kita akan belajar cara "mengirimkan" file dari laptopmu ke kavling tersebut.

## 💻 Latihan Praktik

[Soal atau project latihan terkait materi di atas akan ditambahkan di sini]
