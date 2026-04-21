# Bab 63: Git Branch & Merge

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Memahami konsep *Branching* (Percabangan) sebagai ruang kerja paralel yang aman.
- Mampu membuat, berpindah, dan menghapus branch menggunakan perintah `git branch` dan `git checkout`.
- Mampu menyatukan kembali fitur dari branch ke dalam kode utama menggunakan `git merge`.

## 📚 Materi Utama

Bayangkan kamu sedang membuat website toko online yang sudah sukses berjalan. Tiba-tiba, kamu ingin mencoba membuat fitur baru (misalnya "Fitur Diskon Ramadhan"). 

Jika kamu langsung mengedit kode utama dan ternyata fiturnya *error*, websitemu bisa hancur/mati total. Untuk mencegah hal ini, kita menggunakan **Branching**.

### 1. Apa itu Branch?

**Branch (Cabang)** adalah salinan kodemu yang terpisah dari jalur utama. Jalur utama biasanya bernama `main` atau `master`. 
Kamu bisa membuat cabang baru, ber-eksperimen sesukamu di sana, dan jika gagal, kamu tinggal menghapus cabangnya tanpa merusak kode utama yang sehat.

### 2. Perintah Dasar Branching

**A. Membuat Cabang Baru**
```bash
git branch fitur-diskon
```

**B. Melihat Daftar Cabang**
```bash
git branch
```
Cabang yang sedang aktif akan ditandai dengan tanda bintang (`*`) dan warna hijau.

**C. Berpindah Cabang**
```bash
git checkout fitur-diskon
```
*Tips: Saat ini ada perintah baru yang lebih mudah diingat, yaitu `git switch fitur-diskon`.*

**D. Membuat & Langsung Pindah (Jalan Pintas)**
```bash
git checkout -b fitur-keren
```

### 3. Menggabungkan Kembali (`git merge`)

Setelah fitur barumu sukses dan bebas *error*, sekarang saatnya menggabungkannya ke jalur utama (`main`). 
1. Pindah dulu ke branch utama: `git checkout main`.
2. Tarik fiturnya masuk: `git merge fitur-diskon`.

Sekarang, kode utama websitemu sudah update dengan fitur terbaru secara aman!

**Analogi Branching:**
Bayangkan kamu sedang menulis novel di buku tulis.
- **Main Branch** adalah buku aslimu.
- **Branch Baru** adalah kamu memfotokopi halaman terakhir novelmu. Kamu mengoret-oret ide gila di kertas fotokopi itu. 
- Jika idenya bagus, kamu salin oret-oretan itu ke buku asli (**Merge**). 
- Jika idenya jelek, kamu tinggal buang kertas fotokopi itu tanpa menodai buku aslimu.