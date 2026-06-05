# Bab 51: Destructuring, Spread Operator, Rest Parameter

## Tujuan Pembelajaran
- Menguasai jurus *Destructuring* untuk membongkar cepat isi array dan object.
- Mampu memecah, menduplikasi, dan menggabungkan array/object secara sakti memakai *Spread Operator*.
- Memahami kegunaan *Rest Parameter* untuk menampung argumen inputan mesin yang jumlahnya bervariasi tak tertebak batasannya.

## Materi Utama

Ini adalah Bab di mana kamu akan diperkenalkan secara penuh ke fitur-fitur pamungkas *ES6 JavaScript*. Fitur ini murni mutlak tentang menulis kode yang jauh lebih pendek, bersih, estetik, dan menakjubkan daripada syntax versi jadul. Jika esok lusa kamu belajar ReactJS atau Vue, tiga jurus sintaks ini adalah detak jantung yang bernapas berkeliaran menghiasi 80% baris di setiap blok file kodinganmu.

### 1. Alat Pembongkar Cepat (Destructuring Assignment)

**Destructuring** adalah fitur peretas jalan pintas yang memfasilitasimu membongkar, mengekstrak, mengeluarkan langsung berberapa properti nilai gumpalan dari dalam Array/Object, lantas seraya instan langsung menjadikannya sebagai variabel-variabel mandiri bebas tugas dalam 1x hela nafas barisan ketik!

**A. Membongkar Object KTP:**
```javascript
// Data aseli bawaan Object Jadul
const heroGame = { namaHero: "GatotKaca", kelasBertarung: "Tank", kekuatanNyawa: 5000 };

/* CARA JADUL KUNO YANG SANGAT BOROS LELAH DIKETIK PANJANG BARIS BANYAK : */
// let namaHero = heroGame.namaHero;
// let kekuatanNyawa = heroGame.kekuatanNyawa;

/* JURUS LAHIRNYA DESTRUCTURING ES6 MODERN SANGAT RINGKAS (1 BARIS MATI MUTLAK) : */
const { namaHero, kekuatanNyawa } = heroGame;

console.log(namaHero); // Mesin Tahu! Layar tercetak murni : "GatotKaca"
console.log(kekuatanNyawa); // Tercetak 5000.
```

**B. Membongkar Antrean Array:**
Sama halnya dengan array, kamu bisa mencabut urutan nilainya berdasar kordinat index dan membocorkannya jadi wadah tersendiri semerta-merta:
```javascript
const daftarSumbangan = ["Beras", "Uang", "Pakaian", "Indomie"];

// Membongkar 2 urutan terawal saja mutlak!
const [kebutuhanDasar, donasiTunai] = daftarSumbangan;

console.log(kebutuhanDasar); // Tercetak: "Beras" 
console.log(donasiTunai); // Tercetak: "Uang"
```

### 2. Menyebarkan Memuncratkan Serpihan Array (Spread Operator `...`)

**Spread Operator** ditandakan mutlak dengan bentuk ketik gaib berupa **tiga biji Titik Tiga** (`...`). 

Khasiat utamanya yang tak masuk akal sangat sakti adalah: Ia sanggup melepas sekrup telanjang, menggugurkan membongkar cangkang kotak dari wadah ikatan bungkusan array (atau sebuah properti object), lantas mutlak menghablurkan muncratkan menyebarkan kepingan eceran sebaris datanya agar bisa disedot disalin murni ditelan masuk oleh Array/Object wadah buatan laci rumah yang Baru tanpa menabrak hancur tumpah berceceran merusak strukur referensi asali gawaianya!.

**A. Menduplikasi Mengkopi Copy-Paste Aman:**
```javascript
let timUtama = ["Asep", "Budi"];

// Murni mencetak Array baru wadah baru perawan, dengan jalan menyebur memuncratkan memecah 2 orang tim utama tadi ditambahi item pendatang diakhir.
let timGabunganBaru = [...timUtama, "Chika", "Deni"];

console.log(timGabunganBaru); // Mutlak rukun gabung utuh : ["Asep", "Budi", "Chika", "Deni"]
```
Jurus duplikasi rahasia ini menendang mutlak kengerian mimpi buruk *Bug Referensi Pointer Memori* di kalangan Programmer JS lawas!.

**B. Menggabung Object Secara Sintaks Rapi:**
```javascript
const dataKendaraan = { ban: 4, stir: 1 };
const mesinKendaraan = { silinder: "V8", bensin: "Pertamax" };

// Menghampar menyatukan rapi 2 Object berbeda jadi tubuh makhluk utung perpaduan!
const mobilBalapGilaMewah = { ...dataKendaraan, ...mesinKendaraan, warna: "Merah Menyala" };
```

### 3. Penampung Sisa Vakum Berjuta Argumen (Rest Parameter)

Sintaks ini menggunakan logo kembar sama persis gila yaitu tiga titik **`...`**, tetapi wujud beda lokasinya disumpalkan di dalam **Telinga Lubang Parameter Function**.

Tugas *Rest Parameter*: Memungut dan menelan vakum menghisap habis semua *unlimited* tak terhingga jumlah data argument input mentah apapun yang dilempar ditembakkan disorongkan pengguna pengunjung dari luar pelatuk koding, untuk dikumpulkan dipaket mutlak otomatis menjadi 1 buah wadah bingkisan utuh bungkusan Array yang sangat rapi di lambungnya mesin.

```javascript
/* Mesin Fungsi ini sengaja ga tahu dan masa bodoh, apakah kelak pelangan mesen beli 1 benda doang atau lempar masuk borongan berbelanja 50 daftar barang sekaligus?? */
function boronganCheckout(...barangBelanjaan) {
    // Kini semua barang yg dilempar masuk, sudah mutlak rapi dirantai terbuat jadi 1 Array yg utuh padu gila bernama keranjang 'barangBelanjaan' di perut lambungnya si fungsi!
    console.log("Keranjangmu menahan tumpukan " + barangBelanjaan.length + " buah barang.");
    console.log(barangBelanjaan);
}

// Lempar sembarang masuk 5 buah data murni tak beraturan :
boronganCheckout("Minyak", "Telur", "Mie", "Roti", "Susu"); 

// Layar mesin dengan pintarnya memilah menyusun ngitung rapi jadi Array: 
// Keranjangmu menahan tumpukan 5 buah barang.
// ["Minyak", "Telur", "Mie", "Roti", "Susu"]
```

**Kesimpulan Dewa Terakhir JS Konsep Canggih:**
Ketiga barisan jurus tiga titik mutakhir inilah (`{}`, `...` dan `...` argumen) yang sukses mengantarkan membelah samudera takdir pemakaian Javascript purba jadul menuju wajah bahasa kelas kakap mentereng perancang UI Website mutakhir termasyur seperti ranah pengembagan industri korporat hari ini!
