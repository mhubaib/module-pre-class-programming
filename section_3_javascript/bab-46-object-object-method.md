# Bab 46: Object & Object Method

## Tujuan Pembelajaran
- Memahami konsep Object sebagai struktur data pengelompokan identitas yang kompleks.
- Membaca dan memodifikasi properti di dalam sebuah Object (Dot notation & Bracket notation).
- Membedakan antara variabel biasa (Properti) dengan fungsi yang hidup di dalam Object (Method).

## Materi Utama

Jika sebuah Array (Bab 44) ibarat **Buku Absen Siswa** yang isinya hanya daftar nama berjejer panjang tanpa detail yang spesifik (hanya dipanggil lewat nomor urut index), maka **Object** ibarat sebuah **Kartu Tanda Penduduk (KTP)**.

KTP memuat identitas lengkap dari satu entitas orang yang sama: ada isian untuk "Nama", "Alamat", "Golongan Darah", dll. Di dalam pemrograman JavaScript, Object digunakan untuk merekam detail struktur yang utuh dari sebuah benda maya.

### 1. Membuat dan Mengisi Anatomi Object

Object selalu dibuat menggunakan sepasang **Kurung Kurawal `{}`**. Elemen di dalamnya tidak berdiri sendiri, melainkan harus berpasangan menggunakan format `key: value` (Kunci : Isi Datanya).

```javascript
// Mendeklarasikan profil detail mobil menggunakan struktur Object
const mobilImpian = {
    merek: "Toyota",
    model: "Supra",
    tahunKeluaran: 2024,
    warna: "Silver",
    mesinMenyala: false
};
```
Perhatikan struktur di atas:
- `merek`, `model`, `tahunKeluaran` disebut sebagai **Key (Kunci/Properti)**. (Aturan namanya sama ketatnya seperti menamai variabel).
- `"Toyota"`, `2024`, `false` disebut sebagai **Value (Nilai Data/Isi)**.

### 2. Berinteraksi dengan Object (Membaca & Menulis)

Komputer tidak menggunakan nomor absen/index `0` seperti array jika kamu ingin memanggil tahun keluaran mobilnya. Kamu cukup memanggil langsung nama kuncinya (namanya *Key-value pair*).

**A. Dot Notation (Jalur Titik Murni)**
Ini adalah standar emas yang paling sering dipakai *programmer* untuk membaca properti mutlak karena ketikannya lebih bersih.
```javascript
// Memanggil nama propertinya dengan Titik `.`
console.log(mobilImpian.merek); // Layar mencetak: "Toyota"
console.log(mobilImpian.tahunKeluaran); // Layar mencetak: 2024

// Mengedit / menimpa warna mobil dari Silver menjadi Hitam
mobilImpian.warna = "Hitam Matte";
```

**B. Bracket Notation (Jalur Kurung Siku)**
Digunakan jika nama properti kuncinya berupa huruf aneh berspasi, atau jika kamu memanggil namanya melalui wadah variabel acak dari luar.
```javascript
// Membaca identitas lewat jalur nama bungkus kurung siku string
console.log(mobilImpian["model"]); // Layar mencetak: "Supra"

let x = "merek";
console.log(mobilImpian[x]); // Komputer membaca dari isi x, lalu layar mencetak: "Toyota"
```

### 3. Object Method (Mesin Hidup di Dalam Objek)

Sejauh ini, struktur data Object kita cuma menampung informasi mati (teks dan angka). Tapi tahukah kamu jika Object juga diizinkan memiliki "Aksi/Nyawa" di dalamnya?

Jika di dalam perut `Object` kamu menyelipkan fungsi seutuhnya (`function()`), maka fungsi itu akan ganti nama panggilannya diangkat statusnya menjadi sebuah **Method**.

```javascript
const ksatriaGame = {
    namaPanggung: "Bima",
    nyawaHP: 100,
    
    // Ini dinamakan METHOD: Sebuah Function yang diikat hidup melekat di dalam Object!
    serangMusuh: function() {
        console.log("Pedang Diayunkan! Ciiaaat!");
    },
    
    terkenaHit: function() {
        console.log("Aduh sakit!!");
        // Kata kunci rahasia "this." digunakan untuk menunjuk/memanggil saudara se-objeknya sendiri
        this.nyawaHP -= 10; 
    }
};

// Menjalankan method dalam object 
ksatriaGame.serangMusuh();     // Cetak: Pedang Diayunkan! Ciiaaat!
ksatriaGame.terkenaHit();      // Cetak: Aduh sakit!!
console.log(ksatriaGame.nyawaHP); // Darah sekarang mengurang otomatis tersisa bulat ke 90!
```

**Konsep Sakti Bawaan (`this`)**
Pada bedah fungsi `terkenaHit` di atas, kata kunci `this` bukan sekadar mantra kosong. Di dalam rumah Object, `this` adalah cara komputer merujuk ke *"diriku sendiri (Tuan KsatriaBima ini)"*. Jadi, `this.nyawaHP` diterjemahkan secara harfiah menjadi `"Ambil properti nyawaHP milik diriku Objectku sendiri ini, lalu kurangi 10"`.
