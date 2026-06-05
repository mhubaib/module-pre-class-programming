# Bab 1: Pengenalan CLI

## Tujuan Pembelajaran

- Memahami pengertian dan fungsi CLI (Command Line Interface).
- Mengetahui alasan programmer profesional lebih memilih menggunakan CLI daripada GUI.
- Mengenal berbagai jenis aplikasi Terminal yang populer digunakan (CMD, PowerShell, Git Bash).

---

## Materi Utama

Sejauh ini, kamu mungkin sudah sangat terbiasa berinteraksi dengan komputer menggunakan mouse, mengklik ikon, dan memindahkan folder dengan cara menyeretnya. Cara ini disebut **GUI (Graphical User Interface)**. Namun, di dunia pemrograman, ada cara yang jauh lebih cepat dan efisien untuk memberi perintah kepada komputer: yaitu melalui baris teks yang diketik. Cara ini disebut **CLI (Command Line Interface)**.

---

### 1. Apa itu CLI?

**CLI (Command Line Interface)** adalah antarmuka berbasis teks di mana pengguna memberikan instruksi kepada komputer dengan cara mengetikkan baris perintah (*commands*).

Bayangkan jika GUI adalah cara kita "menunjuk" apa yang kita mau, maka CLI adalah cara kita "berbicara" langsung kepada sistem operasi.

**Perbandingan GUI vs CLI:**

| | GUI | CLI |
|---|---|---|
| Cara berinteraksi | Klik, seret, dan pilih menggunakan mouse | Ketik perintah teks menggunakan keyboard |
| Kecepatan untuk tugas kompleks | Lebih lambat (banyak langkah manual) | Lebih cepat (satu baris perintah) |
| Kurva belajar | Mudah dipelajari sejak awal | Memerlukan waktu untuk menghafal perintah |
| Kemampuan otomatisasi | Terbatas | Sangat tinggi |
| Ketersediaan di server | Tidak selalu ada | Selalu tersedia |

**Contoh perbandingan nyata:**

Untuk membuat folder bernama `proyek-web` di dalam direktori `Dokumen`, kamu bisa:
- **Via GUI**: Buka File Explorer → navigasi ke folder Dokumen → klik kanan → pilih "New Folder" → ketik nama folder → tekan Enter.
- **Via CLI**: Cukup ketik satu baris perintah berikut, lalu tekan Enter:

```bash
mkdir ~/Dokumen/proyek-web
```

Semakin kompleks tugasnya — misalnya membuat 10 folder sekaligus — perbedaan kecepatannya akan semakin terasa.

---

### 2. Mengapa Programmer Menggunakan CLI?

Mungkin kamu bertanya: *"Kenapa harus repot mengetik kalau bisa tinggal klik?"*

Ada beberapa alasan utama:

- **Kecepatan**: Mengetik satu baris perintah seringkali jauh lebih cepat daripada harus membuka banyak jendela folder.
- **Otomatisasi**: Kamu bisa menjalankan banyak tugas sekaligus secara otomatis hanya dengan satu kali tekan Enter.
- **Akses Server**: Sebagian besar komputer server (komputer yang menjalankan website di internet) tidak memiliki tampilan gambar, jadi kita wajib menggunakan CLI.
- **Alat Modern**: Alat-alat pemrograman populer (seperti Git, Node.js, atau React) memang dirancang untuk dijalankan lewat baris perintah.

**Contoh otomatisasi sederhana:**

Bayangkan kamu perlu mengubah nama 50 file gambar sekaligus agar semuanya menggunakan huruf kecil. Dengan GUI, kamu harus melakukannya satu per satu. Dengan CLI, satu perintah dapat menyelesaikan semua itu dalam hitungan detik.

```bash
# Contoh konseptual: mengubah semua nama file .jpg menjadi huruf kecil
# (perintah ini berjalan di Git Bash / Linux / macOS)
for f in *.JPG; do mv "$f" "${f,,}"; done
```

> Kamu belum perlu memahami perintah di atas sepenuhnya. Contoh tersebut hanya untuk menggambarkan betapa ringkasnya sebuah tugas yang kompleks dapat diselesaikan melalui CLI.

---

### 3. Mengenal Aplikasi Terminal

Tempat untuk mengetikkan perintah CLI disebut **Terminal** atau **Console**. Terdapat beberapa aplikasi terminal yang umum digunakan, tergantung pada sistem operasi:

**Windows:**

| Aplikasi | Keterangan |
|---|---|
| **Command Prompt (CMD)** | Terminal bawaan Windows yang paling dasar. Menggunakan sintaks perintah Windows. |
| **PowerShell** | Versi yang lebih canggih dari CMD, dengan kemampuan otomatisasi yang lebih kuat. |
| **Git Bash** | Terminal yang diinstal bersama Git. Menggunakan sintaks Unix/Linux, lebih umum digunakan dalam pengembangan web modern. **Ini yang akan kita gunakan di modul-modul berikutnya.** |

**macOS dan Linux:**

Kedua sistem operasi ini memiliki aplikasi bernama **Terminal** yang sudah terpasang secara bawaan. Terminal di macOS dan Linux menggunakan sintaks yang sama dengan Git Bash, sehingga perintah-perintah yang dipelajari di modul ini berlaku di ketiga lingkungan tersebut.

**Tampilan dasar terminal:**

Ketika kamu membuka terminal, kamu akan disambut oleh teks seperti ini:

```bash
nama-pengguna@nama-komputer:~$
```

Tanda `$` di akhir disebut **prompt** — ini adalah tanda bahwa terminal siap menerima perintah dari kamu. Kamu cukup mengetikkan perintah setelah tanda tersebut, lalu tekan Enter untuk menjalankannya.

```bash
nama-pengguna@nama-komputer:~$ echo "Halo, dunia!"
Halo, dunia!
```

**Analogi CLI:**

Bayangkan kamu berada di sebuah restoran.

- **GUI** adalah menu bergambar; kamu hanya bisa memesan apa yang gambarnya ada di situ.
- **CLI** adalah kamu berbicara langsung dengan koki di dapur; kamu bisa meminta modifikasi masakan yang sangat spesifik yang tidak ada di gambar menu, asalkan kamu tahu cara mengatakannya.

---

### 4. Struktur Sebuah Perintah CLI

Setiap perintah CLI umumnya mengikuti struktur yang konsisten. Memahami strukturnya akan memudahkan kamu mempelajari perintah-perintah baru di masa mendatang.

```
perintah  [opsi]  [argumen]
```

- **Perintah**: Nama aksi yang ingin dijalankan (misalnya `mkdir` untuk membuat folder).
- **Opsi** *(opsional)*: Pengaturan tambahan yang mengubah perilaku perintah, biasanya diawali tanda `-` atau `--` (misalnya `-v` atau `--verbose`).
- **Argumen** *(opsional)*: Target atau nilai yang diberikan kepada perintah (misalnya nama folder atau file).

**Contoh:**

```bash
mkdir proyek-web
#  ^      ^
#  |      argumen: nama folder yang akan dibuat
#  perintah: "make directory" (buat folder)
```

```bash
ls -la
# ^  ^
# |  opsi: -l (format panjang) dan -a (tampilkan file tersembunyi)
# perintah: "list" (tampilkan isi direktori)
```

---

### 5. Perintah Dasar yang Perlu Diketahui

Berikut adalah beberapa perintah dasar yang akan sangat sering kamu gunakan selama belajar pemrograman. Perintah-perintah ini berlaku di Git Bash, macOS Terminal, dan Linux Terminal.

| Perintah | Kepanjangan | Fungsi | Contoh Penggunaan |
|---|---|---|---|
| `pwd` | Print Working Directory | Menampilkan lokasi direktori saat ini | `pwd` |
| `ls` | List | Menampilkan daftar file dan folder | `ls` atau `ls -la` |
| `cd` | Change Directory | Berpindah ke direktori lain | `cd Dokumen` |
| `mkdir` | Make Directory | Membuat folder baru | `mkdir proyek-web` |
| `touch` | — | Membuat file baru yang kosong | `touch index.html` |
| `rm` | Remove | Menghapus file | `rm file.txt` |
| `rm -r` | Remove Recursive | Menghapus folder beserta isinya | `rm -r nama-folder` |
| `cp` | Copy | Menyalin file atau folder | `cp file.txt salinan.txt` |
| `mv` | Move | Memindahkan atau mengubah nama file | `mv lama.txt baru.txt` |
| `clear` | — | Membersihkan tampilan terminal | `clear` |

**Contoh sesi terminal sederhana:**

```bash
# 1. Cek posisi direktori saat ini
pwd
# Output: /c/Users/NamaPengguna

# 2. Masuk ke folder Dokumen
cd Dokumen

# 3. Buat folder proyek baru
mkdir proyek-pertamaku

# 4. Masuk ke folder yang baru dibuat
cd proyek-pertamaku

# 5. Buat file HTML pertama
touch index.html

# 6. Cek apakah file berhasil dibuat
ls
# Output: index.html
```

> **Catatan penting:** Perintah `rm` dan `rm -r` bersifat permanen — file atau folder yang dihapus tidak akan masuk ke Recycle Bin. Pastikan kamu sudah yakin sebelum menjalankan perintah tersebut.

---

### Kesimpulan

CLI adalah keterampilan fundamental yang perlu dimiliki oleh setiap pengembang web. Meskipun pada awalnya terasa asing dibandingkan GUI, kebiasaan menggunakan terminal akan meningkatkan produktivitas dan membuka akses ke berbagai alat pemrograman modern yang tidak dapat dijalankan melalui antarmuka grafis.

Di modul-modul berikutnya, kamu akan mulai menggunakan terminal secara langsung — untuk mengelola proyek, menjalankan perintah Git, hingga menjalankan server pengembangan lokal.

**Ringkasan:**

| Konsep | Penjelasan Singkat |
|---|---|
| CLI | Antarmuka berbasis teks untuk memberi perintah kepada komputer |
| GUI | Antarmuka berbasis grafis yang dioperasikan dengan mouse |
| Terminal / Console | Aplikasi tempat menulis dan menjalankan perintah CLI |
| Prompt (`$`) | Tanda bahwa terminal siap menerima perintah |
| CMD / PowerShell | Terminal bawaan Windows |
| Git Bash | Terminal berbasis Unix untuk Windows, direkomendasikan untuk pengembangan web |
