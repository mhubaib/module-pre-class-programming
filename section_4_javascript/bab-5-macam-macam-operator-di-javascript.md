# Bab 40: Macam-macam Operator di JavaScript

## Tujuan Pembelajaran
- Menggunakan Operator Aritmatika untuk operasi perhitungan matematis.
- Membedakan perbedaan operator kembar Comparison: `==` dengan ketatnya aturan `===`.
- Memahami alur kerja ringkas lewat fungsi Assignment dan Operator Logika (Logical Operators).

## Materi Utama

Komputer sejatinya adalah alat penghitung (komputasi). Supaya bisa menghitung angka atau teks dari tipe data yang sudah kita deklarasikan, JavaScript memerlukan apa yang disebut sebagai **Operator**, yaitu simbol khusus yang memberikan instruksi pada komputer untuk melakukan pengolahan manipulasi.

Kita akan fokus pada empat keluarga besar tipe pembagian Operator.

### 1. Operator Aritmatika (Kalkulator Matematis)

Dipakai murni melakukan tugas penjumlahan dasar pelajaran matematika yang melibatkan pengolahan nilai angka Number.

- `+` (Penjumlahan) : `5 + 2` menjadi `7`
- `-` (Pengurangan) : `5 - 2` menjadi `3`
- `*` (Perkalian) : `5 * 2` menjadi `10`
- `/` (Pembagian) : `10 / 2` menjadi `5`
- `%` (Modulus / Sisa Hasil Bagi) : Mengembalikan nilai ampas yang tak bisa dibagikan habis (Contoh `10 % 3` bersisa hasil jidat adalah `1`. Karena 10 dibagi rata ke 3 orang dapat porsi masing-masing utuh 3, sisa roti 1 tertinggal untuk sisa lalat).

*(Operator Rahasia Increment/Tukang Tambah Cepat:)* 
Penulisan ganda `++` berfungsi instan menaikkan bilangan utuh nilai sebanyak persis 1 poin tanpa basa-basi (Paling sering dipakai buat fungsi penghitung otomatis angka looping).
```javascript
let jumlahSkor = 10;
jumlahSkor++; // Hasil sekarang mutlak menjadi 11.
// Kebalikannya: jumlahSkor--; Akan turun menjadi 10.
```

### 2. Operator Penugasan (*Assignment Operators*)

Gunanya paling mutlak untuk **menyimpan** nilai informasi data ke dalam laci perut variabel. Sangat familier karena simbol rajanya utamanya adalah **Sama Dengan (`=`)**. 

Selain mematok pengisian awal, bisa dipakai mereposisi modifikasi angka cepat di jalur pendek jalan pintas tanpa mengulang nama panjang:
- `x = y` (Memasukkan telak nilai `y` ke dalam `x`)
- `x += y` (Sama maksud aslinya nulis dengan kepanjangan logika kaku : `x = x + y`)
- `x -= y` (Jalan pintas tulisan pendek dari logika : `x = x - y`)

### 3. Operator Perbandingan (*Comparison Operators*)

Operator pembanding tugasnya melarungkan membandingkan kedua data variabel anak kiri dan anak timbangan membanding kanan. Hasil jawaban pengeluaran prosesnya murni cuma dua: Kepastian tipe Boolean utuh saja (alias `true` bila faktanya cocok benar, dan `false` bila gagal tak sinkron/melenceng keliru). 

- `>` (Lebih Tepat Besar) : `5 > 3` balasan kembalian nilai jawabannya benar valid (`true`)
- `<` (Kurang Telak Dari) : `5 < 3` bohong besar salah mutlak (`false`)
- `>=` (Lebih besar atau minimal angkanya setara persis)
- `<=` (Kurang dari atau maksimal persis)

**(PERHATIAN: Jebakan Maut `==` vs `===`)**
Pemula selalu tersesat di titik tebing kecelakaan ini seumur hidupnya pada pemrograman Web Javascript Modern!

- **Sama Dengan Biasa Longgar (`==`)**: Ia berbaik hati mentolerir perbedaan status wujud jenis tipe data kemasan asalnya, asal intinya angka huruf suaranya yang tergambar miripan sama persis.
  ```javascript
  5 == "5" // Jawabannya "TRUE"! (Satu dari trah angka number suci vs Satu lagi angka bajakan wujud huruf string kurungan teks). 
  ```

- **Sama Dengan Identik Ketat Akurat Mutlak (`===`)**: Ia tegas tanpa memandang belas kasih. Wujudnya kudu sama persis, Tipe Datanya pun kudu dari desa asal aselinya trah yang murni setara! (Dihukum wajib dipakai Best Practice Dunia Industri Software Kerja!).
  ```javascript
  5 === "5" // Jawabannya dilempar balik tegas: "FALSE". Sifatnya beda kasta Data Type! Angka Integer Suci Tak Boleh diakui teks palsu huruf ketik.
  5 === 5   // Barulah nilainya sah dibenarkan: TRUE.
  ```

Berlaku juga dengan konsep kebalikannya yakni *Tidak Sama/Berbeda Ciri-cirinya*: Pakai ketatnya hukum tanda seru kembar: `!==` dipaksa paten.

### 4. Operator Logika Silsilah (*Logical Operators*)

Dipakai menggabungkan dua persimpangan hasil pengecek Operator Logika Comparison (Boolean) diatas menuju jalur satu pintu nasib akhir kepastian kemudi saklar aliran listrik aplikasinya:
- **AND (`&&`)**: Jawaban akhirnya bernilai True HANYA jika semua kondisi kiri dan kanan syarat mutlaknya komplit ikut True juga. (Jika satu pintu gagal di periksa palsu `false`, semua otomatis tumbang terbakar jadi total False hancur seluruhnya).
- **OR (`||`)**: Pemurah pengiba. Menghasilkan jawaban tembus portal lolos `true` manakala santai minimal asalkan ada paling tidak Murni satu baris saja syarat berhasil lulus True.
- **NOT (`!`)**: Tukang usil peredam pemutar fakta pembalik janda kepastian nasib balikan 180 drajat. Jika disuruh nilai boolean aselinya True, jika kebetulan digedor diketok palu dipakaikan awalan seru depannya, wujud dia berubah munafik instan menjadi wujud False. 
```javascript
let priaBaik = true;
console.log(!priaBaik); // Keluarnya memutarbalik jadi: false 
```
