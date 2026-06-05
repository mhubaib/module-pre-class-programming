# Bab 37: Sintaks, Statements, & Comments

## Tujuan Pembelajaran
- Memahami aturan dasar penulisan kode (sintaks) JavaScript.
- Membedakan perbedaan mendasar antara *Statement* dan *Expression*.
- Menerapkan penulisan *Comments* (Komentar) untuk dokumentasi kode.

## Materi Utama

Pemrograman adalah cara kita memberikan serangkaian instruksi kepada komputer. Agar komputer (dalam hal ini *Browser Engine*) bisa memahami perintah kita, instruksi tersebut harus ditulis menggunakan tata bahasa baku yang ketat. Tata bahasa baku dalam pemrograman disebut **Sintaks (Syntax)**.

### 1. Aturan Dasar Sintaks JavaScript

JavaScript memiliki beberapa aturan penulisan yang mutlak harus diikuti:

**A. Bersifat *Case-Sensitive***
JavaScript membedakan antara huruf besar dan huruf kecil. Variabel bernama `nama`, `Nama`, dan `NAMA` akan dianggap sebagai tiga hal yang sama sekali berbeda. Pastikan selalu konsisten dalam mengetikkan nama fitur atau variabel.

**B. Penggunaan Titik Koma (Semicolon `;`)**
Serupa dengan CSS, JavaScript menggunakan titik koma (`;`) di akhir baris untuk menandakan bahwa satu kalimat perintah telah selesai. 

Contoh:
```javascript
console.log("Halo Dunia");
alert("Selamat Datang!");
```

*Catatan: Pada JavaScript modern, penggunaan titik koma di akhir baris bersifat opsional (karena fitur Automatic Semicolon Insertion). Namun, untuk pemula yang baru belajar alur logika, sangat disarankan untuk disiplin menggunakan titik koma untuk mencegah error/bug yang sulit dilacak.*

### 2. Statements & Expressions

Dalam JavaScript, kita sering mendengar dua istilah ini. Penting untuk mengetahui perbedaannya sejak awal.

**A. Statement (Pernyataan)**
*Statement* adalah sebuah instruksi instruksi penuh yang memerintahkan komputer untuk melakukan suatu "tindakan". *Statement* tidak menghasilkan nilai balik yang bisa langsung disimpan. Ia hanya menyuruh mesin melakukan sesuatu.

Contoh *Statement*:
```javascript
// Ini adalah statment instruksi membuat variabel
let umurUser; 

// Ini adalah statement percabangan logika
if (umurUser > 18) {
    console.log("Sudah Dewasa");
}
```

**B. Expression (Ekspresi)**
Sedangkan *Expression* adalah potongan kode yang **menghasilkan sebuah nilai** setelah dievaluasi (dihitung) oleh komputer.

Contoh *Expression*:
```javascript
// "5 + 10" adalah ekspresi yang akan berubah menjadi nilai 15
5 + 10;

// "halo" + " " + "budi" adalah ekspresi teks yang menghasilkan string baru
"halo" + " " + "budi";
```

Dalam praktiknya, kita sering menggunakan ekspresi di dalam sebuah *statement*. Misalnya: menyuruh komputer (**statement**) untuk menyimpan hasil hitungan (**expression**) ke dalam sebuah variabel.

### 3. Menulis Komentar (Comments)

Saat mengerjakan sebuah program, jumlah kodemu bisa mencapai ribuan baris. Sangat mungkin kamu atau rekan setimmu lupa apa fungsi dari suatu blok kode setelah berbulan-bulan tidak melihatnya.

Di sinilah **Komentar (Comments)** dibutuhkan. Komentar adalah teks bantuan yang **sepenuhnya diabaikan** oleh mesin komputer. Komentar ditulis murni untuk dibaca oleh manusia sebagai catatan atau dokumentasi.

Ada dua cara menulis komentar di JavaScript:

**Komentar Satu Baris (Single-line Comment)**
Gunakan dua garis miring (`//`). Semua teks yang berada di sebelah kanan simbol ini pada baris tersebut akan dianggap komentar. Diabaikan komputer.

```javascript
// Ini adalah variabel untuk menyimpan data pengunjung hari ini
let totalPengunjung = 150; 
```

**Komentar Banyak Baris (Multi-line Comment)**
Gunakan kombinasi `/*` untuk membuka dan `*/` untuk menutup komentar. Sangat berguna untuk menulis penjelasan yang panjang hingga beberapa paragraf, atau mematikan/menonaktifkan (disable) blok kode sementara saat sedang mencari *error* (proses *debugging*).

```javascript
/* 
  Rumus di bawah ini bertugas menghitung total pajak 11%.
  Dibuat oleh : Hubaib
  Terakhir edit : 2025
*/
let pajak = harga * 0.11;
```

Biasakanlah menulis komentar untuk menjelaskan **"Mengapa"** kode tersebut dibuat seperti itu, bukan "Apa" kode itu (karena "Apa" bisa langsung terlihat dari cara kodenya ditulis oleh programmer lain).
