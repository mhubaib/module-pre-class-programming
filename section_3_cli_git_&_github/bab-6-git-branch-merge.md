# Bab 6: Git Branch & Merge

## Tujuan Pembelajaran

- Memahami konsep *Branching* (percabangan) sebagai ruang kerja paralel yang aman.
- Mampu membuat, berpindah, dan menghapus branch menggunakan `git branch` dan `git switch`.
- Mampu menggabungkan perubahan dari branch fitur ke branch utama menggunakan `git merge`.
- Memahami konsep *Merge Conflict* dan cara menanganinya.

---

## Materi Utama

Bayangkan kamu sedang mengembangkan website toko online yang sudah berjalan dan digunakan oleh pelanggan. Tiba-tiba, kamu ingin mencoba menambahkan fitur baru, misalnya "Fitur Diskon Ramadhan".

Jika kamu langsung mengedit kode utama dan ternyata fitur tersebut mengandung bug, seluruh website bisa terganggu. Untuk mencegah hal ini, Git menyediakan mekanisme yang disebut **Branching**.

---

### 1. Apa itu Branch?

**Branch (cabang)** adalah jalur pengembangan yang terpisah dari jalur utama. Setiap proyek Git secara otomatis memiliki satu branch utama yang biasanya bernama `main` atau `master`.

Dengan membuat branch baru, kamu mendapatkan salinan kode yang sepenuhnya independen. Kamu bebas bereksperimen, menambahkan fitur, atau memperbaiki bug di sana. Jika hasilnya tidak memuaskan, branch tersebut dapat dihapus tanpa memengaruhi kode utama sama sekali.

**Analogi Penulisan Novel:**

- **Branch `main`** adalah naskah asli novelmu yang sudah rapi.
- **Branch baru** adalah kamu memfotokopi beberapa halaman terakhir naskah tersebut, lalu mencoba-coba ide baru di salinannya.
- Jika ide tersebut berhasil, kamu menyalinnya ke naskah asli (**Merge**).
- Jika tidak berhasil, kamu membuang salinan itu tanpa merusak naskah aslimu.

**Ilustrasi alur branch:**

```
main:         A --- B --- C
                           \
fitur-diskon:               D --- E
```

Commit `D` dan `E` hanya ada di branch `fitur-diskon` dan tidak memengaruhi branch `main` sama sekali.

---

### 2. Perintah Dasar Branching

#### A. Melihat Daftar Branch

```bash
git branch
# Output:
# * main          ← tanda bintang menunjukkan branch yang sedang aktif
#   fitur-diskon
#   perbaikan-navbar
```

#### B. Membuat Branch Baru

```bash
git branch fitur-diskon
```

Perintah ini hanya **membuat** branch baru tanpa berpindah ke sana. Kamu masih berada di branch semula.

#### C. Berpindah Branch

```bash
# Cara modern (direkomendasikan)
git switch fitur-diskon

# Cara lama (masih berfungsi)
git checkout fitur-diskon
```

Setelah berpindah, verifikasi posisi branch aktifmu:

```bash
git branch
# Output:
#   main
# * fitur-diskon   ← sekarang kamu berada di sini
```

#### D. Membuat Branch Baru dan Langsung Berpindah

Cara yang paling umum digunakan karena lebih ringkas:

```bash
# Cara modern
git switch -c fitur-pembayaran

# Cara lama
git checkout -b fitur-pembayaran
```

#### E. Menghapus Branch

Setelah sebuah branch selesai digunakan dan sudah digabungkan ke `main`, branch tersebut sebaiknya dihapus agar daftar branch tetap rapi.

```bash
# Menghapus branch yang sudah di-merge (aman)
git branch -d fitur-diskon

# Menghapus branch secara paksa meskipun belum di-merge
git branch -D fitur-diskon
```

**Contoh sesi lengkap membuat dan bekerja di branch baru:**

```bash
# 1. Pastikan kamu berada di branch main terlebih dahulu
git switch main

# 2. Buat branch baru dan langsung pindah ke sana
git switch -c fitur-diskon

# 3. Verifikasi posisi branch aktif
git branch
#   main
# * fitur-diskon

# 4. Buat perubahan dan catat hasilnya
touch diskon.html
git add diskon.html
git commit -m "Menambahkan halaman promo diskon Ramadhan"

# 5. Lakukan pengembangan lebih lanjut
git add .
git commit -m "Menambahkan logika kalkulasi harga setelah diskon"
```

---

### 3. Menggabungkan Branch (`git merge`)

Setelah fitur di branch selesai dikembangkan dan sudah diuji, langkah berikutnya adalah menggabungkannya ke branch utama.

**Langkah-langkah merge:**

```bash
# 1. Pindah ke branch tujuan (branch yang akan menerima perubahan)
git switch main

# 2. Gabungkan branch fitur ke dalam main
git merge fitur-diskon
# Output:
# Updating c3d4e5f..e7f8a9b
# Fast-forward
#  diskon.html | 0
#  1 file changed, 0 insertions(+), 0 deletions(-)
#  create mode 100644 diskon.html

# 3. Verifikasi bahwa perubahan sudah masuk
git log --oneline -4
# e7f8a9b (HEAD -> main, fitur-diskon) Menambahkan logika kalkulasi harga setelah diskon
# d6e7f8a Menambahkan halaman promo diskon Ramadhan
# c3d4e5f Memperbarui tampilan header utama
# b2c3d4e Inisialisasi proyek

# 4. Hapus branch yang sudah tidak diperlukan
git branch -d fitur-diskon
# Output: Deleted branch fitur-diskon (was e7f8a9b).
```

**Ilustrasi setelah merge:**

```
main:         A --- B --- C --- D --- E
                               ↑
                        hasil merge dari fitur-diskon
```

---

### 4. Merge Conflict dan Cara Mengatasinya

**Merge Conflict** terjadi ketika dua branch mengubah bagian yang **sama** dari sebuah file, sehingga Git tidak dapat menentukan secara otomatis versi mana yang harus dipertahankan. Git akan meminta kamu untuk menyelesaikannya secara manual.

**Contoh situasi:**

Di branch `main`, baris ke-5 pada `style.css` berisi:
```css
background-color: white;
```

Di branch `fitur-diskon`, baris yang sama diubah menjadi:
```css
background-color: #ffe0b2;
```

Ketika kedua branch ini di-merge, Git akan menandai konflik tersebut di dalam file:

```css
<<<<<<< HEAD
background-color: white;        ← versi dari branch main
=======
background-color: #ffe0b2;      ← versi dari branch fitur-diskon
>>>>>>> fitur-diskon
```

**Cara menyelesaikan Merge Conflict:**

1. Buka file yang berkonflik di editor teks.
2. Tentukan versi mana yang ingin dipertahankan (atau gabungkan keduanya jika perlu).
3. Hapus seluruh tanda penanda konflik (`<<<<<<<`, `=======`, `>>>>>>>`).
4. Simpan file, lalu catat hasilnya:

```bash
git add style.css
git commit -m "Menyelesaikan konflik pada warna latar di style.css"
```

> **Catatan:** Merge Conflict terlihat menakutkan pada awalnya, namun sebenarnya hanya meminta kamu untuk membuat keputusan: versi mana yang benar. Dengan membaca kedua versi dan memahami konteksnya, konflik ini biasanya dapat diselesaikan dalam hitungan menit.

---

### 5. Simulasi Sesi Kerja Lengkap

Berikut adalah simulasi alur kerja pengembangan fitur baru dari awal hingga selesai menggunakan branch:

```bash
# --- Kondisi awal: berada di branch main ---
git branch
# * main

git log --oneline -2
# c3d4e5f (HEAD -> main) Memperbarui tampilan header
# b2c3d4e Inisialisasi proyek

# --- Mulai mengerjakan fitur baru ---
git switch -c fitur-kontak
git branch
#   main
# * fitur-kontak

touch kontak.html
git add kontak.html
git commit -m "Menambahkan halaman kontak"

# Lanjutkan pengembangan
git add css/style.css
git commit -m "Menambahkan gaya untuk halaman kontak"

# --- Fitur selesai, gabungkan ke main ---
git switch main
git merge fitur-kontak
# Fast-forward
#  kontak.html   | 0
#  css/style.css | 12 ++++++++++++
#  2 files changed, 12 insertions(+)

# --- Verifikasi dan bersihkan ---
git log --oneline -4
# e9f0a1b (HEAD -> main, fitur-kontak) Menambahkan gaya untuk halaman kontak
# d8e9f0a Menambahkan halaman kontak
# c3d4e5f Memperbarui tampilan header
# b2c3d4e Inisialisasi proyek

git branch -d fitur-kontak
# Deleted branch fitur-kontak (was e9f0a1b).

git branch
# * main
```

---

### Kesimpulan

Branching adalah salah satu fitur terpenting Git yang memungkinkan pengembangan fitur baru, perbaikan bug, dan eksperimen dilakukan secara terisolasi tanpa risiko merusak kode yang sudah berjalan. Dengan membiasakan diri bekerja menggunakan branch, kamu menerapkan alur kerja yang sama dengan yang digunakan oleh tim pengembang profesional di seluruh dunia.

**Ringkasan Perintah:**

| Perintah | Fungsi |
|---|---|
| `git branch` | Menampilkan daftar seluruh branch |
| `git branch nama` | Membuat branch baru |
| `git switch nama` | Berpindah ke branch yang disebutkan |
| `git switch -c nama` | Membuat branch baru dan langsung berpindah ke sana |
| `git merge nama` | Menggabungkan branch yang disebutkan ke branch aktif saat ini |
| `git branch -d nama` | Menghapus branch yang sudah di-merge |
| `git branch -D nama` | Menghapus branch secara paksa |
