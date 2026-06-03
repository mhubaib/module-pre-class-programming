# Bab 59: Manipulasi File Menggunakan Command CLI

## Tujuan Pembelajaran

- Mampu bernavigasi antar folder menggunakan perintah `pwd`, `ls`, dan `cd`.
- Mampu membuat, menghapus, serta memindahkan file dan folder melalui Terminal.
- Memahami konsep *Path* (alamat lokasi file dan folder) di dalam sistem komputer.

---

## Materi Utama

Setelah memahami apa itu CLI di Bab 58, sekarang saatnya kamu mempraktikkan perintah-perintah untuk menavigasi folder dan mengelola file tanpa perlu menggunakan mouse.

> **Catatan:** Perintah-perintah dalam modul ini adalah standar yang digunakan di Linux, macOS, dan aplikasi **Git Bash** di Windows.

---

### Konsep Path (Alamat Lokasi)

Sebelum mulai mengetik perintah, penting untuk memahami konsep **Path** — yaitu alamat yang menunjukkan lokasi sebuah file atau folder di dalam sistem penyimpanan komputer.

Terdapat dua jenis path:

- **Absolute Path (Alamat Lengkap)**: Dimulai dari direktori paling atas (root), menunjukkan lokasi yang sama dari mana pun kamu berada.

  ```
  /c/Users/NamaPengguna/Dokumen/proyek-web
  ```

- **Relative Path (Alamat Relatif)**: Dimulai dari direktori yang sedang aktif saat ini. Lebih ringkas, namun hasilnya bergantung pada posisi kamu berada.

  ```
  Dokumen/proyek-web
  ```

**Karakter khusus dalam path:**

| Karakter | Artinya |
|---|---|
| `/` | Pemisah antar folder dalam path |
| `~` | Direktori utama pengguna (Home), misalnya `/c/Users/NamaPengguna` |
| `.` | Direktori saat ini |
| `..` | Direktori satu tingkat di atas direktori saat ini |

---

### 1. Navigasi: Menjelajahi Folder

#### A. `pwd` — Cek Posisi Saat Ini

`pwd` (Print Working Directory) menampilkan path lengkap dari direktori yang sedang aktif. Ini adalah perintah pertama yang sebaiknya kamu jalankan saat membuka terminal, untuk memastikan kamu berada di lokasi yang tepat sebelum menjalankan perintah lainnya.

```bash
pwd
# Output contoh:
# /c/Users/NamaPengguna
```

#### B. `ls` — Tampilkan Isi Direktori

`ls` (List) menampilkan daftar seluruh file dan folder yang ada di dalam direktori saat ini.

```bash
ls
# Output contoh:
# Dokumen  Downloads  Desktop  proyek-web
```

Perintah `ls` juga mendukung beberapa opsi yang berguna:

| Perintah | Fungsi |
|---|---|
| `ls` | Tampilkan file dan folder |
| `ls -l` | Tampilkan dalam format panjang (termasuk ukuran, tanggal, dan izin file) |
| `ls -a` | Tampilkan semua file termasuk file tersembunyi (yang diawali titik) |
| `ls -la` | Gabungan keduanya |

```bash
ls -la
# Output contoh:
# drwxr-xr-x  NamaPengguna  Dokumen
# -rw-r--r--  NamaPengguna  index.html
# -rw-r--r--  NamaPengguna  .gitignore   ← file tersembunyi
```

#### C. `cd` — Berpindah Direktori

`cd` (Change Directory) digunakan untuk berpindah dari satu folder ke folder lainnya.

| Perintah | Fungsi |
|---|---|
| `cd nama-folder` | Masuk ke folder yang disebutkan |
| `cd ..` | Naik satu tingkat ke direktori induk |
| `cd ../..` | Naik dua tingkat sekaligus |
| `cd ~` | Kembali langsung ke direktori Home |
| `cd -` | Kembali ke direktori sebelumnya |

```bash
# Contoh sesi navigasi
pwd
# /c/Users/NamaPengguna

cd Dokumen
pwd
# /c/Users/NamaPengguna/Dokumen

cd proyek-web
pwd
# /c/Users/NamaPengguna/Dokumen/proyek-web

cd ..
pwd
# /c/Users/NamaPengguna/Dokumen

cd ~
pwd
# /c/Users/NamaPengguna
```

---

### 2. Mengelola File dan Folder

#### A. Membuat Folder (`mkdir`)

`mkdir` (Make Directory) membuat satu atau lebih folder baru.

```bash
# Membuat satu folder
mkdir proyek-baru

# Membuat beberapa folder sekaligus
mkdir css js images

# Membuat folder beserta sub-foldernya secara langsung (opsi -p)
mkdir -p proyek-baru/assets/images
```

**Contoh sesi:**

```bash
cd ~/Dokumen
mkdir proyek-web
cd proyek-web
mkdir css js images
ls
# Output: css  images  js
```

#### B. Membuat File (`touch`)

`touch` membuat satu atau lebih file kosong. Perintah ini tersedia di Git Bash, macOS, dan Linux.

```bash
# Membuat satu file
touch index.html

# Membuat beberapa file sekaligus
touch index.html style.css script.js
```

**Contoh sesi:**

```bash
cd ~/Dokumen/proyek-web
touch index.html
cd css
touch style.css reset.css
ls
# Output: reset.css  style.css
```

> **Catatan:** Di Windows Command Prompt (CMD), perintah `touch` tidak tersedia. Gunakan Git Bash atau PowerShell untuk hasil yang konsisten.

#### C. Menampilkan Isi File (`cat`)

`cat` menampilkan isi sebuah file langsung di terminal, tanpa perlu membukanya di editor teks.

```bash
cat index.html
# Output: (isi file index.html ditampilkan di terminal)
```

#### D. Menghapus File dan Folder (`rm`)

`rm` (Remove) menghapus file atau folder. 

> **Peringatan:** Penghapusan melalui CLI bersifat **permanen**. File yang dihapus tidak akan masuk ke Recycle Bin dan tidak dapat dipulihkan dengan cara biasa. Pastikan kamu sudah yakin sebelum menjalankan perintah ini.

| Perintah | Fungsi |
|---|---|
| `rm file.txt` | Menghapus satu file |
| `rm file1.txt file2.txt` | Menghapus beberapa file sekaligus |
| `rm -r nama-folder` | Menghapus folder beserta seluruh isinya |
| `rm -rf nama-folder` | Menghapus folder beserta isinya tanpa meminta konfirmasi |

```bash
# Menghapus satu file
rm catatan.txt

# Menghapus folder dan seluruh isinya
rm -r folder-lama
```

#### E. Memindahkan dan Mengubah Nama (`mv`)

`mv` (Move) digunakan untuk memindahkan file ke lokasi lain, atau mengubah nama file.

```bash
# Memindahkan file ke dalam folder lain
mv style.css css/

# Mengubah nama file
mv lama.txt baru.txt

# Memindahkan sekaligus mengubah nama
mv lama.txt arsip/baru.txt
```

**Contoh sesi:**

```bash
cd ~/Dokumen/proyek-web
touch navbar.css footer.css

# Pindahkan keduanya ke dalam folder css/
mv navbar.css css/
mv footer.css css/

ls css/
# Output: footer.css  navbar.css  reset.css  style.css
```

#### F. Menyalin File dan Folder (`cp`)

`cp` (Copy) membuat salinan file atau folder.

```bash
# Menyalin file
cp index.html tentang.html

# Menyalin folder beserta seluruh isinya (opsi -r)
cp -r proyek-web proyek-web-backup
```

---

### 3. Tips Produktivitas di Terminal

Berikut adalah beberapa kebiasaan dan pintasan yang akan membuat pekerjaan di terminal jauh lebih cepat dan nyaman:

- **Tab Auto-Complete**: Ketikkan beberapa huruf pertama nama file atau folder, lalu tekan tombol **Tab**. Terminal akan melengkapi namanya secara otomatis. Jika terdapat lebih dari satu kemungkinan, tekan Tab dua kali untuk melihat seluruh pilihan yang tersedia.

  ```bash
  cd proy  # tekan Tab → otomatis menjadi: cd proyek-web
  ```

- **Panah Atas / Bawah**: Tekan tombol panah atas (`↑`) untuk memanggil kembali perintah yang sebelumnya dijalankan, sehingga kamu tidak perlu mengetiknya ulang. Tekan panah bawah (`↓`) untuk maju ke perintah berikutnya dalam riwayat.

- **`clear`**: Membersihkan seluruh tampilan terminal agar lebih mudah dibaca. Riwayat perintah tidak hilang — kamu masih bisa menekan panah atas untuk memanggilnya kembali.

  ```bash
  clear
  ```

- **`history`**: Menampilkan daftar seluruh perintah yang pernah kamu jalankan dalam sesi terminal saat ini.

  ```bash
  history
  # Output:
  # 1  pwd
  # 2  cd Dokumen
  # 3  mkdir proyek-web
  # 4  touch index.html
  ```

- **`Ctrl + C`**: Menghentikan perintah yang sedang berjalan secara paksa. Berguna ketika sebuah proses berjalan terlalu lama atau terjadi kesalahan.

---

### 4. Simulasi Sesi Kerja Lengkap

Berikut adalah simulasi sesi terminal yang menggabungkan seluruh perintah yang telah dipelajari — mulai dari membuka terminal hingga menyiapkan struktur folder proyek web pertamamu:

```bash
# 1. Cek posisi awal
pwd
# /c/Users/NamaPengguna

# 2. Masuk ke folder Dokumen
cd Dokumen

# 3. Buat folder proyek baru
mkdir proyek-portfolio
cd proyek-portfolio

# 4. Buat sub-folder untuk aset
mkdir css js images

# 5. Buat file utama
touch index.html

# 6. Buat file CSS di dalam folder css
touch css/style.css css/reset.css

# 7. Buat file JavaScript di dalam folder js
touch js/script.js

# 8. Verifikasi seluruh struktur yang sudah dibuat
ls
# Output: css  images  index.html  js

ls css
# Output: reset.css  style.css

ls js
# Output: script.js

# 9. Bersihkan tampilan terminal
clear
```

Hasil akhir dari sesi di atas adalah struktur folder yang siap digunakan untuk memulai proyek web:

```
proyek-portfolio/
├── css/
│   ├── reset.css
│   └── style.css
├── images/
├── js/
│   └── script.js
└── index.html
```

---

### Kesimpulan

Mengelola file dan folder melalui terminal adalah keterampilan dasar yang akan kamu gunakan setiap hari sebagai seorang pengembang web — mulai dari menyiapkan proyek baru, berpindah antar direktori, hingga mengelola file konfigurasi.

**Referensi Cepat Perintah:**

| Perintah | Fungsi |
|---|---|
| `pwd` | Menampilkan direktori aktif saat ini |
| `ls` | Menampilkan isi direktori |
| `ls -la` | Menampilkan isi direktori secara detail termasuk file tersembunyi |
| `cd nama-folder` | Masuk ke folder yang disebutkan |
| `cd ..` | Naik satu tingkat ke direktori induk |
| `cd ~` | Kembali ke direktori Home |
| `mkdir nama` | Membuat folder baru |
| `touch nama-file` | Membuat file kosong baru |
| `cat nama-file` | Menampilkan isi file di terminal |
| `rm nama-file` | Menghapus file (permanen) |
| `rm -r nama-folder` | Menghapus folder beserta isinya (permanen) |
| `mv sumber tujuan` | Memindahkan atau mengubah nama file/folder |
| `cp sumber tujuan` | Menyalin file |
| `cp -r sumber tujuan` | Menyalin folder beserta isinya |
| `clear` | Membersihkan tampilan terminal |
| `history` | Menampilkan riwayat perintah |
