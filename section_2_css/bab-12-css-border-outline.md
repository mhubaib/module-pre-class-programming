# Bab 12: CSS Border & Outline

## Tujuan Pembelajaran

- Memahami cara menerapkan garis tepi (Border) pada elemen menggunakan CSS.
- Menguasai tiga komponen pembentuk Border: ketebalan, gaya, dan warna.
- Membedakan perilaku dan dampak tata letak antara Border dan Outline.
- Menerapkan `border-radius` untuk menghasilkan sudut elemen yang membulat.

---

## Materi Utama

Setelah memahami Padding sebagai ruang di dalam elemen dan Margin sebagai jarak di luar elemen, kini kita akan membahas lapisan yang berada di antara keduanya: **Border** dan **Outline**.

Border digunakan untuk memberi garis tepi yang terlihat pada sebuah elemen — berguna untuk memisahkan satu bagian dari bagian lain secara visual, maupun untuk memperkuat tampilan komponen seperti tombol dan kartu.

---

### 1. Mengenal Border (Garis Tepi)

**Border** adalah garis yang mengelilingi area padding dan konten suatu elemen. Sesuai dengan konsep Box Model yang telah dibahas di Bab 8, ketebalan border akan menambah ukuran total elemen — kecuali properti `box-sizing: border-box` sudah diterapkan.

Agar sebuah border dapat ditampilkan, terdapat tiga komponen yang wajib ditentukan:

1. **Ketebalan (`border-width`)**: Ukuran tebal garis, misalnya `1px`, `3px`, atau nilai kata kunci seperti `thin`, `medium`, dan `thick`.
2. **Gaya (`border-style`)**: Bentuk garis yang digunakan, misalnya garis lurus, putus-putus, atau titik-titik.
3. **Warna (`border-color`)**: Warna garis yang ditampilkan.

```css
.kotak-peringatan {
  border-width: 2px;
  border-style: solid;
  border-color: red;
}
```

**Contoh penerapan dasar:**

```html
<!-- HTML -->
<div class="kartu-informasi">
  <p>Ini adalah kartu informasi dengan border.</p>
</div>

<div class="kotak-peringatan">
  <p>Perhatian: tindakan ini tidak dapat dibatalkan.</p>
</div>
```

```css
/* CSS */
.kartu-informasi {
  border-width: 1px;
  border-style: solid;
  border-color: #3498db;
  padding: 16px;
  margin-bottom: 12px;
}

.kotak-peringatan {
  border-width: 2px;
  border-style: solid;
  border-color: #e74c3c;
  padding: 16px;
}
```

---

### 2. Jenis-Jenis Gaya Garis (`border-style`)

CSS menyediakan beberapa pilihan gaya garis yang dapat digunakan sebagai nilai `border-style`:

| Nilai    | Tampilan                                                               |
| -------- | ---------------------------------------------------------------------- |
| `solid`  | Garis lurus penuh — paling umum digunakan                              |
| `dashed` | Garis putus-putus                                                      |
| `dotted` | Garis titik-titik kecil                                                |
| `double` | Dua garis sejajar dengan jarak di antaranya                            |
| `none`   | Tidak ada border — umum digunakan untuk menghapus border bawaan elemen |

**Contoh perbandingan gaya garis:**

```html
<!-- HTML -->
<div class="border-solid">solid — garis lurus penuh</div>
<div class="border-dashed">dashed — garis putus-putus</div>
<div class="border-dotted">dotted — garis titik-titik</div>
<div class="border-double">double — garis ganda</div>
```

```css
/* CSS */
div {
  padding: 12px;
  margin-bottom: 10px;
  border-width: 3px;
  border-color: #2c3e50;
}

.border-solid {
  border-style: solid;
}
.border-dashed {
  border-style: dashed;
}
.border-dotted {
  border-style: dotted;
}
.border-double {
  border-style: double;
}
```

---

### 3. Penulisan Ringkas Border (Shorthand)

Alih-alih menuliskan ketiga komponen border secara terpisah, CSS menyediakan penulisan ringkas (_shorthand_) yang menggabungkan ketiganya dalam satu baris. Urutan yang paling umum digunakan adalah: **[Ketebalan] [Gaya] [Warna]**.

```css
.tombol {
  border: 3px solid #2980b9;
}
```

Border juga dapat diterapkan hanya pada sisi-sisi tertentu menggunakan properti individual per sisi:

```css
/* Hanya sisi atas */
border-top: 2px solid #333;

/* Hanya sisi bawah */
border-bottom: 4px dashed #e74c3c;
```

**Contoh penerapan border satu sisi — pola umum pada elemen input form:**

```html
<!-- HTML -->
<form class="form-pendaftaran">
  <input class="input-nama" type="text" placeholder="Nama lengkap" />
  <input class="input-email" type="email" placeholder="Alamat email" />
  <button class="tombol-kirim" type="submit">Daftar</button>
</form>
```

```css
/* CSS */
.form-pendaftaran {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 400px;
}

/* Border hanya di sisi bawah — tampilan minimalis yang umum di form modern */
.input-nama,
.input-email {
  border: none;
  border-bottom: 2px solid #bdc3c7;
  padding: 8px 4px;
  font-size: 1rem;
  outline: none;
  background-color: transparent;
}

.input-nama:focus,
.input-email:focus {
  border-bottom-color: #3498db; /* Warna border berubah saat elemen aktif */
}

/* Border penuh pada tombol */
.tombol-kirim {
  border: 2px solid #27ae60;
  background-color: #27ae60;
  color: white;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 4px;
}
```

---

### 4. Membulatkan Sudut Elemen: `border-radius`

Properti `border-radius` digunakan untuk membulatkan sudut-sudut kotak suatu elemen. Nilai yang diberikan menentukan seberapa besar kelengkungan sudutnya — semakin besar nilainya, semakin bulat sudut yang dihasilkan.

```css
.kartu {
  border-radius: 10px; /* Sudut melengkung dengan radius 10 piksel */
}

.foto-profil {
  width: 200px;
  height: 200px;
  border-radius: 50%; /* Nilai 50% pada elemen persegi menghasilkan bentuk lingkaran */
}
```

`border-radius` juga dapat diterapkan pada sudut-sudut tertentu saja:

```css
border-top-left-radius: 12px;
border-top-right-radius: 12px;
border-bottom-left-radius: 0;
border-bottom-right-radius: 0;
```

**Contoh penerapan `border-radius` pada berbagai komponen:**

```html
<!-- HTML -->
<div class="kartu-produk">
  <div class="foto-profil"></div>
  <h3>Nama Pengguna</h3>
</div>

<button class="tombol-pil">Simpan</button>
<button class="tombol-kotak">Batal</button>
<div class="label-status">Aktif</div>
```

```css
/* CSS */

/* Kartu dengan sudut melengkung — umum digunakan pada komponen kartu */
.kartu-produk {
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 24px;
  max-width: 300px;
  text-align: center;
}

/* Foto profil berbentuk lingkaran */
.foto-profil {
  width: 80px;
  height: 80px;
  background-color: #bdc3c7;
  border-radius: 50%;
  margin: 0 auto 12px;
}

/* Tombol berbentuk pil — border-radius bernilai sangat besar */
.tombol-pil {
  border: 2px solid #3498db;
  border-radius: 999px; /* Nilai besar menghasilkan bentuk setengah lingkaran di kedua sisi */
  padding: 10px 24px;
  background-color: #3498db;
  color: white;
  cursor: pointer;
}

/* Tombol dengan sudut sedikit membulat */
.tombol-kotak {
  border: 2px solid #95a5a6;
  border-radius: 4px;
  padding: 10px 24px;
  background-color: white;
  cursor: pointer;
}

/* Label status dengan sudut membulat hanya di atas */
.label-status {
  display: inline-block;
  background-color: #2ecc71;
  color: white;
  padding: 4px 12px;
  border-radius: 4px;
  font-size: 0.85rem;
}
```

---

### 5. Perbedaan Border dan Outline

**Outline** adalah garis yang tampak serupa dengan border, namun memiliki karakteristik yang berbeda secara fundamental — terutama dalam hal dampaknya terhadap tata letak halaman.

Outline paling sering terlihat secara otomatis pada elemen input atau tombol yang sedang dalam kondisi aktif (focused), ditampilkan oleh browser sebagai indikator aksesibilitas.

**Perbandingan Border dan Outline:**

| Aspek               | `border`                                   | `outline`                                               |
| ------------------- | ------------------------------------------ | ------------------------------------------------------- |
| Posisi              | Di antara padding dan margin               | Di luar border, menumpuk di atas margin                 |
| Dampak tata letak   | Menambah ukuran total elemen               | Tidak memengaruhi ukuran atau posisi elemen lain        |
| Pengaturan per sisi | Dapat diatur per sisi (`border-top`, dll.) | Tidak dapat diatur per sisi — selalu mengelilingi penuh |
| `border-radius`     | Mengikuti lengkungan `border-radius`       | Tidak selalu mengikuti lengkungan (bergantung browser)  |
| Penggunaan umum     | Dekorasi dan struktur visual elemen        | Indikator fokus untuk aksesibilitas                     |

**Analogi — Pagar dan Tanda Sementara:**
Jika elemen adalah sebuah bangunan, maka **border** adalah pagar permanen yang mengelilinginya — memiliki ketebalan fisik dan memengaruhi jarak ke bangunan di sekitarnya. Sedangkan **outline** adalah tanda atau garis penanda sementara yang dipasang di luar pagar — tidak memakan ruang dan tidak menggeser posisi bangunan maupun pagar di sekitarnya.

```css
/* Penulisan outline mengikuti sintaks yang sama dengan border */
input:focus {
  outline: 2px solid #3498db;
}

/* Menonaktifkan outline bawaan browser — perlu diganti dengan indikator fokus alternatif */
button {
  outline: none;
  /* Pastikan tetap ada indikator fokus untuk keperluan aksesibilitas */
}
```

**Contoh penggunaan Outline:**

```html
<!-- HTML -->
<form class="form-contoh">
  <input
    class="input-standar"
    type="text"
    placeholder="Dengan outline bawaan browser"
  />
  <input class="input-kustom" type="text" placeholder="Dengan outline kustom" />
  <input
    class="input-tanpa-outline"
    type="text"
    placeholder="Outline dinonaktifkan"
  />
</form>
```

```css
/* CSS */
.form-contoh {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 400px;
}

.input-standar,
.input-kustom,
.input-tanpa-outline {
  border: 1px solid #ccc;
  padding: 10px 12px;
  font-size: 1rem;
  border-radius: 4px;
}

/* Outline bawaan browser dibiarkan aktif pada .input-standar */

/* Outline diganti dengan warna kustom */
.input-kustom:focus {
  outline: 3px solid #f39c12;
}

/* Outline dinonaktifkan — sebaiknya sertakan indikator fokus pengganti */
.input-tanpa-outline:focus {
  outline: none;
  border-color: #3498db; /* Indikator fokus alternatif melalui perubahan warna border */
}
```

> **Catatan Aksesibilitas:** Menonaktifkan `outline` tanpa menyediakan indikator fokus alternatif akan menyulitkan pengguna yang menavigasi halaman menggunakan keyboard. Pastikan selalu ada penanda visual yang jelas saat sebuah elemen dalam kondisi fokus.

---

### Kesimpulan

Border dan Outline adalah dua properti yang tampak serupa namun memiliki peran yang berbeda. Border bersifat struktural — ia menjadi bagian dari dimensi elemen dan memengaruhi tata letak. Outline bersifat dekoratif dan tidak memengaruhi ukuran elemen sedikit pun, sehingga lebih tepat digunakan sebagai indikator status seperti kondisi fokus pada elemen interaktif.

**Panduan singkat penggunaan:**

- Perlu menambahkan garis tepi yang memengaruhi ukuran elemen? → Gunakan **Border**.
- Perlu menandai elemen aktif tanpa mengubah tata letak? → Gunakan **Outline**.
- Perlu sudut elemen yang membulat? → Gunakan **`border-radius`**.

**Ringkasan Properti:**

| Properti                       | Fungsi                                                      |
| ------------------------------ | ----------------------------------------------------------- |
| `border`                       | Shorthand untuk ketebalan, gaya, dan warna border sekaligus |
| `border-width`                 | Ketebalan garis border                                      |
| `border-style`                 | Gaya garis border (`solid`, `dashed`, `dotted`, dll.)       |
| `border-color`                 | Warna garis border                                          |
| `border-top/right/bottom/left` | Border pada sisi tertentu saja                              |
| `border-radius`                | Membulatkan sudut elemen                                    |
| `outline`                      | Garis di luar border yang tidak memengaruhi tata letak      |

**Panduan Pemilihan Nilai:**

| Kebutuhan                                         | Pendekatan yang Disarankan                                         |
| ------------------------------------------------- | ------------------------------------------------------------------ |
| Garis tepi dekoratif pada kartu atau kotak        | `border: 1px solid [warna]`                                        |
| Garis hanya di satu sisi (misalnya elemen input)  | `border-bottom: 2px solid [warna]`                                 |
| Sudut elemen sedikit membulat                     | `border-radius: 4px` hingga `12px`                                 |
| Elemen berbentuk lingkaran                        | `border-radius: 50%` pada elemen dengan lebar dan tinggi yang sama |
| Tombol berbentuk pil                              | `border-radius: 999px`                                             |
| Indikator elemen aktif tanpa menggeser tata letak | `outline: 2px solid [warna]`                                       |
