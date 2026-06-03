# Bab 60: Pengenalan VCS (Git) & Instalasi

## Tujuan Pembelajaran

- Memahami kegunaan Version Control System (VCS) dalam pengelolaan proyek.
- Mengenal Git sebagai alat pengelola versi yang paling populer.
- Mampu melakukan instalasi Git di Windows secara benar.
- Membedakan antara Git (alat lokal) dan GitHub (layanan online).

---

## Materi Utama

Pernahkah kamu menyimpan file tugas dengan nama `tugas_v1.doc`, `tugas_revisi.doc`, hingga `tugas_REVISI_FINAL_FIX.doc`? Cara manual seperti ini sangat membingungkan dan rawan kesalahan — terutama ketika file sudah banyak dan kamu tidak ingat mana versi yang terakhir benar-benar selesai.

Dalam dunia pemrograman, masalah ini diselesaikan dengan program yang disebut **Version Control System (VCS)**.

---

### 1. Apa itu Version Control System (VCS)?

**Version Control System (VCS)** adalah sistem yang mencatat setiap perubahan yang dilakukan terhadap file-file dalam sebuah proyek dari waktu ke waktu. Dengan VCS, kamu dapat:

- Melihat riwayat lengkap seluruh perubahan yang pernah dibuat.
- Mengetahui siapa yang membuat perubahan tersebut dan kapan.
- Kembali ke versi file sebelumnya kapan saja.
- Mengerjakan proyek secara kolaboratif tanpa khawatir saling menimpa pekerjaan satu sama lain.

**Analogi Dokumen Sekolah:**

Bayangkan VCS seperti fitur *Track Changes* di Microsoft Word, namun jauh lebih canggih. Setiap kali kamu menyimpan versi baru, VCS mencatat seluruh perubahannya secara detail — dan kamu bisa menelusuri kembali seluruh riwayat tersebut kapan pun diperlukan.

---

### 2. Apa itu Git?

**Git** adalah VCS yang paling banyak digunakan di seluruh dunia. Git bekerja secara **lokal** di komputer kamu — artinya semua pencatatan riwayat perubahan tersimpan langsung di dalam folder proyekmu, tanpa memerlukan koneksi internet.

Git membantu kita dalam tiga hal utama:

- **Mencatat Riwayat Perubahan**: Setiap kali kamu menyimpan kemajuan pekerjaan (disebut *commit*), Git mencatat siapa yang membuat perubahan, kapan, dan apa yang berubah secara detail.
- **Mesin Waktu Proyek**: Jika suatu hari kodenya tiba-tiba tidak berfungsi setelah beberapa perubahan, kamu dapat mengembalikan seluruh proyek ke kondisi versi sebelumnya yang masih berjalan dengan baik.
- **Kolaborasi Tim**: Beberapa anggota tim dapat mengerjakan bagian proyek yang berbeda secara bersamaan, lalu menggabungkan hasilnya tanpa risiko menimpa pekerjaan satu sama lain.

**Contoh skenario nyata:**

Bayangkan kamu sedang membangun halaman web. Setelah tiga hari bekerja, kamu mencoba menambahkan fitur baru yang ternyata merusak tampilan halaman. Tanpa Git, kamu harus mengingat sendiri apa yang diubah dan mencoba memperbaikinya secara manual. Dengan Git, kamu cukup menjalankan satu perintah untuk kembali ke kondisi tiga hari yang lalu — semua perubahan yang merusak tadi langsung dibatalkan.

```bash
# Contoh konseptual: kembali ke versi sebelumnya
git checkout nama-versi-yang-aman
```

> Kamu belum perlu memahami perintah di atas sepenuhnya — perintah Git akan dipelajari secara bertahap di modul-modul berikutnya.

---

### 3. Git vs GitHub: Apa Bedanya?

Ini adalah pertanyaan yang sangat umum di kalangan pemula. Git dan GitHub adalah dua hal yang berbeda, meskipun sering disebutkan bersamaan.

| | Git | GitHub |
|---|---|---|
| **Jenis** | Perangkat lunak (aplikasi) | Layanan berbasis web |
| **Lokasi** | Berjalan di komputer lokal | Berjalan di internet (cloud) |
| **Fungsi** | Mencatat dan mengelola riwayat perubahan kode | Menyimpan dan berbagi kode secara online |
| **Koneksi internet** | Tidak diperlukan | Diperlukan |
| **Analogi** | Kamera foto | Platform media sosial untuk berbagi foto |

Dengan analogi tersebut:
- **Git** adalah **kameranya** — alat di komputermu untuk mengambil "foto" (mencatat versi) dari kodemu.
- **GitHub** adalah **platform berbagi foto** — tempat di internet kamu mengunggah foto-foto tersebut agar bisa dilihat, diunduh, dan dikerjakan bersama oleh tim lain.

> **Catatan:** Selain GitHub, terdapat layanan serupa seperti **GitLab** dan **Bitbucket**. Ketiganya menggunakan Git sebagai dasarnya, namun berbeda dalam fitur dan model bisnis masing-masing. GitHub adalah yang paling populer di komunitas pengembang open source.

---

### 4. Instalasi Git di Windows

Ikuti langkah-langkah berikut untuk memasang Git di komputer Windows:

**Langkah 1: Unduh Penginstal**

Kunjungi situs resmi Git di [git-scm.com](https://git-scm.com/) dan klik tombol unduh. Situs tersebut akan secara otomatis mendeteksi sistem operasimu dan menyediakan versi yang sesuai.

**Langkah 2: Jalankan Penginstal**

Buka file `.exe` yang telah diunduh. Kamu akan melihat beberapa layar pengaturan. Untuk pemula, seluruh pengaturan default sudah tepat — klik **Next** di setiap layar hingga proses selesai, lalu klik **Finish**.

**Langkah 3: Verifikasi Instalasi**

Setelah instalasi selesai, verifikasi bahwa Git terpasang dengan benar:

1. Klik kanan di area mana saja di File Explorer, lalu pilih **"Git Bash Here"** untuk membuka terminal Git Bash.
2. Ketikkan perintah berikut dan tekan Enter:

```bash
git --version
```

3. Jika Git terpasang dengan benar, terminal akan menampilkan nomor versinya:

```bash
git version 2.45.0.windows.1
```

Jika output serupa muncul, Git sudah siap digunakan di komputermu.

---

### 5. Konfigurasi Awal Git

Setelah Git terpasang, terdapat satu langkah penting yang **wajib dilakukan sekali** sebelum mulai menggunakannya: mendaftarkan identitas diri. Git akan menggunakan informasi ini untuk mencatat siapa yang membuat setiap perubahan dalam proyek.

Jalankan dua perintah berikut di Git Bash, ganti teks dalam tanda kutip dengan nama dan alamat email kamu:

```bash
git config --global user.name "Nama Lengkap Kamu"
git config --global user.email "emailkamu@contoh.com"
```

**Contoh:**

```bash
git config --global user.name "Budi Santoso"
git config --global user.email "budi.santoso@gmail.com"
```

Untuk memverifikasi bahwa konfigurasi tersimpan dengan benar, jalankan:

```bash
git config --list
# Output:
# user.name=Budi Santoso
# user.email=budi.santoso@gmail.com
```

> **Catatan:** Opsi `--global` berarti konfigurasi ini berlaku untuk seluruh proyek Git di komputermu. Kamu hanya perlu melakukan langkah ini satu kali. Gunakan alamat email yang sama dengan akun GitHub yang akan kamu buat atau gunakan nantinya.

---

### Kesimpulan

Git adalah alat yang wajib dikuasai oleh setiap pengembang web. Dengan Git, kamu tidak perlu lagi menyimpan puluhan salinan file secara manual — seluruh riwayat perubahan tercatat secara otomatis dan dapat diakses kapan saja.

Di modul-modul berikutnya, kamu akan mulai mempraktikkan perintah-perintah Git secara langsung: membuat repositori, mencatat perubahan, serta menghubungkan proyekmu dengan GitHub.

**Ringkasan:**

| Konsep | Penjelasan Singkat |
|---|---|
| VCS | Sistem yang mencatat seluruh riwayat perubahan file dalam sebuah proyek |
| Git | VCS paling populer, bekerja secara lokal di komputermu |
| Commit | Satu titik simpan dalam riwayat Git (seperti satu "foto" versi proyek) |
| GitHub | Layanan web untuk menyimpan dan berbagi repositori Git secara online |
| `git --version` | Perintah untuk memverifikasi instalasi Git |
| `git config --global` | Perintah untuk mendaftarkan identitas pengguna Git |
