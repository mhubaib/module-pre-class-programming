# Bab 24: CSS Padding

## Tujuan Pembelajaran

- Memahami fungsi Padding sebagai "ruang napas" di dalam elemen.
- Menguasai cara penulisan Padding secara spesifik (Atas, Kanan, Bawah, Kiri).
- Menggunakan teknik penulisan singkat (Shorthand) untuk efisiensi kode.

## Materi Utama

Mengingat kembali konsep **Box Model** di Bab 22, kita tahu bahwa setiap elemen HTML adalah sebuah kotak. Terkadang, teks di dalam kotak terlalu mepet dengan tepi kotaknya sendiri, membuatnya terlihat sesak dan sulit dibaca. Di sinilah **Padding** bertugas menyelamatkan desainmu.

### 1. Apa itu Padding?

**Padding** adalah jarak ekstra atau "bantalan" kosong yang berada **di antara isi (konten/teks) dengan batas pinggir kotaknya**. Ruang kosong hasil Padding akan otomatis mengikuti warna latar belakang (background) dari kotak tersebut.

**Analogi Ruang Tamu:**
Bayangkan elemenmu adalah sebuah Ruang Tamu, dan teks di dalamnya adalah Sofa. Jika kamu tidak memberi Padding, sofamu akan menempel rapat menyentuh tembok. Padding adalah seberapa jauh kamu mau menarik sofa tersebut ke tengah ruangan agar ada jarak untuk lewat antara sofa dan tembok.

### 2. Mengatur Padding Secara Spesifik

Kita bisa mengatur ketebalan bantalan di keempat sisi kotak secara terpisah. Ada 4 properti spesifik yang disediakan CSS:

- `padding-top`: Bantalan atas.
- `padding-right`: Bantalan kanan.
- `padding-bottom`: Bantalan bawah.
- `padding-left`: Bantalan kiri.

```css
.kotak-pengumuman {
  background-color: lightgreen;
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 15px;
  padding-right: 15px;
}
```

_Hasilnya: Teks di dalam kotak tidak akan menyentuh garis pinggir hijau, melainkan memiliki jarak jeda 20px di atas/bawah dan 15px di kiri/kanan._

### 3. Teknik Shorthand (Penulisan Singkat)

Menulis 4 baris kode hanya untuk mengatur Padding terasa lambat dan membuat file CSS cepat membengkak. Karena itu, programmer profesional menggunakan teknik **Shorthand**. Kamu cukup memanggil properti `padding` dan memasukkan nilainya sekaligus dengan spasi.

Aturan pembacaannya seperti perputaran arah **Jarum Jam**: Dimulai dari Atas - Kanan - Bawah - Kiri (Top - Right - Bottom - Left).

**A. Lengkap 4 Nilai (Atas-Kanan-Bawah-Kiri)**

```css
.kotak {
  padding: 25px 50px 75px 100px;
}
/* Artinya: Atas 25, Kanan 50, Bawah 75, Kiri 100 */
```

**B. Jika hanya 3 Nilai (Atas - Kiri/Kanan - Bawah)**

```css
.kotak {
  padding: 25px 50px 75px;
}
/* Artinya: Atas 25, Kiri dan Kanan sama-sama 50, Bawah 75 */
```

**C. Paling Sering Dipakai: 2 Nilai (Atas/Bawah - Kiri/Kanan)**
Jika kamu ingin nilai atas sama dengan bawah, dan kiri sama dengan kanan (Simetris).

```css
.tombol {
  padding: 10px 20px;
}
/* Artinya: Atas-Bawah 10px, Kiri-Kanan 20px */
```

_(Tips: Gunakan kombinasi ini saat kamu membuat sebuah Tombol/Button agar proporsinya enak dilihat)._

**D. Cuma 1 Nilai (Semua Sisi Pukul Rata)**

```css
.kartu {
  padding: 20px;
}
/* Artinya: Keempat sisi atas, kanan, bawah, kiri dipukul rata 20px */
```

Sebagai pengingat emas: Jangan lupa aturan `box-sizing: border-box;` (di Bab 22). Tanpa itu, penambahan Padding akan membuat kotaknya malah menjadi mekar tambah membesar ukurannya!
