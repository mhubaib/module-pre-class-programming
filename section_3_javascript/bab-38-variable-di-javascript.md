# Bab 38: Variable di JavaScript

## Tujuan Pembelajaran
- Memahami konsep dasar Variabel sebagai wadah penyimpan data.
- Mengetahui cara mendeklarasikan variabel dengan syntax modern (`let` dan `const`).
- Memahami alasan mengapa penggunaan `var` sudah banyak ditinggalkan.
- Mengikuti aturan dan standar penamaan variabel (Camel Case).

## Materi Utama

Dalam memproses informasi, sebuah program perlu tempat untuk "mengingat" sebuah data sementara waktu sebelum data itu dimasukkan ke dalam perhitungan rumus atau ditampilkan ke layar. Tempat penyimpanan data sementara di dalam memori komputer ini dinamakan **Variabel (Variable)**.

**Analogi Variabel:**
Bayangkan variabel sebagai sebuah **Kotak Laci**.
Bayangkan kamu memiliki laci kosong. Kamu menempelkan label nama di depan laci tersebut dengan tulisan "Koleksi Kemeja". Lalu, kamu memasukkan beberapa kemeja ke dalamnya. Kapan pun kamu butuh kemeja, kamu tidak perlu mencari di seluruh lemari, kamu cukup membuka laci bernama "Koleksi Kemeja" tadi dan isinya akan keluar. 
Di pemrograman, "Koleksi Kemeja" adalah nama variabelnya, dan isinya adalah "Data"-nya.

### 1. Deklarasi Bersama Variabel Modern: `let` dan `const`

Sampai tahun 2015, JavaScript hanya memiliki satu cara membuat variabel, yaitu menggunakan perintah `var`. Namun, perintah ini memiliki beberapa celah sistem yang sering memicu *error* (bug) di aplikasi besar berskala industri.

Oleh karena itu, pada pembaharuan ECMAScript 6 (ES6), lahirlah dua kata kunci pelindung baru: `let` dan `const`. Kedua ini wajib kita gunakan sekarang. Kapan penggunaannya?

#### Kata Kunci: `let` (Bisa Diubah Varian)

Gunakan `let` jika isi wadah variabel tersebut **berpotensi diubah atau ditimpa** dengan nilai yang baru di kemudian hari dalam baris kodemu.

```javascript
// Menginisialisasi (membuat) variabel "skorPemain" dan mengisinya dengan angka 0
let skorPemain = 0;

// Di ronde kedua, skornya diubah.
// Kita tidak perlu menulis kata 'let' lagi, cukup panggil nama lacinya!
skorPemain = 50;

console.log(skorPemain); // Nilai yang akan keluar adalah 50.
```

#### Kata Kunci: `const` (Konstanta Tetap/Permanen)

`const` adalah kebalikan dari `let`. Gunakan `const` untuk variabel yang isinya bersifat mutlak, absolut, dan **dilarang keras untuk diganti/ditimpa** setelah pembentukan pertamanya. Ini digunakan untuk mencegah datamu tidak sengaja terhapus oleh perintah lain secara keliru.

```javascript
// Membuat wadah konstan nilai Phi dalam rumus matematika
const nilaiPhi = 3.14;

// Jika di baris selanjutnya kamu bandel mencoba menimpanya:
nilaiPhi = 3.15; 

// HASIL: BROWSER AKAN ERROR! Program otomatis berhenti menjaga ketetapan nilaiPhi.
```

**Kapan harus pakai yang mana?**
Sebagai praktik pemrograman modern (*Best Practice*), **selalu mulailah dengan menggunakan `const`** saat membuat elemen wadah apa pun (Entah array, object, ID User, dll). Jika suatu saat logikamu membutuhkannya untuk diobrak-abrik/diubah, barulah kamu ubah kata kuncinya menjadi tipe `let`.  Ini menciptakan jaring pengaman agar programmu lebih solid dan minim masalah yang disebsbkan kerusakan tertimpa.

### 2. Aturan Menamai Kotak Variabel

Memberikan sebutan nama variabel memiliki hukum syariahnya di rimbah Javascript:

1. **Kasus Penulisan Unta (Camel Case)**: Jika nama lacimu terdiri dari dua suku kata, JS tidak mengizinkan ada spasi. Standarnya, huruf awal kata pertama dikecilkan, dan awalan huruf kata kedua dst WAJIB DIKAPITALKAN (membentuk pelena tinggi menyerupai punuk unta).
   - Contoh Salah: `let namalengkap;` atau `let NamaLengkap;`
   - Contoh Benar: `let namaLengkap;` atau `let totalHargaAkhir;`
2. **Hanya Boleh Karakter Tertentu**: Nama tidak boleh mengandung spasi atau simbol aneh (seperti `@`, `-`, `*`). Karakter tak baku angka cuma dibatasi kepada penggunaan Garis Bawah (Underscore `_`) serta dan simbol Dolar (`$`).
3. **Mulai Dengan Huruf/Simbol**: Variabel dilarang keras dipanggil dimulai dengan patokan format Angka di huruf paling awalnya. (Misal `let 1Nama;` adalah ilegal. `let nama1;` itu legal).
4. **Hindari Kata Reservasi (Reserved Keywords)**: Kamu nggak boleh pakai nama variabel menggunakan kata-kata yang sudah dibooking oleh sistem dasar perintah aseli Javascript itu sendiri. (Misal: pakai nama `let const = 5;` atau `let function = "Budi";` pasti error!).

Rahasianya Programmer Profesional: Buatlah nama Variabel yang gampang dibaca akal sehat manusia, dengan rujukan jelas isinya apaan, ketimbang nama singkatan sok misterius (Ngetik `let namaPengguna = "Budi"` jauh lebih baik secara mental kerja bertahun-tahun daripada ngetik `let x = "Budi"`).
