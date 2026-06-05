# Bab 56: Asynchronous JavaScript (Logika Tak Sinkron)

## Tujuan Pembelajaran
- Membedakan paradigma eksekusi *Synchronous* (antre linear murni) dengan *Asynchronous* (paralel tanpa tunggu).
- Memahami konsep antrean waktu tenggat tak pasti saat mengeksekusi operasi berat.
- Menguasai syntax canggih ES8: `async` / `await` untuk merapikan alur bacaan kode asinkron.

## Materi Utama

Ini adalah Bab Pendekar! Materi ini adalah pemisah batasan tersulit antara kelas programmer JS kacangan dengan programmer level madya mutlak.

Pertama-tama mari benahi fundamental cara pandangmu:
JavaScript adalah sebuah bahasa yang terlahir cacat luhur: Ia bernyawa **"Single-Threaded"** (Hanya Punya 1 Lengan Pekerja/Terbiasa Antre Lurus Belakang).

Artinya (*Synchronous*), Javascript secara kaku selalu membaca, mengerjakan baris 1 tuntas, baris 2 tuntas, baru sudi merembes membaca perintah ke lantai baris 3. Jika baris 2 memerintahkan *"Pencarian Menghitung Bintang Semesta (1 Jam)"*, maka baris 3 tidak akan dieksekusi selama sesajennya perintah beban 1 jam sebelumnya belum terbayar tuntas terhitung selesai lunas mutlak! Semua layarmu nge-hang dan *freeze*. Ini malapetaka fatal!

Di sinilah dibutuhkan sihir **Asynchronous (Asinkronus)**: Seni mengerjain JS agar "Mendelagasi pekerjaan yang berat butuh nunggu waktu lama ke laci antrian bayangan belakang mesin browser", sembari lengan utamanya dibebaskan langsung loncat mengeksekusi instruksi di baris se-berikutnya sedetik kemudian tanpa ampun repot ikutan nunggu!

### 1. Mensimulasikan Keadaan Beban (Asinkron Bawaan Waktu)

Alat pendemonstrasi beban asinkron buatan klasik Javascript adalah saklar waktu: `setTimeout(FungsiTanggapan, WaktuTungguMiliDetik)`.

```javascript
console.log("1. Perintah Awal Menanak Nasi Mulai...");

// Kita pasang timer delegasi suruh mesin belakang Browser mendidihkannya (Butuh Nunggu 5 Detik / 5000ms):
setTimeout(function() {
    console.log("2. Selesai! Nasi Panas Matang!");
}, 5000);

console.log("3. Goreng Tempe Mendoan Cepat...");

/*
KRONOLOGI HASIL DI TERMINAL:
Langkah eksekusinya melompat!
Cetak: "1. Perintah Awal Menanak Nasi Mulai..."
Cetak: "3. Goreng Tempe Mendoan Cepat..."
(Lalu mesin terdiam hening jangkrik 5 detik)
Cetak Keluar: "2. Selesai! Nasi Panas Matang!"
*/
```
Mesin tidak sudi menunggu *timer 5 detik* memblokir jalan. Dia lempar tungku nasi itu ke belakang, dan langsung gercep maju mengeksekusi gorengan baris ke tiga instan.

### 2. Memahami Sumpah Janji Penungguan (Promises)

Pekerjaan menarik sedot data ke Server/Database adalah tugas Asinkron liar yang durasi balikan selesai beresnya amat *"Tidak pasti ketebak lamanya jam"* karena mengikut dewa kecepatan paket kuota internet tiap pengguna!

Agar antrean data berat begini berbaris damai tanpa error tumpah ruah belum jadi sudah keburu tercetak kosong (*undefined*), JS modern 2015 membentangkan alat peredam penampung wadah asinkron liar yang dinamakan *The Promise* (Sumpah Janji).

Objek *Promise* akan mengepal mengecup pekerjaan berat tersebut dengan ikrar 3 Fase Alur Hidup:
1. **Pending (Menggantung Antre)**: Kerjaannya masih ngubek-ngubek jalan di balik layar belum slesai.
2. **Fulfilled / Resolved (Berhasil Lunas Sakti)**: Datanya komplit berhasil didapat dibungkus kembalian bawaan rejeki.
3. **Rejected (Ditolak Merana / Error)**: Server meledak atau Putus Koneksi!

### 3. Solusi Terang Mutahir Modern Pendek: Syntax `async / await` 

Jika di jaman 2015 programmer mengikat rantai Promise menggunakan mantera sambung-menyambung panjang lelah berbaris `fungsiBeratLama().then().then().catch()` (disebut The Callback Hell/Promise Chaining)... 
Maka di tahun 2017 turunlah wahyu Syntax **`async/await`** yang ajaib!

Ini adalah cara memaksa membekukan secara elok lengan antrian (sok seolah *Synchronous* kembali), dengan ketikan berwujud rapi tegak lurus menakjubkan tanpa ikatan sambung ribet kurung *Callback/Then*!

**Bagaimana Aturan Bermainnya?**
- Mutlak diwajibkan menyegel mencap jidat fungsi pembalut besarnya dengan gelar sertifikasi **`async`** (Artinya: "Hei mesin, di dalam perut kelak bakal ada antrian nunggu ga terduga lelet loh, waspada!").
- Tempelkan palu gembok ketikan penghenti waktu pengerem paksa lengan **`await`** persis HANYA di tepi mulut fungsi sumber perkara penungguan data loding berat saja! 

```javascript
/* Anggap saja kita memanggil fungsi bayangan dari tempat lain yang menjanjikan pengiriman narik data berat API User butuh 3 detik */

// 1. Label Tanda Label Ekstra di Awalan Fungsi!
async function pamerkanBiodataUserBerapapunLamanya() {
    
    console.log("Tunggu Sebentar sedang konek narik data ke Server Planet Mars...");
    
    // 2. Pasang Rem Paksa Gembok `await`! 
    // "Hei mesin lengam lengan kerja lengan.. kamu STOP NENGGONG MATI NUNGGU DISINI DIAM MUTLAK sampai Promise data lemparan paket dari ampar_NarikDataBesar() LUNAS TERRESOLVED DAPAT MASUK SELESAI di tangkat ke kotak wadah `hasilTarik`."
    let hasilTarik = await fungsiJanji_NarikDataBesar_EntahBerapaLama(); 
    
    // (Mesin benar-benar bekumenunggu macet di baris itu dihentikan sang `await`).
    
    // Begitu Datanya beres terkirim, mesin jalan buka kran gas maju ke lantai bawahnya beres. 
    console.log("Data Lunas Didapat! Ini Tampangnya: " + hasilTarik);
    
}
```

Jurus mantera kembar ikatan `async...await` ini kelak merupakan kunci pelatuk kemudi setirmu dalam menarik pasokan pundi pundi eceran isi sembako produk harga Shopee dari Server database Backend lewat alat kurir pos khusus JS mutlak bernama sang API Fetch di Bab Paling Pamungkas Puncak Terakhir sana! (Bab 57).
