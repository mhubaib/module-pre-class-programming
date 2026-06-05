# Bab 9: Merge Conflict

## Tujuan Pembelajaran

- Memahami penyebab terjadinya *Merge Conflict*.
- Mampu membaca tanda konflik di dalam file kode.
- Mampu menyelesaikan konflik secara aman menggunakan Visual Studio Code maupun terminal.

---

## Materi Utama

Ketika bekerja dalam tim, ada situasi di mana dua orang mengubah bagian yang sama dari sebuah file secara bersamaan. Saat perubahan tersebut digabungkan, Git tidak dapat menentukan secara otomatis versi mana yang harus dipertahankan. Inilah yang disebut **Merge Conflict**.

Merge Conflict terdengar menakutkan bagi pemula, namun sebenarnya ini adalah mekanisme perlindungan Git — daripada memilih sendiri dan berpotensi menghapus pekerjaan seseorang, Git meminta kamu untuk membuat keputusan tersebut secara sadar.

---

### 1. Mengapa Merge Conflict Terjadi?

Konflik terjadi ketika dua branch mengubah **baris yang sama** pada **file yang sama**, sehingga Git tidak dapat menentukan versi mana yang benar saat kedua branch digabungkan.

**Contoh skenario:**

1. Kamu dan temanmu sama-sama bekerja pada file `index.html`.
2. Di branch milikmu, kamu mengubah baris ke-10 menjadi:
   ```html
   <h1 style="color: red;">Selamat Datang</h1>
   ```
3. Di branch milik temanmu, baris yang sama diubah menjadi:
   ```html
   <h1 style="color: blue;">Selamat Datang</h1>
   ```
4. Saat kalian mencoba menggabungkan kedua branch, Git mendeteksi pertentangan dan menghentikan proses merge — meminta kamu untuk menyelesaikannya secara manual.

**Situasi yang memicu Merge Conflict:**

| Situasi | Penjelasan |
|---|---|
| Dua branch mengubah baris yang sama | Penyebab paling umum |
| Satu branch mengubah file, branch lain menghapusnya | Git tidak tahu apakah file harus dipertahankan atau dihapus |
| Dua branch menambahkan baris berbeda di posisi yang berdekatan | Git merasa posisi akhirnya ambigu |

---

### 2. Cara Mengenali Merge Conflict

Ketika konflik terjadi, Git akan menampilkan pesan seperti ini di terminal:

```bash
git merge branch-teman
# Output:
# Auto-merging index.html
# CONFLICT (content): Merge conflict in index.html
# Automatic merge failed; fix conflicts and then commit the result.
```

Di dalam file yang berkonflik, Git akan menyisipkan penanda khusus yang menandai kedua versi yang bertentangan:

```html
<<<<<<< HEAD
<h1 style="color: red;">Selamat Datang</h1>
=======
<h1 style="color: blue;">Selamat Datang</h1>
>>>>>>> branch-teman
```

**Penjelasan setiap penanda:**

| Penanda | Artinya |
|---|---|
| `<<<<<<< HEAD` | Awal dari versi milikmu (branch yang sedang aktif) |
| `=======` | Garis pemisah antara kedua versi |
| `>>>>>>> branch-teman` | Akhir dari versi yang datang dari branch lain |

Untuk melihat seluruh file yang berkonflik, gunakan `git status`:

```bash
git status
# Output:
# You have unmerged paths.
#   (fix conflicts and run "git commit")
#
# Unmerged paths:
#   (use "git add <file>..." to mark resolution)
#         both modified:   index.html
```

---

### 3. Cara Menyelesaikan Konflik

Terdapat dua cara untuk menyelesaikan Merge Conflict: menggunakan Visual Studio Code atau langsung di terminal.

#### A. Menggunakan Visual Studio Code (Direkomendasikan untuk Pemula)

VS Code menampilkan konflik secara visual dengan warna berbeda dan menyediakan tombol pilihan di atas area konflik:

- **Accept Current Change** — Pertahankan versimu dan buang versi yang datang.
- **Accept Incoming Change** — Buang versimu dan gunakan versi yang datang.
- **Accept Both Changes** — Gabungkan keduanya; kedua baris akan dipertahankan.
- **Compare Changes** — Tampilkan perbandingan kedua versi secara berdampingan.

Pilih opsi yang paling sesuai berdasarkan kebutuhan proyekmu. Jika ragu, diskusikan dengan rekan tim yang membuat perubahan tersebut.

#### B. Secara Manual di Editor Teks

1. Buka file yang berkonflik.
2. Temukan seluruh blok penanda konflik (`<<<<<<<`, `=======`, `>>>>>>>`).
3. Putuskan versi mana yang ingin dipertahankan — atau tulis ulang baris tersebut dengan menggabungkan kedua versi jika diperlukan.
4. Hapus seluruh baris penanda konflik.
5. Simpan file.

**Contoh — sebelum diselesaikan:**

```html
<<<<<<< HEAD
<h1 style="color: red;">Selamat Datang</h1>
=======
<h1 style="color: blue;">Selamat Datang</h1>
>>>>>>> branch-teman
```

**Contoh — setelah diselesaikan (memilih versi biru):**

```html
<h1 style="color: blue;">Selamat Datang</h1>
```

**Contoh — setelah diselesaikan (menggabungkan keduanya):**

```html
<h1 style="color: red; border-bottom: 2px solid blue;">Selamat Datang</h1>
```

#### C. Menyelesaikan dan Mencatat Hasil

Setelah seluruh konflik pada semua file diselesaikan, lanjutkan dengan langkah berikut:

```bash
# 1. Tandai file yang konfliknya sudah diselesaikan
git add index.html

# Jika ada beberapa file yang berkonflik, tambahkan semuanya
git add .

# 2. Verifikasi tidak ada konflik yang tersisa
git status
# Output:
# All conflicts fixed but you are still merging.
#   (use "git commit" to conclude merge)

# 3. Catat hasilnya dengan commit
git commit -m "Menyelesaikan konflik pada warna judul di index.html"
# Output:
# [main f1a2b3c] Menyelesaikan konflik pada warna judul di index.html
```

---

### 4. Membatalkan Merge yang Berkonflik

Jika kamu ingin membatalkan proses merge dan kembali ke kondisi sebelum merge dimulai, gunakan:

```bash
git merge --abort
# Output:
# (kembali ke kondisi sebelum git merge dijalankan)

git status
# On branch main
# nothing to commit, working tree clean
```

Perintah ini berguna ketika konflik terlalu kompleks dan kamu ingin mendiskusikannya dengan rekan tim terlebih dahulu sebelum melanjutkan.

---

### 5. Praktik Terbaik untuk Menghindari Konflik

Merge Conflict tidak dapat dihindari sepenuhnya, namun frekuensinya dapat diminimalkan dengan kebiasaan kerja yang baik:

- **Selalu `git pull` sebelum mulai bekerja** — Pastikan kode lokalmu selalu sinkron dengan versi terbaru di GitHub sebelum membuat perubahan baru.
- **Buat commit yang kecil dan terfokus** — Semakin sedikit baris yang diubah dalam satu commit, semakin mudah konflik yang muncul untuk diselesaikan.
- **Komunikasi dengan tim** — Jika kamu dan rekan tim akan mengerjakan file yang sama, koordinasikan pembagian tugasnya terlebih dahulu.
- **Segera selesaikan konflik** — Jangan menunda. Semakin lama konflik dibiarkan, semakin banyak perubahan yang menumpuk dan semakin sulit untuk diselesaikan.
- **Gunakan branch yang terfokus** — Setiap branch sebaiknya hanya mengerjakan satu fitur atau perbaikan. Branch yang terlalu besar dengan banyak perubahan lebih rentan menghasilkan konflik.

---

### 6. Simulasi Sesi Merge Conflict Lengkap

Berikut adalah simulasi lengkap dari munculnya konflik hingga penyelesaiannya:

```bash
# === Kondisi awal: branch main ===
git log --oneline -2
# b2c3d4e (HEAD -> main) Menambahkan halaman utama
# a1b2c3d Inisialisasi proyek

# === Branch pertama: fitur-warna-merah ===
git switch -c fitur-warna-merah
# (ubah baris di index.html menjadi warna merah)
git add index.html
git commit -m "Menggunakan warna merah untuk judul utama"

# === Kembali ke main, buat branch kedua ===
git switch main
git switch -c fitur-warna-biru
# (ubah baris yang SAMA di index.html menjadi warna biru)
git add index.html
git commit -m "Menggunakan warna biru untuk judul utama"

# === Gabungkan branch pertama ke main ===
git switch main
git merge fitur-warna-merah
# Fast-forward (tidak ada konflik)

# === Gabungkan branch kedua → konflik! ===
git merge fitur-warna-biru
# CONFLICT (content): Merge conflict in index.html
# Automatic merge failed; fix conflicts and then commit the result.

# === Lihat file yang berkonflik ===
git status
# Unmerged paths:
#   both modified:   index.html

# === Buka index.html, selesaikan konflik secara manual ===
# (hapus penanda <<, ==, >>, pilih atau gabungkan versi yang tepat)

# === Catat hasil penyelesaian ===
git add index.html
git commit -m "Menyelesaikan konflik: memilih warna biru untuk judul utama"

# === Verifikasi ===
git log --oneline -4
# f3g4h5i (HEAD -> main) Menyelesaikan konflik: memilih warna biru untuk judul utama
# e2f3g4h Menggunakan warna merah untuk judul utama (dari fitur-warna-merah)
# b2c3d4e Menambahkan halaman utama
# a1b2c3d Inisialisasi proyek
```

---

### Kesimpulan

Merge Conflict adalah bagian normal dari alur kerja kolaboratif menggunakan Git. Kemampuan membaca penanda konflik, menentukan versi yang tepat, dan menyelesaikannya dengan benar adalah keterampilan penting yang akan semakin terasah seiring pengalaman bekerja dalam tim.

**Ringkasan Perintah:**

| Perintah | Fungsi |
|---|---|
| `git merge nama-branch` | Menggabungkan branch — dapat memicu konflik |
| `git status` | Melihat file mana yang masih berkonflik |
| `git add nama-file` | Menandai bahwa konflik pada file tersebut sudah diselesaikan |
| `git commit` | Menyelesaikan proses merge setelah semua konflik ditangani |
| `git merge --abort` | Membatalkan proses merge dan kembali ke kondisi sebelumnya |
