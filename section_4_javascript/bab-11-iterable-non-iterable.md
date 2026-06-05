# Bab 47: Iterable & Non-Iterable

## Tujuan Pembelajaran
- Memahami konsep data sekuel terukur (Iterable) dan bongkahan utuh sepotong tunggal (Non-Iterable).
- Mengetahui peruntukan perulangan bawaan `for...of` khusus untuk tipe Iterable.
- Mengetahui pengunaan perulangan spesifik untuk menyisir Object dengan `for...in`.

## Materi Utama

Dalam dunia struktur data JavaScript, benda-benda dikelompokkan berdasarkan kemampuannya untuk "dijabarkan" atau diurai secara berurutan langkah demi langkah secara hitungan jari. 

### 1. Apa itu Iterable (Bisa Diurai / Disisir)?

**Iterable** adalah wadah kumpulan data terstruktur yang mana potongan isinya **bisa ditarik keluar satu per satu secara berurutan (disisir)** oleh mesin program tanpa tersesat. Mereka ini benda-benda yang otomatis punya nomor urut gerbong kordinat panjangnya (*length*).

Hanya ada 2 Penguasa Raja Iterable Mutlak yang paling disering dipakai sehari-hari di JS:
- **String (Teks Huruf)**: Kata "Rumah" bisa diurai huruf demi huruf => `R` - `u` - `m` - `a` - `h`. 
- **Array (Kumpulan Daftar)**: Tumpukan `["Budi", "Siti"]` jelas 100% bisa disisir orang per orang, gerbong per gerbong.

**Kelebihan Istimewa Si Iterable: Menggunakan `for...of`**
Karena mereka diakui bisa disisir terurut, para tipe Iterable ini dikaruniai sebuah Mesin Looping gaul super pendek dari langit ES6 modern ketimbang memakai balok kuno `for(let i=0; i<x.length)` panjang yang melelahkan. Jurus itu bernama Loop **`for...of`**.

```javascript
/* Contoh Menyisir Teks String */
let kota = "JAKARTA";

// "Sapu setiap 1 abjad dari si kota, tampung sementara ke laci 'huruf', cetak terus berulang!"
for (let huruf of kota) {
    console.log(huruf);
}
// Layar otomatis mencetak runtut mendatar ke bawah murni 1 persatu otomatis:
// J
// A
// K
// (dstnya)

/* Contoh Menyisir Antrean Array */
let daftarSembako = ["Beras", "Telur", "Minyak"];

for (let barang of daftarSembako) {
    console.log("Membeli: " + barang);
}
// Mesin otomatis mendeteksi sendirinya ada 3 antrian, tanpa perlu kamu mengetik hitungan batasan sama sekali!
```

### 2. Konsep Oposisi: Non-Iterable (Gumpalan Tak Terurai Tuntas)

Berkebalikan total, sebagian besar tipe data lainnya di JS sifatnya adalah **Non-Iterable** (Gumpalan 1 bongkahan utuh mandul yang mustahil bisa dijabarkan per abjad).

- **Number**: Angka utuh murni `4500` tidak bisa diurai angkanya disisir 4 lalu 5 lalu 0 dst oleh mesin *looping for-of*.
- **Boolean**: Kata `true` atau `false` mutlak mentok di situ sebagai status kepastian, tak bisa dijabarkan sama sekali.
- **OBJECT `{}`**: Ini fakta unik paling menjebak! Walau isi properti Object itu sangat menjalar menjuntai panjang ada ratusan isi... Di mata komputer inti, ia tetaplah 1 Kartu KTP Gumpalan Murni Tak Bernomor Urut Kordinat Absen! Object **bukan** barang yang bisa di-*Loop* acak sembarangan menggunakan putaran mulus `for...of`. 

Lalu Muncullah Masalah:
*Gimana nasib nasibnya jika aku benar-benar dipaksa mutlak harus mengecek isi perut laci properti KTP di dalam sebuah Object satu persatu padahal dia bukan Iterable?*

**Solusi Object: Menggunakan `for...in`**
Karena Object diciptakan tiada dikaruniai nilai *Index/Length* (Urutan Keberapanya), maka dia punya pasangan *Looping* sedarah pelacak spesifiknya sendiri. Namanya adalah **`for...in`** (Huruf akhirnya "IN" ya, perhatikan ketajaman perbedaan penulisannya).

```javascript
let profilKaryawan = {
    namaDiri: "Dono",
    umur: 30,
    pekerjaan: "Programmer"
};

// Komputer akan ngubek ngoyak nyari Kunci-Kuncinya didalam properti object raksasa itu:
for (let kunciKiri in profilKaryawan) {
    console.log("Kategori: " + kunciKiri + " = Isinya: " + profilKaryawan[kunciKiri]);
}

// Hasilnya keekstrak tumpah kelayar urut satu persatu aman jaya tanpa crash:
// Kategori: namaDiri = Isinya: Dono
// Kategori: umur = Isinya: 30
// Kategori: pekerjaan = Isinya: Programmer
```

**Kesimpulan Cepat Mutlak:**
- Jika mau menyisir mulus daftar antrian gerbong panjang hitungan **Array/String** -> Pakailah pelacak **`for...of`**.
- Jika kepepet mutlak mengekstrak pembedahan struktur bongkar laci isi properti **Object** -> Pakailah pelacak **`for...in`**.
