# Bab 42: Percabangan (Control Flow)

*(Catatan Pemandu: Bab 41 sengaja dilompati dalam susunan roadmap modul ini)*

## Tujuan Pembelajaran
- Memahami konsep logika kondisional membelokkan arah jalan persimpangan program.
- Menulis logika `if`, `else if`, dan `else` berdasarkan serangkaian syarat pengecekan operator.
- Menguasai perbandingan jamak bercabang statis menggunakan tata susun struktur kaku rapi bernama `switch/case`.
- Mengenali nilai *Truthy* dan *Falsy* tak terbantahkan pada evaluasi Boolean dasar rahasia sang JS.

## Materi Utama

Komputer sejatinya sangat menurut, ia akan membaca kodingan kaku lurus terus lari merunut pelan membaca mengeksekusi merambat barikade runtut eksekusi instruksi turun membaris vertikal persis arah tegak dari paling baris atas mentok hingga ke paling dasar kodinganmu terbawah layaknya aliran sungai gravitasi mendatar tumpah.

Namun di dalam dunia nyata, program aplikasimu pasti dihadapkan oleh **suatu pilihan kondisi persimpangan hidup realita kacamata**. "Jikalau si User lupa memasukkan input Nomor KTP, Janganlah diizinkan Lanjut nge-Save Data Formulirnya!". 

Di sinilah peran pintu penjaga tikungan **Control Flow**!

### 1. Struktur Kendali Dasar: `if...else` Logika Kondisi 

Perintah `if` (JIKALAU) adalah pilar penyangga jalan masuk gerbang memeriksa memvalidasi nilai mutlak dari `Boolean` (True ataukah False).

**A. Kondisi Pemeriksaan Tunggal Blok Mandiri (`if` Utama)**
```javascript
let sisaBensinDarah = 10;

// Blok Pintu Pemeriksaan Penjaga Mulai :
if (sisaBensinDarah < 20) {
    // Kalau benar terbukti syaratnya dipenuhi sah (True), maka mesin gerbang ini dibuka paksa terjalankan:
    console.log("Hei.. Lampu Peringatan Darah Bahan Bakarmu Menipis Parah Segera isikan Bensin ke SPBU");
}
```

**B. Kondisi Alternatif Sandaran Terakhir Akhir Sisa Jaga Kandang (`else` Blok)**
Apabila gerbang pemeriksaan gerbang `if` tak penuhi spesifikasi lolos alias bernilai gagal tertolak mutlak `false`, kemana takdir alur logika membuang hasil larinya mesin program? Disinilah dipasang kantung ranjang tidur penutup panti jompo pengaman alternatif `else`.
```javascript
let nilaiRaporSiswa = 60;

if (nilaiRaporSiswa >= 75) {
    console.log("SELAMAT. Kau Tuntas Lulus Lanjut Menikmati Pergi Liburan!");
} else {
    // Dipanggil merespon otomatis murni mengeksekusi hal hal sisa terbuang keping karena kondisi ujian porsi pertama if di hancurkan. 
    console.log("Mati Kau Nangis Kudu Wajib Bayar Hutang Lakukan Ujian Remidi Remedial Ngulang di Kelas Mengabdi!!");
}
```

**C. Rantai Logika Pemeriksaan Berlapis Tahapan Uji Cabang Tingkat Tinggi (`else if`)**
Terkadang dunia tak sempit terbatas 2 pilihan jalan warna belok Hitam & Putih semata. Ketika kondisional berjejal menghamba jenjang 3 pilihan rentang lebih berturut terhubung.. selipkan sambungkan balok kerangka jenjang jembatan `else if`.
```javascript
let lampuSinyalJalanTop = "kuning";

if (lampuSinyalJalanTop === "merah") {
    console.log("Berhenti Totallah di Tempat!");
} else if (lampuSinyalJalanTop === "kuning") {
    console.log("Kurangi Tarikan Perlanhan Injek Remmu.. Awas siap berenti mundur..");
} else if (lampuSinyalJalanTop === "hijau") {
    console.log("Injak Pedal Gas Kuat Melaju!");
} else {
    // Filter saringan aspal paling penutup tong sampah mentok tak tersisa bila semuanya tiada cocok tak karuan warna yg tertulis biru gelap sekalipun
    console.log("Tinggalkan Mobil Hancur! Tiang Lampu Jalan Traffic Light Nya Sedang Eror Dihack!");
}
```

### 2. Saklar Penyeleksi Nilai Pasti: `switch / case`

Jika suatu saat kamu bosan menderet panjang ketikan nulis untaian ranting cekcok tali kabel panjang pakai rumus syarat pengecek kesetaraan kembar `if (... === ...)` yang tiada habis berlarut panjang mengunyah merusak visual capek baris-baris rumit, JavaScript memberimu pil sakti penyeimbang rapi khusus bernama pintu **`switch`**. 

Ia sanggup membelah rute sangat lurus mutlak mengecek sebuah "Label Variabel Nilai Kasus Tetap" yang pastinya kaku terukur.

```javascript
let hariUrutanKini = 3;

switch (hariUrutanKini) {
    case 1:
        console.log("Senin Awal Membuka Minggu Yang Kejam");
        break; // Tali Jangkar Rem Pemberhentian Mandat Eksekusi mesin Wajib Dipasang 
    case 2:
        console.log("Selasa Semangat Melanjutkan");
        break;
    case 3:
        console.log("Rebo Puncak Lelah Puncak Minggu Bertarung Keras");
        break;
    default: // Fungsinya mirip panti jompo `else` pembuangan terakhir tak kenal target 
        console.log("Angkanya Bukan Rentang Hari Sah Libur Sembarang..");
}
```
**Peraturan Sakti Mutlak Pakai `Switch`**: Anda haram kelewatan tiada luput membubuhkan gembok portal berbunyi kalimat perantai perintah instruksi suci `break;` diselusup penghujung masing-masing lantai blok instruksi selasar *case*, sebab bila sengaja atau amnesia terlewat menulis baris patahan break ini, aliran kucuran eksekusi perintah JS nya akan membludak blong kebablasan numpang bocor merembes meluber ikut mengeksekusi hasil cetak terminal bawah lantainya secara bersamaan (Sebuah Fenomena Kelalaian Programmer Pemula dinamakan *"Kejadian Fatal Fall-through"*).

---
**(Rahasia Singkat Tambahan Ahli Uji Coba Lulus Mutlak Terjamin / Truthy & Falsy)**
Javascript punya logika mesin bawah sadar evaluasi instan bawaan pabrik murni yang mana semua seluruh wadah jenis Tipe Data di sistemnya akan di-CAP mengiyakan dianggap bernilai Boolean Sah Lolos Lulus Positif `true` (istilah dewanya di sebut = **Truthy**)... 
KECUALI nilai racun daftar gerombloan enam data kutukan yang melompong murni bernilai palsu kegagalan negatif saklek `false` (**Daftar Hitam Falsy Values**) : `false`, angka `0`, serpihan teks kutip kosong sama sekali bolong `""`, variabel gagal pesanan `null`, janin variabel terbuang `undefined`, plus nanah gagal ngitung angka `NaN`. Murni hafal diluar jidat kepala logikamu.
