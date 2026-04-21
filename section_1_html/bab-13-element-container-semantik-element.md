# Bab 13: Element Container & Semantik Element

## Tujuan Pembelajaran

- Membedakan perilaku bawaan layout: _Block-level Element_ vs _Inline Element_.
- Menggunakan Tag `<div>` dan `<span>` sebagai pembungkus layout utama.
- Mendalami pemahaman lanjutan mengapa kita harus meninggalkan dominasi `<div>` kotor dan pindah menjadi elegan memakai _Semantic Tag_ (HTML5).

## Materi Utama

Pada bab tentang _Style CSS inline_ (Bab 6), kita pernah menyinggung bahwa setiap elemen HTML tanpa disadari memiliki bentukan sifat kotak pembungkus.
Namun, bagaimana cara menyatukan sekumpulan elemen terpisah—misal: _satu gambar profile_, _satu judul H2 nama_, dan _satu paragraf profesi_—menjadi sebuah "Kotak KTP Visual" gabungan yang solid?

Jawabannya adalah dibungkus menggunakan dewa pembantu: **Elemen Container**.

### 1. Karakteristik "Sifat Alami" HTML (Block vs Inline)

Sebelum main bungkus-bungkus, kita wajb hukumnya mengerti watak temperamen setiap tag HTML sewaktu dicentang jejer di Browser. Element terbagi jadi dua kaum besar.

**Kaum A: Block-Level Element (Penguasa Penuh Garis)**
Element yang memiliki watak maruk/egois. Ia akan "memaksa" mendorong setiap tetangga di sampingnya buat turun ke baris baru, tak peduli isinya sedikit, ia selalu melebarkan daerah otonomnya _full 100%_ menabrak tembok browser dari ujung kiri ke ujung kanan kertas panggung.
_Contoh gank ini:_ Paragraf `<p>`, Judul `<h1>...<h6>`, Tabel `<table>`, dan List `<ul> / <ol>`.

**Kaum B: Inline Element (Toleran Berjejer)**
Element kalem penakut. Ia akan menempel jejer damai sebalahan dengan tetangganya dalam "satu baris" lurus yang sama selagi ruang kanvas kanan browser masih muat. Ia cuma memakan wilayah sempit persis ukurkan kontennya sendiri tanpa membuat garis break baru.
_Contoh gank ini:_ Hyperlink `<a>`, Format huruf Tebal Miring `<b>` `<i>`, dan sisipan `<img>`.

### 2. Duo Kontainer Kosong: `<div>` vs `<span>`

Lalu ada tag spesial bernama **Containers**. Fungsinya hampa (tidak menghasilkan efek visual apa-apa kalau cuma dipanggil berdiri mentah), TAPI kekuatan sakti dewa terbesarnya adalah: Digunakan mempartisi batas wilayah untuk merapikan penyusunan CSS kelas berat Layouting.

Ini terbagi kembali sesuai watak Kaum di atas, yakni:

- **`<div>` (Division)** perwakilan geng **Block-Level**.
  Digunakan mengikat banyak baris tag raksasa jadi sekumpulan partisi struktur rapi.
  _Analogi:_ Menyusun piring, sendok, dan sumpit kotor (element-element bebas) dan memasukannya sekaligus ke dalam Ember cucian berskala Jumbo (`<div>`). Saat CSS disuruh menggerakkan embernya, maka otomatis piring dan sendok terikat itu ikutan geser serentak.

```html
<div style="background-color: lightgreen;">
  <h2>Box Kartu Hijau</h2>
  <p>Halo, saya di dalam pagar container div!</p>
</div>
```

- **`<span>`** perwakilan geng kalem **Inline**.
  Secara spesifik digunakan "Menarget modifikasi/CSS" pada sebiji selipan suku kata atau frase di perut aliran kalimat (Tanpa ngebobol turun baris).

```html
<p>
  Kamera cctv itu merekam
  <span style="color:red; font-weight:bold;">TINDAKAN KRIMINAL</span> semalam
  suntuk.
</p>
```

### 3. Move On dari "Mabuk Div" (Div-itis) ke Semantic Tag (HTML5)

Di era internet purba (tahun 2008), saking enaknya mendesain pembungkus pakai `<div>`, orang-orang keranjingan memakai code _Mabuk Div_.
Di mana-mana `<div>` isinya tumpuk `<div id="navbar">`, lalu ditumpuk `<div id="body-bawah">`, dst. Susunan kodalnya bikin merinding mata coder orang lain (dan Google Bingung total membacanya, tidak bisa membedakan mana isi berita asli, mana sisipan banner iklran sampah!).

Nah, **Semantic Elements (Tag Bermakna)** datang menyelamatkan peradaban layouting web sejak kehadiran paten HTML5. Struktur `<div id="kepala">` buatan programmer digantikan dengan kosa-kata elemen otentik yang spesifik memiliki fungsi definitif. (_(Catatan: Kami telah menyinggung ini di rangkuman SEO Bab 9, kini kita ulik mendalam pemetaan layoutnya!_).

_Blueprint Semantik Standard:_

1. **`<header>`**: Rumah bagi banner utama hero layar dan Menu.
2. **`<nav>`**: Lokasi sarang link navigasi (`<a>`).
3. **`<section>`**: Pemisah Bab Bab Topik artikel raksasa terisolasi independen.
4. **`<article>`**: Wadah esay inti liputan / produk detail dagangan.
5. **`<aside>`**: Menyimpan kotak kecil "Iklan Sidebar / Widget Kategori Terpopuler" yang numpang di pojok sisi.
6. **`<footer>`**: Pijakan basement web terbawah, menyimpan teks _Copyright_ 2026 dan sisa link hukum.

Jadilah Developer Front-End bermartabat, ganti `<div>` mu untuk Layout berkerangka besar dengan rajutan Semantic Elements HTML5 ini supaya gawai/komputer robot bersahabat ramah menyapamu.
