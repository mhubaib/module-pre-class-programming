# Bab 57: Web API

## Tujuan Pembelajaran
- Memahami pengertian kolaborasi serah terima API (*Application Programming Interface*) dalam komunikasi Web.
- Mampu menarik (GET) sumber suplai pasokan data eksternal dari Server Backend nyata menggunakan alat modern JS `fetch()`.
- Mengimplementasikan pembedahan manipulasi data bungkusan bongkar format *Response JSON*.
- Mampu memadankan merajut menggabungkan seluruh kombinasi Asinkronus `async/await`, pengolahan bongkar `JSON`, hingga ke cetak layar langsung `DOM Manipulasi`.

## Materi Utama

Ini adalah gerbang kelulusan akhir. Bab puncak perpaduan di mana kita menggabungkan seluruh keilmuan yang telah dirintis dari Bab 36 hingga Bab 56. 

Pertanyaan fundamental mutlak pengembangan Web Front-End murni: "Dari manakah asal muasal gambar-gambar thumbnail produk berderet beribu-ribu di web Tokopedia? Bukankah mustahil programmernya mengetikkan *hardcode* susun capek lelah manual satu persatu nama diskon tiap barangnya ke dalam HTML?"

Jawabannya murni total: Penampilan Front-End kosong itu "Menarik memungut Suplai Pasokan Bahan Bakar Lemparan Data yang disediakan disediakan disajikan matang oleh Server Back-End lewat alat penyambung lorong Pipa yang bernama **API (Application Programming Interface)**."

### 1. Apa itu Web API?

Singkatnya murni mutlak, API adalah "Pelayan Resepsionis Penghubung Restoran". 
Kamu (Website Front-End) adalah Customer penonton yang duduk diam membaca menu minta dilayani, lalu Dapur Masak di belakang layar tebal berasap kompor (Database Back-End / MySQL / dll). 

Kamu tidak diizinkan menerobos paksa kasar masuk memegang wajan memutar motong bawang data ke Dapur sana. Kamu WAJIB harus bicara mengorder piringan menu (meminta aliran data) kepada Pelayan Lorong Jembatannya si **API**. (Biasanya API ini berwujud penampakan sebuah alamat URL panjang khusus berakhiran kumpulan teks sembako data `.json`).

### 2. Memanggil Kurir Pasokan Data Tarikan: Alat Sakti `fetch()`

Di dalam mesin browser JS mutakhir The V8 modern, telah disematkan di-build 1 Kurir Paketan Pengambil data khusus yang paling laris sakti tanpa tanding menggantikan mesin XMLHttpRequest kuno jadul. Namanya The `fetch()`.

*Fetch* aslinya ditakdirkan murni menjinjing fungsi luhur *Promise (Asinkronus / Nunggu Antrian tak ketebak detiknya)* karena pekerjaannya mengarungi kabel aspal paket laut Samudera Internet nyata. Sehingga ia wajib dan mutlak ditunggangi ditaklukkan dijahit memakai pelana kekang rantai Bab 56 kita: yaitu sang pengerem **`async/await`**.

### 3. Operasi Membedah Tuntas Mengirim & Mencetak API Ke Layar

Mari kita racik praktek nyata pamungkas ini berlatih memungut murni data Nama Judul Blog Acak (Dummy Data Placeholder) di situs uji coba seluruh dunia: `https://jsonplaceholder.typicode.com/posts`

**Skenario Rangkuman Akhir:**
- Buat Kerangka Fungsi Async pelana gembok `async`.
- Lontarkan alat `fetch()` dengan tembakan peluru gembok rem rem antrian `await`.
- Response balikan mentah bungkusan aspal dari Fetch-nya mutlak wajib disucikan dibersihkan dibongkar dilucuti cangkang segel bungkus pakét perjalanannya dari wujud String kiriman kaku kurir (Ingat Bab 55 `JSON`) menjadi Objek JS lumer Murni dengan menggunakan gembok rem penungguan ke 2: `await namaResponTarikan.json()`.
- Lakukan Pembedahan Pencetakan DOM ke Layar Penonton!

```html
<!-- Cuma Sebuah Div Kosong Kaku Semata Di File HTML awalmu -->
<div id="keranjang-layar">Sedang Memuat Tarikan Gila Data Server...</div>
```

```javascript
// 1. Gembok Fungsi Pelana Sakti AWALAN (Bab 56)
async function narikDataBeritaAPI() {
    try {
        // 2. Kurir Fetch ngegas ngambil data nyelam ke server internet luar!
        // REM PAKSA pakai await karena tarikan internet ke Amerika bisa aja molor 3 detikan!
        console.log("Proses terbang menyedot ke server...");
        const kotakBingkisanResponseMurni = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        
        // 3. Unboxing! Data Bingkisan masih kaku terbalut bungkus tebal JSON String bawaan perjalanan API kurir, cucikan dibongkar jadikan Lumer murni balikkan ke kastanya Object Array berlendir JS biasa! (Bab 55)
        // INGAT: Proses unboxing json() ini juga termasuk proses Antre Nunggu (Promise)! Wajib dikalungkan `await` Rem kedua!
        const objDataTarikLumer = await kotakBingkisanResponseMurni.json();

        // 4. Proses Puncaknya! (DOM Manipulasi Bab 52)
        // Manipulasi buang tulisan Loding HTML ganti timpa isi DOM layarnya menjadi lemparan data yang berhasil ditarik didapatin hasil dari field "title" yg diambil melintas mutlak dari server sana!
        document.getElementById("keranjang-layar").innerHTML = `
            <h1 style="color: blue;">Berita Update Terbaru:</h1>
            <h2>${objDataTarikLumer.title}</h2>
            <p>${objDataTarikLumer.body}</p>
        `;
        
    } catch (ancamanError) {
        // Sedia payung pencegah The Rejected apabila internet User mendadak Kena Putus Jaringannya atau Server target lagi Kebakaran Down!
        console.log("Mohon maaf Gagal Total Mutlak Menarik API! Jaringan Padam: " + ancamanError);
    }
}

// Terakhir, mutlak Jalankan Palu Eksekusi Panggilannya Fungsine Nyala:
narikDataBeritaAPI();
```

🎉 **Selamat Luar Biasa!!** 🎉
Jika logikamu sudah sampai luntur tembus mendarah daging membayangkan dan sanggup meniru mengulangi praktek penarikan manipulasi API terakhir kodingan berantai di atas... Anda secara resmi absah mutlak lulus tuntas dari status Pemula buta ke fase *Front-End Developer Madya*! Silabus utama koding rekayasa website mutlak Anda sudah komplit paripurna meramu Logika Javascript. Semua tinggal landasan pengokohan pemolesan. Waktumu merdeka! 🚀
