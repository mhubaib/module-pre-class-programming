# Bab 1: Web Browser, HTML, & Sejarah HTML

## Tujuan Pembelajaran

- Memahami pengertian dan peran krusial Web Browser dalam ekosistem internet.
- Mengenal cara kerja website secara sederhana.
- Memahami apa itu HTML dan perannya dalam membangun website (melalui analogi yang mudah).
- Mengetahui alur sejarah perkembangan HTML hingga menjadi standar modern (HTML5) yang kita nikmati saat ini.

## Materi Utama

### 1. Apa itu Web Browser dan Bagaimana Cara Kerjanya?

Sebelum kita belajar membuat website, kita harus paham dulu di mana website itu "hidup" dan "ditampilkan". Jawabannya adalah di **Web Browser**.
Web Browser (atau peramban web) adalah sebuah perangkat lunak (software) atau aplikasi yang tugas utamanya adalah mengambil dan menampilkan konten berisi teks, gambar, video, dan interaksi dari internet (World Wide Web) ke layar perangkat kita.

Contoh Web Browser populer: Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, dan Opera.

**Cara Kerja Web Browser (Analogi Restoran):**
Bayangkan kamu sedang makan di sebuah restoran:

1. **Kamu (sebagai User/Pengguna):** Memilih menu makanan (misalnya, kamu mengetikkan `youtube.com` di browser dan menekan Enter).
2. **Pelayan (sebagai Web Browser):** Menerima pesananmu, mencatatnya, dan membawanya ke dapur.
3. **Dapur (sebagai Server):** Dapur tempat koki memasak ini adalah sebuah komputer super yang berada jauh di belahan dunia lain. Dapur ini menyimpan semua resep (kode website). Dapur memproses pesanan pelayan dan menyiapkan "makanannya".
4. **Pelayan Membawa Makanan (Proses Rendering):** Dapur menyerahkan bahan mentah berupa kode-kode (seperti HTML, CSS, JavaScript) kepada pelayan. Sang pelayan (Web Browser) kemudian bertugas "menata" dan "menyajikan" bahan-bahan mentah tersebut menjadi hidangan visual yang indah di mejamu (layar komputermu) agar bisa langsung dinikmati.

Tanpa Web Browser, internet hanyalah kumpulan kode teks mesin yang tidak bisa dibaca oleh manusia biasa.

### 2. Apa itu HTML?

HTML merupakan kependekan dari **HyperText Markup Language**.
Satu hal yang paling penting untuk diingat: **HTML BUKANLAH Basa Pemrograman (Programming Language).** HTML adalah **Bahasa Markup (Markup Language).**

- Bahasa pemrograman (seperti JavaScript, Python, C++) memiliki fitur logika komputasi seperti `jika A maka B` (If-Else), perulangan (Looping), dan manipulasi data.
- Bahasa Markup tidak punya itu semua. Tugas HTML HANYA SATU: **Menandai dan menstrukturkan sebuah dokumen atau teks.** HTML sekadar memberi tahu browser: "Hei browser, teks yang ini adalah judul utama. Teks yang ini adalah paragraf biasa. Kalau yang ini adalah gambar, dan yang itu adalah tombol."

**Analogi Membangun Rumah (Hubungan HTML, CSS, dan JavaScript):**
Untuk memahami peran HTML dalam Front-End Web Development, bayangkan kamu sedang membangun sebuah rumah dari nol.

- **HTML adalah Fondasi dan Rangka Bangunan (Batu bata, Semen, Tiang).** HTML menentukan bentuk struktur rumahnya (Di mana letak ruang tamu, di mana letak jendela, di mana toilet). Tanpa HTML, rumah tersebut tidak akan berdiri sama sekali.
- **CSS adalah Dekorasi (Cat, Lantai Keramik, Gorden, Taman).** CSS membuat rangka rumah tadi menjadi cantik, estetik, dan nyaman dipandang. Rumah tanpa CSS hanyalah susunan bata mentah yang jelek.
- **JavaScript adalah Instalasi Listrik dan Air (Stopkontak, Pintu Otomatis, AC).** JavaScript membuat rumahmu menjadi "hidup" dan interaktif. Jika kamu menekan saklar lampu (tombol ditekan), maka lampu akan menyala (pop-up muncul di website).

Oleh karena itu, langkah pertama bermimpi menjadi Web Developer harus selalu dimulai dari menguasai fondasinya, yaitu HTML.

### 3. Sejarah Singkat Evolusi HTML

Mengapa kita harus belajar HTML5? Karena HTML telah melalui perjalanan panjang:

- **1989-1991 (Era Kelahiran):** Diciptakan oleh **Tim Berners-Lee**, seorang ilmuwan di CERN. Niat awal beliau sangat sederhana: beliau ingin membuat sebuah sistem di mana dokumen laporan penelitian para ilmuwan di berbagai komputer bisa saling terhubung lewat "Link" (HyperText). Tidak ada pikiran membuat desain web atau main game di browser seperti sekarang! Tampilannya saat itu murni teks hitam putih.
- **1995 (HTML 2.0):** Versi ini mulai memperkenalkan fitur sederhana seperti form input dan tabel.
- **1997-1999 (HTML 3.2 hingga HTML 4.01):** Era di mana internet mulai booming secara komersial (Era Dotcom). Desain website mulai ada warna dan struktur yang lebih rapi menggunakan CSS sederhana. HTML 4.01 menjadi standar legendaris yang dipakai selama belasan tahun.
- **Era 2000-an (XHTML):** Sempat muncul usaha untuk membuat versi HTML yang saking ketat aturannya, sangat sulit dipelajari oleh pemula. Jika lupa 1 karakter saja, website akan error total. Karena terlalu ketat, standar ini pelan-pelan ditinggalkan.
- **2014 - Sekarang (Era HTML5):** Sebuah gebrakan besar. HTML5 dirilis untuk merevolusi internet. Fitur canggih HTML5 antara lain:
  1. Bisa memutar Video dan Audio langsung tanpa perlu menginstal aplikasi bantuan seperti Adobe Flash Player.
  2. Struktur yang lebih spesifik ("Semantik") yang disukai oleh Google Search Engine.
  3. Mendukung pembuatan web responsif (menyesuaikan ukuran layar HP).
  4. Mendukung kinerja web yang bisa berjalan secara _offline_.
