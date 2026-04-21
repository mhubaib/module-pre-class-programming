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
