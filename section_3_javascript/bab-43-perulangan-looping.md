# Bab 43: Perulangan (Looping)

## Tujuan Pembelajaran
- Memahami konsep otomasi perulangan tugas di pemrograman.
- Menguasai dasar-dasar struktur perulangan `for`.
- Menguasai cara kerja perulangan `while` dan `do...while`.
- Mengetahui cara menghentikan perulangan paksa menggunakan `break`.

## Materi Utama

Salah satu alasan mengapa komputer diciptakan adalah untuk melakukan pekerjaan berulang-ulang dengan cepat tanpa merasa bosan. Di JavaScript, konsep melakukan pekerjaan berulang ini difasilitasi oleh mekanisme iterasi atau **Looping** (Perulangan). 

Bayangkan jika kamu disuruh mencetak tulisan teks "Halo Dunia" ke layar sebanyak 100 kali. Jika kamu mengetiknya manual satu per satu secara berurutan (*hardcode*), tentu akan sangat melelahkan dan membuang waktu. Dengan *Looping*, kamu cukup menulis teks tersebut **1 kali**, dan sisanya dikerjakan secara otomatis oleh mesin.

### 1. Perulangan Pasti: `for` Loop

Perulangan `for` digunakan ketika kita **sudah mengetahui dengan sadar** dan pasti seberapa banyak jumlah putaran baris yang ingin diulang. 

Format standarnya berisi 3 pilar yang dipisahkan titik koma (`;`): 
1. **Inisialisasi**: Variabel pencatat nilai awalnya berapa.
2. **Kondisi Maut**: Syarat batasan kapan putaran harus terus berjalan.
3. **Penaikan / Penurunan (Increment/Decrement)**: Tambahan nilai pelangkah yang akan menyalakan penggerak mesin menuju batas kondisi maut.

```javascript
/* 
Penjelasan:
- Dimulai dari angka 1 (let i = 1)
- Mesin akan terus berputar menyetak layar SELAMA nilai i kurang dari atau sama dengan 5 (i <= 5).
- Tiap satu putaran selesai dibaca, i ditambah 1 poin secara instan (i++) 
*/

for (let i = 1; i <= 5; i++) {
    console.log("Antrean ke-" + i);
}

// Hasilnya di terminal otomatis tercepat dan tersusun:
// Antrean ke-1
// Antrean ke-2
// Antrean ke-3
// Antrean ke-4
// Antrean ke-5
```

### 2. Perulangan Bersyarat: `while`

Berbeda dengan sahabatnya `for`, *Looping* model `while` ini lebih cocok digunakan saat **kamu belum tahu** jumlah pas pasti repetisinya ada berapa banyak. Ia tidak bergantung pada hitungan saklek angka mekanis. Ia hanya peduli dengan 1 hal: **"Selama syarat kondisi masih bernilai benar (True), hajar putar terus blok kodenya!"**. 

```javascript
let saldo = 10000;

// Selama saldomu tidak nol... 
while (saldo > 0) {
    console.log("Kamu masih cukup kaya tuk main game!");

    // PERINGATAN! Pastikan ada mekanisme yang perlahan mengubah nilai syaratnya.
    // Misal: tiap kali main, saldomu kita kurangi 5000:
    saldo -= 5000;
}
```
*Catatan Kritis:* Jika kamu lupa merubah/mengurangi saldo dari dalam blok kurung kurawal, komputermu akan memutar instruksi tanpa batas (keadaan yang disebut *Infinite Loop*) sehingga bisa membuat browser/komputer nge-*hang* dan *crash* layarnya akibat kehabisan sisa memori otak!

### 3. Eksekusi Dulu, Baru Tanya: `do...while`

Ini adalah adik kandung `while`, namun dia bertindak sedikit agresif.
Pada standar `while`, komputer akan mengecek dulu syaranya. Jika dari awal sudah Salah (False), bloknya 100% mutlak dan tidak akan pernah disentuh dieksekusi babar blas. 

Tapi di `do...while`, komputer akan menjankan kode **minimal 1 kali mutlak terlebih dahulu** sebelum sempat menoleh untuk mengecek apakah syarat kebenarannya valid.
```javascript
let hujan = false;

do {
    // Karena perintah "DO" ditulis duluan, ia langsung berjalan tak minta izin.
    console.log("Jemur pakaian di luas.");
    // Baru pas sampe mendarat baris bawah ini, mesin sadar "Eh, hujannya false deng! Stop ulangan."
} while (hujan === true); 
```

### 4. Tombol Panik Penghenti Darurat: `break`

Ketika sebuah putaran mesin *Looping* sedang agresif berputar ria (misal dari jatah target berputar 1 hingga 100), terkadang kita menemukan sebuah kondisi pencarian spesifik nyeleneh di tengah jalan yang membuat kita ingin seketika menghentikan total berhentinya *looping* mesin secara instan paksa tanpa menunggu nilai syaratnya batas atasnya tercapai mutlak habis. Fitur itu bernama saklar instruksi `break`.

```javascript
for (let id = 1; id <= 100; id++) {
    console.log("Mencari peserta " + id);

    // Kalau tiba-tiba nomer pesertanya cocok sama pencarian buronan "10"..
    if (id === 10) {
        console.log("Si Buronan ketemu! Segera stop pencarian, gausah capek lanjut ngitung ngecek ke 100!");
        break; // Putaran sisa perulangan ke 11 sampai 100 sukses dimusnahkan.
    }
}
```
