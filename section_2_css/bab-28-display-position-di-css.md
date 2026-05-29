# Bab 28: Display & Position di CSS

## Tujuan Pembelajaran

- Membedah rahasia kemampuan mengubah watak bawaan HTML dengan properti `display`.
- Menguasai pemosisian elemen ala kordinat peta lewat properti `position`.
- Memahami bedanya letak statis, melayang abadi (fixed), tertancap (absolute), dan lengket (sticky).

## Materi Utama

Ini adalah bab yang paling ditakuti, namun akan seketika menaikkan tahta lebel programmer-mu jika dikuasai. Bab ini menjelaskan cara mendeportasi dan melayang-layangkan elemen di manapun sesuka hatimu.

### 1. Merubah Watak Asli Kotak (`display`)

Di Bab 13 kita pernah bahas ada dua sifat orisinil elemen HTML: Element Block (Makan batas 1 baris _full_) Element Inline (Nempel sebelahan tanpa nendang ke bawah). Sifat tersebut dibagikan oleh pencipta HTML saat mereka lahir.

Namun CSS mampu melakukan operasi plastik pengubah watak lewat instruksi **`display`**!

- `display: block;` : Merayu elemen kalem seperti `<span>` supaya mendadak menjadi serakah turun minta baris baru dan ukurannya bisa di-seting.
- `display: inline;` : Menghilangkan kekuatan arogansi tag `<div>` atau `<p>` sehingga ukurannya kerucut menyusut dan bisa disusun nempel sebelahan menyamping. Sayangnya ia jadi cacat, tidak bisa disetting ukuran `width` atau `height`-nya.
- `display: inline-block;` : Kasta **Hibrida Kesempurnaan**! Element ini akan bisa berteman rukun dipasang jejer menyamping (inline), TETAPI wujud dimensinya tetap reaktif bisa dinaikturunkan `width/height` nya selayaknya dewa Block. (Cocok untuk membuat grup menu bar di pojok kanan).
- `display: none;` : Ilmu menghilang. Element tersebut akan **terhapus lebur mutlak** dari permukaan layar (bahkan sisa ampas ukurannya margin paddingnya semua hilang dari perhitungan tata letak mata manusia, namun masih ngumpet di barisan code asli).

**Contoh `display`:**

```html
<!-- HTML -->
<span class="label-block">Saya span, tapi bertingkah seperti div!</span>
<div class="kotak-inline">Saya div, tapi mau berbagi baris!</div>
<div class="kotak-inline">Saya juga div, nempel di sebelahnya!</div>
<button class="menu-item">Beranda</button>
<button class="menu-item">Tentang</button>
<button class="menu-item">Kontak</button>
<p class="hantu">Saya paragraf yang lenyap dari muka bumi.</p>
```

```css
/* span dipaksa jadi block — bisa diatur lebar & tingginya */
.label-block {
  display: block;
  width: 200px;
  background-color: salmon;
}

/* div dijinak jadi inline — mengalah berbagi baris */
.kotak-inline {
  display: inline;
  background-color: skyblue;
}

/* Tombol menu jejer rapi, tapi tetap bisa diatur ukurannya */
.menu-item {
  display: inline-block;
  width: 100px;
  height: 40px;
  text-align: center;
  background-color: steelblue;
  color: white;
}

/* Paragraf ini menghilang total dari layar */
.hantu {
  display: none;
}
```

> **Hasil:** Label span kini memakan satu baris penuh, dua div berdampingan mesra, tiga tombol menu berjejer rapi dengan ukuran seragam, dan paragraf `.hantu` lenyap tak berbekas dari tampilan.

---

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

**Contoh `relative`:**

```html
<!-- HTML -->
<div class="kotak-normal">Kotak Normal A</div>
<div class="kotak-geser">Kotak Geser B</div>
<div class="kotak-normal">Kotak Normal C</div>
```

```css
.kotak-normal {
  background-color: lightgray;
  margin-bottom: 5px;
}

.kotak-geser {
  position: relative;
  top: 20px;
  left: 50px;
  background-color: orange;
}
```

> **Hasil:** Kotak B akan tampak bergeser 20px ke bawah dan 50px ke kanan dari posisi aslinya. Kotak C tidak naik mengisi kekosongan — "bekas tempat duduk" Kotak B tetap dipesan dan dikosongkan.

---

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

**Contoh `fixed`:**

```html
<!-- HTML -->
<div class="konten-panjang">
  <!-- Bayangkan ini artikel panjang yang bisa di-scroll -->
  <p>Paragraf 1... Lorem ipsum panjang sekali...</p>
  <p>Paragraf 2... terus ke bawah...</p>
  <!-- ...dan seterusnya... -->
</div>

<a class="tombol-wa-melayang" href="https://wa.me/6281234567890">
  💬 Chat WA
</a>
```

```css
.tombol-wa-melayang {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: #25D366;
  color: white;
  padding: 12px 18px;
  border-radius: 50px;
  text-decoration: none;
  font-weight: bold;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}
```

> **Hasil:** Tombol "Chat WA" akan selalu nongkrong di pojok kanan bawah layar — tidak peduli seberapa jauh pengunjung men-scroll halaman ke bawah, tombol itu tetap setia menempel di sana.

---

**C. Absolute (Tempelan Jangkar Parent)**
Status pergerakannya **mutlak** lepas hantu liar kayak `fixed`, NAMUN pergerakan kordinatnya patuh (diukur/dijangkarkan) pada pelukan induk terdekat (Bapaknya) yang juga sudah diseting tak-biasa (`relative`). _Ini rumus paling rumit namun andalan UI desain: Jika ingin memanipulasi obyek benda kecil di dalam perut kartu, maka si Kartu Induk harus di set Relative, dan si Benda Kecil (Absolute) bisa bebas lari-lari di dalam pagar batas kartu induknya itu._

**Contoh `absolute`:**

```html
<!-- HTML -->
<div class="kartu-produk">
  <img src="baju.jpg" alt="Baju Keren" />
  <h3>Baju Keren Limited</h3>
  <span class="label-diskon">SALE 50%</span>
</div>
```

```css
/* Kartu Induk WAJIB di-set relative sebagai "pagar kandang" */
.kartu-produk {
  position: relative;
  width: 200px;
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
}

/* Label diskon bebas ditempel di sudut manapun dalam kartu */
.label-diskon {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: red;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 12px;
  font-weight: bold;
}
```

> **Hasil:** Label "SALE 50%" akan menempel tepat di pojok kanan atas kartu produk, mengambang di atas gambar baju. Ia tidak memengaruhi posisi elemen lain di dalam kartu, dan selalu patuh pada batas si kartu induk — bukan pada batas seluruh halaman.

---

**D. Sticky (Lem Super Ganda)**
Penggabungan watak hibrida. Saat awal dia patuh normal diam di barisan `relative`. Namun saaat kamu mulai mescroll layar pelan-pelan ke bawah, dan ujung leher kepala kotak tersebut menabrak bibir atas layar, seketika ia akan berubah wujud jadi `fixed` tak bisa kabur terus ikut nge-scroll nempel di atap, lalu jika scroll dibalik lagi ke atas, lemnya akan luruh lepas dia kembali diam tidur nyantai di pojok asal.
_(Ini adalah jurus rahasia bikin deretan "Menu Header Navbar" yang nampak melekat lengket di atap saat ngeliat artikel panjang!)._

**Contoh `sticky`:**

```html
<!-- HTML -->
<header class="navbar-lengket">
  <nav>
    <a href="#">Beranda</a>
    <a href="#">Produk</a>
    <a href="#">Kontak</a>
  </nav>
</header>

<main>
  <p>Konten artikel sangat panjang di sini...</p>
  <!-- banyak paragraf ke bawah... -->
</main>
```

```css
.navbar-lengket {
  position: sticky;
  top: 0; /* Titik "lem aktif": tepat saat menyentuh tepi atas layar, dia nempel! */
  background-color: white;
  padding: 15px 30px;
  border-bottom: 2px solid #eee;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  z-index: 100; /* Pastikan navbar tampil di atas konten lain */
}

.navbar-lengket a {
  margin-right: 20px;
  text-decoration: none;
  color: #333;
  font-weight: bold;
}
```

> **Hasil:** Navbar pertama kali muncul di posisi normalnya di atas halaman. Begitu pengguna mulai scroll ke bawah dan navbar menyentuh tepi atas layar, ia langsung "nempel" dan tidak ikut terbawa scroll. Saat pengguna scroll balik ke atas, navbar kembali ke posisi semula dengan mulus.
