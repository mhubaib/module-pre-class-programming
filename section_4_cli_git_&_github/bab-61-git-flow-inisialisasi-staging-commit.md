# Bab 61: Git Flow (inisialisasi, staging, commit)

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Mampu mengaktifkan Git pada sebuah folder proyek menggunakan `git init`.
- Memahami konsep *Three States* dalam Git (Working Directory, Staging Area, Repository).
- Mampu membungkus perubahan kode dengan perintah `git add` dan `git commit`.

## 📚 Materi Utama

Setelah berhasil menginstal Git, sekarang kita akan masuk ke inti dari cara kerja Git. Menggunakan Git itu seperti memotret sebuah proses pembangunan gedung: ada saatnya kamu meletakkan batu bata, ada saatnya kamu memotret untuk mencatat kemajuan.

### 1. Memulai Projek Baru (`git init`)

Untuk membuat folder di laptopmu mulai "diawasi" oleh Git, kamu harus menginisialisasinya terlebih dahulu. 
- Buka terminal (Git Bash).
- Masuk ke folder projekmu.
- Ketik perintah: `git init`.

Seketika, Git akan menciptakan folder tersembunyi bernama `.git` di dalam foldermu. Ini adalah "otak" dari Git yang akan mencatat segala perubahan.

### 2. Alur Kerja 3 Tahapan (The Three States)

Git tidak otomatis mencatat setiap huruf yang kamu ketik. Kamu harus melewati 3 tahapan resmi:

1. **Working Directory**: Folder tempatmu mengetik kode. File di sini statusnya masih bebas (*Untracked* atau *Modified*).
2. **Staging Area**: "Ruang Tunggu". Tempat mengumpulkan file-file yang sudah siap untuk dicatat versinya.
3. **Repository (Local)**: "Gudang Penyimpanan". Tempat versi permanen dari kodemu disimpan setelah difoto (di-commit).

### 3. Langkah Mencatat Versi (Add & Commit)

**Langkah 1: Cek Status (`git status`)**
Gunakan ini untuk melihat file mana yang baru saja kamu ubah tapi belum dicatat.

**Langkah 2: Masukkan ke Ruang Tunggu (`git add`)**
- `git add nama-file.html`: Memasukkan satu file spesifik.
- `git add .`: Memasukkan SEMUA file yang berubah di folder saat ini ke ruang tunggu.

**Langkah 3: Ambil Foto Versi (`git commit`)**
Ini adalah bagian terpenting. Kamu memberikan catatan pada versimu.
```bash
git commit -m "Catatan: Menambahkan judul di halaman home"
```
*Tips: Pesan commit haruslah jelas dan menjelaskan "apa" yang kamu ubah agar teman setimmu paham.*

**Analogi Sederhana:**
1. **Working Directory** = Kamu sedang memasukkan barang ke kardus belanjaan (ngetik kode).
2. **Staging Area** = Kamu membawa kardus ke meja kasir (siap-siap bayar).
3. **Repository** = Kasir memberikan struk belanja (pencatatan resmi selesai/Commit).