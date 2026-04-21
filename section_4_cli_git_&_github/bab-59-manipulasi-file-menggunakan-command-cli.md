# Bab 59: Manipulasi File Menggunakan Command CLI

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Mampu bernavigasi antar folder menggunakan perintah `pwd`, `ls`, dan `cd`.
- Mampu membuat, menghapus, serta memindahkan file dan folder melalui Terminal.
- Memahami konsep *Path* atau alamat folder di komputer.

## 📚 Materi Utama

Sekarang saatnya kamu mempelajari "kata-kata sakti" untuk menavigasi folder dan mengelola file tanpa perlu menyentuh mouse.

*Catatan: Perintah-perintah ini adalah standar yang digunakan di Linux, macOS, dan aplikasi Git Bash di Windows.*

### 1. Navigasi: Menjelajahi Folder

**A. `pwd` (Print Working Directory)**
Cek di mana posisimu sekarang. Komputer akan menampilkan alamat folder yang sedang aktif.

**B. `ls` (List)**
Tampilkan isi dari folder tersebut (file dan sub-folder apa saja yang ada di dalamnya).

**C. `cd` (Change Directory)**
Berpindah antar folder:
- `cd nama-folder`: Masuk ke folder tersebut.
- `cd ..`: Keluar ke folder yang setingkat lebih tinggi (kembali).
- `cd ~`: Kembali langsung ke folder utama User (*Home*).

### 2. Mengelola File & Folder

**A. Membuat Folder (`mkdir`)**
Singkatan dari *Make Directory*. Contoh: `mkdir projek-baru`.

**B. Membuat File (`touch`)**
Perintah untuk membuat file kosong. Contoh: `touch style.css`. (Catatan: Di Windows CMD perintahnya berbeda, tapi di Git Bash kamu bisa pakai `touch`).

**C. Menghapus (`rm` & `rm -rf`)**
- `rm file.txt`: Menghapus satu file.
- `rm -rf folder/`: Menghapus folder beserta seluruh isinya.
*Hati-hati! CLI tidak pindah ke Recycle Bin. Jika sudah dihapus lewat sini, data hilang selamanya.*

**D. Memindah & Ganti Nama (`mv`)**
- `mv file.txt folder/`: Memindahkan file ke dalam folder tujuan.
- `mv lama.txt baru.txt`: Mengganti nama file.

### 3. Tips Canggih

- **Tab (Auto-Complete)**: Ketikkan huruf pertama sebuah folder, lalu tekan tombol **Tab**. Terminal akan melengkapi nama foldernya secara otomatis.
- **Panah Atas**: Tekan panah atas di keyboard untuk memanggil kembali perintah yang baru saja kamu ketikkan agar tidak capek mengetik ulang.
- **`clear`**: Bersihkan layar terminalmu agar terlihat rapi kembali.