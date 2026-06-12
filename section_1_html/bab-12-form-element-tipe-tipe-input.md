# Bab 12: Form Element & Tipe-tipe Input

## Tujuan Pembelajaran

- Mengenal tag `<label>` sebagai penanda kolom isian.
- Menguasai berbagai tipe `<input>` yang tersedia di HTML.
- Mampu menggunakan `<textarea>` untuk teks panjang dan `<select>` untuk menu dropdown.
- Mengetahui tipe input khusus HTML5 seperti email, tanggal, warna, dan lainnya.
- Membuat tombol submit untuk mengirimkan data formulir.

---

## Materi Utama

Di Bab 11, kita membahas tag `<form>` sebagai wadah formulir. Sekarang saatnya mengisi wadah tersebut dengan berbagai elemen input yang memungkinkan pengguna memasukkan data.

---

### 1. Tag Label: `<label>`

`<label>` adalah teks keterangan yang menjelaskan fungsi sebuah kolom input. Selain sebagai petunjuk visual, `<label>` memiliki fungsi aksesibilitas penting: ketika atribut `for` pada label disamakan dengan atribut `id` pada input, mengklik teks label akan otomatis memindahkan fokus ke kolom input yang bersangkutan.

```html
<label for="nama-pengguna">Nama Pengguna:</label>
<input type="text" id="nama-pengguna" />
```

Ini sangat membantu pengguna di perangkat mobile di mana area klik yang kecil sulit ditekan dengan tepat.

**Cara penulisan alternatif — label membungkus input:**

```html
<!-- Input di dalam label — tidak memerlukan atribut for/id -->
<label>
  Nama Pengguna:
  <input type="text" />
</label>
```

---

### 2. Tag Input: `<input>`

`<input>` adalah elemen form paling fleksibel. Tampilannya berubah sesuai nilai atribut `type`. Tag ini bersifat self-closing (tidak memiliki tag penutup).

#### A. Tipe Teks Dasar

**`type="text"` — Teks satu baris:**

```html
<label for="nama">Nama Lengkap:</label>
<input type="text" id="nama" name="nama" placeholder="Contoh: Budi Santoso" />
```

Atribut `placeholder` menampilkan teks petunjuk yang menghilang saat pengguna mulai mengetik.

**`type="password"` — Kata sandi tersembunyi:**

```html
<label for="sandi">Kata Sandi:</label>
<input type="password" id="sandi" name="sandi" />
```

Karakter yang diketik digantikan dengan titik atau bintang untuk melindungi privasi pengguna.

**`type="checkbox"` — Pilihan ganda (boleh memilih lebih dari satu):**

```html
<p>Hobi:</p>
<label><input type="checkbox" name="hobi" value="membaca" /> Membaca</label>
<label><input type="checkbox" name="hobi" value="bersepeda" /> Bersepeda</label>
<label><input type="checkbox" name="hobi" value="memasak" /> Memasak</label>
```

**`type="radio"` — Pilihan tunggal (hanya boleh memilih satu):**

Seluruh tombol radio yang merupakan satu kelompok harus memiliki atribut `name` yang sama.

```html
<p>Jenis Kelamin:</p>
<label
  ><input type="radio" name="jenis-kelamin" value="laki-laki" />
  Laki-laki</label
>
<label
  ><input type="radio" name="jenis-kelamin" value="perempuan" />
  Perempuan</label
>
```

#### B. Tipe Data Tervalidasi (HTML5)

Browser akan memvalidasi format data sebelum formulir dapat dikirim.

**`type="email"` — Alamat email:**

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email" placeholder="nama@contoh.com" />
```

Browser menolak pengiriman jika format email tidak valid (tidak ada `@` atau domain).

**`type="number"` — Angka:**

```html
<label for="usia">Usia:</label>
<input type="number" id="usia" name="usia" min="1" max="120" />
```

Atribut `min` dan `max` membatasi rentang nilai yang dapat dimasukkan. Keyboard angka otomatis muncul di perangkat mobile.

**`type="tel"` — Nomor telepon:**

```html
<label for="telepon">Nomor Telepon:</label>
<input type="tel" id="telepon" name="telepon" placeholder="+62812345678" />
```

Keyboard numerik telepon otomatis muncul di perangkat mobile.

**`type="url"` — Alamat URL:**

```html
<label for="website">Website:</label>
<input
  type="url"
  id="website"
  name="website"
  placeholder="https://contoh.com"
/>
```

Browser memvalidasi bahwa nilai diawali dengan `http://` atau `https://`.

#### C. Tipe Kalender dan Waktu

HTML5 menyediakan komponen kalender dan waktu bawaan tanpa perlu JavaScript tambahan.

```html
<!-- Tanggal: menampilkan kalender pilih tanggal -->
<label for="tgl-lahir">Tanggal Lahir:</label>
<input type="date" id="tgl-lahir" name="tgl-lahir" />

<!-- Waktu: menampilkan pemilih jam dan menit -->
<label for="jam-booking">Waktu Booking:</label>
<input type="time" id="jam-booking" name="jam-booking" />

<!-- Bulan dan tahun: berguna untuk masa berlaku kartu kredit -->
<label for="berlaku">Berlaku Hingga:</label>
<input type="month" id="berlaku" name="berlaku" />

<!-- Tanggal dan waktu sekaligus -->
<label for="jadwal">Jadwal:</label>
<input type="datetime-local" id="jadwal" name="jadwal" />
```

#### D. Tipe Visual dan Interaktif

**`type="color"` — Pemilih warna:**

```html
<label for="warna-tema">Warna Tema:</label>
<input type="color" id="warna-tema" name="warna-tema" value="#3498db" />
```

Membuka panel pemilih warna bawaan sistem operasi.

**`type="range"` — Slider nilai:**

```html
<label for="volume">Volume: <span id="nilai-volume">50</span></label>
<input type="range" id="volume" name="volume" min="0" max="100" value="50" />
```

**`type="file"` — Unggah file:**

```html
<label for="foto">Foto Profil:</label>
<input type="file" id="foto" name="foto" accept="image/png, image/jpeg" />
```

Atribut `accept` membatasi jenis file yang dapat dipilih.

#### E. Tipe Khusus

**`type="hidden"` — Data tersembunyi:**

```html
<!-- Tidak terlihat oleh pengguna, namun ikut terkirim bersama form -->
<input type="hidden" name="csrf-token" value="abc123xyz" />
```

Digunakan untuk menyertakan data teknis yang tidak perlu diisi oleh pengguna.

**`type="submit"` — Tombol kirim:**

```html
<input type="submit" value="Daftar Sekarang" />
```

---

### 3. Kotak Teks Panjang: `<textarea>`

Untuk teks yang lebih panjang dari satu baris — seperti komentar, ulasan, atau pesan — gunakan `<textarea>`. Berbeda dengan `<input>`, `<textarea>` memiliki tag penutup.

```html
<label for="ulasan">Tulis ulasan Anda:</label>
<textarea
  id="ulasan"
  name="ulasan"
  rows="5"
  cols="50"
  placeholder="Ceritakan pengalaman Anda..."
></textarea>
```

| Atribut       | Fungsi                                              |
| ------------- | --------------------------------------------------- |
| `rows`        | Jumlah baris yang terlihat (tinggi awal textarea)   |
| `cols`        | Jumlah karakter per baris (lebar awal textarea)     |
| `placeholder` | Teks petunjuk yang ditampilkan saat textarea kosong |

---

### 4. Menu Dropdown: `<select>` dan `<option>`

Untuk pilihan dari daftar yang sudah ditentukan, gunakan kombinasi `<select>` sebagai wadah dan `<option>` sebagai setiap pilihannya.

```html
<label for="kota">Pilih Kota:</label>
<select id="kota" name="kota">
  <option value="">-- Pilih Kota --</option>
  <option value="jakarta">Jakarta</option>
  <option value="bandung">Bandung</option>
  <option value="yogyakarta">Yogyakarta</option>
  <option value="surabaya">Surabaya</option>
</select>
```

**Mengelompokkan pilihan dengan `<optgroup>`:**

```html
<select name="kategori-produk">
  <optgroup label="Pakaian">
    <option value="kaos">Kaos</option>
    <option value="kemeja">Kemeja</option>
  </optgroup>
  <optgroup label="Elektronik">
    <option value="laptop">Laptop</option>
    <option value="smartphone">Smartphone</option>
  </optgroup>
</select>
```

**Pilihan yang dipilih secara default:**

```html
<select name="metode-bayar">
  <option value="transfer">Transfer Bank</option>
  <option value="kartu-kredit" selected>Kartu Kredit</option>
  <option value="dompet-digital">Dompet Digital</option>
</select>
```

---

### 5. Contoh Lengkap — Form Registrasi

```html
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <title>Form Registrasi</title>
  </head>
  <body>
    <h1>Buat Akun Baru</h1>

    <form action="/proses-daftar" method="POST">
      <!-- Informasi Pribadi -->
      <h2>Informasi Pribadi</h2>

      <label for="nama">Nama Lengkap:</label><br />
      <input
        type="text"
        id="nama"
        name="nama"
        placeholder="Contoh: Budi Santoso"
        required
      /><br /><br />

      <label for="email">Alamat Email:</label><br />
      <input
        type="email"
        id="email"
        name="email"
        placeholder="nama@contoh.com"
        required
      /><br /><br />

      <label for="telepon">Nomor Telepon:</label><br />
      <input
        type="tel"
        id="telepon"
        name="telepon"
        placeholder="+62812345678"
      /><br /><br />

      <label for="tgl-lahir">Tanggal Lahir:</label><br />
      <input type="date" id="tgl-lahir" name="tgl-lahir" /><br /><br />

      <p>Jenis Kelamin:</p>
      <label
        ><input type="radio" name="jenis-kelamin" value="laki-laki" />
        Laki-laki</label
      >
      <label
        ><input type="radio" name="jenis-kelamin" value="perempuan" />
        Perempuan</label
      >
      <br /><br />

      <!-- Akun -->
      <h2>Data Akun</h2>

      <label for="sandi">Kata Sandi:</label><br />
      <input type="password" id="sandi" name="sandi" required /><br /><br />

      <label for="kota">Kota Domisili:</label><br />
      <select id="kota" name="kota">
        <option value="">-- Pilih Kota --</option>
        <option value="jakarta">Jakarta</option>
        <option value="bandung">Bandung</option>
        <option value="yogyakarta">Yogyakarta</option></select
      ><br /><br />

      <!-- Minat -->
      <p>Minat (boleh pilih lebih dari satu):</p>
      <label
        ><input type="checkbox" name="minat" value="desain" /> Desain</label
      >
      <label
        ><input type="checkbox" name="minat" value="coding" /> Coding</label
      >
      <label
        ><input type="checkbox" name="minat" value="bisnis" /> Bisnis</label
      >
      <br /><br />

      <label for="bio">Bio Singkat:</label><br />
      <textarea
        id="bio"
        name="bio"
        rows="4"
        placeholder="Ceritakan sedikit tentang diri Anda..."
      ></textarea>
      <br /><br />

      <!-- Persetujuan -->
      <label>
        <input type="checkbox" name="setuju" required />
        Saya menyetujui <a href="/syarat-ketentuan">Syarat & Ketentuan</a>
      </label>
      <br /><br />

      <input type="submit" value="Buat Akun" />
    </form>
  </body>
</html>
```

---

### Kesimpulan

HTML menyediakan berbagai elemen input yang dirancang untuk jenis data yang berbeda-beda. Memilih tipe input yang tepat tidak hanya meningkatkan pengalaman pengguna (keyboard yang sesuai di mobile, validasi otomatis), tetapi juga membantu memastikan data yang dikirim memiliki format yang benar.

**Ringkasan Elemen Form:**

| Elemen                    | Kegunaan                                          |
| ------------------------- | ------------------------------------------------- |
| `<label>`                 | Teks keterangan kolom; meningkatkan aksesibilitas |
| `<input type="text">`     | Teks satu baris umum                              |
| `<input type="password">` | Kata sandi tersembunyi                            |
| `<input type="email">`    | Email dengan validasi format                      |
| `<input type="number">`   | Angka dengan batas min/max opsional               |
| `<input type="tel">`      | Nomor telepon                                     |
| `<input type="date">`     | Pemilih tanggal dengan kalender                   |
| `<input type="checkbox">` | Pilihan ganda (boleh lebih dari satu)             |
| `<input type="radio">`    | Pilihan tunggal dari satu kelompok                |
| `<input type="file">`     | Unggah file                                       |
| `<input type="color">`    | Pemilih warna                                     |
| `<input type="range">`    | Slider nilai                                      |
| `<input type="hidden">`   | Data tersembunyi yang ikut terkirim               |
| `<input type="submit">`   | Tombol kirim formulir                             |
| `<textarea>`              | Teks panjang multi-baris                          |
| `<select>` + `<option>`   | Menu dropdown pilihan                             |
