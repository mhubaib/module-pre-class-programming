# Bab 17: Cara-cara Menambahkan CSS ke HTML

## Tujuan Pembelajaran

- Mengetahui tiga metode utama menyambungkan CSS ke dalam dokumen HTML.
- Memahami konsep Inline, Internal, dan External CSS.
- Mampu menentukan metode terbaik yang digunakan berdasarkan kebutuhan projek.

## Materi Utama

Kamu sudah paham cara menulis kode CSS, tapi di mana seharusnya kode itu diletakkan agar browser bisa membacanya? Ada tiga pintu masuk untuk memasukkan CSS ke dalam website kita.

### 1. Inline CSS (Gaya Langsung)

Kode CSS dituliskan langsung di dalam tag pembuka HTML menggunakan atribut `style`.

```html
<h1 style="color: blue; text-align: center;">Judul Berwarna Biru</h1>
```

- **Kelebihan:** Sangat cepat untuk perbaikan darurat pada satu elemen saja.
- **Kekurangan:** Sangat tidak rapi jika digunakan terus-menerus. Jika kamu punya 100 paragraf dan ingin mengubah warnanya, kamu harus mengubahnya satu per satu di setiap tag. Melehkan, bukan?

### 2. Internal CSS (Gaya di Dalam Dokumen)

Kode CSS dituliskan di dalam satu file HTML yang sama, biasanya diletakkan di dalam bagian `<head>` menggunakan tag `<style>`.

```html
<head>
  <style>
    body {
      background-color: lightgrey;
    }
    h1 {
      color: maroon;
    }
  </style>
</head>
```

- **Kelebihan:** Semua pengaturan gaya untuk satu halaman tersebut terkumpul di satu tempat di bagian atas. Lebih mudah diatur daripada Inline CSS.
- **Kekurangan:** Jika kamu punya website dengan banyak halaman (misal: Beranda, Profil, Kontak), dan ingin semua halamannya punya warna latar yang sama, kamu harus menyalin kode `<style>` tersebut ke semua file HTML-mu.

### 3. External CSS (Gaya dari Luar - Standar Profesional)

Inilah cara yang paling disukai dan digunakan oleh semua Web Developer profesional. Kamu membuat satu file terpisah khusus berisi kode CSS (misal: `style.css`), lalu memanggilnya ke dalam file HTML menggunakan tag `<link>`.

**Langkah-langkahnya:**

1. Buat file baru bernama `style.css`.
2. Isi `style.css` dengan kode CSS murni (tanpa tag `<style>`):
   ```css
   p {
     color: navy;
     line-height: 1.6;
   }
   ```
3. Hubungkan di dalam bagian `<head>` file HTML-mu:
   ```html
   <head>
     <link rel="stylesheet" href="style.css" />
   </head>
   ```

- **Kelebihan:** Sangat rapi. Satu file CSS bisa mengontrol tampilan SEBANYAK APAPUN halaman HTML simpananmu. Cukup edit satu file, ribuan halaman web berubah seketika.
- **Kekurangan:** Membutuhkan satu langkah tambahan untuk menghubungkan file.

### 4. Mana yang Harus Saya Gunakan?

**Analogi Memilih Pakaian:**

- **Inline CSS** ibarat menempelkan stiker langsung di baju yang sedang kamu pakai. Cepat, tapi berantakan kalau terlalu banyak stiker.
- **Internal CSS** ibarat kamu punya catatan daftar pakaian (lemari) di dalam kamar yang sama. Cukup rapi untuk kamar itu saja.
- **External CSS** ibarat kamu punya butik atau gudang pakaian pusat. Apa pun yang kamu ambil dari gudang pusat itu bisa dipakai di kamar mana saja di seluruh rumahmu.

**Kesimpulan:**
99% waktu kerjamu nanti akan dihabiskan menggunakan **External CSS**. Inline CSS hanya digunakan untuk hal yang sangat jarang, dan Internal CSS biasanya hanya untuk ujicoba cepat satu halaman saja.
