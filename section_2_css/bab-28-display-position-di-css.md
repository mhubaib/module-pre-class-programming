# Bab 28: Display & Position di CSS

## Tujuan Pembelajaran

- Membedah rahasia kemampuan mengubah watak bawaan HTML dengan properti `display`.
- Menguasai pemosisian elemen ala kordinat peta lewat properti `position`.
- Memahami bedanya letak statis, melayang abadi (fixed), tertancap (absolute), dan lengket (sticky).

## Materi Utama

Ini adalah bab rahasia yang paling ditakuti, namun akan seketika menaikkan tahta lebel programmer-mu jika dikuasai. Bab ini menjelaskan cara mendeportasi dan melayang-layangkan elemen di manapun sesuka hatimu.

### 1. Merubah Watak Asli Kotak (`display`)

Di Bab 13 kita pernah bahas ada dua sifat orisinil elemen HTML: Kaum Egois Block (Makan batas 1 baris _full_) dan Kaum Toleran Inline (Nempel sebelahan tanpa nendang ke bawah). Sifat tersebut dibagikan oleh Tuhan-nya HTML saat mereka lahir.

Namun CSS mampu melakukan operasi plastik pengubah watak lewat instruksi **`display`**!

- `display: block;` : Merayu elemen kalem seperti `<span>` supaya mendadak menjadi serakah turun minta baris baru dan ukurannya bisa di-seting.
- `display: inline;` : Menghilangkan kekuatan arogansi tag `<div>` atau `<p>` sehingga ukurannya kerucut menyusut dan bisa disusun nempel sebelahan menyamping. Sayangnya ia jadi cacat, tidak bisa disetting ukuran `width` atau `height`-nya.
- `display: inline-block;` : Kasta **Hibrida Kesempurnaan**! Element ini akan bisa berteman rukun dipasang jejer menyamping (inline), TETAPI wujud dimensinya tetap reaktif bisa dinaikturunkan `width/height` nya selayaknya dewa Block. (Cocok untuk membuat grup menu bar di pojok kanan).
- `display: none;` : Ilmu menghilang. Element tersebut akan **terhapus lebur mutlak** dari permukaan layar (bahkan sisa ampas ukurannya margin paddingnya semua hilang dari perhitungan tata letak mata manusia, namun masih ngumpet di barisan code asli).

### 2. Memindahkan Kotak dengan Koordinat (`position`)

Normalnya, struktur kotak turun mendasar berbaris ke bawah di Web itu dinamakan Document Flow (Alur Normal/`static`). Tapi misal kamu mau nempelin kotak Tombol Bantuan (Call Center) yang melayang terus memburu pelanggan miski digeser webnya... Pakailah keluarga **`position`**.

Jika kamu mengubah letak `position`, kamu WAJIB menggunakan tombol kemudi (Steer) berwujud properti: **`top`, `right`, `bottom`, `left`**.

**A. Relative (Tarik Ulur dari Tempat Asal)**
Jika diaktifkan, kordinatnya dihitung **berdasar letak asli awal** elemen itu berdiri. Dan anehnya, meski dia kamu geser-geser layangannya, posisi aslinya yang "kosong ditinggalkan" akan tetap memakan spasi hantu, menolak diinjak elemen lain.

```css
.kotak-geser {
  position: relative;
  top: 20px; /* Saya turun (menjauhi asbes atas) sejauh 20px dari titik awal lahirku! */
  left: 50px; /* Saya lari ke kanan (menjauhi batas kiri asli) sejauh 50px! */
}
```

**B. Fixed (Melayang Abadi di Kaca Layar)**
Dia lepas berstatus ghaib total dari dimensi rumah HTML (Dimenso document flow). Posisinya berpatokan pada bingkai TV/Layar kacamu (Viewport), BUKAN letak elemen asalnya. Cocok buat bikin "Pita Tanda Diskon" melayang yang nge-stuck terus tak bisa discroll kabur.

```css
.tombol-wa-melayang {
  position: fixed;
  bottom: 0px;
  right: 0px;
  /* Artinya: Menempel rapet di pojok kanan paling bawah bodi monitor, dipantek mati tak perduli discroll panjang sedunia */
}
```

**C. Absolute (Tempelan Jangkar Parent)**
Status pergerakannya **mutlak** lepas hantu liar kayak `fixed`, NAMUN pergerakan kordinatnya patuh (diukur/dijangkarkan) pada pelukan induk terdekat (Bapaknya) yang juga sudah diseting tak-biasa (`relative`). _Ini rumus paling rumit namun andalan UI desain: Jika ingin memanipulasi obyek benda kecil di dalam perut kartu, maka si Kartu Induk harus di set Relative, dan si Benda Kecil (Absolute) bisa bebas lari-lari di dalam pagar batas kartu induknya itu._

**D. Sticky (Lem Super Ganda)**
Penggabungan watak hibrida. Saat awal dia patuh normal diam di barisan `relative`. Namun saaat kamu mulai mescroll layar pelan-pelan ke bawah, dan ujung leher kepala kotak tersebut menabrak bibir atas layar, seketika ia akan berubah wujud jadi `fixed` tak bisa kabur terus ikut nge-scroll nempel di atap, lalu jika scroll dibalik lagi ke atas, lemnya akan luruh lepas dia kembali diam tidur nyantai di pojok asal.
_(Ini adalah jurus rahasia bikin deretan "Menu Header Navbar" yang nampak melekat lengket di atap saat ngeliat artikel panjang!)._
