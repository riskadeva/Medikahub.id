# Dokumen Rencana Pengujian (Test Plan)
## MedikaHub — Platform Informasi Kesehatan Digital

---

### Informasi Dokumen

| Bidang | Detail |
| :--- | :--- |
| **Identifikasi Test Plan** | `TP-MEDIKAHUB-MOD1-202310370311371` |
| **Nama Aplikasi** | MedikaHub |
| **Versi** | v1.0 |
| **Peran yang Dipilih untuk Diuji** | **Masyarakat / Pasien** *(Hanya satu peran, konsisten sampai penilaian akhir)* |
| **Nama Praktikan** | Riska Nurhayati Deva |
| **NIM** | 202310370311371 |
| **Kelas** | Praktikum Pengujian Perangkat Lunak D |
| **Tanggal Dibuat** | 09 Oktober 2026 |
| **Tanggal Terakhir Diperbarui** | 09 Oktober 2026 |
| **Status** | Final (Draf Modul 1) |

---

### Riwayat Revisi

| Versi | Tanggal Revisi | Diperbarui Oleh | Deskripsi Perubahan |
| :---: | :---: | :---: | :--- |
| 1.0 | 09 Oktober 2026 | Riska Nurhayati Deva | Draf awal dokumen Test Plan Modul 1 (Konteks Pengujian, Risiko, Strategi, Lingkungan, Jadwal, dan Luaran). |

---

## DAFTAR ISI

- [1. Konteks Pengujian](#1-konteks-pengujian)
  - [1.1 Item Uji](#11-item-uji)
  - [1.2 Cakupan Pengujian](#12-cakupan-pengujian)
  - [1.3 Peran yang Dipilih untuk Diuji](#13-peran-yang-dipilih-untuk-diuji)
  - [1.4 Asumsi dan Batasan](#14-asumsi-dan-batasan)
- [2. Daftar Risiko](#2-daftar-risiko)
- [3. Strategi Pengujian](#3-strategi-pengujian)
  - [3.1 Pendekatan Keseluruhan](#31-pendekatan-keseluruhan)
  - [3.2 Arah Pengujian yang Direncanakan](#32-arah-pengujian-yang-direncanakan)
  - [3.3 Kriteria](#33-kriteria)
- [4. Lingkungan Pengujian](#4-lingkungan-pengujian)
  - [4.1 Perangkat dan Perangkat Keras](#41-perangkat-dan-perangkat-keras)
  - [4.2 Perangkat Lunak dan Alat](#42-perangkat-lunak-dan-alat)
  - [4.3 Jaringan dan Backend](#43-jaringan-dan-backend)
  - [4.4 Data Uji](#44-data-uji)
- [5. Jadwal Pengujian](#5-jadwal-pengujian)
- [6. Luaran Pengujian](#6-luaran-pengujian)
- [Lampiran A: Glosarium](#lampiran-a-glosarium)

---

## 1. Konteks Pengujian

Dokumen kebutuhan awal merupakan salah satu item kesiapan yang akan digunakan pada Modul 2. Pada Modul 1, praktikan cukup mengidentifikasi sumber kebutuhan yang tersedia dan mulai melengkapinya secara bertahap; dokumen tersebut belum harus selesai pada modul ini.

### 1.1 Item Uji

| Bidang | Deskripsi |
| :--- | :--- |
| **Nama Aplikasi** | MedikaHub |
| **Platform** | Web (Single Page Application / Desktop & Mobile Browser) |
| **Versi** | v1.0 |
| **URL Deployment / Akses** | `http://localhost:5500` / `file:///d:/PKLP%20SMTR%207/Medikahub/index.html` |
| **Tumpukan Teknologi** | HTML5, CSS3, Vanilla JavaScript (ES6+), Google Sheets API (Google Apps Script), LocalStorage |
| **Deskripsi Singkat** | MedikaHub adalah platform informasi kesehatan digital terintegrasi untuk masyarakat guna mencari dokter spesialis terverifikasi, membaca artikel edukasi kesehatan, mengajukan pertanyaan medis di forum diskusi terbuka, serta mendaftar webinar kesehatan secara daring. |

---

### 1.2 Cakupan Pengujian

#### Fitur dalam Cakupan (In-Scope)
Terdapat 8 (delapan) fitur utama yang diuji secara menyeluruh untuk peran yang dipilih, mencakup aspek autentikasi dan fungsionalitas inti:

| No. | Nama Fitur | Jenis Fitur | Deskripsi Singkat |
| :---: | :--- | :---: | :--- |
| 1 | **Login** | Fitur Autentikasi | Autentikasi pengguna terdaftar dengan validasi format email, pengecekan password, verifikasi role masyarakat, dan penanganan pesan error jika data tidak valid. |
| 2 | **Register** | Fitur Autentikasi | Pendaftaran akun baru pengguna dengan validasi kelengkapan nama, format nomor telepon, format email, standar kekuatan password (minimal 8 karakter, huruf kapital, angka, dan simbol), kecocokan konfirmasi password, serta pencegahan duplikasi email. |
| 3 | **Forgot Password & Reset** | Fitur Autentikasi | Pengajuan pemulihan akun melalui verifikasi email terdaftar, pembangkitan kode OTP 6-digit (simulasi), dan penggantian password baru dengan validasi keamanan. |
| 4 | **Pencarian & Filter Dokter** | Fitur Tambahan | Penelusuran daftar dokter berdasarkan spesialisasi, domisili kota, filter kepesertaan BPJS Kesehatan, serta penyortiran berdasarkan rating, ulasan, atau abjad (A–Z). |
| 5 | **Eksplorasi & Filter Info Penyakit (Artikel)** | Fitur Tambahan | Pencarian artikel kesehatan berbasis kata kunci, penyaringan artikel berdasarkan kategori spesialisasi (Kardiologi, Pediatri, dsb.), serta navigasi membaca detail isi artikel medis. |
| 6 | **Pengajuan Pertanyaan Forum Diskusi** | Fitur Tambahan | Formulir pembuatan pertanyaan kesehatan baru ke forum publik dengan memilih kategori medis, validasi isian wajib, penyimpanan data, serta pemfilteran status pertanyaan (Semua, Terjawab, Menunggu). |
| 7 | **Pendaftaran Agenda & Webinar Kesehatan** | Fitur Tambahan | Pendaftaran partisipasi webinar/seminar kesehatan daring melalui pengisian formulir, validasi kuota peserta, pencegahan email ganda, dan pengiriman konfirmasi pendaftaran. |
| 8 | **Peninjauan Modal Detail & Jadwal Dokter** | Fitur Tambahan | Penampilan popup rincian profil dokter yang mencakup nomor registrasi STR/SIP terverifikasi IDI, biografi singkat dokter, rincian jadwal praktik mingguan, serta tautan konsultasi forum. |

#### Di Luar Cakupan (Out-of-Scope)

| No. | Fitur / Aspek | Alasan Pengecualian |
| :---: | :--- | :--- |
| 1 | **Dashboard Khusus Dokter** (Menjawab forum dokter, kelola jadwal praktik, statistik performa) | Pengujian difokuskan secara konsisten hanya pada peran Masyarakat/Pasien sesuai regulasi praktikum. Fitur manajemen dokter berada pada peran yang berbeda. |
| 2 | **Verifikasi Otomatis STR/SIP ke Konsil Kedokteran Indonesia (KKI / Kemenkes)** | Belum diimplementasikan integrasi API eksternal pihak ketiga ke server Kemenkes; data nomor STR/SIP disajikan secara statis terverifikasi. |
| 3 | **Sistem Transaksi Pembayaran Online (Payment Gateway)** | Platform MedikaHub saat ini berfokus pada edukasi dan informasi kesehatan publik non-komersial tanpa modul pembiayaan berbayar. |

---

### 1.3 Peran yang Dipilih untuk Diuji

| Bidang | Detail |
| :--- | :--- |
| **Nama Peran** | **Masyarakat / Pasien** |
| **Deskripsi Peran** | Aktor pengguna umum (end-user) yang memanfaatkan platform MedikaHub untuk memperoleh informasi kesehatan kredibel, mencari referensi dokter, mengajukan pertanyaan di forum, dan mendaftar acara webinar kesehatan. |
| **Fitur yang Dapat Diakses** | Login, Register, Forgot Password, Cari & Filter Dokter, Detail Profil & Jadwal Dokter, Info Penyakit/Artikel, Forum Tanya Jawab Kesehatan (bertanya, melihat thread, filter status), dan Pendaftaran Agenda/Webinar Kesehatan. |
| **Alasan Pemilihan** | Peran Masyarakat/Pasien memiliki cakupan interaksi pengguna terbanyak dan terlengkap pada platform, mencakup alur input data yang kompleks (validasi registrasi multi-syarat, formulir pertanyaan, pendaftaran webinar), manipulasi state (LocalStorage/Session), serta penyaringan data interaktif yang sangat relevan untuk kebutuhan skenario pengujian komprehensif pada rangkaian praktikum. |

---

### 1.4 Asumsi dan Batasan

| Jenis | Deskripsi |
| :--- | :--- |
| **Asumsi** | Seluruh fitur antarmuka web MedikaHub dapat dijalankan dan dieksekusi secara lokal melalui web browser modern tanpa memerlukan instalasi web server backend terpisah. |
| **Asumsi** | Data awal dokter, artikel medis, jadwal agenda webinar, serta akun pengguna demo tersedia dan dapat diakses dengan baik di sisi klien (in-memory JavaScript & LocalStorage). |
| **Asumsi** | Lingkungan pengujian terhubung dengan jaringan internet untuk memuat font eksternal (Google Fonts) dan webhook integrasi (Google Apps Script). |
| **Batasan** | Pengujian dibatasi secara ketat hanya pada fungsionalitas peran Masyarakat/Pasien, tidak mencakup pengujian hak akses internal peran Dokter. |
| **Batasan** | Tidak dilakukan pengujian performa beban tinggi (stress testing skala server) atau pengujian penetrasi keamanan tingkat lanjut (penetration testing) karena aplikasi dibangun sebagai SPA statis client-side. |

---

## 2. Daftar Risiko

Identifikasi minimal lima risiko yang terkait dengan proyek yang dipilih.  
**Perhitungan Prioritas = Dampak (1–5) × Kemungkinan (1–5)**, dengan 1 = Sangat Rendah dan 5 = Sangat Tinggi.

| ID Risiko | Deskripsi Risiko | Jenis | Dampak (I) | Kemungkinan (L) | Prioritas (I×L) | Strategi Mitigasi |
| :---: | :--- | :---: | :---: | :---: | :---: | :--- |
| **R-01** | Pengguna menginput kombinasi email dan password yang tidak memenuhi standar keamanan sehingga memicu bug validasi atau pendaftaran akun tidak valid. | Produk | 4 | 2 | **8** | Menerapkan pengujian *boundary value analysis* dan *equivalence partitioning* pada regex validasi email dan password di sisi klien. |
| **R-02** | Pengguna mendaftar webinar yang sama lebih dari satu kali (*duplicate submission*) sehingga mendistorsi data kuota peserta. | Produk | 3 | 3 | **9** | Menyiapkan skenario uji pendaftaran berulang dengan email identik serta memastikan validasi duplikasi LocalStorage dan disable button saat submit berjalan optimal. |
| **R-03** | Kegagalan koneksi internet atau timeout pada saat integrasi pengiriman data (Google Apps Script / Webhook) untuk forum dan registrasi webinar. | Produk | 4 | 3 | **12** | Menyiapkan penanganan error asinkron (try-catch block) yang informatif pada antarmuka pengguna serta data fallback cadangan secara lokal. |
| **R-04** | Perubahan spesifikasi kebutuhan atau struktur form input aplikasi di tengah jalannya modul praktikum yang mengakibatkan dokumen rancangan uji tidak sinkron. | Proyek | 3 | 2 | **6** | Melakukan pembekuan ruang lingkup (*scope freezing*) fungsionalitas untuk pengujian praktikum serta menjaga matriks keterlacakan (*traceability matrix*). |
| **R-05** | Keterbatasan waktu pengujian praktikan dalam mengeksekusi seluruh variasi skenario uji akibat jadwal perkuliahan dan tugas lainnya yang padat. | Proyek | 4 | 3 | **12** | Menyusun checklist test cases yang terstruktur, memprioritaskan fitur bertingkat risiko tertinggi terlebih dahulu, dan memanfaatkan dokumentasi terstandar. |
| **R-06** | Ketidaksesuaian tampilan antarmuka (UI broken) dan fungsi filter interaktif saat diuji pada resolusi layar ponsel/tablet atau peramban yang berbeda. | Produk | 3 | 3 | **9** | Melakukan pengujian kompatibilitas lintas peramban (*cross-browser testing* di Chrome dan Firefox) serta uji responsivitas layout via Device Mode DevTools. |

---

## 3. Strategi Pengujian

### 3.1 Pendekatan Keseluruhan

| Bidang | Deskripsi |
| :--- | :--- |
| **Pendekatan Pengujian** | `<Belum ditetapkan; dilengkapi pada modul berikutnya>` |
| **Tingkat Pengujian** | `<Belum ditetapkan; dilengkapi pada modul berikutnya>` |
| **Jenis Pengujian Utama** | `<Belum ditetapkan; dilengkapi pada modul berikutnya>` |
| **Fitur Berprioritas Tinggi** | **Fitur Autentikasi Pengguna (Login, Register, Forgot Password)** dan **Fitur Pendaftaran Webinar & Pengajuan Forum Kesehatan** *(Fitur dengan skor risiko tertinggi dari Bagian 2)* |

### 3.2 Arah Pengujian yang Direncanakan

Pada Modul 1, arah dan teknik pengujian belum perlu ditentukan. Bagian ini dilengkapi secara bertahap setelah materi terkait dipelajari pada modul berikutnya.

| Aspek | Status | Catatan |
| :--- | :---: | :--- |
| **Arah dan Teknik Pengujian** | `<Belum ditetapkan>` | Dilengkapi setelah materi terkait dipelajari pada modul berikutnya. |

> *Catatan: Placeholder dipertahankan dan nama teknik tidak ditambahkan pada Modul 1 sesuai petunjuk template praktikum.*

### 3.3 Kriteria

| Jenis Kriteria | Deskripsi |
| :--- | :--- |
| **Kriteria Masuk** | Seluruh kode sumber aplikasi MedikaHub versi v1.0 telah stabil dan dapat dibuka di peramban tanpa sintaks error fatal; seluruh akun uji, data simulasi dokter, artikel, dan agenda telah siap; formulir input berfungsi; dan perangkat pengujian telah siap digunakan. |
| **Kriteria Keluar** | 100% test case yang direncanakan untuk peran Masyarakat telah dieksekusi; seluruh defect dengan tingkat keparahan Kritis (Critical) dan Tinggi (High) telah diperbaiki dan diverifikasi ulang; serta ringkasan dokumen hasil pengujian telah lengkap. |
| **Kriteria Lolos** | Hasil aktual yang diamati dari eksekusi aplikasi persis sama dengan hasil yang diharapkan (expected result) pada test scenario, alur data berjalan lancar, dan validasi berfungsi sebagaimana mestinya. |
| **Kriteria Gagal** | Hasil aktual tidak sesuai dengan hasil yang diharapkan, terjadi crash/freeze pada browser, muncul error unhandled pada console browser, atau sistem meloloskan input tidak valid yang seharusnya ditolak. |
| **Pengujian Ulang** | Setiap test case yang menghasilkan status *Gagal* (Failed) wajib dieksekusi ulang secara cermat setelah pengembang melakukan perbaikan bug (bug fix) untuk mengonfirmasi bahwa masalah telah tuntas. |
| **Pengujian Regresi** | Eksekusi ulang pada sekumpulan test case kritis pada alur kerja utama aplikasi setelah adanya modifikasi kode atau penutupan defect guna menjamin tidak ada dampak negatif atau bug baru yang muncul pada fitur lain yang sebelumnya berfungsi normal. |

---

## 4. Lingkungan Pengujian

### 4.1 Perangkat dan Perangkat Keras

| Item | Detail |
| :--- | :--- |
| **Jenis Perangkat** | Laptop |
| **Processor** | Intel Core i5 / AMD Ryzen 5 (atau setara) |
| **RAM** | 8 GB / 16 GB DDR4 |
| **Sistem Operasi** | Windows 11 Home 64-bit |

### 4.2 Perangkat Lunak dan Alat

| Alat / Perangkat Lunak | Versi / Detail | Tujuan |
| :--- | :---: | :--- |
| **Browser / Perangkat** | Google Chrome v125+ / Mozilla Firefox v126+ | Eksekusi pengujian aplikasi web dan inspeksi konsol/responsivitas |
| **Alat Dokumentasi** | Microsoft Word / Google Docs / VS Code Markdown | Penyusunan dokumen Test Plan dan pelaporan hasil uji praktikum |
| **Alat Tangkapan Layar** | Windows Snipping Tool / Lightshot | Pengumpulan bukti hasil eksekusi pengujian (screenshot bukti lulus/gagal) |

### 4.3 Jaringan dan Backend

| Item | Detail |
| :--- | :--- |
| **Jaringan** | Koneksi Internet Aktif (Wi-Fi Kampus / Hotspot Pribadi) |
| **Backend / API** | Google Apps Script Webhook API (sinkronisasi data formulir) & Web Storage API (LocalStorage) |
| **URL Dasar Pengujian** | `http://localhost:5500/index.html` atau berkas lokal `file:///D:/PKLP%20SMTR%207/Medikahub/index.html` |

### 4.4 Data Uji

Identifikasi jenis data uji secara umum yang dibutuhkan. Kumpulan data uji secara detail akan disiapkan pada modul berikutnya.

| Jenis Data | Deskripsi |
| :--- | :--- |
| **Akun Uji Valid** | Akun pengguna peran Masyarakat yang telah terdaftar, contoh: Email: `demo@medikahub.id`, Password: `Demo@1234`. |
| **Akun Uji Tidak Valid** | Akun dengan format email salah (`user@`, `user@domain`), kata sandi salah, kata sandi kurang dari 8 karakter (`Pass1!`), kata sandi tanpa simbol/angka, atau email yang belum terdaftar pada sistem. |
| **Contoh Data Input** | Data registrasi pengguna baru (Nama: Riska, No HP: 081234567890, Email: riska@test.com); kata kunci pencarian dokter ("dr. Riska", "Kardiologi"); data postingan pertanyaan forum; serta data formulir pendaftaran webinar kesehatan (Nama, Email, No HP). |
| **Data Uji Tambahan** | `<Belum ditetapkan; dilengkapi pada modul berikutnya>` |

---

## 5. Jadwal Pengujian

Pada Modul 1, isi hanya jadwal dan luaran yang memang ditetapkan untuk Modul 1. Detail Modul 2 sampai Modul 6 dan UAP tetap berupa placeholder sampai modul terkait dibahas dan ditetapkan.

| Modul | Aktivitas Pengujian Utama | Perkiraan Waktu | Luaran Utama |
| :---: | :--- | :---: | :--- |
| **Modul 1** | Perencanaan pengujian, analisis risiko, dan registrasi proyek | Oktober 2026 (Minggu 1 – 2) | Dokumen Test Plan dan entri registrasi proyek |
| **Modul 2** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 3** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 4** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 5** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 6** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **UAP** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |

---

## 6. Luaran Pengujian

Pada Modul 1, luaran yang perlu diselesaikan adalah dokumen Test Plan dan entri registrasi proyek. Luaran, format, dan status untuk Modul 2 sampai Modul 6 serta UAP belum ditetapkan pada dokumen ini.

| Modul | Luaran | Format | Status |
| :---: | :--- | :---: | :---: |
| **Modul 1** | Dokumen Test Plan | DOCX / PDF | Sedang Berjalan |
| **Modul 1** | Entri Lembar Registrasi Proyek | Google Sheets | Sedang Berjalan |
| **Modul 2** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 3** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 4** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 5** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **Modul 6** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |
| **UAP** | `<Belum ditetapkan>` | `<Belum ditetapkan>` | `<Belum ditetapkan>` |

---

## Lampiran A: Glosarium

Istilah kunci yang digunakan dalam dokumen ini, berdasarkan ISO/IEC/IEEE 29119-1:

| Istilah | Definisi |
| :--- | :--- |
| **Item Uji** | Objek yang diuji. Dalam praktikum ini, objek tersebut adalah aplikasi web atau mobile yang dipilih oleh masing-masing praktikan (MedikaHub). |
| **Dasar Pengujian** | Sumber diturunkannya sebuah test condition, dapat berupa kebutuhan, user story, atau perilaku yang sudah disepakati. |
| **Kondisi Pengujian** | Aspek dari aplikasi yang dapat diuji secara spesifik, dan menjadi dasar penulisan test case. |
| **Kasus Uji** | Input konkret, langkah-langkah, dan hasil yang diharapkan, yang digunakan untuk memeriksa satu test condition. |
| **Lingkungan Pengujian** | Perangkat, software, dan akses yang dibutuhkan untuk benar-benar menjalankan pengujian. |
| **Risk** | Kemungkinan terjadinya suatu masalah, baik pada produk itu sendiri (Risiko Produk) maupun pada proyek di sekitarnya, seperti tenggat waktu yang ketat (Risiko Proyek). |
| **Incident** | Segala sesuatu yang tidak terduga yang ditemukan selama pengujian dan perlu ditelusuri lebih lanjut. |
| **Traceability** | Kemampuan untuk menelusuri hubungan dari sebuah kebutuhan, ke sebuah fitur, hingga ke test case yang memeriksanya. |
| **Dampak** | Seberapa serius akibat yang akan timbul apabila sebuah risiko benar-benar terjadi, dinilai dengan skala 1 sampai 5. |
| **Kemungkinan** | Seberapa besar kemungkinan sebuah risiko benar-benar terjadi, dinilai dengan skala 1 sampai 5. |
| **Prioritas** | Tingkat kepentingan suatu risiko secara keseluruhan, dihitung sebagai Dampak dikalikan Kemungkinan. Digunakan untuk menentukan risiko mana yang perlu ditangani lebih dulu. |
| **Strategi Mitigasi** | Tindakan yang direncanakan untuk mengurangi dampak suatu risiko atau kemungkinan risiko tersebut terjadi. |
| **Kriteria Masuk** | Kondisi yang harus terpenuhi sebelum pengujian dapat dimulai. |
| **Kriteria Keluar** | Kondisi yang menandakan bahwa pengujian telah selesai. |
