# Bab 12: Form Element & Tipe-tipe Input

## Tujuan Pembelajaran

- Mengenal tag penyedia nama kolom isian (`<label>`).
- Menguasai macam-macam bentuk `<input>` (Text, Password, Checkbox, Radio, dll).
- Mampu menggunakan kotak isian panjang (`<textarea>`) dan opsi gulir ke bawah (`<select>`).
- Mengetahui kekuatan ragam tipe data khusus bawaan HTML5 (Email, Tanggal, Warna, Angka).
- Membuat tombol ajaib _"Submit"_ untuk meroketkan data form.

## Materi Utama

Dalam wadah ampli `<form>` yang kita bahas di Bab 11, kita siap memasukkan kertas formulirnya. Ada beragam balok komponen penyusun lembar form, mulai dari kotak ketikan polos hingga centang persetujuan (Terms & Conditions).

Mari kita preteli organ-organ dalam form!

### 1. Tag Keterangan Kolom: `<label>`

Bayangkan ada sebuah kotak putih kosong di layar tanpa ada tulisan "Nama Lengkap" di sampingnya. User pasti kebingungan harus mengisi kotak itu dengan apa. Oleh sebab itu, kita butuh elemen `<label>`.

`<label>` berfungsi sekadar sebagai papan nama (teks petunjuk). Namun ia punya satu rahasia ajaib: Jika atribut `for` pada label disamakan dengan `id` pada kotak input, maka ketika sang pengguna (terutama pemakai HP jari besar) meng-klik teks label tersebut, kursor akan otomatis masuk menyala ke kotak isian di sebelahnya!

```html
<label for="kotak-username">Nama Pengguna:</label>
<input type="text" id="kotak-username" />
```

### 2. Sang Bunglon: Tag `<input>`

`<input>` adalah elemen terpenting form HTML yang bentuknya bisa berubah rupa menyesuaikan perintah atribut `type` (Tipe). Ingat, `input` adalah bentuk Tag Tunggal.

Dulu di era HTML4, tipe input sangat terbatas. Namun lewat revolusi HTML5, browser modern kini sangat cerdas! Browser HP kini otomatis memunculkan "_keyboard angka saja_" ketika bertemu input angka, atau "_keyboard email (ada tombol @)_" ketika bertemu input email.

Berikut kamus lengkap macam-macam penjelmaan tag `<input>` yang sangat memukau:

**1. Tipe Dasar (Klasik)**

- **Teks Pendek (`type="text"`)**
  Untuk isian 1 baris umum seperti Nama, Pekerjaan, dll.

```html
<input type="text" placeholder="Ketik nama kamu di sini" />
```

_(Tips: Atribut `placeholder` menampilkan teks bayang-bayang abu yang sirna waktu kita mulai mengetik)._

- **Kata Sandi Rahasia (`type="password"`)**
  Pengguna sedang mengetik, namun di layar yang muncul hanyalah simbol titik hitam bulat tebal atau bintang `*******` agar menghindari orang di belakang mengintip privasimu.

```html
<input type="password" />
```

- **Centang Pilihan Ganda (`type="checkbox"`)**
  Berwujud "Kotak Centang". Digunakan kala kamu membebaskan pengguna memilih **LEBIH DARI SATU** jawaban (Multyple Choice).

```html
<input type="checkbox" /> Membaca <input type="checkbox" /> Bersepeda
```

- **Pilihan Bulat Mutlak (`type="radio"`)**
  Berwujud "Lingkaran Bulat". The Rule of The Game: **HANYA BOLEH PILIH SALAH SATU!** Syarat rahasianya: Atribut `name` dari kumpulan tombol-tombol radio tersebut harus di set NAMA PERSIS AGAR BERALIANSI.

```html
<input type="radio" name="gender" /> Laki-laki
<input type="radio" name="gender" /> Perempuan
```

**2. Tipe Terpesifikasi Bentuk Data (HTML5 Canggih)**

- **Alamat Email (`type="email"`)**
  Visualnya sama dengan teks biasa, tapi browser akan **menolak** jika pengguna salah mengetik format (misal lupa menaruh lambang `@` atau `.com`).

```html
<input type="email" placeholder="contoh@gmail.com" />
```

- **Angka Murni (`type="number"`)**
  Hanya mengizinkan ketikan format angka numeric. Browser PC akan ngasih tombol panah "naik-turun" kecil di dalam kotaknya. Di HP, keyboard otomatis ganti ke tombol Numerik.

```html
<!-- Atribut min dan max bisa membatasi batas jangkau -->
<input type="number" min="1" max="100" />
```

- **Nomor Handphone (`type="tel"`)**
  Digunakan untuk memasukkan nomor telepon internasional. Keyboard di HP akan langsung membuka keypad telepon.

```html
<input type="tel" />
```

- **Link URL (`type="url"`)**
  Pendeteksi kebenaran sebuah Link. Browser akan mencegat jikalau kamu lupa ngetik awalan `http://` atau `https://`.

```html
<input type="url" placeholder="https://websitekamu.com" />
```

**3. Tipe Kalender & Waktu (Date/Time Picker)**
Tidak perlu repot membuat tabel kalender menyusahkan. HTML5 memanggilkan langsung komponen Kalender bawaan Sistem HP/Windows!

- **Tanggal Lengkap (`type="date"`)**: Memunculkan kalender (Tahun-Bulan-Tanggal).
- **Waktu Jam/Jam (`type="time"`)**: Memunculkan scroll _rotary_ jam dan menit digital.
- **Bulan Saja (`type="month"`)**: Mengambil data Tahun dan Bulan (Bagus untuk pengisian masa berlaku Kartu Kredit).

```html
<label>Tanggal Lahir:</label> <input type="date" />
```

**4. Tipe Interaktif Visual & Lainnya**

- **Pemilih Warna (`type="color"`)**
  Ajaib! Memunculkan jendela Color Palette (Spektrum Palet Warna) bawaan Windows/Mac di mana kamu bisa mengambil racikan komposisi warna RGB bebas lepas pakai pipet.

```html
<input type="color" />
```

- **Garis Slider (`type="range"`)**
  Membuat pentolan volume _Slider_ geser horisontal. Pengguna nggeser mentol dari ujung kiri (terendah) mentok ke kanan (tertinggi).

```html
<input type="range" min="0" max="100" />
```

- **File Upload (`type="file"`)**
  Gembok gerbang utama yang menyuruh sistem membuka "File Explorer/Gallery" buat mendownload Pas Foto atau PDF Lamaran Kerja masuk menclok ke Server.

```html
<input type="file" accept=".pdf, .png, .jpg" />
```

**5. Eksekutor Misi**

- **Sembunyi Total (`type="hidden"`)**: Kolom data GHAIB yang tidak terlihat wujudnya di kanvas sama sekali, ini rahasia dipakai Developer Backend nempelkin data racikan robot otomatis ke form.
- **Tombol Pengirim Final (`type="submit"`)**: The Postman! Kliklah ini agar paketan `<form>` terhisap dan diserahkan ke Server di sebrang awan.

```html
<input type="submit" value="Kirim Data Sekarang!" />
```

### 3. Kotak Cerita Panjang: `<textarea>`

Kalau mau menulis "Ulasan/Review" komplain atau sebuah esai sepanjang 3 paragraf, maka kotak input biasa 1 baris bakalan mentok!
Di sinilah dewa paragraf mendadak muncul `<textarea>`. Menariknya, ini bukan tag tunggal, dia HARUS punya penutup `</textarea>`.
Kamu bisa atur bawaan rentang kerangkanya dari atribut `rows` (panjang vertikal baris galian) dan `cols` (lebar mendatar per karakter kata).

```html
<label>Curhat di sini dong bro:</label><br />
<textarea rows="5" cols="40"></textarea>
```

### 4. Menu Dropp-Down Gulir Bawah: `<select>` dan `<option>`

Pernah berbelanja di _E-Commerce_, lantas dimintai memilih Domisili "Provinsi/Kota Asal Pindahan"? Daripada si pengguna harus membuang napas ngetik manual nama kotanya, kita kasih laci pilihan jatuh ke bawah menggunakan grup elemen bersarang (`<select>` meremaja membungkus pilihan-pilihan `<option>`).

```html
<label>Pilih Kelas Pelajaran:</label>
<select>
  <option>Reguler Pagi</option>
  <option>Reguler Malam</option>
  <option>Kelas Eksekutif (Ahli)</option>
</select>
```

> **Catatan Pengingat Rantai Utama Form:** Jangan sampai lupa, jika semua hal-hal ajaib di atas tidak dijepit secara solid di dalam lingkup tag `<form>` dan `</form>`, maka data ketikan kamu bakal meluap tidak pernah terkirim alias mentah-mentah masuk neraka Error Log!
