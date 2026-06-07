# Bab 3: Cara-cara Menambahkan CSS ke HTML

## Tujuan Pembelajaran

- Mengetahui tiga metode untuk menyertakan CSS ke dalam dokumen HTML.
- Memahami konsep Inline CSS, Internal CSS, dan External CSS.
- Mampu menentukan metode yang tepat berdasarkan kebutuhan proyek.

---

## Materi Utama

Kamu sudah memahami cara menulis kode CSS. Sekarang, di mana kode tersebut harus diletakkan agar browser dapat membacanya? Terdapat tiga cara untuk menyertakan CSS ke dalam halaman web.

---

### 1. Inline CSS

Kode CSS ditulis langsung di dalam tag HTML menggunakan atribut `style`. Gaya ini hanya berlaku untuk satu elemen tempat atribut tersebut ditulis.

```html
<h1 style="color: blue; text-align: center;">Judul Berwarna Biru</h1>
<p style="color: gray; font-size: 14px;">Paragraf dengan gaya khusus.</p>
```

**Kelebihan:**

- Cepat untuk menerapkan gaya pada satu elemen tertentu.
- Tidak memerlukan file atau tag tambahan.

**Kekurangan:**

- Tidak dapat digunakan kembali. Jika ada 50 paragraf yang ingin diubah gayanya, setiap tag harus diubah satu per satu.
- Mencampur struktur HTML dan gaya CSS dalam satu baris, membuat kode sulit dibaca dan dipelihara.
- Sulit di-override menggunakan selektor dari file CSS eksternal.

**Kapan digunakan:**
Sebatas untuk keperluan yang sangat spesifik — misalnya menerapkan gaya sementara selama pengembangan, atau mengatur nilai style yang ditetapkan secara dinamis melalui JavaScript.

---

### 2. Internal CSS

Kode CSS ditulis di dalam tag `<style>` yang ditempatkan di bagian `<head>` dokumen HTML. Gaya ini hanya berlaku untuk satu dokumen HTML tempat tag `<style>` tersebut berada.

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Contoh Internal CSS</title>

    <style>
      body {
        background-color: #f5f5f5;
        font-family: sans-serif;
      }

      h1 {
        color: #2c3e50;
      }

      p {
        color: #555;
        line-height: 1.6;
      }
    </style>
  </head>
  <body>
    <h1>Judul Halaman</h1>
    <p>Ini adalah paragraf dengan gaya dari Internal CSS.</p>
  </body>
</html>
```

**Kelebihan:**

- Seluruh gaya untuk satu halaman tersimpan di satu tempat, lebih terorganisir dibandingkan Inline CSS.
- Tidak memerlukan file tambahan.

**Kekurangan:**

- Gaya tidak dapat digunakan ulang di halaman lain. Jika ada 10 halaman HTML yang ingin menggunakan gaya yang sama, blok `<style>` harus disalin ke setiap file.
- File HTML menjadi lebih panjang karena memuat dua jenis kode sekaligus.

**Kapan digunakan:**
Cocok untuk prototipe cepat atau halaman HTML tunggal yang tidak memerlukan berbagi gaya dengan halaman lain.

---

### 3. External CSS

Kode CSS ditulis di file terpisah berekstensi `.css`, lalu dihubungkan ke dokumen HTML menggunakan tag `<link>` di dalam `<head>`. Ini adalah metode yang digunakan dalam pengembangan web profesional.

**Langkah-langkah:**

1. Buat file baru bernama `style.css` di folder yang sama dengan file HTML.
2. Isi `style.css` dengan kode CSS (tanpa tag `<style>`):

```css
/* style.css */
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background-color: #f5f5f5;
}

h1 {
  color: #2c3e50;
}

p {
  color: #555;
  line-height: 1.6;
}
```

3. Hubungkan file CSS ke file HTML di bagian `<head>`:

```html
<!-- index.html -->
<head>
  <meta charset="UTF-8" />
  <title>Website Saya</title>
  <link rel="stylesheet" href="style.css" />
</head>
```

**Satu file CSS dapat dihubungkan ke banyak file HTML:**

```
proyek/
├── index.html      ← <link href="style.css">
├── tentang.html    ← <link href="style.css">
├── kontak.html     ← <link href="style.css">
└── style.css       ← Satu file ini mengontrol tampilan semua halaman
```

**Kelebihan:**

- Satu file CSS dapat mengontrol tampilan seluruh halaman di website. Mengubah satu baris di `style.css` dapat langsung berdampak ke semua halaman sekaligus.
- Memisahkan struktur (HTML) dari tampilan (CSS) secara bersih — prinsip yang disebut _Separation of Concerns_.
- File HTML menjadi lebih ringkas dan mudah dibaca.
- File CSS di-cache oleh browser sehingga meningkatkan kecepatan muat halaman.

**Kekurangan:**

- Memerlukan satu langkah tambahan untuk membuat dan menghubungkan file.

**Kapan digunakan:**
Untuk semua proyek nyata — baik skala kecil maupun besar. External CSS adalah standar industri yang digunakan di hampir semua website profesional.

---

### 4. Perbandingan Ketiga Metode

|                            | Inline CSS               | Internal CSS                 | External CSS                    |
| -------------------------- | ------------------------ | ---------------------------- | ------------------------------- |
| **Lokasi kode**            | Atribut `style` pada tag | Tag `<style>` dalam `<head>` | File `.css` terpisah            |
| **Cakupan gaya**           | Satu elemen              | Satu halaman HTML            | Semua halaman yang menautkannya |
| **Kemudahan pemeliharaan** | Rendah                   | Sedang                       | Tinggi                          |
| **Dapat digunakan ulang**  | Tidak                    | Tidak                        | Ya                              |
| **Direkomendasikan untuk** | Kasus khusus/JS          | Prototipe cepat              | Semua proyek nyata              |

**Analogi:**

- **Inline CSS** — menuliskan instruksi langsung di setiap barang yang ingin diubah. Cepat untuk satu item, tidak praktis untuk banyak item.
- **Internal CSS** — memiliki lembar panduan di setiap ruangan. Rapi untuk ruangan itu sendiri, tetapi perlu disalin jika ingin digunakan di ruangan lain.
- **External CSS** — memiliki satu panduan terpusat yang bisa dirujuk oleh semua ruangan sekaligus. Ubah satu panduan, semua ruangan ikut menyesuaikan.

---

### Kesimpulan

Dalam praktik pengembangan web sehari-hari, External CSS adalah metode yang hampir selalu digunakan. Inline CSS sesekali digunakan untuk kasus yang sangat spesifik, dan Internal CSS umumnya hanya untuk percobaan cepat pada satu halaman.

**Ringkasan:**

| Metode       | Cara Penulisan            | Rekomendasi                       |
| ------------ | ------------------------- | --------------------------------- |
| Inline CSS   | `<tag style="...">`       | Hindari kecuali sangat perlu      |
| Internal CSS | `<style>` dalam `<head>`  | Untuk prototipe atau satu halaman |
| External CSS | `<link href="style.css">` | Standar untuk semua proyek nyata  |
