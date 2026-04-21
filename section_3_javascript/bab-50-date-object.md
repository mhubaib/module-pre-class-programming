# Bab 50: Date Object

## Tujuan Pembelajaran
- Memahami kegunaan Date Object dalam JavaScript untuk manajemen waktu nyata.
- Mampu membuat object penanda waktu, baik waktu saat ini maupun waktu spesifik di masa lampau/depan.
- Mampu membedah dan mengambil data hitungan bulan, hari, tahun menggunakan *Date Methods*.

## Materi Utama

Dalam membuat aplikasi, waktu adalah kordinat mutlak kehidupan yang tak bisa dihiraukan. Kapan User mendaftarkan akun? Jam berapa batas akhir (deadline) pembayaran Shopee ini akan basi / kadaluarsa? 

JavaScript menyediakan mesin waktu bawaan paten yang bernama **Date Object**. 

Ini adalah sebuah pabrik struktur objek khusus (seperti Bab 46) yang di dalamnya telah dibekali puluhan method otomatis sakti untuk meraba mencerna detak detik almanak waktu Gregorian kalender dunia (dan sangat bergantung akurat menyesuaikan jam zona waktu (*Timezone*) OS sistem bawaan asal muasal komputer sang penontonmu sendiri).

### 1. Mencetak Cetak Biru Waktu (Instance Date Baru)

Untuk menyalakan mesin pemanggil waktu, kita diwajibkan menggunakan deklarasi ritual kalimat `new Date()`. Menulisnya pakai awalan huruf Kapital **D**.

```javascript
/* MENCATAT DETIK SAAT INI (REAL-TIME LAPTOP DIBUKA) */
let waktuSekarang = new Date();
console.log(waktuSekarang); 
// Tercetak format ribet kasar mesin utuh, misal: "Wed Oct 25 2024 15:30:00 GMT+0700 (Western Indonesia Time)"

/* MEMBUAT CATAAN WAKTU KHUSUS MASA LALU/DEPAN */
// Format Standar: new Date(Tahun, IndeksBulan, Tanggal, Jam, Menit, Detik);
// Catatan Kutukan Javascript = INDEKS BULAN DIMULAI DARI ANGKA 0 (0 itu Januari, 11 itu Desember).

let hariKemerdekaan = new Date(1945, 7, 17, 10, 0, 0); 
// 7 merujuk ke Bulan Agustus (karena 0 itu Januari).
console.log(hariKemerdekaan);
```

### 2. Membedah Objek Tanggal dengan Date Methods (Alat Ekstrak)

Format mentah balikan kasar *"Wed Oct 25 2024 dll"* dari `new Date()` di atas mustahil dan jelek sekali untuk dipamerkan tertulis dipajang ke hadapan Layar Web tampilan (*UI*) pengunjungmu. Kita diharuskan mengekstrak memecah nilai mentah itu murni spesifik pertitel elemen detiknya. 

Gunakan senjata utilitas fungsi "Getters" (Pengekstrak) milik Object Date ini:

- `getFullYear()` : Memeras mengambil data 4 digit tahun (eg: 2025).
- `getMonth()` : Mengintip nomer indeks bulannya (Ingat, angkanya balik mutlak berkisar 0 - 11 mulainya).
- `getDate()` : Menoreh mencabut tanggalnya pas di bulan tersebut (1 - 31).
- `getDay()` : Mengembalikan nomer baris antrian hari mingguan abjad. (Dimulai mutlak Angka Hari 0 = Minggu, 1 = Senin, dst sampai 6 = Sabtu).
- `getHours()`, `getMinutes()`, `getSeconds()` : Untuk menarik intip nilai penunjuk rincian waktu detaknya jam.

**Contoh Kasus Pengolahan Tampil Rapi:**
Kita mau mencetak tulisan kalender rapi bergaya Indonesia: "Tahun: 2024, Tanggal 15".

```javascript
let almanakKini = new Date();

let tahunTerambil = almanakKini.getFullYear();
let tanggalToko = almanakKini.getDate();
let indeksBulan = almanakKini.getMonth();

console.log("Faktur Dibuat Pada: " + tanggalToko + "-" + (indeksBulan + 1) + "-" + tahunTerambil); 
// Layar Mulus Mencetak: "Faktur Dibuat Pada: 15-10-2024"

// (Perhatikan kita akalin di atas `indeksBulan + 1` agar angka bulannya manusiawi dibaca pas, bukan turun selisih 1 hitungan karena hitungan nol JS!)
```

### 3. Manipulasi Mengubah Waktu (*Setter Methods*)

Selain sekedar mengekstrak ("Get"), object Date juga sanggup mutlak mengubah / loncat memaju-mundurkan patokan rekam jejak ("Set").
- `setFullYear(2099)` : Menyulap data ubahan menendang rekam ke masa depan.
- `setDate(25)` : Memodifikasi paksa tanggalnya.

```javascript
let kalenderCicilan = new Date(); // Hari ini

// Memerintahkan waktu melompat paksa ke tanggal 30 (Bayaran Hutang):
kalenderCicilan.setDate(30);

console.log("Silahkan Tuntaskan Bayaran di Tanggal: " + kalenderCicilan.getDate());
```

Date Object di JavaScript sering kali ditakuti dibenci pemula karena logikanya sering tak terkalibrasi lurus gara-gara format sistem *Indeks 0* bulannya yang gila aneh, ditambah perihnya senggolan antar zona waktu dunia nyata. 

Maka wajar kelak suatu saat jika proyemu sudah masuk kerumitan skala dewa, biasanya tim ahli Developer akan menyerah lalu menggunakan bantuan ekstensi (*Library*) *pihak ketiga eksternal* seperti `date-fns` atau `Luxon` agar manajemen format hitung mundur waktunya (Semisal fitur *Di-Upload 2 Hari Yang Lalu*) jadi mutlak tak mudah meleset eror berantakan kalakulasi di segala browser!
