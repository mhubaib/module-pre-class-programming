# Bab 15: Z-Index & Overflow Elemen

## Tujuan Pembelajaran

- Memahami konsep sumbu-Z sebagai dimensi kedalaman dalam tata letak CSS.
- Mengendalikan urutan tumpukan elemen menggunakan properti `z-index`.
- Menguasai properti `overflow` untuk mengelola konten yang melebihi batas dimensi elemen.
- Membedakan keempat nilai `overflow` dan menentukan kapan masing-masing digunakan.

---

## Materi Utama

Pada bab-bab sebelumnya yang membahas properti `position`, kita telah melihat bahwa elemen dapat dilepas dari alur normal dokumen dan ditempatkan secara bebas di halaman. Kondisi ini menimbulkan situasi baru: ketika dua elemen atau lebih menempati posisi yang sama secara horizontal dan vertikal, elemen mana yang tampil di atas dan mana yang tertutup?

Bab ini membahas dua properti CSS yang menjawab pertanyaan tersebut: `z-index` untuk mengatur urutan tumpukan, dan `overflow` untuk mengelola konten yang melebihi batas elemen.

---

### 1. Sumbu-Z dan Properti `z-index`

Layar komputer menampilkan konten dalam dua dimensi: sumbu-X (horizontal) dan sumbu-Y (vertikal). **Sumbu-Z** adalah dimensi ketiga yang bersifat imajiner — merepresentasikan kedalaman atau jarak elemen dari layar menuju pengguna yang melihatnya.

Properti **`z-index`** digunakan untuk menentukan posisi suatu elemen pada sumbu-Z, yaitu mengatur elemen mana yang tampil di lapisan atas dan mana yang tersembunyi di lapisan bawah ketika beberapa elemen saling bertumpukan.

**Syarat penggunaan `z-index`:**
Properti `z-index` hanya aktif pada elemen yang memiliki nilai `position` selain `static` — yaitu `relative`, `absolute`, `fixed`, atau `sticky`.

**Aturan nilai `z-index`:**

- Nilai berupa bilangan bulat tanpa satuan.
- Semakin **besar** nilainya, semakin depan posisi elemen (lebih dekat ke pengguna).
- Semakin **kecil** nilainya — termasuk nilai negatif seperti `-1` — semakin elemen tersebut berada di lapisan belakang.
- Nilai bawaan (_default_) adalah `auto`, yang setara dengan `0`.

```css
.elemen-atas {
  position: absolute;
  z-index: 10; /* Tampil di lapisan paling depan */
}

.elemen-bawah {
  position: absolute;
  z-index: 2; /* Tertutup oleh elemen dengan z-index lebih tinggi */
}
```

**Analogi — Susunan Kertas di Atas Meja:**
Bayangkan beberapa lembar kertas diletakkan secara bertumpuk di atas meja. Kertas yang diletakkan paling akhir dengan posisi teratas akan menutupi kertas di bawahnya. Nilai `z-index` menentukan urutan tumpukan tersebut — semakin tinggi nilainya, semakin ke atas posisi elemen dalam susunan.

**Contoh penerapan:**

```html
<!-- HTML -->
<div class="arena-tumpuk">
  <div class="kartu kartu-merah">Merah (z-index: 1)</div>
  <div class="kartu kartu-biru">Biru (z-index: 3)</div>
  <div class="kartu kartu-hijau">Hijau (z-index: 2)</div>
</div>
```

```css
/* CSS */
.arena-tumpuk {
  position: relative;
  height: 150px;
}

/* Semua kartu harus memiliki position agar z-index aktif */
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
  z-index: 1; /* Lapisan paling bawah — tertutup oleh kedua kartu lainnya */
}

.kartu-biru {
  background-color: steelblue;
  top: 30px;
  left: 40px;
  z-index: 3; /* Lapisan paling atas — menimpa semua kartu lainnya */
}

.kartu-hijau {
  background-color: seagreen;
  top: 20px;
  left: 70px;
  z-index: 2; /* Lapisan tengah — menimpa kartu merah, tertutup oleh kartu biru */
}
```

> **Hasil:** Ketiga kartu saling bertumpukan di area yang sama. Kartu biru tampil paling depan, kartu hijau berada di tengah, dan kartu merah berada di lapisan paling bawah — mengikuti urutan nilai `z-index` masing-masing.

**Contoh penerapan umum — Modal dialog di atas konten halaman:**

```html
<!-- HTML -->
<div class="halaman-konten">
  <p>Ini adalah konten utama halaman.</p>
</div>

<div class="overlay"></div>
<div class="modal">
  <h2>Konfirmasi</h2>
  <p>Apakah Anda yakin ingin melanjutkan tindakan ini?</p>
  <button>Ya, Lanjutkan</button>
</div>
```

```css
/* CSS */
.halaman-konten {
  position: relative;
  z-index: 1; /* Konten utama berada di lapisan dasar */
}

/* Lapisan gelap semi-transparan yang menutupi konten di belakang modal */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 10; /* Di atas konten utama */
}

/* Kotak dialog yang tampil di atas overlay */
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 32px;
  border-radius: 8px;
  z-index: 20; /* Di atas overlay */
}
```

---

### 2. Mengelola Konten yang Melampaui Batas Elemen (`overflow`)

Ketika sebuah elemen memiliki dimensi yang ditetapkan secara eksplisit — misalnya `width: 200px` dan `height: 100px` — namun konten di dalamnya melebihi ukuran tersebut, konten akan melampaui batas elemen. Kondisi ini disebut **overflow**.

Properti **`overflow`** digunakan untuk menentukan bagaimana browser menangani konten yang melebihi batas dimensi elemen.

**Empat nilai yang tersedia:**

| Nilai     | Perilaku                                                                                |
| --------- | --------------------------------------------------------------------------------------- |
| `visible` | **(Bawaan)** Konten yang melebihi batas tetap ditampilkan di luar area elemen           |
| `hidden`  | Konten yang melebihi batas dipotong dan tidak ditampilkan                               |
| `scroll`  | Scrollbar selalu ditampilkan meskipun konten tidak melebihi batas; konten dapat digulir |
| `auto`    | Scrollbar hanya muncul jika konten benar-benar melebihi batas; tampilan lebih bersih    |

**Analogi — Konten dan Wadahnya:**
Bayangkan sebuah kotak penyimpanan dengan ukuran tertentu dan sejumlah buku yang perlu disimpan di dalamnya:

- `visible`: Buku yang tidak muat dibiarkan menonjol keluar dari kotak.
- `hidden`: Buku yang tidak muat dipotong agar kotak tetap rapi dan tertutup.
- `scroll`: Kotak dilengkapi laci geser yang selalu terpasang, sehingga semua buku dapat diakses dengan menggeser.
- `auto`: Laci geser hanya terpasang jika buku memang tidak muat; jika muat, kotak tampak seperti biasa.

```css
/* Contoh dasar keempat nilai */
.kotak-visible {
  overflow: visible;
}
.kotak-hidden {
  overflow: hidden;
}
.kotak-scroll {
  overflow: scroll;
}
.kotak-auto {
  overflow: auto;
}
```

**Contoh perbandingan langsung keempat nilai:**

```html
<!-- HTML -->
<div class="kotak kotak-visible">
  <strong>visible (bawaan)</strong><br />
  Konten yang melebihi batas elemen akan tetap ditampilkan dan dapat menimpa
  elemen lain di sekitarnya.
</div>

<div class="kotak kotak-hidden">
  <strong>hidden</strong><br />
  Konten yang melebihi batas elemen akan dipotong tepat di tepi elemen dan tidak
  dapat diakses.
</div>

<div class="kotak kotak-scroll">
  <strong>scroll</strong><br />
  Scrollbar selalu ditampilkan meskipun konten tidak melampaui batas. Konten
  dapat digulir untuk dibaca seluruhnya.
</div>

<div class="kotak kotak-auto">
  <strong>auto</strong><br />
  Scrollbar hanya muncul jika konten melampaui batas elemen. Tampilan lebih
  bersih saat konten sedikit.
</div>
```

```css
/* CSS */

/* Dimensi dasar yang diterapkan pada semua kotak */
.kotak {
  width: 200px;
  height: 80px;
  border: 2px solid #555;
  padding: 8px;
  margin-bottom: 40px; /* Jarak ekstra untuk mengantisipasi luberan pada mode visible */
  background-color: #fafafa;
  font-size: 0.9rem;
}

.kotak-visible {
  overflow: visible;
}
.kotak-hidden {
  overflow: hidden;
}
.kotak-scroll {
  overflow: scroll;
}
.kotak-auto {
  overflow: auto;
}
```

> **Hasil:**
>
> - Kotak `visible` — konten melampaui batas dan menimpa elemen di sekitarnya.
> - Kotak `hidden` — konten terpotong rapi di tepi elemen; bagian yang tersembunyi tidak dapat diakses.
> - Kotak `scroll` — scrollbar vertikal dan horizontal selalu terpasang; seluruh konten dapat digulir.
> - Kotak `auto` — scrollbar hanya muncul saat dibutuhkan; tampilan lebih rapi.

---

### 3. Mengontrol Overflow per Sumbu (`overflow-x` dan `overflow-y`)

CSS juga menyediakan properti terpisah untuk mengontrol overflow pada masing-masing sumbu secara independen:

- **`overflow-x`**: Menangani overflow pada arah horizontal.
- **`overflow-y`**: Menangani overflow pada arah vertikal.

Kombinasi keduanya berguna ketika hanya satu arah yang perlu dikendalikan — misalnya, tabel dengan banyak kolom yang memerlukan scroll horizontal tanpa mengganggu scroll vertikal halaman.

```css
.wrapper-tabel {
  overflow-x: auto; /* Scroll horizontal jika tabel lebih lebar dari kontainer */
  overflow-y: visible; /* Arah vertikal dibiarkan normal */
}
```

**Contoh penerapan — Tabel dengan banyak kolom pada layar sempit:**

```html
<!-- HTML -->
<div class="wrapper-tabel">
  <table class="tabel-lebar">
    <thead>
      <tr>
        <th>Nama</th>
        <th>Kota</th>
        <th>Pekerjaan</th>
        <th>Usia</th>
        <th>Status</th>
        <th>Divisi</th>
        <th>Tanggal Bergabung</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Andi Pratama</td>
        <td>Surabaya</td>
        <td>Frontend Developer</td>
        <td>27</td>
        <td>Aktif</td>
        <td>Teknologi</td>
        <td>12 Januari 2022</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
/* CSS */

/* Wrapper yang membatasi lebar dan mengaktifkan scroll horizontal */
.wrapper-tabel {
  overflow-x: auto;
  overflow-y: visible;
  border: 1px solid #ddd;
  border-radius: 6px;
}

/* Tabel dengan lebar lebih besar dari kontainernya */
.tabel-lebar {
  width: 900px; /* Sengaja lebih lebar dari kontainer untuk mensimulasikan kondisi nyata */
  border-collapse: collapse;
}

.tabel-lebar th,
.tabel-lebar td {
  border: 1px solid #ddd;
  padding: 10px 16px;
  white-space: nowrap; /* Mencegah teks dalam sel patah ke baris baru */
  font-size: 0.9rem;
}

.tabel-lebar th {
  background-color: #f0f0f0;
  text-align: left;
}
```

> **Hasil:** Pada layar yang lebih sempit dari lebar tabel, pengguna dapat menggeser tabel ke arah horizontal untuk melihat seluruh kolom, tanpa memengaruhi scroll vertikal halaman secara keseluruhan.

---

### Kesimpulan

Properti `z-index` dan `overflow` menangani dua kategori masalah yang sering muncul dalam tata letak CSS: elemen yang saling bertumpukan dan konten yang melebihi batas dimensi elemen. Keduanya merupakan alat penting untuk membangun antarmuka yang tertata dan dapat diprediksi.

**Panduan singkat penggunaan:**

- Perlu mengatur elemen mana yang tampil di atas saat bertumpukan? → Gunakan **`z-index`** (pastikan elemen memiliki `position` selain `static`).
- Perlu menyembunyikan konten yang melebihi batas elemen? → Gunakan **`overflow: hidden`**.
- Perlu konten yang dapat digulir di dalam elemen? → Gunakan **`overflow: auto`** atau **`overflow: scroll`**.
- Perlu scroll hanya pada satu arah? → Gunakan **`overflow-x`** atau **`overflow-y`**.

**Ringkasan Properti:**

| Properti     | Fungsi                                                          |
| ------------ | --------------------------------------------------------------- |
| `z-index`    | Menentukan urutan lapisan elemen pada sumbu-Z                   |
| `overflow`   | Menentukan penanganan konten yang melebihi batas dimensi elemen |
| `overflow-x` | Menentukan penanganan overflow pada arah horizontal             |
| `overflow-y` | Menentukan penanganan overflow pada arah vertikal               |

**Panduan Pemilihan Nilai:**

| Kebutuhan                                            | Pendekatan yang Disarankan                                |
| ---------------------------------------------------- | --------------------------------------------------------- |
| Elemen modal atau tooltip tampil di atas konten lain | `z-index` tinggi dengan `position: fixed` atau `absolute` |
| Elemen latar belakang tersembunyi di balik konten    | `z-index: -1` dengan `position: relative`                 |
| Konten yang melampaui batas disembunyikan            | `overflow: hidden`                                        |
| Area konten dapat digulir dengan tampilan bersih     | `overflow: auto`                                          |
| Scrollbar selalu ditampilkan tanpa syarat            | `overflow: scroll`                                        |
| Tabel lebar yang dapat digeser secara horizontal     | `overflow-x: auto` pada elemen pembungkus                 |
