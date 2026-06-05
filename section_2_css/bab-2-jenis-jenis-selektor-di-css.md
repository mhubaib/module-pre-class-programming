# Bab 16: Jenis-jenis Selektor di CSS

## Tujuan Pembelajaran

- Memahami konsep Selektor untuk menargetkan elemen HTML tertentu.
- Mampu menggunakan Element Selector, Class Selector, dan ID Selector dengan tepat.
- Mengenal Universal Selector dan kegunaannya.
- Memahami perbedaan penggunaan antara Class dan ID.

## Materi Utama

Di materi sebelumnya, kita tahu bahwa **Selector** bertugas sebagai "pencari sasaran". Namun, bagaimana jika kita punya sepuluh paragraf tapi hanya ingin mewarnai satu paragraf saja menjadi merah? Atau bagaimana jika kita ingin mewarnai semua elemen di halaman web secara serentak?

Inilah gunanya kita mempelajari berbagai jenis Selektor.

### 1. Element Selector (Tag Selector)

Ini adalah cara paling umum dan sederhana. Kamu langsung memanggil nama tag HTML-nya. Semua tag yang namanya sama akan terkena dampak desain yang sama.

```css
p {
  color: green;
}
```

_Efeknya: SEMUA paragraf di website tersebut akan berubah warnanya menjadi hijau._

### 2. Class Selector (Selektor Grup)

Class selector sangat fleksibel karena bisa digunakan berkali-kali pada elemen yang berbeda. Untuk memanggilnya di CSS, kamu wajib menggunakan tanda **titik (.)** diikuti nama kelasnya.

Di HTML:

```html
<p class="teks-penting">Ini paragraf penting.</p>
<h2 class="teks-penting">Ini judul yang juga penting.</h2>
```

Di CSS:

```css
.teks-penting {
  font-weight: bold;
  color: red;
}
```

**Analogi Seragam Sekolah:**
Katakanlah di sebuah sekolah ada banyak murid (Element). Murid yang memakai **seragam Pramuka** (Class) akan berkumpul untuk latihan. Siapa pun bisa memakai seragam Pramuka, dan siapa pun yang memakainya akan dianggap sebagai bagian dari grup tersebut.

### 3. ID Selector (Selektor Unik)

ID selector bersifat sangat eksklusif atau unik. Dalam satu halaman HTML, sebuah nama ID **hanya boleh digunakan oleh satu elemen saja**. Untuk memanggilnya di CSS, gunakan tanda **pagar (#)**.

Di HTML:

```html
<div id="header-utama">
  <h1>Selamat Datang</h1>
</div>
```

Di CSS:

```css
#header-utama {
  background-color: yellow;
  padding: 20px;
}
```

**Analogi KTP atau NIK:**
Setiap orang mungkin punya seragam yang sama (Class), tapi setiap orang hanya punya satu Nomor Induk Kependudukan (ID) yang berbeda satu sama lain. ID digunakan untuk menunjuk satu target yang sangat spesifik.

### 4. Universal Selector

Jika kamu ingin mengatur satu properti untuk **seluruh** elemen yang ada di halaman web tanpa terkecuali, gunakan tanda **bintang (\*)**.

```css
* {
  margin: 0;
  padding: 0;
  font-family: Arial;
}
```

_Selektor ini biasanya digunakan di awal penulisan CSS untuk "meriset" atau menyamakan pengaturan dasar browser agar konsisten._

### 5. Ringkasan Perbedaan: Kapan Pakai Apa?

| Jenis Selektor |   Simbol   | Sifat             | Kegunaan Utama                                                    |
| :------------- | :--------: | :---------------- | :---------------------------------------------------------------- |
| **Element**    | (nama tag) | Massal            | Mengatur tampilan dasar dasar (misal: font untuk semua p).        |
| **Class**      |    `.`     | Reusable (Banyak) | Mengatur gaya yang bisa dipakai di banyak tempat berbeda.         |
| **ID**         |    `#`     | Unik (Hanya 1)    | Mengatur elemen besar yang cuma ada satu (misal: Navbar, Footer). |
| **Universal**  |    `*`     | Seluruh Halaman   | Mengatur reset dasar website.                                     |

**Aturan Penamaan:**
Nama Class dan ID bebas kamu tentukan, tapi **tidak boleh** diawali dengan angka, tidak boleh pakai spasi (gunakan tanda hubung `-`), dan sebaiknya gunakan nama yang mendeskripsikan fungsinya agar mudah diingat.
