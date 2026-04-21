# Bab 34: CSS Grid

## Tujuan Pembelajaran
- Mengenali batas fiksi sistem Flexbox dan alasan munculnya CSS Grid.
- Membuka dimensi ke-2 (Baris dan Kolom menyilang sekaligus).
- Membedah anatomi dan istilah-istilah teknis dalam sistem CSS Grid.
- Mampu mendesain pondasi petak ubin dengan `grid-template-columns` & `grid-template-rows`.
- Menggunakan satuan jagoan baru pecahan ubin: `fr` (Fraction) dan fungsi `repeat()`.

## Materi Utama

Di Bab 33 kita melihat keajaiban Flexbox. Namun ada kelemahannya: Flexbox hanya jago menata antrian 1 Arah secara bersamaan (Cuma bisa Baris saja, atau Kolom saja). 

Jika kamu diminta membikin papan Papan Catur, Mosaik Foto Galeri Komplek, atau kerangka Layout Halaman Facebook lama (Ada Navbar di Atas, Sidebar Teman di Kiri, Konten Video di Tengah, Footer Paling Bawah)... Flexbox akan menyerah.

Selamat menyambut Kasta Tertinggi Aristokrat penataan letak: **CSS GRID**. Ini adalah mandor tata perkotaan **2-Dimensi (Simultan Atas-Bawah dan Kanan-Kiri barengan).**

---

### Istilah Penting dalam CSS Grid

Sebelum mulai mengoding dan mengatur ubin, kita harus memahami "bahasa" yang digunakan oleh para engineer Grid. Bayangkan kita sedang membangun sebuah kompleks perumahan:

| Istilah | Penjelasan Singkat | Analogi |
| :--- | :--- | :--- |
| **Grid Container** | Elemen induk yang memiliki `display: grid`. | Seluruh area tanah kompleks perumahan. |
| **Grid Item** | Elemen anak langsung di dalam container. | Rumah-rumah yang berdiri di dalam kompleks. |
| **Grid Line** | Garis pembagi horisontal dan vertikal. | Pagar pembatas antar kaveling tanah. |
| **Grid Track** | Ruang di antara dua garis grid (Baris atau Kolom). | Jalan raya atau deretan blok rumah. |
| **Grid Cell** | Unit terkecil dari grid (pertemuan 1 baris & 1 kolom). | Satu petak kaveling tanah terkecil. |
| **Grid Area** | Ruang yang dikelilingi oleh 4 garis grid (bisa banyak cell). | Gabungan beberapa kaveling (misal untuk taman atau ruko). |

---

### Kamus Semua Properti CSS Grid

Berikut adalah daftar perintah sakti secara lengkap untuk mengendalikan tata kota Grid ini. 

**A. Properti untuk Container (Si Bapak / Pemilik Tanah)**
| Properti | Fungsi |
| :--- | :--- |
| `display: grid;` | Mengaktifkan mode arsitek grid. |
| `grid-template-columns` | Menentukan jumlah dan lebar kolom (vertikal) yang direncakan. |
| `grid-template-rows` | Menentukan jumlah dan tinggi baris (horisontal) yang direncakan. |
| `gap` (atau `grid-gap`) | Mengatur jarak selokan antar ubin secara vertikal dan horisontal. |
| `row-gap` / `column-gap` | Mengatur jarak selokan khusus untuk baris saja atau kolom saja. |
| `justify-items` | Meratakan orientasi isi anak di dalam ubinnya sendiri secara mendatar (kiri/tengah/kanan). |
| `align-items` | Meratakan orientasi isi anak di dalam ubinnya sendiri secara vertikal (atas/tengah/bawah). |
| `justify-content` | Meratakan keseluruhan balok grid jika ukurannya lebih kecil dari lebar layar wadahnya. |
| `align-content` | Meratakan keseluruhan balok grid jika tingginya lebih kecil dari tinggi layar wadahnya. |
| `grid-template-areas` | Memberi nama area blok untuk dipanggil secara visual (Sangat mempermudah baca kode). |
| `grid-auto-rows` / `grid-auto-columns` | Menentukan ukuran ubin ekstra pabila ada konten meluap (Grid Implicit). |
| `grid-auto-flow` | Menentukan bagaimana algoritma mengisi slot ubin kosong (apakah ditumpuk ke baris bawah atau kolom samping). |

**B. Properti untuk Item (Si Anak / Rumahnya)**
| Properti | Fungsi |
| :--- | :--- |
| `grid-column-start` / `end` | Menentukan garis pagar mana kolom dimulai dan pagar mana dia berakhir mendatar. |
| `grid-row-start` / `end` | Menentukan garis pagar mana baris mulai dan pagar mana dia berakhir vertikal. |
| `grid-column` | Shorthand (jalan pintas) untuk start dan end kolom (misal `1 / 3`). |
| `grid-row` | Shorthand (jalan pintas) untuk start dan end baris (misal `1 / 4`). |
| `grid-area` | Memberikan nama pada elemen agar nyambung dengan `grid-template-areas` bapaknya, atau penulisan sangat super singkat col/row. |
| `justify-self` | Penyesuaian horizontal khusus untuk anomali pada satu anak ini saja. |
| `align-self` | Penyesuaian vertikal khusus untuk anomali pada satu anak ini saja. |

---

### 1. Sabuk Pengaman Grid

Mirip ajaran Bab Flexbox, ilmu utamanya dihidupkan pada Petak Bapak/Parent.

```css
.wadah-album {
    display: grid; /* Kekuatan arsitek ubin diaktifkan */
}
```

### 2. Memetakan Jalur Ubin Lantai (`template`)

Jika kamu bilang ke Tukang Bangunan "Tolong pasangkan lantai keramik", sang Tukang akan tanya: "Mau keramik ukuran berapa sentimeter dan berapa biji per sekat?".

- `grid-template-columns`: Menjebol pemisah pagar Kolom (Vertikal).
- `grid-template-rows`: Memilah irisan tinggi Baris (Horisontal).

```css
.papan-bapak {
    display: grid;
    /* Bikin 3 Jalur Kolom Vertikal: Lebar 100px, 200px, 100px */
    grid-template-columns: 100px 200px 100px;
    
    /* Bikin 2 Celah Baris Mendatar: Tinggi 50px dan 100px */
    grid-template-rows: 50px 100px;
}
```

**Satuan Cerdas Milik Grid: `fr` (Fraction / Pecahan)**
`px` itu ribet dan tak melar lentur (cek Bab 32). Grid mengenalkan serdadu baru bernama `fr`. Konsepnya seperti "Jatah Sisa Warisan layar".

```css
.arsitek-fr {
    display: grid;
    /* Bagi layar jadi 3 Kolom sama rata elastis (1 Jatah, 1 Jatah, 1 Jatah) */
    grid-template-columns: 1fr 1fr 1fr;
}
```
*Trik Pengulangan `repeat()`*: 
Daripada nulis: `grid-template-columns: 1fr 1fr 1fr 1fr 1fr;`
Orang pintar pakai jurus: `grid-template-columns: repeat(5, 1fr);`

**Tips Profesional Paling Sakti: `minmax()`**
Ingin kolom lentur elastis tapi tak bisa menciut terlalu jelek/kecil? Gunakan kombinasi `repeat` dan `minmax()`.
```css
/* "Bikin kolom sebanyak-banyaknya otomatis, tapi paling kecil kudu 200px tebelnya, sisanya ngaret melar!" */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); 
```

### 3. Explicit Grid vs Implicit Grid (Grid Terencana vs Grid Otomatis)

Ini adalah konsep cerdas di mana browser membantu kita menata ubin yang "lupa" kita rencanakan.

- **Explicit Grid (Grid Terencana)**: Adalah ubin yang kamu buat secara sadar kemauannya menggunakan `grid-template-columns` atau `grid-template-rows`. Kamu sudah tentukan pastinya.
- **Implicit Grid (Grid Otomatis)**: Adalah baris atau kolom baru yang **dibuat otomatis oleh browser** ketika jumlah konten/item (bambunya/anaknya) yang kamu masukkan ketambahan dan jumlahnya melebihi kapasitas ubin yang kamu rencanakan explicit tadi.

**Analogi Pesta Ulang Tahun:**
- **Explicit**: Kamu mengundang 10 orang teman dan menyiapkan **10 Kursi** di meja makan. Semuanya tertata rapi sesuai rencana.
- **Implicit**: Ternyata ada 5 orang teman lagi yang datang mendadak tanpa undangan. Karena kursinya kurang, browser (si tuan rumah yang baik) otomatis akan **menarik kursi tambahan** dari dapur dan membuat baris tempat duduk baru di belakang agar tamu tambahan tetap duduk rapi.

Kamu bisa mengatur seberapa tinggi "kursi tambahan ajaib" tersebut menggunakan properti `grid-auto-rows`:
```css
.papan-pesta {
    display: grid;
    grid-template-columns: repeat(2, 1fr); /* Terencana cuma 2 kolom */
    
    /* Jika ada blok anak meluap (Implicit), cetak otomatis tinggi baris barunya 100px statis */
    grid-auto-rows: 100px; 
}
```

### 4. Jarak Selokan antar Ubin (`gap`)

Saat ubin grid tertanam jejer, mereka nempel mepet. Jangan repot pasang si Margin (Bab 25) manual satu-satu di file Anak. Grid punya properti jarak selokan sendiri!

```css
.album-foto {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px; /* Selokan spasi horisontal maupun vertikal semuanya dipukul rata jarak 20px! Menghemat kode drastis. */
}
```

### 5. Lompatan Kuasa Penuh (Menelan Petak Orang / Grid Spanning)

Ini perbedaan mutlak kekastaan Flexbox dan Grid. Pada Grid, si anak Petak boleh Serakah menguasai perluasan kapling tanah (mencaplok sel di sebelahnya).

Ingat analogi batas **Grid Line (Garis Pagar)**: Jika kita punya 3 kolom ubin, maka kita punya **4 Garis Pagar**. (Garis 1 di paling pinggir kiri, Garis 4 di bibir paling ujung kanan layarnya).

Misal kita panggil anak ruko nomer satu, ingin dia melebar mendominasi jalur dari garis rel 1 tembus numplak nutupin rel ke 3.
Gunakan properti `grid-column: [garis-mulai] / [garis-akhir];`.

```css
.kepala-header-kerakus {
    background-color: merah;
    /* Melebar mulai dari garis setapak 1... Membentang pecah nutupin, berhenti sesaat menabrak garis ke-4 ujung layar */
    grid-column: 1 / 4; 
    
    /* Dia juga melahap 2 baris kebawah secara vertikal */
    grid-row: 1 / 3;
}
```
Dengan instruksi rakus ini, si Header akan merentang super lebar, sementara anak ruko ke-2 akan otomatis ditendang mengalah, mencari slot ubin sisa kosong di sekitarnya tanpa berani merusak bangunan yang sudah diduduki Header.

**Analogi Buku Bergaris (Buku Strimin Matematika):**
- Flexbox itu ibarat menata buku tebal di atas Rak Perpustakaan 1 Baris Papan. (Kalo buku kebanyakan, bingung geser dorongnya).
- Grid itu ibarat insinyur arsitek menggambar pakai **Buku Berantai Strimin Kotak**. Kita mau corat-coret nge-blok ubin berukuran 2x3 kotak, lalu disebelahnya blok kecil 1x1, dengan sangat dijamin ukirannya tak akan menggeser ambyarkan letak kotak lain pabila proporsinya sudah dipetakan dengan rapi.
