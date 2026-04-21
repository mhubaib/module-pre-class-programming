# Bab 48: String & Number Built-in Function

## Tujuan Pembelajaran
- Menguasai fungsi-fungsi pabrik bawaan (*Built-in Function*) pemroses huruf Teks (String).
- Memecah pisaunya fungsi Teks untuk mencari kata, merubah pelafalan BESAR/kecil huruf.
- Menguasai fungsi-fungsi bawaan pengerem pembungkusan Angka Matematik (Number).
- Mampu mengubah bulatan koma liar dengan gampang menggunakan fungsi mutakhir.

## Materi Utama

Sama seperti Array List panjang yang memiliki alat bengkel bengkel mesin bawaan gratis (seperti `.push()` dan `.length` pada Bab 44), tipe dasar murni seperti **String (Teks Huruf)** dan **Number (Angka Hitung)** juga diam-diam dibekali kotak harta utilitas persenjataannya tersendiri oleh Dewa perancang JavaScript asalnya.

### 1. Kotak Perkakas Canggih Menggiling String (Teks Algoritma)

Sangat penting menguasai properti si pengolah teks huruf, karena seluruh pergerakan input ketikan form pendaftaran kolom website pengunjung pada antarmuka nyata terkirim ke server sebagai wujud teks (*String*).

**A. Merubah Casing (Huruf Besaran/Kecilan)**
- `.toUpperCase()` : Menggaruk paksa seluruh isi teks menjadi huruf BALOK RAKSASA murni tanpa sisa.
- `.toLowerCase()` : Menyetrika seluruh kalimat menjadi kumpulan huruf cebol tulisan halus kecil beriringan (Biasanya disuruh dipakai diam-diam menyembunyikan input alamat email validasi dari penonton ke database agar tak repot dicek case-nya).

```javascript
let sapaanTeks = "Hai Apa Kabar kawan!";

console.log(sapaanTeks.toUpperCase()); // Tercetak besar gila: "HAI APA KABAR KAWAN!"
console.log(sapaanTeks.toLowerCase()); // Tercetak murni gembrot cebol: "hai apa kabar kawan!"
```

**B. Alat Mata-Mata Teks Pencari Rahasia**
- `.includes("kata")` : Alat mesin pelacak apakah teks tersebut bersembunyi berdiam menyelinap di dalam rawa lautan kalimat besar? Hasilnya mesin meretur balik cuman kepastian mutlak `true / false`.
- `.indexOf("huruf")` : Lebih canggih, dia bukan sekedar bilang ya/tidak.. tapi ia menunjuk letak pasti huruf itu kepergok ditemukan pertama kali nongkrong diam di urutan indeks posisi ke-berapa secara tepat.

```javascript
let statusBerita = "Harga Beras Melonjak Kuat Terus";

// Mengecek mendeteksi hoax berita apakah berisi info cuaca?
let apakahAdaBeras = statusBerita.includes("Beras"); // Menangkap hasil kepastian: true
let intaiKataMelonjak = statusBerita.indexOf("Melonjak"); // Memergoki mendapati kata ini nongkol sembunyi perdana di urutan indeks karakter ke- 12
```

**C. Pemotong Mengiris Kue Bolu Teks**
- `.slice(mulai_index, akhir_index)` : Berfunsi memotong mengiris bagian serpihan utuh tengah teks lantas mengumpulkannya utuh mengambil untuk diekstrak jadi tulisan baru tunggal.
```javascript
let buahKeranjang = "Mangga Apel Anggur";
let ekstrakBagi = buahKeranjang.slice(7, 11); 
console.log(ekstrakBagi); // Memotong sukses merebus keluar memunculkan irisan: "Apel"
```

### 2. Kotak Alat Pertukangan Mengasah Angka (Number Object Math)

Karena dunia bisnis hitungan e-commerce selalu penuh dengan keruwetan angka desimal pajak yang berekor panjang (seperti `14.502932` pecahan rupialnya), alat JS dibekali pengasah angkanya.

**A. Memutus Tali Ekor Desimal**
- `.toFixed(jumlahDibelakangKoma)` : Fungsi membulatkan mengunci mengekseskui memenggal koma tak bernilai mengikatnya mutlak sisa sekian angka belakang di ekornya secara otomatis merubah wujudnya dilempar tertuang jadi cetakan String teks untuk dipamer tampilkan rapih dicetak layar *Invoice*.

```javascript
let hargaPajakDiskon = 50000.41928421;

// Potong dan Rapikan mutlak cuma sisakan maksimal 2 buntut ekor desimal yang waras 
let hargaFinalNota = hargaPajakDiskon.toFixed(2);
console.log(hargaFinalNota); // Terminal mutlak diam menyorakkan sisa bulatan ringkas : "50000.42"
```

**B. Pengkonversi String Tipuan Jadi Angka Aseli**
Sering sebuah kolom harga website penonton tak disengaja dibungkus terketik oleh format wujud palsu `String` (Misal isi data text dari file JSON luar: `"150"` pakaikutip). Angka teks itu haram dan di tolak jika kamu masukan mesin perjumlahan, ia akan menggeser menggencet baris koding lain (Jadi `"150" + 2` nanti error memuntahkan baris teks nempel `"1502"` kacau bukannya `152`). 
Obatnya satu sebelum dicampur olah mesin aritmatika: Dicuci murni dileburkan ditranseksual ganti dikembalikan kastanya ke tipe Number aselinya pake mesin obeng `parseInt` atau `parseFloat`.

- `parseInt("angka_teks")` : Melucuti teks kembali jadi hitungan Angka Bulat Mutlak.
- `parseFloat("angka_desimal_teks")` : Melucuti menyalakan teks jadi perhitungan Angka Koma Desimal pecahan.

```javascript
let tagihanMasukTeksTersasar = "500";
let biayaAdminPasti = 250;

// Agar ga error jadi "500250", kita sucikan kembali tagihan jadi kastanya Number mampat bulat dulu:
let tagihanSuciDibersihkan = parseInt(tagihanMasukTeksTersasar);
let totalTagihanGakErrorLagi = tagihanSuciDibersihkan + biayaAdminPasti; // Kini hasilnya sukses total berwujud luhur: 750 murni.
```
