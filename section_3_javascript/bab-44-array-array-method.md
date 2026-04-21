# Bab 44: Array & Array Method

## Tujuan Pembelajaran
- Mengingat kembali konsep dasar tipe data majemuk kumpulan Array.
- Menguasai teknik operasi membaca, memanggil, dan menambah data barisan (Index).
- Mengenal utilitas fungsi alat berat bawaan Array (*Built-in Array Methods*) seperti `push`, `pop`, `shift`, `unshift`, `length`.

## Materi Utama

Seperti yang telah diulas sekilas di Bab 39, Array adalah penampung wadah cerdas (*Data Structure*) khusus yang mampu meletakkan banyak kumpulan serpihan data bertumpuk berbaris dalam 1 slot variabel identitas. 

Bayangkan jika kamu merekapitulasi nama 50 orang pendaftar mahasiswa baru. Jika tanpa Array, kamu terpaksa harus lelah menderita membuat deklarasi: `let siswa1 = "Budi"; let siswa2 = "Asep"; let siswa3 = "Joko";` hingga habis sampai nomor 50 baris terpisah. Itu sungguh metode pengerjaan yang keliru secara mental logis. 

Solusinya masuk akal: Buatlah 1 Array panjang mengular!

### 1. Struktur Tulang Array & Memanggil Nilai Berdasar 'Index'

Pembuatan Array wajib memanfaatkan tanda Kurung Siku Penuh `[ ]`. Serpihan item data yang disusun satu per satu di dalamnya akan dirantai koma `,` sebagai pemisah gilirannya.

**Hukum Mutlak Nomering Programmer (Index = 0)**: 
Komputer mesin tidak pernah diajarkan pandai menghiraukan hitungan jari belajar mulai dari angka romawi "1". Di belantika mesin, angka letak urutan terdepan yang menduduki bangku antrean bangku Array akan selalu mutlak dinomori hitungan berawal dari **0 (Nol)**.

```javascript
// Array berisi kumpulan ragam string
let barangTas = ["Buku", "Pulpen", "Laptop", "Dompet"];

/*
Urutan Mesin aslinya:
- Index ke-0 : "Buku"
- Index ke-1 : "Pulpen"
- Index ke-2 : "Laptop"
- Index ke-3 : "Dompet"
*/

// Jika kau bermaksud khusus untuk menarik melirik murni mengambil memanggil data item "Laptop":
console.log( barangTas[2] ); // Akan tercetak "Laptop" di layar

// Jika kamu bermaksud meniban atau mengubah isi laci yang nomer dua tadi jadi barang lain:
barangTas[2] = "Kotak Makan";
```

### 2. Fungsi Mesin Utilitas Sakti Array (Method Bawaan JS)

Array di JavaScript sangat canggih karena dibekali serangkaian **Fungsi Bawaan (*Array Methods*)** menanak masak yang siap sedia merombak mengacak-acak barisan data barisannya instan tanpa keringat.

**A. Mengukur Ketebalan Total Panjang Gerbong Antrian: `.length`**
(Fungsi pemanggil mutlak yang ditugaskan khusus memberitahumu berapa banyak persis serdadu serpihan anggota barang yang numpang di dalam daftar variabel).
```javascript
let peserta = ["Dani", "Yanto", "Gilang"];
console.log(peserta.length); // Pencetak akan menunjuk total bulat murni "3" utuh.
```

**B. Menghapus Item Ujung-Ujung Murni**
Terdapat perintah kembar sepasang yang spesialisasi menghancurkan mengambil data baris depan atau data dari antrian kursi belakang.
- **`.pop()`**: Menarik buang item ujung paling kanan (buntut antrian paling terakhir).
- **`.shift()`**: Memotong buang item nomer 0 (orang pertama terdepan) sampai hancur sisa sisanya ikut maju kedepan selaras 1 slot baris hitungan.

```javascript
let daftarObat = ["Paracetamol", "Amoxicillin", "Vitamin C"];

daftarObat.pop(); 
// Efek aslinya sekarang daftar array murni tinggal ["Paracetamol", "Amoxicillin"] (Vitamin C dibuang)

daftarObat.shift();
// Sekarang tersisa cuma ["Amoxicillin"]. (Paracetamol melesat terbang hilang dihisap).
```

**C. Menyekrap Menambahkan Benda Serpihan Susulan**
Terkadang form web kita meminta penonton klik kiriman formulir dan kita harus masukkkan pendaftaran nama mereka ke wadah database array. Ini alat bongkar pasangnya:
- **`.push(nilai_baru)`**: Meletakkan memasukkan sumpel data barang utuh menaruhnya duduk antri manis menduduki kursi memanjang antrian nomer bangku **paling belakang aspal terakhir buntut sisa**.
- **`.unshift(nilai_baru)`**: Secara biadab nyerobot menaruh nilai sesak desak numplak di barisan antrian kursi nomer 0 (terawal) memaksa gerbong lama mundur digeser ganti nilai.

```javascript
let namaBulan = ["Februari", "Maret"];

// Merombak menambah paksa sela
namaBulan.unshift("Januari"); // Jadi -> ["Januari", "Februari", "Maret"]

namaBulan.push("April"); // Selesai mutlak panjang antri jadi -> ["Januari", "Februari", "Maret", "April"]
```
*(Array adalah nadi utama pengolahan big-data pemrograman, hampir 70% pengolahan struktur alur datamu esok kelak di dunia kerja nyata bertumpuk bertarung di olahan laci data mutlak Array semata).*
