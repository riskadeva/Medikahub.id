# MedikaHub — Platform Informasi Kesehatan Digital

> Tugas Daily Project 7 — Rekayasa Kebutuhan D  
> Riska Nurhayati Deva · NIM: 202310370311371  
> Universitas Muhammadiyah Malang

---

## Tentang Proyek

MedikaHub adalah platform informasi kesehatan berbasis web yang dirancang untuk masyarakat Indonesia. Tujuan utamanya sederhana: memudahkan orang menemukan informasi kesehatan yang akurat, menemukan dokter terverifikasi, dan mengajukan pertanyaan medis tanpa harus langsung ke klinik.

Platform ini **bukan** aplikasi telemedicine dan **tidak** menyediakan diagnosis otomatis. Semua jawaban dokter di forum bersifat informatif sebagai bahan edukasi.

---

## Fitur Utama

### 🔍 Cari Dokter & Rumah Sakit
Pengguna bisa mencari dokter berdasarkan spesialisasi, kota, rating, dan ketersediaan BPJS. Setiap profil dokter menampilkan jadwal praktik, nomor STR/SIP, dan biografi singkat.

### 📋 Info Penyakit
Kumpulan artikel kesehatan yang ditulis dan ditinjau oleh dokter. Mencakup gejala, penyebab, penanganan awal, dan panduan obat generik. Artikel bisa difilter berdasarkan kategori seperti Kardiologi, Diabetes, Pediatri, dll.

### 💬 Forum Tanya Jawab
Pengguna yang sudah login bisa mengajukan pertanyaan kesehatan. Pertanyaan diklasifikasikan berdasarkan spesialisasi dan akan masuk ke dashboard dokter yang relevan untuk dijawab.

### 📊 Dashboard Dokter
Panel khusus untuk dokter terverifikasi. Di sini dokter bisa mengelola profil, melihat pertanyaan masuk sesuai spesialisasinya, menjawab pertanyaan, mengatur jadwal praktik, dan memantau statistik keterlibatan.

---

## Aktor Sistem

| Aktor | Peran |
|---|---|
| Masyarakat / Pasien| Mencari dokter, membaca artikel, bertanya di forum (setelah login) |
| Dokter Terverifikasi| Mengelola profil dan jadwal, menjawab pertanyaan dari dashboard |
| Admin Sistem** | Memverifikasi STR/SIP dokter, moderasi konten platform |

---

## Teknologi

Proyek ini dibangun sebagai **Single Page Application (SPA)** murni tanpa framework eksternal:

- **HTML5** — struktur dan semantik halaman
- **CSS3** — styling custom dengan CSS Variables untuk theming yang konsisten
- **Vanilla JavaScript** — navigasi antar halaman, render data dinamis, filter & sorting
- **Google Fonts** — tipografi menggunakan Lora (serif) dan Plus Jakarta Sans

Tidak ada backend, database, atau library JavaScript eksternal yang digunakan. Semua data bersifat statis dan di-render langsung dari objek JavaScript.

---

## Struktur Halaman

```
index.html
│
├── Beranda (Hero, Fitur Unggulan, Dokter Unggulan, Artikel, CTA)
├── Cari Dokter (Filter panel + daftar dokter + modal profil)
├── Info Penyakit (Grid artikel + filter kategori + halaman detail)
├── Forum Tanya Jawab (Post pertanyaan + list Q&A + modal thread)
└── Dashboard Dokter (Sidebar nav + 6 sub-halaman manajemen)
```

---

## Cara Menjalankan

Karena ini adalah file HTML statis, tidak perlu instalasi apapun.

1. Download atau clone repositori ini
2. Buka file `index.html` langsung di browser
3. Selesai — tidak perlu server lokal

```bash
# Atau kalau mau pakai live server sederhana:
npx serve .
```

---

## Data & Konten

Semua data dokter, artikel, dan pertanyaan forum sudah tersedia sebagai data statis di dalam file HTML (array JavaScript). Data ini mencakup:

- **6 dokter** dari berbagai spesialisasi (Kardiologi, Pediatri, Penyakit Dalam, Neurologi, Obstetri & Ginekologi, Dermatologi)
- **6 artikel** kesehatan lengkap dengan konten medis
- **5 pertanyaan forum** dengan contoh jawaban dokter

---

## Hasil Pengujian

Pengujian dilakukan secara manual dengan membuka `index.html` di browser Chrome (desktop) dan Firefox (mobile emulator). Aspek pengujian mengacu pada kebutuhan fungsional dan non-fungsional yang telah didefinisikan di Daily Project 6.

---

### 1. Pengujian Fungsional

#### Fitur 1 — Pencarian Dokter & Rumah Sakit

| No | Skenario Uji | Langkah | Hasil yang Diharapkan | Hasil Aktual | Status |
|----|---|---|---|---|---|
| F1-01 | Tampil daftar dokter saat halaman dibuka | Buka halaman "Cari Dokter" | 6 kartu dokter tampil dengan nama, spesialisasi, dan rating | 6 dokter ter-render dengan benar | ✅ Lulus |
| F1-02 | Filter berdasarkan spesialisasi | Pilih "Kardiologi" → klik "Terapkan Filter" | Hanya dokter Kardiologi yang tampil | Hanya dr. Riska Nurhayati Deva yang muncul | ✅ Lulus |
| F1-03 | Filter berdasarkan kota | Pilih kota "Malang" → klik "Terapkan Filter" | Hanya dokter di Malang yang tampil | dr. Muhammad Syukri (Malang) muncul | ✅ Lulus |
| F1-04 | Filter BPJS | Centang "Menerima BPJS" → klik "Terapkan Filter" | Dokter non-BPJS tersembunyi | dr. Dewi Pratiwi dan dr. Ratna Permata tidak muncul | ✅ Lulus |
| F1-05 | Sorting dokter | Pilih "Urutkan: A - Z" dari dropdown | Daftar dokter terurut alfabetis | Daftar berubah urutan sesuai abjad | ✅ Lulus |
| F1-06 | Lihat profil lengkap dokter | Klik tombol "Lihat Profil" pada salah satu dokter | Modal profil muncul dengan jadwal, STR/SIP, dan biografi | Modal muncul dengan data lengkap | ✅ Lulus |
| F1-07 | Tutup modal profil | Klik tombol ✕ atau area di luar modal | Modal tertutup | Modal tertutup dengan benar | ✅ Lulus |
| F1-08 | Tombol navigasi ke Forum dari modal | Klik "Tanya Dokter Ini di Forum →" dalam modal | Modal tertutup, pindah ke halaman Forum | Berhasil pindah ke halaman Forum | ✅ Lulus |

#### Fitur 2 — Informasi Penyakit

| No | Skenario Uji | Langkah | Hasil yang Diharapkan | Hasil Aktual | Status |
|----|---|---|---|---|---|
| F2-01 | Tampil grid artikel saat halaman dibuka | Buka halaman "Info Penyakit" | 6 kartu artikel tampil | 6 artikel ter-render dengan benar | ✅ Lulus |
| F2-02 | Filter artikel per kategori | Klik chip "🫀 Kardiologi" | Hanya artikel kategori Kardiologi yang tampil | Hanya 1 artikel Kardiologi muncul | ✅ Lulus |
| F2-03 | Filter kembali ke semua artikel | Klik chip "Semua" | Semua 6 artikel tampil kembali | 6 artikel muncul kembali | ✅ Lulus |
| F2-04 | Buka detail artikel | Klik kartu artikel mana saja | Tampilan beralih ke halaman detail artikel | Konten artikel lengkap tampil | ✅ Lulus |
| F2-05 | Kembali dari halaman detail | Klik "← Kembali ke Info Penyakit" | Tampilan kembali ke grid artikel | Grid artikel tampil kembali | ✅ Lulus |
| F2-06 | Info box dan warning box tampil | Buka artikel "Serangan Jantung" | Kotak biru (info) dan oranye (warning) terlihat jelas | Kedua kotak tampil dengan warna dan teks yang benar | ✅ Lulus |

#### Fitur 3 — Forum Tanya Jawab

| No | Skenario Uji | Langkah | Hasil yang Diharapkan | Hasil Aktual | Status |
|----|---|---|---|---|---|
| F3-01 | Tampil daftar pertanyaan | Buka halaman "Forum" | 5 kartu pertanyaan tampil | 5 pertanyaan ter-render | ✅ Lulus |
| F3-02 | Form post pertanyaan tersembunyi sebelum login | Buka Forum tanpa login | Muncul notifikasi "Login diperlukan" | Pesan login muncul, form tersembunyi | ✅ Lulus |
| F3-03 | Simulasi login berhasil | Klik tombol "Masuk / Daftar" | Toast sukses muncul, form pertanyaan terbuka | Toast "Login berhasil!" muncul, form tampil | ✅ Lulus |
| F3-04 | Validasi form kosong | Login → klik "Kirim Pertanyaan" tanpa isi | Toast peringatan muncul | Toast "Mohon lengkapi" muncul | ✅ Lulus |
| F3-05 | Submit pertanyaan baru | Isi judul + detail → klik "Kirim Pertanyaan" | Pertanyaan baru muncul di atas daftar, toast sukses | Pertanyaan baru tampil di daftar, toast muncul | ✅ Lulus |
| F3-06 | Filter pertanyaan "Sudah Dijawab" | Klik tombol "Sudah Dijawab" | Hanya pertanyaan berstatus answered yang tampil | 3 pertanyaan answered tersaring | ✅ Lulus |
| F3-07 | Filter pertanyaan "Menunggu" | Klik tombol "Menunggu" | Hanya pertanyaan berstatus waiting yang tampil | 2 pertanyaan waiting tersaring | ✅ Lulus |
| F3-08 | Buka thread pertanyaan | Klik kartu pertanyaan yang sudah dijawab | Modal thread muncul dengan jawaban dokter | Modal tampil dengan badge "✅ Terverifikasi" | ✅ Lulus |
| F3-09 | Buka thread pertanyaan belum dijawab | Klik kartu pertanyaan yang masih menunggu | Modal muncul dengan pesan "Menunggu jawaban dokter" | Teks ⏳ muncul di dalam modal | ✅ Lulus |
| F3-10 | Sidebar dokter online terlihat | Buka halaman Forum | Panel kanan menampilkan daftar dokter online | 3 dokter tampil dengan status dot | ✅ Lulus |

#### Fitur 4 — Dashboard Dokter

| No | Skenario Uji | Langkah | Hasil yang Diharapkan | Hasil Aktual | Status |
|----|---|---|---|---|---|
| F4-01 | Halaman ringkasan terbuka secara default | Buka "Dashboard Dokter" | Tab Ringkasan aktif, statistik 4 kartu tampil | Halaman overview tampil dengan benar | ✅ Lulus |
| F4-02 | Navigasi sidebar berfungsi | Klik "Pertanyaan Masuk" di sidebar | Konten berganti ke daftar pertanyaan masuk | Konten berganti, tab aktif berubah | ✅ Lulus |
| F4-03 | Tab Edit Profil | Klik "Edit Profil" di sidebar | Form edit profil dengan data pre-filled tampil | Form tampil dengan data dokter | ✅ Lulus |
| F4-04 | Simpan perubahan profil | Klik "Simpan Perubahan" | Toast konfirmasi muncul | Toast "Profil berhasil disimpan!" muncul | ✅ Lulus |
| F4-05 | Tab Jadwal Praktik | Klik "Jadwal Praktik" di sidebar | Tabel jadwal 6 hari tampil | Tabel tampil dengan status aktif/libur | ✅ Lulus |
| F4-06 | Simpan jadwal | Klik "Simpan Jadwal" | Toast konfirmasi muncul | Toast "Jadwal berhasil diperbarui!" muncul | ✅ Lulus |
| F4-07 | Tab Statistik | Klik "Statistik" di sidebar | Grafik bar distribusi pertanyaan tampil | Progress bar per kategori tampil | ✅ Lulus |
| F4-08 | Modal jawab pertanyaan | Klik "Jawab Sekarang" pada pertanyaan pending | Modal tulis jawaban muncul dengan pertanyaan di atas | Modal tampil dengan konteks pertanyaan | ✅ Lulus |
| F4-09 | Validasi jawaban kosong | Buka modal jawab → klik "Kirim Jawaban" tanpa isi | Toast peringatan muncul | Toast "Kolom jawaban tidak boleh kosong" muncul | ✅ Lulus |
| F4-10 | Submit jawaban | Isi textarea → klik "Kirim Jawaban" | Modal tertutup, toast sukses muncul | Modal tutup, toast "Jawaban terkirim!" muncul | ✅ Lulus |
| F4-11 | Tab Pengaturan Notifikasi | Klik "Pengaturan Notifikasi" | 4 toggle opsi notifikasi tampil | Semua toggle tampil dan bisa diklik | ✅ Lulus |

---

### 2. Pengujian Non-Fungsional

#### Performa

| No | Aspek | Kriteria (DP6) | Cara Uji | Hasil Aktual | Status |
|----|---|---|---|---|---|
| NF-01 | Waktu muat halaman awal | Response time < 2 detik | Buka `index.html` dari lokal, amati waktu render | Halaman selesai render < 1 detik (file statis tanpa request jaringan) | ✅ Lulus |
| NF-02 | Perpindahan antar halaman | Navigasi terasa instan | Klik setiap menu navbar secara berulang | Perpindahan halaman < 50ms, tidak ada delay terasa | ✅ Lulus |
| NF-03 | Render daftar dokter | Tidak ada lag saat filter | Terapkan beberapa filter berturut-turut | List langsung ter-render ulang tanpa jeda terlihat | ✅ Lulus |

#### Keamanan

| No | Aspek | Kriteria (DP6) | Cara Uji | Hasil Aktual | Status |
|----|---|---|---|---|---|
| NF-04 | Pembatasan akses forum | Hanya pengguna login yang bisa posting | Coba akses form tanpa klik login | Form tersembunyi, hanya notifikasi login yang tampil | ✅ Lulus |
| NF-05 | Disclaimer medis terlihat | Konten sesuai UU ITE | Cek semua halaman | Disclaimer bar tampil di setiap halaman, jawaban forum diberi label "bukan diagnosis resmi" | ✅ Lulus |
| NF-06 | Batasan sistem tegas | Tidak ada klaim diagnosis otomatis | Baca semua teks pada UI | Tidak ditemukan klaim diagnosis; peringatan "bukan telemedicine" tampil di beranda | ✅ Lulus |

#### Skalabilitas & Kompatibilitas

| No | Aspek | Kriteria (DP6) | Cara Uji | Hasil Aktual | Status |
|----|---|---|---|---|---|
| NF-07 | Responsif di layar kecil (≤600px) | Mendukung akses mobile | Buka di Chrome DevTools mode mobile (375px) | Navbar berubah jadi hamburger, grid menjadi 1 kolom, layout menyesuaikan | ✅ Lulus |
| NF-08 | Responsif di tablet (≤900px) | Layout menyesuaikan ukuran layar | Buka di mode tablet (768px) | Fitur grid berubah 2 kolom, sidebar forum tersembunyi | ✅ Lulus |
| NF-09 | Kompatibilitas multi-browser | Berjalan di browser modern | Buka di Chrome dan Firefox | Tampilan dan fungsi konsisten di kedua browser | ✅ Lulus |

#### Kepatuhan Konten

| No | Aspek | Kriteria (DP6) | Cara Uji | Hasil Aktual | Status |
|----|---|---|---|---|---|
| NF-10 | Data dokter terverifikasi | Profil dokter menampilkan STR & SIP | Buka modal profil dokter | Nomor STR dan SIP tampil di setiap profil dokter | ✅ Lulus |
| NF-11 | Artikel ditinjau dokter | Setiap artikel mencantumkan nama dokter pengulas | Buka beberapa artikel | Semua artikel mencantumkan nama dan spesialisasi dokter penulis | ✅ Lulus |
| NF-12 | Peringatan darurat medis tersedia | Ada panduan darurat yang jelas | Cek forum dan artikel | Box "Darurat Medis? Hubungi 119" tersedia di sidebar forum dan artikel | ✅ Lulus |

---

### Ringkasan Hasil Pengujian

| Kategori | Total Uji | Lulus | Tidak Lulus |
|---|---|---|---|
| Fungsional – Cari Dokter | 8 | 8 | 0 |
| Fungsional – Info Penyakit | 6 | 6 | 0 |
| Fungsional – Forum | 10 | 10 | 0 |
| Fungsional – Dashboard | 11 | 11 | 0 |
| Non-Fungsional – Performa | 3 | 3 | 0 |
| Non-Fungsional – Keamanan | 3 | 3 | 0 |
| Non-Fungsional – Skalabilitas | 3 | 3 | 0 |
| Non-Fungsional – Kepatuhan | 3 | 3 | 0 |
| **Total** | **47** | **47** | **0** |

> Semua skenario pengujian lulus. Catatan: pengujian dilakukan pada prototype statis sehingga beberapa aspek seperti autentikasi OAuth 2.0 dan uptime 99.5% belum bisa diuji secara nyata karena tidak ada backend aktif.

---

## Batasan Sistem

- Tidak ada autentikasi sungguhan — tombol login hanya simulasi untuk keperluan demo
- Data tidak tersimpan ke database — refresh halaman akan mereset semua perubahan
- Fitur pencarian belum terhubung ke filter (hanya navigasi ke halaman Cari Dokter)
- Tidak ada fitur upload dokumen atau gambar

---

## Catatan Medis & Disclaimer

> ⚠️ Seluruh informasi di MedikaHub bersifat **edukatif** dan **bukan pengganti diagnosis atau saran medis profesional**. Selalu konsultasikan kondisi kesehatan Anda kepada dokter yang kompeten.

Platform ini dikembangkan sesuai prinsip-prinsip UU ITE dan Permenkes RI terkait informasi kesehatan digital.

---

