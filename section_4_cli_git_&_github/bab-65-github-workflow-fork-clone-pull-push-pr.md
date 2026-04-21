# Bab 65: Github Workflow (fork, clone, pull, push, PR)

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Memahami dan mempraktikkan alur pengiriman kode dari lokal ke server (`push`).
- Mampu menyalin proyek orang lain (`fork` & `clone`).
- Memahami cara memperbarui kode lokal dari server (`pull`).
- Mengenal konsep *Pull Request* (PR) sebagai cara berkontribusi di proyek tim.

## 📚 Materi Utama

Setelah punya akun GitHub, sekarang kita akan belajar bahasa "Lalu Lintas" kode antara Laptopmu (Lokal) dan GitHub (Remote).

### 1. Mengirim Kode ke GitHub (`git push`)

Inilah saatnya memamerkan kodemu!
1. Hubungkan folder lokatmu ke alamat Repo GitHub:
   ```bash
   git remote add origin https://github.com/username-mu/nama-repo.git
   ```
2. Kirim (Pukul keatas) hasil *commit*-mu:
   ```bash
   git push -u origin main
   ```
*Sekarang, coba buka halaman GitHub-mu di browser. Simsalabim! Kodemu sudah muncul di sana.*

### 2. Mengambil Kode dari GitHub (`git clone` & `git pull`)

**A. `git clone` (Menyalin Utuh)**
Digunakan saat kamu ingin mengambil proyek orang lain (atau proyekmu sendiri di komputer baru).
```bash
git clone https://github.com/orang-lain/projeknya.git
```
Ini akan menciptakan folder baru yang berisi seluruh kode dan riwayat Git proyek tersebut.

**B. `git pull` (Memperbarui)**
Jika temanmu sudah melakukan *push* perubahan baru ke GitHub, kodemu di laptop akan ketinggalan zaman. Gunakan ini untuk menyedot perubahan terbaru masuk ke laptopmu:
```bash
git pull origin main
```

### 3. Kontribusi: Fork & Pull Request (PR)

Ini adalah alur "Sopan Santun" di dunia Open Source:
1. **Fork**: Klik tombol Fork di repo orang lain (Ini seperti "Me-Retweet" proyek mereka ke akunmu sendiri).
2. **Clone**: Download hasil *fork*-mu ke laptop.
3. **Push**: Perbaiki kodenya, lalu *push* kembali ke akunmu.
4. **Pull Request (PR)**: Klik tombol PR untuk meminta pemilik asli proyek tersebut menerima perbaikanmu. Jika dia setuju, kodemu akan resmi bergabung ke proyek mereka!

**Ringkasan Cepat:**
- **Push**: Lokal -> GitHub (Upload).
- **Pull**: GitHub -> Lokal (Update).
- **Clone**: GitHub -> Lokal (Baru pertama kali ambil).

## 💻 Latihan Praktik

[Soal atau project latihan terkait materi di atas akan ditambahkan di sini]
