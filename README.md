# Web Pengumuman Ranking

**Web Pengumuman Ranking** adalah sebuah aplikasi web sederhana yang dirancang agar siswa atau orang tua dapat mencari dan melihat hasil pengumuman kelulusan, nilai rata-rata, serta peringkat (ranking) siswa secara mandiri. Pencarian dilakukan dengan memasukkan Nomor Induk Siswa Nasional (NISN) atau Nomor Induk Siswa (NIS) yang valid.

Aplikasi ini dibuat secara **statis (tanpa database backend kompleks)**, sehingga sangat cepat, ringan, dan sangat mudah untuk dimodifikasi maupun di-hosting di mana saja.

---

## 🛠️ Teknologi yang Digunakan

Aplikasi ini dibangun menggunakan tumpukan teknologi (tech stack) sisi klien yang modern namun ringan:

*   **HTML5 & CSS3**: Sebagai kerangka dasar dan penataan desain antarmuka (UI).
*   **JavaScript (ES6)**: Untuk penanganan logika dasar.
*   **Vue.js 3 (Composition API)**: Diimpor melalui CDN. Vue digunakan karena kemampuannya dalam mengelola *state* (reaktivitas) antarmuka, pengikatan data dua arah (*two-way binding*), serta memperbarui tampilan secara otomatis tanpa manipulasi DOM yang rumit.

---

## ✨ Fitur dan Keunggulan

1.  **Pencarian Cepat & Reaktif**: Menampilkan data seketika setelah tombol cari ditekan dengan simulasi animasi *loading* yang halus.
2.  **Mode Gelap / Terang (Dark/Light Mode)**: Tersedia fitur penggantian tema yang otomatis menyimpan preferensi pengguna (via *Local Storage*) atau mengikuti pengaturan sistem perangkat.
3.  **Desain Responsif & Elegan**: Tampilan dirancang dengan estetika modern, warna yang memanjakan mata, kartu profil yang interaktif, dan dapat menyesuaikan ukuran layar (HP, Tablet, PC).
4.  **Validasi Input**: Mencegah pencarian kosong atau karakter yang salah (seperti huruf) sebelum proses pencarian dilakukan.
5.  **Tanpa Backend (Serverless)**: Karena data disimpan dalam bentuk *Array Object* (`mockStudents`) di file JavaScript, Anda tidak perlu mengelola server atau database SQL.

---

## 🚀 Panduan Deployment (Cara Hosting)

Karena aplikasi ini sepenuhnya bersifat *statis* (hanya terdiri dari HTML, CSS, dan JS), mendeploy-nya ke internet sangatlah mudah dan bahkan **bisa dilakukan secara gratis**. Berikut beberapa opsi cara upload (hosting) aplikasi ini:

### Opsi 1: Menggunakan cPanel (Hosting Biasa/Berbayar)
Jika sekolah atau Anda sudah memiliki domain dan hosting sendiri:
1. Buka File Manager di cPanel hosting Anda.
2. Masuk ke folder `public_html` (atau folder sub-domain yang Anda inginkan).
3. Jadikan seluruh file di dalam folder proyek ini (`index.html`, `style.css`, `app.js`, dan file lain jika ada) ke dalam format `.zip`.
4. Upload file `.zip` tersebut ke File Manager, lalu **Extract**.
5. Selesai! Web sudah bisa diakses melalui domain Anda.

### Opsi 2: Menggunakan Vercel atau Netlify (Gratis & Sangat Direkomendasikan)
Vercel dan Netlify adalah platform hosting khusus *frontend* yang sangat cepat dan gratis:
1. Buat akun di [Vercel](https://vercel.com/) atau [Netlify](https://www.netlify.com/).
2. Anda bisa menghubungkan akun GitHub Anda (jika kode ini disimpan di sana) atau cukup gunakan fitur **Drag & Drop** folder aplikasi secara manual.
3. Tunggu beberapa detik, dan platform tersebut akan memberikan Anda sebuah tautan/URL (contoh: `pengumuman-ranking.vercel.app`) yang sudah aktif dan bisa dibagikan.

### Opsi 3: Menggunakan GitHub Pages (Gratis)
1. Buat repositori baru di GitHub.
2. Upload semua file web ini (`index.html`, `app.js`, dll) ke repositori tersebut.
3. Masuk ke tab **Settings** repositori > menu **Pages**.
4. Pada bagian *Source*, pilih *branch* `main` dan simpan. GitHub akan mempublikasikan web Anda (contoh: `https://username.github.io/nama-repo/`).

---

## 📝 Panduan Menambahkan Data Siswa

Dokumen ini berisi panduan singkat tentang cara menambahkan data siswa baru ke dalam aplikasi pengumuman kelulusan/nilai.

### Langkah-langkah

1. Buka folder proyek aplikasi ini.
2. Cari dan buka file bernama `app.js` menggunakan *code editor* (seperti VS Code, Notepad++, atau Sublime Text).
3. Di bagian atas file (sekitar baris ke-4), cari variabel `mockStudents` yang dideklarasikan seperti berikut `const mockStudents = [`. Bagian ini berfungsi menyimpan seluruh data siswa.
4. Anda akan melihat data yang sudah ada diapit oleh tanda kurung kurawal `{ ... }` dan dipisahkan dengan tanda koma.

### Cara Menambahkan Data Baru

Untuk menambahkan siswa baru, berikan **tanda koma (`,`)** di akhir data terakhir, lalu buat baris kurung kurawal baru dengan format properti yang sama persis.

**Format Data:**
- `nama`: Nama lengkap siswa (harus diapit tanda kutip `""`).
- `nisn`: Nomor Induk Siswa Nasional (harus diapit tanda kutip `""`). Ini digunakan sebagai salah satu kunci pencarian.
- `nis`: Nomor Induk Siswa (harus diapit tanda kutip `""`). Ini juga digunakan sebagai kunci pencarian.
- `rataRata`: Nilai rata-rata siswa (berupa angka murni, gunakan titik `.` untuk desimal, bukan koma).
- `totalNilai`: Total seluruh nilai siswa (berupa angka bulat murni).
- `peringkat`: Peringkat atau ranking siswa (berupa angka murni).

**Contoh Penambahan Data:**
Misalnya, kita ingin menambahkan siswa ke-3 bernama "Budi Santoso". Anda perlu menyisipkan datanya ke dalam array tersebut sehingga kodenya menjadi seperti ini:

```javascript
const mockStudents = [
    { nama: "Amat Soemardji", nisn: "00098765432", nis: "25.12345", rataRata: 77.73, totalNilai: 855, peringkat: 1 },
    { nama: "Noor Hardjo", nisn: "00098765433", nis: "25.12346", rataRata: 83.36, totalNilai: 917, peringkat: 2 },
    // Di bawah ini adalah baris data baru yang ditambahkan
    { nama: "Budi Santoso", nisn: "00098765434", nis: "25.12347", rataRata: 85.50, totalNilai: 940, peringkat: 3 }
];
```

### Catatan Penting
* Perhatikan penulisan nama properti! Pastikan **huruf besar/kecil** sama persis (contoh: huruf 'R' pada `rataRata` dan huruf 'N' pada `totalNilai` harus kapital/huruf besar).
* Jangan lupa menyematkan **tanda koma `,`** pemisah antar blok data siswa `{...}, {...}`. Jika terlewat satu saja, aplikasi akan error dan halaman akan nge-blank (putih).
* Setelah selesai menambahkan data, jangan lupa untuk **Simpan / Save** file `app.js` tersebut (tekan `Ctrl + S` atau `Cmd + S`).
* Coba buka web aplikasinya dan lakukan pencarian menggunakan NIS/NISN yang baru saja Anda tambahkan untuk memastikan data telah masuk dan bekerja dengan baik.
