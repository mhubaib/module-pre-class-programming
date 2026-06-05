# Bab 30: CSS Pseudo Classes

## Tujuan Pembelajaran

- Memahami konsep Pseudo-Class sebagai "Status/Keadaan" sesaat dari sebuah elemen.
- Menguasai properti interaktif seperti `:hover`, `:active`, dan `:focus`.
- Mampu menyeleksi anak elemen spesifik menggunakan `:nth-child` dan `:first-child`.

---

## Materi Utama

Sejauh ini, kita mewarnai sebuah tombol secara permanen. Tombol berwarna biru, ya akan terus biru. Tetapi, bagaimana cara kita membuat tombol tersebut "menyala" atau berubah warna hanya ketika kursor mouse menyentuhnya?

Di sinilah kita memanggil ilmu **Pseudo-Class** (Kelas Semu).

---

### 1. Apa itu Pseudo-Class?

Pseudo-class digunakan untuk memberikan gaya pada sebuah elemen hanya ketika elemen tersebut berada dalam **keadaan atau status tertentu**.

Penulisannya sangat khas, yaitu menempelkan tanda titik dua tunggal (`:`) setelah nama selektor utama tanpa spasi.

**Sintaks Dasar:**

```css
selektor:pseudo-class {
  properti: nilai;
}
```

**Contoh:**

```html
<!-- HTML -->
<button class="tombol-login">Login</button>
```

```css
/* CSS */
.tombol-login {
  background-color: steelblue;
  color: white;
  padding: 10px 20px;
}

/* Berubah warna saat mouse melayang di atasnya */
.tombol-login:hover {
  background-color: navy;
}
```

> Tanpa pseudo-class, kamu harus pakai JavaScript untuk efek seperti ini. Pseudo-class membuatnya jauh lebih ringkas dan efisien.

---

### 2. Status Interaksi Pengguna (Interactive States)

Ini adalah kelompok pseudo-class yang bereaksi terhadap respon fisik dari pengguna (mouse atau sentuhan).

- **`:hover` (Disentuh Mouse)**: Keadaan saat anak panah (kursor) mouse melayang di atas elemen, tapi belum diklik. Sangat sering dipakai untuk membuat tombol yang terasa _"hidup"_.
- **`:active` (Sedang Ditekan)**: Momen sepersekian detik ketika klik kiri mouse sedang dalam posisi ditekan tahan pada elemen tersebut.
- **`:focus` (Jadi Perhatian)**: Status saat sebuah elemen sedang "aktif/menyala" karena baru saja diklik atau diakses menggunakan tombol TAB di keyboard (Sering dipakai pada kotak input form).

```css
/* Gaya tombol saat normal diam */
.tombol-beli {
  background-color: blue;
  color: white;
}
/* Saat mouse mampir di atas tombol (belum klik) */
.tombol-beli:hover {
  background-color: darkblue; /* Berubah jadi biru gelap */
  cursor: pointer; /* Ubah panah mouse jadi gambar tangan menunjuk */
}
/* Saat tombol sedang ditekan keras (klik kiri tahan) */
.tombol-beli:active {
  background-color: red; /* Sedetik jadi merah */
}
/* Saat kotak input form sedang di-klik siap diketik */
.kotak-nge-chat:focus {
  background-color: lightyellow;
  border: 3px solid orange;
}
```

**Analogi Bunglon:**

Elemen HTML pada dasarnya adalah bunglon. Saat diam di dahan, ia berwarna hijau (normal css). Namun saat ia merasa didekati pemangsa (kursor `hover`), ia otomatis mengubah warna kulitnya menjadi coklat.

**Contoh Lengkap — Tombol Belanja Online:**

```html
<!-- HTML -->
<button class="tombol-beli">🛒 Tambah ke Keranjang</button>

<form>
  <input class="kotak-nge-chat" type="text" placeholder="Tulis pesanmu..." />
</form>
```

```css
/* CSS */

/* --- Tombol Beli --- */
.tombol-beli {
  background-color: blue;
  color: white;
  padding: 12px 24px;
  border: none;
  border-radius: 6px;
  font-size: 16px;
}

/* Mouse melayang → biru gelap */
.tombol-beli:hover {
  background-color: darkblue;
  cursor: pointer;
}

/* Klik ditahan → merah sebentar (efek "ditekan") */
.tombol-beli:active {
  background-color: red;
  transform: scale(0.97); /* tombol terkesan "masuk" saat diklik */
}

/* --- Kotak Input Chat --- */
.kotak-nge-chat {
  padding: 10px;
  border: 2px solid gray;
  border-radius: 4px;
  width: 300px;
}

/* Input diklik siap diketik → border berubah oranye */
.kotak-nge-chat:focus {
  background-color: lightyellow;
  border: 3px solid orange;
  outline: none; /* hilangkan outline bawaan browser */
}
```

> **Catatan:** Urutan penulisan `:hover`, `:focus`, dan `:active` di CSS sebaiknya mengikuti urutan ini agar tidak saling menimpa satu sama lain.

---

### 3. Status Urutan Silsilah (Tree-Structural States)

Lalu, bagaimana jika kamu punya 10 baris di dalam tabel HTML, dan kamu hanya ingin mewarnai baris nomer 1 saja, atau mewarnai selang-seling genap-ganjil tanpa harus memberi ID satu-satu?

Gunakan kelompok pseudo-class logika matematika silsilah ini!

- **`:first-child`**: Menargetkan anak sulung (urutan pertama mutlak).
- **`:last-child`**: Menargetkan anak bungsung (urutan terakhir mutlak).
- **`:nth-child(angka/rumus)`**: Menargetkan urutan persis sesuai angka yang kamu kirim, atau pakai rumus canggih.

```css
/* Mewarnai paragraf urutan pertama menjadi tebal */
p:first-child {
  font-weight: bold;
}
/* Mewarnai baris ketiga (urutan ke-3) persis di tabel */
tr:nth-child(3) {
  background-color: gray;
}
/* Trik Dewa: Mewarnai selang-seling (Zebra Cross) genap ganjil! */
tr:nth-child(even) {
  background-color: white;
} /* Untuk urutan 2,4,6... */
tr:nth-child(odd) {
  background-color: lightblue;
} /* Untuk urutan 1,3,5... */
```

**Contoh Lengkap — Daftar Menu Restoran:**

```html
<!-- HTML -->
<ul class="menu-restoran">
  <li>Nasi Goreng Spesial</li>   <!-- urutan ke-1 -->
  <li>Mie Ayam Bakso</li>        <!-- urutan ke-2 -->
  <li>Soto Betawi</li>           <!-- urutan ke-3 -->
  <li>Rendang Daging</li>        <!-- urutan ke-4 -->
  <li>Es Teh Manis</li>          <!-- urutan ke-5 (terakhir) -->
</ul>
```

```css
/* CSS */

/* Semua item: tampilan dasar */
.menu-restoran li {
  padding: 8px 12px;
  list-style: none;
}

/* Item PERTAMA → ditandai sebagai "Rekomendasi Chef" */
.menu-restoran li:first-child {
  font-weight: bold;
  color: darkgreen;
  border-left: 4px solid gold;
}

/* Item TERAKHIR → warna berbeda sebagai penutup */
.menu-restoran li:last-child {
  color: steelblue;
  font-style: italic;
}

/* Item urutan ke-3 tepat → highlight khusus */
.menu-restoran li:nth-child(3) {
  background-color: lightyellow;
}

/* Efek Zebra: genap putih, ganjil abu-abu muda */
.menu-restoran li:nth-child(even) {
  background-color: #f5f5f5;
}
.menu-restoran li:nth-child(odd) {
  background-color: #ffffff;
}
```

**Contoh Rumus Matematika di `:nth-child`:**

```css
/* Setiap 3 elemen mulai dari elemen ke-1: 1, 4, 7, 10, ... */
li:nth-child(3n+1) {
  color: tomato;
}

/* 5 elemen pertama saja */
li:nth-child(-n+5) {
  font-weight: bold;
}
```

> **Rumus umum:** `nth-child(An+B)` — di mana **A** adalah interval pengulangan dan **B** adalah titik mulainya. Contoh: `nth-child(2n+1)` = setiap 2 elemen mulai dari ke-1 = sama dengan `odd`.

---

### 4. Pseudo-Class Tambahan yang Berguna

Selain tiga kelompok di atas, ada beberapa pseudo-class lain yang sering dipakai dalam praktik nyata:

- **`:visited`**: Tautan yang sudah pernah dikunjungi oleh pengguna.
- **`:disabled`**: Elemen form (tombol/input) yang sedang dinonaktifkan.
- **`:checked`**: Checkbox atau radio button yang sedang dalam kondisi tercentang.
- **`:not(selektor)`**: Menargetkan semua elemen **kecuali** yang cocok dengan selektor di dalam kurung.

**Contoh:**

```html
<!-- HTML -->
<a href="https://google.com" class="tautan">Kunjungi Google</a>

<button class="tombol-kirim" disabled>Kirim (Tidak Aktif)</button>

<input type="checkbox" id="setuju" class="kotak-centang" />
<label for="setuju">Saya setuju dengan syarat & ketentuan</label>

<ul class="daftar-fitur">
  <li>Fitur A</li>
  <li class="premium">Fitur B (Premium)</li>
  <li>Fitur C</li>
  <li class="premium">Fitur D (Premium)</li>
</ul>
```

```css
/* Tautan yang sudah pernah dikunjungi → warna ungu */
.tautan:visited {
  color: purple;
}

/* Tombol yang disabled → tampak pudar dan tidak bisa diklik */
.tombol-kirim:disabled {
  background-color: lightgray;
  color: darkgray;
  cursor: not-allowed;
}

/* Checkbox saat dicentang → label berubah hijau */
.kotak-centang:checked + label {
  color: green;
  font-weight: bold;
}

/* Semua li KECUALI yang punya class "premium" */
.daftar-fitur li:not(.premium) {
  color: black;
}

/* Khusus item premium */
.daftar-fitur li.premium {
  color: goldenrod;
  font-weight: bold;
}
```

> **Catatan `:not()`:** Sangat berguna ketika kamu ingin menggaya "semua elemen kecuali satu kondisi tertentu" — menghindari penulisan class baru yang tidak perlu.

---

### Kesimpulan

Pseudo-Class adalah jalan pintas CSS agar kita tidak perlu menumpuk puluhan teks nama `class="baru"` di dokumen HTML hanya untuk mengubah visual sesaat. Biarkan CSS yang pintar melacak keadaan status (interaksi dan urutan) dan mengaplikasikan kosmetiknya secara gaib otomatis.

**Ringkasan Pseudo-Class yang Sudah Dipelajari:**

| Pseudo-Class | Kategori | Kapan Aktif |
|---|---|---|
| `:hover` | Interaksi | Mouse melayang di atas elemen |
| `:active` | Interaksi | Elemen sedang diklik/ditekan |
| `:focus` | Interaksi | Elemen sedang aktif/dipilih |
| `:first-child` | Struktural | Anak pertama dari induknya |
| `:last-child` | Struktural | Anak terakhir dari induknya |
| `:nth-child(n)` | Struktural | Anak ke-n sesuai angka/rumus |
| `:visited` | Tautan | Link sudah pernah dikunjungi |
| `:disabled` | Form | Elemen form dinonaktifkan |
| `:checked` | Form | Checkbox/radio tercentang |
| `:not(x)` | Logika | Semua elemen kecuali `x` |
