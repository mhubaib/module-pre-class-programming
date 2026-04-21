# Bab 67: Git & Github Best Practice

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Mampu menulis pesan *commit* yang profesional dan bermakna.
- Memahami pentingnya penggunaan `.gitignore`.
- Mengikuti standar industri dalam penamaan *branch* dan struktur proyek.

## 📚 Materi Utama

Menjadi programmer bukan hanya soal membuat kode jalan, tapi juga soal bekerja dengan rapi. Berikut adalah panduan agar kamu dipandang sebagai programmer yang profesional oleh tim lain.

### 1. Aturan Pesan Commit yang Baik

Jangan menulis pesan commit yang malas seperti:
- `git commit -m "update"` ❌
- `git commit -m "fix bug"` ❌ (Bug yang mana?)
- `git commit -m "asdjaslkd"` ❌ (Ini sangat buruk!)

Gunakan format **[Aksi]: [Penjelasan Singkat]**:
- `git commit -m "Feat: Menambahkan fitur tombol dark mode"` ✅
- `git commit -m "Fix: Memperbaiki warna teks yang tidak terbaca di footer"` ✅
- `git commit -m "Docs: Update tutorial cara instalasi di README"` ✅

### 2. Mengenal `.gitignore`

Ada file yang **haram** masuk ke GitHub, misalnya:
- File password atau kunci rahasia aplikasi.
- Folder instalasi raksasa (seperti `node_modules`).
- File sampah buatan sistem operasi (seperti `.DS_Store` di Mac).

Caranya: Buat file bernama `.gitignore` (depannya pakai titik), lalu ketikkan nama folder/file yang ingin disembunyikan di dalamnya. Git akan otomatis mengabaikannya seolah tidak pernah ada.

### 3. Standar Kolaborasi

1. **Satu Fitur, Satu Branch**: Jangan campur aduk fitur Login, Fitur Produk, dan Fitur Profil di satu branch yang sama. Pecahlah menjadi cabang kecil-kecil agar rapi.
2. **Jangan Commit Kode yang Masih Error**: Pastikan kodemu "jalan" sebelum difoto (di-commit). 
3. **ReadMe adalah Wajahmu**: Selalu buat file `README.md` di setiap reponu. Jelaskan proyek ini tentang apa, dan cara menjalankannya bagaimana.

**Penutup:**
Selamat! Kamu sudah menyelesaikan seluruh rangkaian modul Web Development tingkat dasar. Kamu sudah menguasai HTML (Kerangka), CSS (Wajah), JavaScript (Otak), dan Git (Mesin Waktu/Penyimpanan). 

Dunia programming sangat luas, tetaplah haus akan ilmu dan jangan berhenti berlatih!

## 💻 Latihan Praktik

[Soal atau project latihan terkait materi di atas akan ditambahkan di sini]
