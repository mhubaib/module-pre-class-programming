# Bab 33: CSS Flexbox

## Tujuan Pembelajaran
- Memahami konsep Flexbox sebagai sistem tata letak 1-Dimensi yang fleksibel.
- Menguasai pengaturan poros utama (`Main Axis`) dan poros silang (`Cross Axis`).
- Mampu mendistribusikan ruang antar elemen dengan berbagai variasi `justify-content` dan `align-items`.
- Mengatur properti individual pada sisi Anak (Item) seperti `flex-grow` dan `flex-basis`.
- Mampu memusatkan elemen secara sempurna (Centering) dengan trik rahasia.

## Materi Utama

Ini adalah revolusi terbesar dalam sejarah gaya *styling* Web Modern. Di masa lalu, jika programmer ingin membuat 3 kotak berjajar menyamping dengan jarak sama rata, mereka harus pusing berurusan dengan properti kuno seperti `float` atau hitungan Margin/Persen matematika yang rentan meleset merusak halaman web.

Sejak kemunculan **Flexbox (Flexible Box)**, tata letak menyamping atau menumpuk tiba-tiba menjadi sangat ajaib, santai, dan anti pecah!

### 1. Konsep Poros: Main Axis & Cross Axis

Ini adalah fondasi kunci. Flexbox bekerja secara Spesialis **1 Dimensi**. Artinya, di suatu waktu ia murni hanya fokus menata deret menyamping vertikal (Baris) ATAU tumpukan meruncing (Kolom).

Bayangkan sebuah **Rel Kereta Api**.
- **Main Axis (Poros Utama)**: Arah kereta api dibariskan berjalan (Secara default/bawaan: Kiri ke Kanan).
- **Cross Axis (Poros Silang)**: Arah yang memotong rel secara tegak lurus (Secara default: Atas ke Bawah).

Jika kamu nanti mengubah arahnya menjadi baris kolom ke bawah, maka Main Axis-nya merubah orientasi menjadi Atas ke Bawah, dan Cross Axis-nya jadi Kiri ke Kanan.

### 2. Deklarasi Kekuatan Flexbox (Properti Si Bapak)

Untuk mengaktifkan tenaga sulap Flexbox, kita harus menerapkannya ke Bapak Wadahnya (**Container / Parent**), BUKAN menaruh instruksinya ke tag anak-anak box di dalamnya.

```css
.wadah-bapak {
    display: flex; /* Sabuk hitam diaktifkan! */
    border: 2px solid black;
    height: 300px;
}
.kotak-anak {
    background-color: orange;
    width: 50px;
}
```
*Hasil Instan:* Sifat alami tag `div` anak yang tadinya egois "Nurunin Baris ke Bawah memakan 1 layar penuh (Block)", akan mendadak ciut dipaksa berjejer mematuhi antrian sejajar Menyamping dari Kiri ke Kanan!

### 3. Penentuan Arah Rel Kereta (`flex-direction`)

Atur rel kereta berjalan kemana:
- `row` (Default): Anak berjejer mendatar dari kiri ke kanan.
- `row-reverse`: Berjejer mendatar secara terbalik! (Anak pertama/bungsu malah dipaksa terdepan di kiri, yang membalik urutan berjejer dari Kanan ke Kiri).
- `column`: Memaksa rel kereta putar balik untuk baris antrian memanjang tumpukan Atas ke Bawah.
- `column-reverse`: Tumpukan ke bawah layar lalu ditarik naiki terbang mumbul urutannya ke atas.

### 4. Distribusi Jarak Poros Utama (`justify-content`)

Jika masih ada ruangan sisa saat anak ditaruh berjejeran di atas Rel Main Axis (mendatar *row*), bagaimana sisa sela kerenggangannya disebar?

- `flex-start` (Default): Semua anak mepet jongkok di garis *Start* ujung kiri.
- `flex-end`: Semua anak numpuk bergerombol menepi nempel tembok di *End* ujung kanan.
- `center`: Semua anak bergerombol jadi satu asik rapat berkumpul di titik persis tengah-tengah rentang layar!
- `space-between`: Anak ke-satu nempel tembok kiri batas mati, anak terakhir mentok tembok kanan, sisanya dibagi jarak super longgar adil merata di rongga perantara perutnya.
- `space-around`: Jarak dibagi merata secara komplit, TAPI ditambahi sisa nafas spasi sedikit perbatasan di pinggir paling kiri kanan rel.
- `space-evenly`: Jarak spasi kosong mutlak dibelah rasio ukur persis presisi seukuran kotak sama rata ke tiap-tiap antar selipan bata.

*(Hafalan Praktis: `justify-content` adalah fokusmu jika ingin ngatur sebaran Jarak KANAN-KIRI asalkan bentuk keretamu Jejer Mendatar "Row").*

### 5. Perataan Poros Silang / Sumbu Baliknya (`align-items`)

Jika si Bapak punya perut Lebar dan Tinggi layang renggang lebar (`height: 300px`), dan gerbong anak dilempar menjejer mendatar asyik Kiri Kanan... pertanyaan besarnya: Apakah tubuh gerbong itu mengambang nyundul tempel atap perut bapaknya, ataukah guling ke dasar lantai pijakannya?

- `stretch` (Default): Karet elastis mengubah anak memanjang ngotot nutupin setinggi-tingginya sampai nyundul nempel atap atas hingga telapak nabrak plat landasan dasar kaki pantat bapaknya sekaligus!
- `flex-start`: Ngambang jongkok ditarik gravitasi nampak nempel di jajaran langit-langit Atap.
- `center`: Ngambang mengudara asyik seimbang di titk jantung perut atas-bawah.
- `flex-end`: Berendam nempel di pantat aspal bumi terbawah.

**Analogi Tusuk Sate:**
- Bapak wadah (`display: flex;`) adalah cerutu Panggangan Sate arang melintang panjang.
- Anak-anak kotaknya adalah Potongan Daging lezat tipis-tipis.
- `flex-direction: row` adalah batang Tusuk bambu Horizontal memanjang menjepit sekumpulan daging.
- `justify-content` ibarat pak juru panggang ngatur-ngatur geser melonggarkan jarak renggang daging satu dengan sebelah kirinya dan daging kanannya untuk dibakar disepanjang bambu sate.
- `align-items` ibarat menata di rak nomor mana daging diposisikan, apakah mau merapat dicium tinggi di dekat rak atap teratas jauh dari arang, atau diturunkan menempel panas di rak bara api terbawah?

### 6. Properti Kekuasaan untuk Anak (Si Item Flex)

Sang anak panggangan sate itu sendiri nyatanya ternyata juga dapat dipersenjatai status mandiri:

- **`flex-grow`**: Tingkat Nafsu Rakus. Seberapa doyan si anak mau meregangkan badannya menghisap sisa area kosong bapaknya? (Beri nilai `flex-grow: 1;` maka dia meral menyolong ruang kosong sepenuhnya memanjangkan diri sendirian).
- **`flex-shrink`**: Nilai keikhlasan si anak untuk nyusut menciut kurus menelan luka kalah apabila lebar layar monitor mulai kepepet sesak menyempit total.
- **`flex-basis`**: Nilai modal lebar ideal (`width`) murni si anak sebelum diizinkan perang di arena susut menyusut layar *grow/shrink* tadi (Sering dipakai setingan persen lebar kasarnya, eg: `flex-basis: 50%`).
- **`align-self`**: Kelakuan anak nakal. Dia memecahkan diri dari keseragaman instruksi `align-items` bapaknya, lantas bebas memilih titik berdiri ngambang vertikal posisi aneh lain cuman bagi dia sendiri!

**Analogi Kasir Supermarket (flex-grow):**
Bayangkan Bapak `display:flex` itu antrian Pita Kasir.
Anak-anaknya si kasir jejer berbaris manis. Namun anak ke-2 diberi jampi `flex-grow: 1;`.. Ia menjelma jadi raksasa gendut mengangkang membuka lengannya panjang menyabotase seluruh celah nafas spasi yang ada lalu memaksa pelanggan mepet, sementara kasir anak lainnya ngalah badannya tetep kurus-kering minggir ketendang pelan!

### Trik Super Rahasia: Centering Sempurna Vertikal & Horisontal!

Jurus rahasia turun-temurun yang telah sukses mengakhiri ratusan jam mimpi buruk stress Programmer era batu Zaman Netscape zaman dahulu selama 15 Tahun kebingungan!
Cara ini meletakkan Kotak Login persis mutlak ada di tengah-tengah Monitor Kordinat X (Mendatar) maupun Kordinat Y-nya (Tinggi)!

```css
.super-parent-layar {
    /* Nyalakan Dewa Flex! */
    display: flex;

    /* Posisi taruh jidat tengahkan sumbu mendatar X! */
    justify-content: center; 
    
    /* Gantung asik terbang di awang tengah sumbu Y (ketinggian) */
    align-items: center; 

    /* Kasih modal aspal tinggi pijakan 1 layar Full Monitor penuh TV-nya penonton */
    height: 100vh;
}
```