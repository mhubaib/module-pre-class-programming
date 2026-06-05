# Bab 55: Penggunaan JSON

## Tujuan Pembelajaran
- Memahami pengertian JSON (JavaScript Object Notation) sebagai format pertukaran data universal.
- Membedakan antara struktur file JSON murni dengan Object bawaan JavaScript biasa.
- Menguasai perintah penerjemah data `JSON.stringify()` dan `JSON.parse()`.

## Materi Utama

Dalam menelusuri dunia pengembangan web modern, aplikasi *Front-End* (yang kamu buat) pada suatu saat mutlak harus meminta data/berkomunikasi dengan *Server Back-End* atau *Database*. 

Namun, *Server* mungkin dibangun menggunakan bahasa pemrograman lain (seperti Python, PHP, atau Go). Bahasa Python jelas tidak mengerti apa itu *struktur Object JavaScript*. Lalu, bagaimana caranya agar aplikasi kita bisa bertukar data biodata pengunjung lintas bahasa dengan Server?

Jawabannya adalah: **Berbicara menggunakan bahasa pertukaran universal (Data Format). Dan rajanya bahasa pertukaran data di alam semesta saat ini adalah JSON**.

### 1. Apa itu JSON?

**JSON** (singkatan dari *JavaScript Object Notation*) pada dasarnya adalah murni sebuah wujud **Mata Uang Teks (*String*)** panjang berekstensi `.json` yang cara penulisannya meniru bulat-bulat arsitektur penyusunan struktur Objek milik JavaScript (`{}`).

Karena JSON sejatinya hanyalah teks *String* (karakter mentah), semua bahasa pemrograman apa pun di muka bumi ini dijamin pasti sanggup membaca, menyalurkan, dan membedahnya.

### 2. Pembeda Fatal Antara Object JS Vs File JSON

Walau rupa mukanya sama persis persis, format JSON memiliki undang-undang hukum ketikan yang amat kaku dan tidak boleh ditoleransi melenceng sedikit pun.

- **Syarat Mutlak 1**: Semua Kunci/Properti (*Keys*) HUKUMNYA WAJIB dikurung dibungkus selimut tanda Kutip Dua Ganda murni `""`. (Di JS biasa, *Key* kan bebas polosan).
- **Syarat Mutlak 2**: Nilai *Value* teks (*String*) di dalam isinya HUKUMNYA WAJIB Kutip Ganda `""` juga. Dilarang keras memakai Kutip Tunggal `''`.
- **Syarat Mutlak 3**: File murni JSON TIDAK BOLEH mengandung nyawa Fungsi (*Method*), rumus perhitungan *Date* murni, ataupun isian *undefined*. Ia cuma mensupport data kaku mutlak: *String, Number, Boolean, Array, Object (Nested)*, dan *null*.

**Contoh Format Perbandingan:**
```javascript
// BENTUK ASLI LENTUR OBJEK JS BIASA:
const userJS = {
    namaUser: 'Asep',   // Pakai kutip tunggal aman
    umurAsep: 20
};

// --- BERBEDA 180° ---

// BENTUK KAKU BAKU FILE MURNI: data.json
{
    "namaUser": "Asep", // KEY DAN VALUE WAJIB KUTIP GANDA MUTLAK!
    "umurAsep": 20
}
```

### 3. Mesin Penerjemah Utilitas: Parse VS Stringify

Lalu, bagaimana jadinya jika di dalam kode JavaScript kita tiba-tiba menerima paket lemparan *String JSON* kaku tersebut dari Server luar? 

Mesin JS kamu punya Mesin Penerjemah Dwi Fungsi bawaan pabrik namanya obeng Object global **`JSON`**.

**A. Mengubah Data JS Dibungkus Jadi JSON Teks Murni (`JSON.stringify()`)**
Ketika kamu mau mensubmit Formulir Pendaftaran Pijat Refleksi Webmu dan ingin melempar Datanya menyelusuri kabel internet lintas bahasa ke Server Go/PHP, **haram** melempar bongkahan *Object JS*-mu mentah-mentah. Kamu harus mencetaknya membungkus vakum dipress jadi wujud teks JSON melintang panjang.

```javascript
/* Data Objek Basah di RAM Komputermu */
const keranjangBelanja = {
    barang1: "Sampo",
    harga: 5000,
    dibayar: false
};

// MANTERA BUNGKUS VAKUM:
const paketTeksVakumSiapKirim = JSON.stringify(keranjangBelanja);

console.log(paketTeksVakumSiapKirim);
// Layar mencetak teks kaku panjang mendatar: 
// '{"barang1":"Sampo","harga":5000,"dibayar":false}'
```

**B. Membongkar Teks JSON Diubah Jadi Object JS (`JSON.parse()`)**
Skenario kebalikannya! Kamu baru saja menarik File Suplai dari Server berwujud teks kaku dan ingin memecahnya melucutinya kembali ke wujud bongkaran Objek Data lentur murni yang bisa di-*loop/disisir* dan ditarik-tarik isi titik-nya (*Dot Notation*) di dalam perut memorimu.

```javascript
/* Ada lemparan paket teks beku kaku dari luar datang */
let paketTerimaJSON = '{"namanya":"Budi","lulus":true}'; 
// (Bentuknya Teks String. Kalau kamu nekat nge-console log "paketTerimaJSON.namanya" pasti isinya undefined karena dia sebongkah teks murni tak ada Key).

// MANTERA MELUCUTI MEMBONGKAR (PARSING/Unboxing):
const bongkaranDataObjectMurni = JSON.parse(paketTerimaJSON);

// Sekarang wujud dia hidup berganti menjadi Objek JS murni aseli:
console.log(bongkaranDataObjectMurni.namanya); 
// Hore Lulus! Tercetak: "Budi"
console.log(bongkaranDataObjectMurni.lulus); // Tercetak boolean: true
```

*Bab ini adalah kunci vital jembatan pondasi awal komunikasi pernapasan antar Server sebelum masuk ke materi super gila menakjubkan selanjutnya di Javascript API (Fetch) di belakang ini!*
