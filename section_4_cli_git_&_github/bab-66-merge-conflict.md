# Bab 66: Merge Conflict

> Modul ini disusun khusus untuk kamu yang baru mulai belajar programming (Front-End web development) setelah lulus SMA/sederajat. Semangat!

## 🎯 Tujuan Pembelajaran
- Memahami penyebab terjadinya *Merge Conflict*.
- Mampu membaca tanda konflik di dalam file kode.
- Mampu menyelesaikan konflik secara aman menggunakan Visual Studio Code.

## 📚 Materi Utama

Terkadang, hidup tidak selalu mulus. Di dalam Git, ada sebuah momen horor bagi pemula yang disebut **Merge Conflict**. 

### 1. Mengapa Terjadi Konflik?

Konflik terjadi ketika Git merasa bingung. Misalnya:
1. Kamu mengubah baris ke-10 di file `index.html` menjadi warna Merah.
2. Temanmu (di komputer berbeda) mengubah baris ke-10 yang sama menjadi warna Biru.
3. Saat kalian ingin menyatukan kodenya, Git akan berteriak: *"Waduh! Baris ini mau jadi Merah atau Biru nih? Saya gak berani milih, tolong putuskan sendiri!"*

### 2. Cara Mengenali Konflik

Saat terjadi konflik, file-mu akan terlihat berantakan dengan simbol aneh seperti ini:

```html
<<<<<<< HEAD
<h1>Warna Merah Milikmu</h1>
=======
<h1>Warna Biru Milik Temanmu</h1>
>>>>>>> branch-teman
```
- **HEAD (Current Change)**: Kode yang ada di tanganmu sekarang.
- **=======**: Garis pembatas (seperti wasit).
- **Incoming Change**: Kode yang baru saja datang dari luar/branch lain yang menabrak kodemu.

### 3. Cara Menyelesaikan (Resolve)

Jangan panik! Gunakan Visual Studio Code. VS Code akan memberikan tombol otomatis di atas teks tersebut:
- **Accept Current Change**: Pilih kodemu sendiri.
- **Accept Incoming Change**: Pilih kode lawan/temanmu.
- **Accept Both Changes**: Ambil dua-duanya.

Setelah kamu pilih salah satu, hapus simbol-simbol aneh (`<<<`, `===`, `>>>`) tersebut, simpan filenya, lalu lakukan proses **Add** dan **Commit** ulang. 

**Tips Terhindar Konflik:**
Sesering mungkinlah melakukan `git pull` sebelum mulai mengetik kode baru, agar kodemu selalu sinkron dengan apa yang dikerjakan temanmu. Mencegah lebih baik daripada mengobati!

## 💻 Latihan Praktik

[Soal atau project latihan terkait materi di atas akan ditambahkan di sini]
