# Bab 10: Git & GitHub Best Practice

## Tujuan Pembelajaran

- Mampu menulis pesan _commit_ yang profesional dan bermakna.
- Memahami fungsi dan cara penggunaan `.gitignore`.
- Mengikuti standar industri dalam penamaan _branch_, penulisan commit, dan struktur proyek.

---

## Materi Utama

Menguasai perintah-perintah Git secara teknis adalah langkah pertama. Langkah berikutnya adalah menggunakannya dengan cara yang rapi, konsisten, dan mudah dipahami oleh orang lain. Inilah yang membedakan seorang pemula dari seorang pengembang yang siap bekerja dalam tim profesional.

---

### 1. Menulis Pesan Commit yang Baik

Pesan commit adalah catatan permanen yang menjelaskan perubahan apa yang dilakukan dan mengapa. Pesan yang buruk membuat riwayat proyek sulit dibaca; pesan yang baik memungkinkan siapa pun — termasuk dirimu sendiri di masa mendatang — untuk memahami konteks setiap perubahan hanya dari membaca satu baris.

**Contoh pesan commit yang kurang baik:**

```bash
git commit -m "update"           # Tidak menjelaskan apa yang diperbarui
git commit -m "fix bug"          # Bug yang mana? Di bagian mana?
git commit -m "coba-coba"        # Tidak bermakna sama sekali
```

**Format yang direkomendasikan — Conventional Commits:**

Format `[Tipe]: [Deskripsi singkat dalam kalimat aktif]` adalah standar yang banyak digunakan di industri:

```bash
git commit -m "feat: menambahkan fitur tombol dark mode"
git commit -m "fix: memperbaiki warna teks yang tidak terbaca di footer"
git commit -m "docs: memperbarui panduan instalasi di README"
git commit -m "style: merapikan indentasi dan spasi pada style.css"
git commit -m "refactor: menyederhanakan fungsi validasi form"
git commit -m "chore: menambahkan node_modules ke .gitignore"
```

**Tipe commit yang umum digunakan:**

| Tipe       | Digunakan untuk                                             |
| ---------- | ----------------------------------------------------------- |
| `feat`     | Menambahkan fitur baru                                      |
| `fix`      | Memperbaiki bug                                             |
| `docs`     | Perubahan pada dokumentasi (README, komentar kode)          |
| `style`    | Perubahan format kode yang tidak memengaruhi fungsionalitas |
| `refactor` | Perbaikan struktur kode tanpa mengubah perilakunya          |
| `chore`    | Pembaruan konfigurasi, dependensi, atau alat bantu          |

**Panduan tambahan untuk pesan commit yang baik:**

- Gunakan kalimat aktif: "Menambahkan..." bukan "Sudah ditambahkan..."
- Batasi baris pertama hingga sekitar 72 karakter.
- Jika perubahan kompleks, tambahkan penjelasan lebih panjang setelah baris pertama:

```bash
git commit -m "fix: memperbaiki validasi form pendaftaran

Sebelumnya, form dapat dikirim meskipun kolom email dikosongkan.
Ditambahkan pengecekan panjang minimal dan format email sebelum
pengiriman diizinkan."
```

---

### 2. Menggunakan `.gitignore`

Tidak semua file dalam folder proyek perlu atau boleh diunggah ke GitHub. File seperti konfigurasi rahasia, folder dependensi yang besar, atau file sementara buatan sistem operasi sebaiknya tidak masuk ke repositori.

**Jenis file yang umum diabaikan:**

| Jenis File           | Contoh                                   | Alasan                                                             |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------ |
| Konfigurasi rahasia  | `.env`, `secrets.json`                   | Berisi kata sandi atau kunci API yang tidak boleh tersebar         |
| Folder dependensi    | `node_modules/`                          | Berukuran sangat besar dan dapat diunduh ulang dari `package.json` |
| File sistem operasi  | `.DS_Store` (Mac), `Thumbs.db` (Windows) | File sampah yang tidak relevan dengan proyek                       |
| File hasil kompilasi | `dist/`, `build/`                        | Dapat dibuat ulang dari kode sumber                                |
| Log aplikasi         | `*.log`                                  | File log tidak perlu dilacak oleh Git                              |

**Cara membuat `.gitignore`:**

Buat file bernama `.gitignore` di direktori utama proyek, lalu isi dengan daftar file atau folder yang ingin diabaikan:

```bash
touch .gitignore
```

```
# Isi file .gitignore

# Folder dependensi Node.js
node_modules/

# File konfigurasi rahasia
.env
.env.local

# File sistem operasi
.DS_Store
Thumbs.db

# Folder hasil build
dist/
build/

# File log
*.log
npm-debug.log*
```

Setelah `.gitignore` dibuat, Git akan otomatis mengabaikan file dan folder yang terdaftar di dalamnya:

```bash
# Verifikasi bahwa node_modules tidak terlacak
git status
# Output:
# Untracked files:
#   .gitignore
#   index.html
#   css/
# (node_modules tidak muncul di sini meskipun foldernya ada)

git add .gitignore
git commit -m "chore: menambahkan konfigurasi .gitignore"
```

> **Catatan:** Jika sebuah file sudah terlanjur di-commit sebelum ditambahkan ke `.gitignore`, kamu perlu menghapusnya dari pelacakan Git secara eksplisit dengan `git rm --cached nama-file` terlebih dahulu.

---

### 3. Standar Penamaan Branch

Penamaan branch yang konsisten membuat daftar branch lebih mudah dibaca dan dipahami, terutama dalam tim yang besar.

**Format yang direkomendasikan:**

```
[tipe]/[deskripsi-singkat-dengan-tanda-hubung]
```

**Contoh:**

```bash
# Branch untuk fitur baru
git switch -c feat/halaman-login
git switch -c feat/dark-mode
git switch -c feat/filter-produk

# Branch untuk perbaikan bug
git switch -c fix/tombol-submit-tidak-merespons
git switch -c fix/layout-rusak-di-mobile

# Branch untuk pembaruan dokumentasi
git switch -c docs/update-readme-instalasi
```

**Hal yang sebaiknya dihindari dalam penamaan branch:**

| Kurang Baik                 | Lebih Baik                             |
| --------------------------- | -------------------------------------- |
| `git switch -c cobacoba`    | `git switch -c feat/halaman-galeri`    |
| `git switch -c branch-baru` | `git switch -c fix/navigasi-mobile`    |
| `git switch -c punya-budi`  | `git switch -c feat/keranjang-belanja` |

---

### 4. Standar Kolaborasi Tim

**Satu branch untuk satu tujuan:**

Setiap branch sebaiknya hanya mengerjakan satu fitur atau satu perbaikan. Mencampur beberapa perubahan yang tidak berkaitan dalam satu branch mempersulit proses peninjauan kode dan meningkatkan risiko konflik.

```
# Baik: setiap branch punya satu tujuan yang jelas
feat/halaman-login
feat/halaman-profil
fix/validasi-form

# Kurang baik: satu branch untuk banyak hal sekaligus
branch-baru-semua-fitur
```

**Commit hanya kode yang berfungsi:**

Sebelum melakukan commit, pastikan kode tidak mengandung error yang membuat halaman tidak dapat dimuat. Commit yang berisi kode rusak menyulitkan rekan tim yang ingin menggunakan riwayat tersebut sebagai acuan.

**Selalu buat file `README.md`:**

`README.md` adalah halaman pertama yang dilihat orang saat mengunjungi repositorimu. File ini sebaiknya memuat:

```markdown
# Nama Proyek

Deskripsi singkat tentang proyek ini dan tujuannya.

## Cara Menjalankan

1. Clone repositori ini
2. Buka file `index.html` di browser

## Teknologi yang Digunakan

- HTML5
- CSS3 (Flexbox & Grid)
- JavaScript (ES6)

## Kontributor

- Nama Kamu (github.com/username-kamu)
```

**Tinjau perubahan sebelum push:**

Sebelum mengirim kode ke GitHub, biasakan untuk memeriksa apa yang akan dikirimkan:

```bash
# Lihat semua commit yang belum dikirimkan
git log origin/main..HEAD --oneline

# Lihat detail perubahan yang akan dikirimkan
git diff origin/main
```

---

### 5. Simulasi Alur Kerja Profesional Lengkap

Berikut adalah simulasi alur kerja yang menerapkan seluruh praktik terbaik dari modul ini:

```bash
# === Awal sesi kerja ===
git switch main
git pull                          # selalu mulai dengan kode terbaru

# === Buat branch untuk fitur baru ===
git switch -c feat/halaman-kontak

# === Kerjakan fitur ===
touch kontak.html
# ... isi kontak.html dengan kode yang berfungsi ...
touch css/kontak.css

# === Commit secara bertahap dengan pesan yang bermakna ===
git add kontak.html
git commit -m "feat: menambahkan struktur HTML halaman kontak"

git add css/kontak.css
git commit -m "feat: menambahkan gaya CSS untuk halaman kontak"

# === Verifikasi sebelum push ===
git log --oneline -3
# a1b2c3d (HEAD -> feat/halaman-kontak) feat: menambahkan gaya CSS untuk halaman kontak
# 9e8f7a6 feat: menambahkan struktur HTML halaman kontak
# 7c6d5e4 (origin/main, main) fix: memperbaiki layout footer

git diff origin/main --stat
# kontak.html    | 32 ++++++++++++++++++++++++++++++++
# css/kontak.css | 18 ++++++++++++++++++
# 2 files changed, 50 insertions(+)

# === Kirim ke GitHub dan buat Pull Request ===
git push origin feat/halaman-kontak

# (buka GitHub → buat Pull Request → minta review dari rekan tim)

# === Setelah Pull Request di-merge ===
git switch main
git pull
git branch -d feat/halaman-kontak

git log --oneline -3
# b2c3d4e (HEAD -> main) feat: menambahkan gaya CSS untuk halaman kontak
# a1b2c3d feat: menambahkan struktur HTML halaman kontak
# 7c6d5e4 fix: memperbaiki layout footer
```

---

### Penutup

Selamat! Kamu telah menyelesaikan hampir seluruh rangkaian modul pengembangan web tingkat dasar. Perjalanan yang telah kamu tempuh mencakup:

- **HTML** — Membangun struktur dan kerangka halaman web.
- **CSS** — Mendesain tampilan, tata letak, dan responsivitas.
- **JavaScript** — Menambahkan logika dan interaktivitas.
- **Git & GitHub** — Mengelola versi kode dan bekerja secara kolaboratif.

Penguasaan keempat fondasi ini adalah modal yang sangat kuat untuk melanjutkan ke tahap berikutnya — menambahkan logika dan interaktivitas pada halaman website menggunakan bahasa yang sangat populer — Javascript.

Dunia pengembangan web terus berkembang. Tetaplah berlatih, terus membangun proyek nyata, dan jangan ragu untuk belajar dari komunitas.

**Ringkasan Best Practice:**

| Aspek           | Praktik yang Direkomendasikan                                              |
| --------------- | -------------------------------------------------------------------------- |
| Pesan commit    | Gunakan format `[tipe]: [deskripsi]` yang jelas dan spesifik               |
| `.gitignore`    | Sertakan di setiap proyek; abaikan `node_modules`, `.env`, dan file sistem |
| Penamaan branch | Gunakan format `[tipe]/[deskripsi]`, misalnya `feat/halaman-login`         |
| Ukuran branch   | Satu branch untuk satu fitur atau perbaikan                                |
| Kualitas commit | Hanya commit kode yang berfungsi                                           |
| Dokumentasi     | Selalu buat `README.md` yang menjelaskan proyek secara ringkas             |
| Sebelum push    | Jalankan `git pull` terlebih dahulu untuk menghindari konflik              |
