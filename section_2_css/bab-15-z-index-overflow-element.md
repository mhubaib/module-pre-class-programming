# Bab 29: Z-Index & Overflow Element

## Tujuan Pembelajaran
- Mengerti ilusi lapisan layer kertas 3 Dimensi via konsep Sumbu-Z.
- Mampu mengendalikan elemen mana yang menimpa atau ditimpa (Z-Index).
- Menguasai properti Overflow agar halaman web tidak bocor dan rusak struktur.

## Materi Utama

Dalam dua bab sebelumnya (termasuk soal Position), kita sadar bahwa elemen kini memiliki kesaktian "melayang di atas" struktur yang wajar, saling bertabrakan dan menjepit lokasi.

Kini masalah seriusnya: Jika dua elemen dipaksa bertumpukan melayang di tempat yang persis sama, mana yang terlihat di atas, dan mana yang ketindihan di bawah meja?

### 1. Rahasia Sumbu Ketiga (Sumbu-Z) dan `z-index`

Monitor komputer kita itu layar datar 2 Dimensi (Lebar itu sumbu-X, Tinggi itu sumbu-Y). Sumbu-Z adalah ukuran imajinatif "Kedalaman" yang membidik meruncing moncongnya mengarah **tembus ke wajahmu** selaku penonton.

Untuk memanipulasi tumpukan elemen seperti menyusun Kertas Folio di atas meja (siapa di depan mata, siapa dibelakang tertutup), pakailah **`z-index`**.

**Syarat Mutlak Pakai Z-Index:**
Perintah ini cuma aktif (hidup fungsinya) pada elemen yang properti **`position`**-nya BUKAN statis (alias dia diatur jadi `relative`, `absolute`, `fixed`, atau `sticky`).

**Aturan Penilaian Angka Leveling:**
Angkanya berupa bilangan bulat biasa. Tidak butuh px.
- Semakin **TINGGI** angkanya: Artinya layernya makin tebal naik menimpa mendekat ke layar wajah penonton (Kotak Terdepan).
- Semakin **RENDAH** (bahkan bisa angka minus `-1`): Artinya kartunya posisinya merayap menyelusup diseret ke posisi alas bawah.
- (Nilai dasar original otomatis di sistem adalah `auto` atau `0`).

```css
.kertas-atas {
  position: absolute;
  z-index: 10; /* Menang tumpukan (Maju tampil utuh) */
}
.kertas-bawah {
  position: absolute;
  z-index: 2; /* Kalah posisi, akan tertutup sebagian wajah si kertas atas */
}
```

**Contoh `z-index`:**

```html
<!-- HTML -->
<div class="arena-tumpuk">
  <div class="kartu kartu-merah">Merah (z: 1)</div>
  <div class="kartu kartu-biru">Biru (z: 3)</div>
  <div class="kartu kartu-hijau">Hijau (z: 2)</div>
</div>
```

```css
.arena-tumpuk {
  position: relative;
  height: 150px;
}

/* Fondasi bersama: semua kartu harus ber-position agar z-index aktif */
.kartu {
  position: absolute;
  width: 120px;
  height: 80px;
  padding: 8px;
  border-radius: 6px;
  font-weight: bold;
  color: white;
}

.kartu-merah {
  background-color: crimson;
  top: 10px;
  left: 10px;
  z-index: 1; /* Paling bawah, ketindihan dua kartu lainnya */
}

.kartu-biru {
  background-color: steelblue;
  top: 30px;
  left: 40px;
  z-index: 3; /* Paling atas, menimpa semuanya */
}

.kartu-hijau {
  background-color: seagreen;
  top: 20px;
  left: 70px;
  z-index: 2; /* Di tengah: menimpa merah, tapi ditimpa biru */
}
```

> **Hasil:** Ketiga kartu saling bertumpukan di area yang sama. Kartu Biru tampil paling depan menimpa semuanya, Kartu Hijau ada di tengah, dan Kartu Merah paling tertindih di lapisan terbawah — persis seperti susunan kertas folio di atas meja.

---

### 2. Bahaya Tumpahan Isi Air (`overflow`)

Bayangkan kamu memaksa memasukan air terjun galon ke dalam mulut botol yakult kecil. Hasilnya? Airnya akan banjir berhamburan kemana-mana membanjiri lantai menembus wadah aslinya.

Anatomi Web persis sama. Jika ada wadah `div` kardus yang dikerangkeng mati `width: 200px` dan `height: 100px`, TAPI kamu menjejalkan teks Esai sepanjang 50 Ribu Kata di perut box itu... kalimat tersebut akan hancur tumpah menembus keluar garis kotak (overflow)!

**Gaya Manajemen Pencegahan Tumpah (Properti `overflow`)**

Ada 4 senjata saksi penahan bendungan banjir CSS ini:

1. `overflow: visible;` (Bawaan Defaul Pabrik): Wadah pasrah dan membiarkan teks mbleber kabur dari perbatasan penjara kotak, menembus nimpa kotak orang lain agar kebaca visualisasinya.
2. `overflow: hidden;` (Besi Algojo Pembunuh): Teks yang tak muat akan **Dipenggal putus Hilang Lenyap** (Gaib disensor browser) secara paksa persis sejajar pagar perbatasan kotaknya terhenti.
3. `overflow: scroll;` (Teknologi Pintu Cerdas): Memaksa kardusnya merakit rel laci penggulung (**Scrollbar**) mati permanen mau isinya penuh atau kosong agar orang bisa tetep scrol baca isinya.
4. `overflow: auto;` (Mode Smart Responsive): Mirip `scroll`, namun cuma bakal ngeluarin panel rel penggulung vertikal JIKA memang nyata ada banjir isi data teksnya. Kalau isi datanya secuil dan muat, laci gulung scrool itu gak ditampikan.

**Analogi Pakaian di Koper Wisata:**
- Bawaan `visible`: Kamu maksa masukin baju sampai koper ga bisa ditutup (Baju ndlawer blewer kemana-mana).
- Model `hidden`: Semua lengan baju berlebih yang gak muat dijejel ke kardus bakalan digunting dibuang hancur demi koper bisa ketutup dipaksa utuh.
- Model `auto`: Kopermu punya resleting elastis yang nambah ngembang rapi nyiapin roda penggulung biar isinya bisa masuk tapi tetep ringkas.

_(Note: Kadang developer cuma ingin mengatasi tumpahan memanjang kesamping (Horizontal Scroll). Ia memanggil kodenya pakai spesifik sumbu `overflow-x: auto;` dan menyingkirkan vertikal `overflow-y`)_.

**Contoh `overflow`:**

```html
<!-- HTML: Kotak yang sama, keempat mode berbeda -->
<div class="kotak kotak-visible">
  <strong>visible (default)</strong><br>
  Ini teks sangat panjang yang sengaja dijejal ke dalam kotak kecil supaya meluber keluar batas dinding kotaknya dan menimpa elemen di sekitarnya tanpa rasa bersalah.
</div>

<div class="kotak kotak-hidden">
  <strong>hidden</strong><br>
  Ini teks sangat panjang yang sengaja dijejal ke dalam kotak kecil supaya meluber keluar batas dinding kotaknya dan menimpa elemen di sekitarnya tanpa rasa bersalah.
</div>

<div class="kotak kotak-scroll">
  <strong>scroll</strong><br>
  Ini teks sangat panjang yang sengaja dijejal ke dalam kotak kecil supaya meluber keluar batas dinding kotaknya dan menimpa elemen di sekitarnya tanpa rasa bersalah.
</div>

<div class="kotak kotak-auto">
  <strong>auto</strong><br>
  Ini teks sangat panjang yang sengaja dijejal ke dalam kotak kecil supaya meluber keluar batas dinding kotaknya dan menimpa elemen di sekitarnya tanpa rasa bersalah.
</div>
```

```css
/* Fondasi bersama: semua kotak dikunci ukurannya */
.kotak {
  width: 200px;
  height: 80px;
  border: 2px solid #333;
  padding: 8px;
  margin-bottom: 40px; /* Beri jarak ekstra buat si 'visible' yang suka banjir */
  background-color: #fffbe6;
}

/* 1. Teks mbleber bebas, tidak dipedulikan */
.kotak-visible {
  overflow: visible;
}

/* 2. Teks lebih dipenggal paksa di tepi kotak */
.kotak-hidden {
  overflow: hidden;
}

/* 3. Scrollbar selalu muncul, isi bisa digulir */
.kotak-scroll {
  overflow: scroll;
}

/* 4. Scrollbar hanya muncul jika isi memang meluber */
.kotak-auto {
  overflow: auto;
}
```

> **Hasil:**
> - Kotak `visible` — teks tumpah keluar dan menimpa kotak di bawahnya.
> - Kotak `hidden` — teks terpotong rapi tepat di tepi kotak, sisanya hilang tak terbaca.
> - Kotak `scroll` — scrollbar vertikal dan horizontal selalu terpasang meski kosong, isi bisa digulir.
> - Kotak `auto` — scrollbar muncul hanya saat dibutuhkan; kotak tampak bersih jika isi sedikit.

**Contoh bonus `overflow-x` untuk tabel lebar:**

```html
<!-- HTML -->
<div class="wrapper-tabel">
  <table class="tabel-lebar">
    <tr>
      <th>Nama</th><th>Kota</th><th>Pekerjaan</th>
      <th>Umur</th><th>Status</th><th>Hobi</th>
    </tr>
    <tr>
      <td>Budi</td><td>Yogyakarta</td><td>Developer</td>
      <td>25</td><td>Lajang</td><td>Ngoding</td>
    </tr>
  </table>
</div>
```

```css
/* Wrapper hanya diberi scroll horizontal, vertikal dibiarkan normal */
.wrapper-tabel {
  overflow-x: auto;
  overflow-y: visible;
  border: 1px solid #ccc;
}

.tabel-lebar {
  width: 800px; /* Lebih lebar dari layar HP — dijamin butuh scroll samping */
  border-collapse: collapse;
}

.tabel-lebar th,
.tabel-lebar td {
  border: 1px solid #ddd;
  padding: 10px 16px;
  white-space: nowrap; /* Mencegah teks patah baris sendiri */
}
```

> **Hasil:** Di layar HP yang sempit, tabel bisa digeser ke kanan-kiri secara horizontal tanpa merusak layout halaman. Scrollbar vertikal halaman tetap normal seperti biasa.
