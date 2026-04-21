# Bab 25: CSS Margin

## Tujuan Pembelajaran

- Memahami Margin sebagai jarak tolak-menolak antar elemen.
- Menguasai cara penulisan Margin pada tiap sisi secara fleksibel.
- Menerapkan trik ajaib memusatkan elemen secara otomatis dengan `margin: auto;`.
- Memahami anomali rahasia bernama _Margin Collapse_ (Margin yang bersatu).

## Materi Utama

Jika Padding di Bab 24 mengatur urusan "ruang di dalam kotak", maka sekarang kita membahas urusan tetangga. **Margin** mengatur urusan di "luar kotak".

Tanpa Margin, dua buah paragraf akan saling bertabrakan kening layaknya baris tanpa spasi.

### 1. Apa itu Margin?

**Margin** adalah ruang kosong memisahkan batas luar sebuah kotak dengan kotak elemen lain di sekelilingnya. Area margin selalu transparan/bening, dan dia tidak memiliki warna latar belakang (_background-color_).

**Analogi Jaga Jarak (Social Distancing):**
Jika Padding adalah menambah ketebalan kulit mantelmu agar kamu hangat, Margin adalah seberapa panjang kamu merentangkan kedua tanganmu agar orang yang lewat di depanmu tidak menyenggol wajahmu.

### 2. Aturan Penulisan Margin

Cara kamu menentukan seberapa spesifik jaraknya sangat identik dengan Padding. Kamu memiliki 4 penjuru angin.

```css
.kotak-dijauhi {
  margin-top: 50px; /* Jauhkan kotak di atasku sebanyak 50px */
  margin-bottom: 30px;
  margin-left: 10px;
  margin-right: 10px;
}
```

**Penulisan Singkat (Shorthand: Atas Kanan Bawah Kiri):**

```css
.kotak-simetris {
  /* Atas-Bawah 20px, Kanan-Kiri 40px */
  margin: 20px 40px;
}
```

### 3. Trik Ajaib Tengah Layar: `margin: auto;`

Pernah bertanya-tanya bagaimana desainer web membuat satu kotak utama berdiri kokoh persis di tengah-tengah layar kiri dan kanan secata akurat? Cukup gunakan nilai mutlak `auto` pada Margin horisontal.

Ketika kamu menyetel `margin-left: auto;` dan `margin-right: auto;`, browser akan melakukan perhitungan matematika otomatis membagi sisa ruang layar sama rata di kiri dan kanannya.

```css
.konten-tengah {
  width: 600px; /* Syarat Wajib: Harus punya ukuran Fix */
  margin: 0 auto; /* Atas/Bawah nol, Kiri/Kanan Auto */
}
```

_(Catatan Mandiri: Trik ini hanya bekerja pada sisi horisontal (mendatar). `auto` tidak bisa membuat kotak melayang ke tengah vertikal alias layar atas-bawah)._

### 4. Hal Mengerikan: Margin Collapse (Menyatunya Dua Margin)

Ada penyakit turunan unik dalam sejarah CSS yang sering membuat pemula kebingungan menghitung piksel. Anomali ini disebut **Margin Collapse**.

**Kasus:**
Bayangkan ada _Kotak A_ persis di atas _Kotak B_.

- Kotak A diberikan `margin-bottom: 50px;` (Kotak A minta jarak 50px ke bawah).
- Kotak B diberikan `margin-top: 30px;` (Kotak B minta jarak 30px ke atas).

Secara logika biasa, kamu pasti berpikir jarak total yang akan tercipta di antara mereka adalah `50px + 30px = 80px`. Ternyata **SALAH!**

Khusus untuk _Margin Atas/Bawah (Vertikal)_ yang saling bertemu langsung tanpa penghalang, CSS tidak akan menjumlahkannya. CSS akan memilih **Angka Tertinggi** yang menang, dan angka yang rendah akan dilebur (Kolaps).
Hasil jarak akhirnya di layar komputermu hanyalah 50px.
