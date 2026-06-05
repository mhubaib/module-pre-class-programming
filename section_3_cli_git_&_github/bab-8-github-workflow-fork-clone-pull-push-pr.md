# Bab 65: GitHub Workflow (Fork, Clone, Pull, Push, PR)

## Tujuan Pembelajaran

- Memahami dan mempraktikkan alur pengiriman kode dari komputer lokal ke GitHub (`push`).
- Mampu menyalin proyek dari GitHub ke komputer lokal (`clone`).
- Memahami cara memperbarui kode lokal dengan perubahan terbaru dari GitHub (`pull`).
- Mampu menyalin repositori orang lain ke akun sendiri (`fork`).
- Mengenal konsep *Pull Request* (PR) sebagai cara berkontribusi pada proyek tim atau open source.

---

## Materi Utama

Setelah memiliki akun GitHub dan repositori pertama (Bab 64), kini saatnya mempelajari alur kerja pengiriman dan penerimaan kode antara komputer lokal dan GitHub.

Terdapat dua arah aliran kode yang perlu dipahami:

```
[ Komputer Lokal ] ---git push---> [ GitHub ]
[ Komputer Lokal ] <--git pull---- [ GitHub ]
```

---

### 1. Mengirim Kode ke GitHub (`git push`)

`git push` adalah perintah untuk mengirimkan commit yang ada di repositori lokal ke repositori GitHub.

**Langkah-langkah:**

```bash
# 1. Pastikan folder proyekmu sudah terhubung ke repositori GitHub
#    (lihat Bab 64 — langkah git remote add)
git remote -v
# Output:
# origin  https://github.com/username-kamu/belajar-frontend.git (fetch)
# origin  https://github.com/username-kamu/belajar-frontend.git (push)

# 2. Kirim seluruh commit dari branch main ke GitHub
git push -u origin main
# Output:
# Enumerating objects: 5, done.
# Counting objects: 100% (5/5), done.
# Writing objects: 100% (5/5), 432 bytes | 432.00 KiB/s, done.
# To https://github.com/username-kamu/belajar-frontend.git
#  * [new branch]      main -> main
# Branch 'main' set up to track remote branch 'main' from 'origin'.
```

**Penjelasan opsi pada `git push`:**

| Bagian | Penjelasan |
|---|---|
| `origin` | Nama alias untuk alamat repositori GitHub (didaftarkan via `git remote add`) |
| `main` | Nama branch yang dikirimkan |
| `-u` | Singkatan dari `--set-upstream`; menghubungkan branch lokal dengan branch di GitHub sehingga perintah `git push` berikutnya tidak perlu menyebutkan `origin main` lagi |

Setelah perintah di atas berhasil, perintah push selanjutnya cukup:

```bash
git push
```

**Contoh sesi kerja push rutin:**

```bash
# Kamu sudah melakukan beberapa perubahan dan commit
git log --oneline -3
# c7d8e9f (HEAD -> main) Menambahkan halaman tentang kami
# b5c6d7e Memperbaiki warna tombol
# a3f2c1d Inisialisasi proyek

# Kirim ke GitHub
git push
# Output:
# To https://github.com/username-kamu/belajar-frontend.git
#    a3f2c1d..c7d8e9f  main -> main
```

Setelah push berhasil, buka halaman repositorimu di browser — seluruh file dan riwayat commit akan terlihat di sana.

---

### 2. Menyalin Repositori dari GitHub (`git clone`)

`git clone` digunakan untuk mengunduh sebuah repositori dari GitHub ke komputermu secara lengkap, termasuk seluruh file dan riwayat commit-nya. Perintah ini digunakan ketika:

- Kamu ingin mulai mengerjakan proyek di komputer baru.
- Kamu ingin mempelajari atau menggunakan proyek milik orang lain.
- Kamu baru bergabung ke sebuah tim dan perlu mengunduh proyek yang sudah ada.

```bash
# Format dasar
git clone https://github.com/username/nama-repo.git

# Contoh: mengunduh proyekmu sendiri ke komputer lain
git clone https://github.com/username-kamu/belajar-frontend.git

# Output:
# Cloning into 'belajar-frontend'...
# remote: Enumerating objects: 12, done.
# remote: Counting objects: 100% (12/12), done.
# Receiving objects: 100% (12/12), done.
```

Perintah ini akan membuat folder baru bernama `belajar-frontend` yang berisi seluruh isi repositori, lengkap dengan folder `.git` sehingga langsung siap digunakan sebagai proyek Git.

```bash
# Verifikasi isi folder hasil clone
cd belajar-frontend
ls
# Output: index.html  css  js  README.md

git log --oneline -3
# c7d8e9f (HEAD -> main, origin/main) Menambahkan halaman tentang kami
# b5c6d7e Memperbaiki warna tombol
# a3f2c1d Inisialisasi proyek
```

> **Catatan:** Tidak perlu menjalankan `git init` setelah `git clone` — koneksi ke repositori GitHub sudah otomatis terkonfigurasi.

---

### 3. Memperbarui Kode Lokal dari GitHub (`git pull`)

Ketika kamu bekerja dalam tim, anggota tim lain mungkin telah mengirimkan perubahan baru ke GitHub. Perintah `git pull` mengambil perubahan tersebut dari GitHub dan menggabungkannya ke branch lokalmu.

```bash
git pull origin main
# Output (jika ada pembaruan):
# remote: Enumerating objects: 4, done.
# Updating c7d8e9f..e9f0a1b
# Fast-forward
#  css/style.css | 6 +++---
#  1 file changed, 3 insertions(+), 3 deletions(-)

# Output (jika sudah terkini):
# Already up to date.
```

Setelah `-u` ditetapkan sebelumnya, perintah pull cukup:

```bash
git pull
```

**Kapan perlu menjalankan `git pull`:**

- Sebelum mulai mengerjakan sesuatu di pagi hari, untuk memastikan kamu bekerja pada versi terbaru.
- Sebelum melakukan `git push`, untuk menghindari konflik dengan perubahan yang sudah dikirimkan orang lain.

**Alur kerja harian yang direkomendasikan:**

```bash
# Awal hari kerja
git pull                          # ambil pembaruan terbaru dari GitHub

# ... kerjakan perubahan ...

git add .
git commit -m "Deskripsi perubahan"
git push                          # kirim hasil kerja ke GitHub
```

---

### 4. Fork — Menyalin Repositori Orang Lain ke Akunmu

**Fork** adalah fitur GitHub (bukan perintah Git di terminal) yang menyalin sebuah repositori milik orang lain ke dalam akunmu sendiri. Hasil fork adalah repositori yang sepenuhnya independen — kamu bebas mengubahnya tanpa memengaruhi repositori aslinya.

**Kapan Fork digunakan:**

- Saat ingin berkontribusi pada proyek open source yang tidak kamu miliki.
- Saat ingin mempelajari sebuah proyek dengan cara mencoba-coba tanpa merusak yang asli.

**Cara melakukan Fork:**

1. Buka repositori yang ingin kamu fork di GitHub.
2. Klik tombol **Fork** di pojok kanan atas halaman repositori.
3. GitHub akan membuat salinan repositori tersebut di akunmu, misalnya `github.com/username-kamu/nama-repo-asli`.

---

### 5. Alur Kontribusi: Fork, Clone, Push, Pull Request

Inilah alur kerja standar saat berkontribusi pada proyek milik orang lain atau proyek tim di GitHub:

```
1. Fork repositori asli ke akunmu
2. Clone fork tersebut ke komputermu
3. Buat branch baru untuk perubahanmu
4. Lakukan perubahan dan commit
5. Push branch ke fork di akunmu
6. Buka Pull Request ke repositori asli
```

**Langkah-langkah lengkap:**

```bash
# Langkah 2: Clone fork milikmu ke komputer
git clone https://github.com/username-kamu/nama-repo-asli.git
cd nama-repo-asli

# Langkah 3: Buat branch baru untuk perubahan yang akan dilakukan
git switch -c perbaikan-typo-readme

# Langkah 4: Lakukan perubahan, misalnya memperbaiki README
# ... edit file README.md ...
git add README.md
git commit -m "Memperbaiki kesalahan pengetikan di README"

# Langkah 5: Push branch ke fork di akunmu
git push origin perbaikan-typo-readme
```

**Langkah 6 — Membuat Pull Request:**

1. Buka halaman fork repositorimu di GitHub.
2. GitHub akan menampilkan notifikasi bahwa branch baru sudah di-push. Klik tombol **Compare & pull request**.
3. Isi judul dan deskripsi Pull Request dengan jelas: apa yang diubah dan mengapa.
4. Klik **Create pull request**.

Pemilik repositori asli akan menerima notifikasi, meninjau perubahanmu, dan memutuskan apakah akan menerimanya (**Merge**) atau memberikan masukan untuk diperbaiki lagi.

**Ilustrasi alur:**

```
[Repo Asli: pemilik/proyek]
        ↓ Fork
[Fork: username-kamu/proyek]
        ↓ Clone
[Komputer Lokal]
        ↓ Push (branch baru)
[Fork: username-kamu/proyek]
        ↓ Pull Request
[Repo Asli: pemilik/proyek]
```

---

### 6. Simulasi Sesi Kerja Lengkap

Berikut adalah simulasi alur kerja lengkap dari push pertama hingga kolaborasi tim:

```bash
# === SKENARIO: Menambahkan fitur baru dan mengirimnya ke GitHub ===

# 1. Pastikan kode lokal sudah terkini
git pull
# Already up to date.

# 2. Buat branch untuk fitur baru
git switch -c fitur-halaman-galeri

# 3. Kerjakan fitur
touch galeri.html
git add galeri.html
git commit -m "Menambahkan struktur halaman galeri"

# 4. Kirim branch ke GitHub
git push origin fitur-halaman-galeri
# Output:
# To https://github.com/username-kamu/belajar-frontend.git
#  * [new branch]  fitur-halaman-galeri -> fitur-halaman-galeri

# 5. Buka GitHub → buat Pull Request dari fitur-halaman-galeri ke main
# (dilakukan di antarmuka web GitHub)

# 6. Setelah Pull Request di-merge oleh reviewer,
#    perbarui branch main lokal
git switch main
git pull
# Updating c7d8e9f..f1a2b3c
# Fast-forward
#  galeri.html | 0
#  1 file changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 galeri.html

# 7. Hapus branch yang sudah tidak diperlukan
git branch -d fitur-halaman-galeri
```

---

### Kesimpulan

Alur kerja GitHub yang telah dipelajari di modul ini adalah inti dari cara kerja pengembang web profesional setiap harinya. Dengan menguasai `push`, `pull`, `clone`, `fork`, dan Pull Request, kamu siap untuk berkolaborasi dalam proyek tim maupun berkontribusi pada proyek open source.

**Ringkasan Alur dan Perintah:**

| Perintah / Fitur | Arah | Fungsi |
|---|---|---|
| `git push` | Lokal → GitHub | Mengirim commit ke GitHub |
| `git pull` | GitHub → Lokal | Mengambil dan menggabungkan pembaruan dari GitHub |
| `git clone` | GitHub → Lokal | Mengunduh repositori secara lengkap (pertama kali) |
| `git remote add origin URL` | — | Mendaftarkan alamat repositori GitHub ke proyek lokal |
| Fork | GitHub → GitHub | Menyalin repositori orang lain ke akunmu di GitHub |
| Pull Request (PR) | Fork → Repo Asli | Mengajukan perubahan untuk ditinjau dan digabungkan |
