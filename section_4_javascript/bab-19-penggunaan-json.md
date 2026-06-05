# Bab 19: Penggunaan JSON

## Tujuan Pembelajaran

- Memahami pengertian JSON (JavaScript Object Notation) sebagai format pertukaran data universal.
- Membedakan antara struktur file JSON murni dengan Object bawaan JavaScript biasa.
- Menguasai perintah penerjemah data `JSON.stringify()` dan `JSON.parse()`.

## Materi Utama

Dalam menelusuri dunia pengembangan web modern, aplikasi _Front-End_ (yang kamu buat) pada suatu saat mutlak harus meminta data/berkomunikasi dengan _Server Back-End_ atau _Database_.

Namun, _Server_ mungkin dibangun menggunakan bahasa pemrograman lain (seperti Python, PHP, atau Go). Bahasa Python jelas tidak mengerti apa itu _struktur Object JavaScript_. Lalu, bagaimana caranya agar aplikasi kita bisa bertukar data biodata pengunjung lintas bahasa dengan Server?

Jawabannya adalah: **Berbicara menggunakan bahasa pertukaran universal (Data Format). Dan rajanya bahasa pertukaran data di alam semesta saat ini adalah JSON**.

### 1. Apa itu JSON?

**JSON** (singkatan dari _JavaScript Object Notation_) pada dasarnya adalah murni sebuah wujud **Mata Uang Teks (_String_)** panjang berekstensi `.json` yang cara penulisannya meniru bulat-bulat arsitektur penyusunan struktur Objek milik JavaScript (`{}`).

Karena JSON sejatinya hanyalah teks _String_ (karakter mentah), semua bahasa pemrograman apa pun di muka bumi ini dijamin pasti sanggup membaca, menyalurkan, dan membedahnya.

### 2. Pembeda Fatal Antara Object JS Vs File JSON

Walau rupa mukanya sama persis persis, format JSON memiliki undang-undang hukum ketikan yang amat kaku dan tidak boleh ditoleransi melenceng sedikit pun.

- **Syarat Mutlak 1**: Semua Kunci/Properti (_Keys_) HUKUMNYA WAJIB dikurung dibungkus selimut tanda Kutip Dua Ganda murni `""`. (Di JS biasa, _Key_ kan bebas polosan).
- **Syarat Mutlak 2**: Nilai _Value_ teks (_String_) di dalam isinya HUKUMNYA WAJIB Kutip Ganda `""` juga. Dilarang keras memakai Kutip Tunggal `''`.
- **Syarat Mutlak 3**: File murni JSON TIDAK BOLEH mengandung nyawa Fungsi (_Method_), rumus perhitungan _Date_ murni, ataupun isian _undefined_. Ia cuma mensupport data kaku mutlak: _String, Number, Boolean, Array, Object (Nested)_, dan _null_.

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

Lalu, bagaimana jadinya jika di dalam kode JavaScript kita tiba-tiba menerima paket lemparan _String JSON_ kaku tersebut dari Server luar?

Mesin JS kamu punya Mesin Penerjemah Dwi Fungsi bawaan pabrik namanya obeng Object global **`JSON`**.

**A. Mengubah Data JS Dibungkus Jadi JSON Teks Murni (`JSON.stringify()`)**
Ketika kamu mau mensubmit Formulir Pendaftaran Pijat Refleksi Webmu dan ingin melempar Datanya menyelusuri kabel internet lintas bahasa ke Server Go/PHP, **haram** melempar bongkahan _Object JS_-mu mentah-mentah. Kamu harus mencetaknya membungkus vakum dipress jadi wujud teks JSON melintang panjang.

```javascript
/* Data Objek Basah di RAM Komputermu */
const keranjangBelanja = {
  barang1: "Sampo",
  harga: 5000,
  dibayar: false,
};

// MANTERA BUNGKUS VAKUM:
const paketTeksVakumSiapKirim = JSON.stringify(keranjangBelanja);

console.log(paketTeksVakumSiapKirim);
// Layar mencetak teks kaku panjang mendatar:
// '{"barang1":"Sampo","harga":5000,"dibayar":false}'
```

**B. Membongkar Teks JSON Diubah Jadi Object JS (`JSON.parse()`)**
Skenario kebalikannya! Kamu baru saja menarik File Suplai dari Server berwujud teks kaku dan ingin memecahnya melucutinya kembali ke wujud bongkaran Objek Data lentur murni yang bisa di-_loop/disisir_ dan ditarik-tarik isi titik-nya (_Dot Notation_) di dalam perut memorimu.

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

_Bab ini adalah kunci vital jembatan pondasi awal komunikasi pernapasan antar Server sebelum masuk ke materi super gila menakjubkan selanjutnya di Javascript API (Fetch) di belakang ini!_
