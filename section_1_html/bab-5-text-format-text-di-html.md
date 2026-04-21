# Bab 5: Text & Format Text di HTML

## Tujuan Pembelajaran

- Mengenali berbagai macam elemen pemformatan teks di HTML.
- Memahami perbedaan antara elemen format yang murni mengubah visual vs elemen yang memiliki makna semantik.
- Mampu menebalkan, memiringkan, dan memberikan stabilo pada teks di dalam web.

## Materi Utama

Dalam aplikasi pengolah kata seperti Microsoft Word, kita seringkali menggunakan fitur _Bold_ (Tebal), _Italic_ (Miring), atau _Underline_ (Garis Bawah) agar teks atau kalimat tertentu mendapat perhatian ekstra.
Di HTML, kita juga bisa melakukan manipulasi (pemformatan) teks tersebut secara langsung menggunakan Tag khusus tanpa bantuan desain CSS.

### 1. Menebalkan Teks: `<b>` vs `<strong>`

Jika kamu ingin membuat sebuah kata **bercetak tebal**, ada dua pilihan tag yang bisa digunakan:

- Tag `<b>` (Bold): Hanya membuat teks menjadi tebal secara visual/mata telanjang.
- Tag `<strong>`: Membuat teks menjadi tebal, **namun** memiliki pesan terselubung ke Browser dan Google bahwa teks tersebut saking pentingnya butuh ditekankan.

**Kapan menggunakan yang mana? (Analogi Membaca Buku):**
Jika kamu membuat huruf tebal hanya demi _aesthetic_ atau mempercantik tampilan artikel biasa, gunakan `<b>`.
Tapi jika huruf tebal itu memperingatkan nyawa ("**Awas Racun!**"), gunakan `<strong>`. Aplikasi tuna netra (Screen Reader) akan membacakan teks dengan nada suara yang lebih tinggi dan menekan jika bertemu dengan tag `<strong>`.

```html
<p>
  Belajar HTML itu <b>mudah</b> dan sangat <strong>penting</strong> untuk masa
  depan.
</p>
```

### 2. Memiringkan Teks: `<i>` vs `<em>`

Mirip dengan konsep tebal tadi, untuk _memiringkan teks_ kita punya 2 saudara kembar:

- Tag `<i>` (Italic): Membuat karakter menjadi miring secara visual. Umumnya dipakai di istilah kalimat asing, bahasa Latin, atau kata pikiran.
- Tag `<em>` (Emphasis): Membuat karakter menjadi miring sekaligus menegaskan intonasinya (mirip dengan `strong`).

```html
<p>Kucing peliharaanku berjenis <i>Felis catus</i>.</p>
<p>Tolong dengarkan, kamu <em>harus</em> belajar setiap hari secata rutin!</p>
```

### 3. Elemen Pemformatan Teks Unik Lainnya

HTML ternyata memiliki segudang tag untuk memodifikasi teks layaknya buku tulis sungguhan. Berikut tag-tag berguna yang sering kamu temui:

- **`<mark>` (Efek Stabilo):**
  Digunakan untuk menyoroti tulisan (teks _highlight_) seakan-akan kamu mewarnainya dengan spidol stabilo kuning neon.

  ```html
  <p>Jangan lupa bawa <mark>KTP asli</mark> saat ujian besok.</p>
  ```

- **`<del>` (Teks Tercoret / Deleted):**
  Untuk memunculkan garis coretan menyamping tepat menembus teks (Serupa teknik _Strikethrough_).
  Sangat cocok digunakan untuk mencoret harga barang toko online yang sedang diskon.

  ```html
  <p>Promo! Harga dari <del>Rp 100.000</del> kini hanya Rp 20.000 saja!</p>
  ```

- **`<ins>` (Teks Tergaris-bawahi / Inserted):**
  Biasa dipasangkan dengan `<del>`. Mengubah tampilan teks yang baru disisipkan dengan memberinya garis aspal/garis bawah (Underline).

  ```html
  <p>Jadwal diundur menjadi <ins>hari Minggu</ins>.</p>
  ```

- **`<sub>` (Subscript):**
  Membuat ukuran teks lebih mengecil dan turun setengah garis ke arah **bawah**.
  Analogi: Digunakan oleh anak Kimia untuk menulis rumus senyawa kimia.

  ```html
  <p>Rumus air adalah H<sub>2</sub>O.</p>
  ```

- **`<sup>` (Superscript):**
  Lawan dari sub. Membuat ukuran teks lebih menyusut dan naik setengah garis ke arah **atas**.
  Analogi: Digunakan oleh anak Matematika untuk menulis bilangan kuadrat (pangkat) atau urutan tanggal.
  ```html
  <p>Kalkulasikan hasil 5<sup>2</sup> + 10.</p>
  ```
