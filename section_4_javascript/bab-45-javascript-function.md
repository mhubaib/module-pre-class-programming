# Bab 45: JavaScript Function

## Tujuan Pembelajaran
- Memahami konsep Function sebagai blok alat mesin pabrik cetak mesin untuk mendaur ulang logika kode.
- Menguasai format struktur mutlak anatomi Function (Parameter dan Return).
- Mengenal variasi tipe fungsi rahasia terbaru: *Arrow Function* ringkas yang revolusioner.

## Materi Utama

Dalam membedah membangun website yang rumit, terkadang kamu menemui insiden dimana kamu terpaksa harus **mengetik tumpukan logika baris kode yang berfungsi hitungan serupa yang sama persis sifat berulangnya** diberbagai rentetan sudut file dan diulang-ulang. 
Ini menganggar hukum dewa koding: *Mendaur Ulang Kode (DRY: Don't Repeat Yourself)*. Karena hal ini kotor merepotkan di perbaikannya kelak.

Solusinya mutlak: Serahkan ke Mesin **Function** (Fungsi). 

Bayangkan sebuah **Fungsi (Function)** itu bagaikan alat pabrik cetak mesin Giling Blender buah Jus. Kau rakit dulu onderdil mata pisaunya (buat blok `function`-nya), lantas kau tinggal setorkan berulangkali lempar buah mangga ke corong input (lempar nilai masukannya), lalu mesinnya diam-diam otomatis menghancurkan matematis mangga terolah tersebut menjadi air jus (kembalian nilai), dan kau tinggal mewadahi ampas jus keluarannya berulang ulang asyik secara mudah!

### 1. Deklarasi Anatomi Dasar Fungsi (Fungsi Reguler Standar)

Untuk membuat membuat cetak biru mesin blender ini, kamu memakai kata instruksi kunci awalan: `function` lalu tuliskan identitas nama fungsi tersebut (*biasakan pakai kata aksi kata kerja aktif Camel Case*), ditidurkan kebalutan kurung `()`, dan disatukan blok pemrosesan perut lambungnya si kurung kurawal `{}`.

```javascript
/* 1. MENCIPTAKAN MERAKIT MESIN FUNGSI */
function sapaanPerkenalan() {
    console.log("Halo Pelanggan Terhormat! Mari Menyelesaikan Tagihan Belanja.");
}

/* 2. EKSEKUSI PEMANGGILAN MUTLAK GILING PABRIK FUNGSI */
// Meski kau buat 1000 baris asik diatas, jika tak ada perintah aksi "Pemanggilan Eksekusi Function ()", fungsimu ga akan nyala nyetak kelayar selamanya.
sapaanPerkenalan(); 
// Hasil Layar : "Halo Pelanggan Terhormat! Mari Menyelesaikan Tagihan Belanja."
```

### 2. Lubang Input Variasi Corong (Parameter) dan Data Celah (Argument)

Mesin aslinya tak asyik kalau ia mencetak tulisan kaku statis terus menerus tanpa pembeda interaksi gilir. 
Untuk merubah mesin jadi dinamis meladeni nilai dinamis.. buatlah lubang di jidat kurungnya yang bernama **Parameter**.

- **Parameter**: Laci nama corong khusus buat corong selang tangkapan di mulut si deklarasi `function ()`.
- **Argument**: Benda angka yang mutlak disodorkan ditembakkan pasang kedalam telinga si fungsi saat proses Panggilan kerjanya eksekusi.

```javascript
// Membikin mesin pertambahan dinamis dengan 2 corong bolong (angkaA dan angkaB).
// Kedua lubang nama nilai diatas tersebut bebas dinamai sembarang mutlak.
function hitungTambahPenjumlahan(varAngkaA, varAngkaB) {
    let hasilTotal = varAngkaA + varAngkaB;
    console.log("Totalnya adalah mutlak berjumlah mutlak : " + hasilTotal);
}

// Melempar masuk argument nyata (melempar mangganya):
hitungTambahPenjumlahan(5, 7); // Tercetak: 12
hitungTambahPenjumlahan(100, 25); // Setengah detik ganti cetak: 125
```

### 3. Jembatan Penghubung Kembalian Air Sirup Mesin (`return`)

Sering kali mesin tak boleh nyetak seenaknya merusak tampilan *console* langsung berdarah tumpah ruah kotor berjejal. Seringnya mesin murni dilarang log ke layar, ia **diharuskan meretur merubah mengembalikan membungkus angka mentah berdarah di botol botol tertutup kembali utuh** ke arah jalur depan sang agen pemesan instruksi agar angkanya bisa diolah di-save kedalam database pendaftaran!

Mantera ini murni adalah hak eksklusif hak milik perintah `return`. Saat palu hakim `return` dieksekusi berjalan diketok.. seketika itu putaran tugas sang mesin function ditutup langsung tak bersisa seketika mutlak.

```javascript
function cekBiayaDiskon(hargaPenuh) {
    let potongan = hargaPenuh * 0.5; // Potong dikali setengah
    
    // Mesin disuruh membungkus ulang angka aspal diskon diam-diam diam bungkam diserahkan meretur mutlak hasilnya.. 
    return potongan; 
    
    // (Bila seumpama asiknya aja kamu mengetik asal nyelip baris intruksi console.log dibawah baris return ini.. mutlak instruksi console bawahmu tidak bakalan tereksekusi dibaca dijalankan..).
}

// Beda banget manggil eksekusinya: (angkanya tak langsung meledak nyembur kelayar terminal diam hening!)
cekBiayaDiskon(50000); 

// Kita tangkap sembunyikan curi botol angka balikan "25000" hasil returnnya, masukan tuangkan ke laci botol baru untuk dipamer kelayar.
let hitungHasilReturnya = cekBiayaDiskon(50000);
console.log(hitungHasilReturnya); // Murni tercetak 25000
```

### 4. Panah Cinta Mutakhir: Rahasia ES6 `Arrow Function` 

Pada 2015, JS mengenalkan syntax gaul revolusioner singkat nulis yang membuat ketikan *function* yang kuno panjang boros abjad dipangkas dipotong kompas habis menjadi sintaks satu baris panah panahan pendek ciamik gila: Menggunakan pisau sakti **Arrow `=>`**.

```javascript
// Model fungsi kaku gaya jadul (Murni Standar Normal Bawaan Nenek Moyang) :
let fungsiHitungJadul = function(x, y) {
    return x * y;
};

// --- DIUBAH MENULAR GAYA GAUL ARROW FUNCTION (Super Mutakhir Pendek Sakti Sebaris) --- :
let fungsiPanahCepat = (x, y) => x * y;

// Hasil ketikan gila sebaris itu otomatis sudah termasuk dibungkus dikasih perintah 'return' balikan instannya oleh JS langsung! Wow! Canggih efisien ketikannya! 
console.log( fungsiPanahCepat(3, 4) ) // Layar mutlak menyorakkan hasil silang: 12.
```
*Catatan Sampingan Dunia Nyata:* Industri Framework Web termahsyur di abad ini yakni perpustakaan dunia koding **React**, mewajibkan penganut pengikutnya nyaris mutlak mutlak 100% menggunakan jurus gaya tulis format peredam ringkas padat berisi **Arrow Function** di segalam nafas detak proyek mereka ketimbang fungsi kuno function(). Jadi wajib hafalkan bentuk `=>` ini di luar jidat otakmu!
