<div align="center">
  <h1 style="text-align: center;">Project Charter Container Based App<br>
Mobile Apps e-Klinik PENS</h1>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>

<p align="center"><img src="images/logo.png" alt="logo"></p>

<div align="center">
  <h3>KEMLOMPOK 4:</h3>
  <p align="center">Mirta Chadhirotin Nachlah 3122500009</p>
  <p align="center">Mohammad Ilham Ramadani 3122500020</p>
  <p align="center">Masyitha Fahra Nabila 3122500023</p>
  <p align="center">Rifqi Rayita Dhiyaulhaq 3122500027</p>
  <p align="center">Muhammad Syahrul Ramadhan 3122500030</p>
</div>

<div align="center">
  <h3>PROGRAM STUDI TEKNIK INFORMATIKA <br>
      POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br>
      TAHUN 2023/2024 <br>
  </h3>
</div>


<hr>

## Abstrak

Proyek "Mobile Apps e-Klinik PENS" bertujuan untuk mengembangkan aplikasi mobile berbasis container yang akan digunakan oleh Politeknik Elektronika Negeri Surabaya (PENS) untuk mengelola layanan kesehatan kliniknya. Aplikasi ini dirancang untuk memberikan akses mudah dan cepat kepada mahasiswa, staf, dan dosen untuk memesan janji temu, mendapatkan informasi medis, dan mengakses berbagai layanan kesehatan lainnya yang disediakan oleh klinik PENS.

Penggunaan teknologi container dalam pengembangan aplikasi ini memungkinkan skalabilitas, portabilitas, dan efisiensi dalam pengelolaan infrastruktur TI. Dengan pendekatan ini, setiap komponen aplikasi, seperti server backend, database, dan antarmuka pengguna, dapat dikelola secara terpisah dan lebih mudah di-deploy di berbagai lingkungan.

Proyek ini mencakup beberapa tahap utama, yaitu analisis kebutuhan, desain sistem, pengembangan, pengujian, dan implementasi. Selain itu, proyek ini juga melibatkan pelatihan pengguna akhir dan dukungan teknis berkelanjutan untuk memastikan aplikasi dapat digunakan secara optimal.

Tujuan utama dari proyek ini adalah untuk meningkatkan efisiensi operasional klinik, memberikan pengalaman pengguna yang lebih baik, dan memfasilitasi akses layanan kesehatan yang lebih cepat dan mudah bagi seluruh sivitas akademika PENS. Dengan adanya aplikasi e-Klinik ini, diharapkan dapat meningkatkan kualitas layanan kesehatan di lingkungan PENS secara signifikan.

<hr>

## Daftar Isi

- [Daftar Isi](#daftar-isi)
- [Pendahuluan](#pendahuluan)
- [Ruang Lingkup](#ruang-lingkup)
- [Desain Sistem](#desain-sistem)
- [Tim dan Tugas](#tim-dan-tugas)
- [Tahapan Pelaksanaan](#tahapan-pelaksanaan)
- [Sistem testing](#sistem-testing)
- [Kesimpulan](#kesimpulan)

<hr>

## Pendahuluan

Docker adalah platform open-source yang dirancang untuk mengotomatisasi penyebaran aplikasi sebagai paket yang dapat dieksekusi, yang dikenal sebagai kontainer, dalam lingkungan yang terisolasi dan konsisten. Kontainer ini berisi semua yang dibutuhkan aplikasi untuk berjalan, termasuk kode, runtime, pustaka, dan pengaturan sistem, sehingga aplikasi dapat dijalankan dengan andal di berbagai lingkungan, dari pengembangan hingga produksi. Dengan Docker, pengembang dapat membuat, menguji, dan menyebarkan aplikasi dengan cepat dan efisien, mengurangi masalah kompatibilitas dan meningkatkan skalabilitas serta portabilitas aplikasi. Docker juga mendukung orkestrasi kontainer, memungkinkan pengelolaan dan penskalaan aplikasi di berbagai host dengan mudah.

Pada aplikasi E-Klinik PENS, kami menggunakan Storage Server untuk menyimpan dan mengambil data, seperti file atau dokumen besar. Backend framework Laravel mengelola request pengguna serta berinteraksi dengan Storage Server dan MySQL Database untuk data yang relasional. MongoDB Database digunakan untuk menyimpan data aplikasi yang lebih fleksibel dan tidak relasional. Docker Engine dipakai untuk mengembangkan, mengirimkan, dan menjalankan aplikasi dalam kontainer, serta menghubungkan antarmuka pengguna pada perangkat mobile dengan backend Laravel, Storage Server, dan berbagai layanan database.

## Ruang Lingkup

E-Klinik PENS adalah aplikasi rekam medis di klinik PENS berbasis mobile yang dikembangkan dengan Flutter, memungkinkan pengguna untuk mengakses rekam medis secara online. Aplikasi ini terdiri dari tiga peran (role), yaitu: User, Admin, dan Dokter.

- Role User: Pengguna dapat melihat riwayat rekam medisnya, termasuk tanggal periksa, dokter, gejala, diagnosa, kritik & saran. Selain itu, mereka bisa melihat jadwal dokter.
- Role Admin: Admin dapat mengelola data aplikasi rekam medis.
- Role Dokter: Dokter dapat mengisi rekam medis pasien.

Backend aplikasi menggunakan framework Laravel untuk mengatur autentikasi pengguna dan berinteraksi dengan database untuk penyimpanan dan pengambilan data. MySQL digunakan sebagai database untuk menyimpan dan mengambil data rekam medis serta memberikan respons terhadap permintaan pengguna.

Server berfungsi sebagai perantara antara aplikasi mobile, backend, dan database. Server menerima request dari pengguna, kemudian meneruskannya ke backend dan database yang nantinya akan mengirimkan kembali respons kepada pengguna

## Design Sistem
<p align="center"><img src="images/diagram sistem1.png" alt="desain_sistem"></p>

Deskripsi desain sistem dari aplikasi E-Klinik PENS sesuai dengan diagram yang disediakan adalah sebagai berikut:

### *1A: Data Source*
- *MySQL Database*: Bagian ini berfungsi sebagai sumber data utama untuk aplikasi. MySQL digunakan untuk menyimpan berbagai jenis data yang terkait dengan rekam medis, informasi pengguna, jadwal dokter, dan lain-lain. Data yang disimpan di sini mencakup tabel-tabel yang berhubungan dengan:
  - *Profil Pengguna*: Data pribadi pengguna termasuk nama, alamat, kontak, dll.
  - *Rekam Medis*: Data medis pengguna seperti diagnosa, gejala, resep, riwayat periksa, dll.
  - *Fitur Tambahan*: Informasi lain yang mungkin diperlukan oleh aplikasi.

### *1B: Data Processing*
- *Endpoint*: Ini adalah lapisan logika bisnis yang mengelola pemrosesan data dan menyediakan antarmuka (API) bagi aplikasi mobile untuk berinteraksi dengan data di MySQL.
  - *Authentication*: Proses autentikasi untuk memastikan bahwa hanya pengguna yang berwenang yang dapat mengakses sistem. Ini mencakup fitur login, registrasi, pengelolaan sesi, dan manajemen hak akses.
  - *Clinic History*: Pengelolaan riwayat klinik yang mencakup data rekam medis, jadwal dokter, dan interaksi medis lainnya. Endpoint ini memungkinkan aplikasi mobile untuk mengambil dan memperbarui data rekam medis pengguna.

### *1C: Mobile Apps*
- *Profile*: Bagian antarmuka pengguna di aplikasi mobile yang menampilkan dan memungkinkan pengeditan informasi profil pengguna.
- *Medical Records*: Bagian yang menampilkan data rekam medis pengguna. Pengguna dapat melihat riwayat periksa, diagnosa, gejala, resep, dll.
- *Feature*: Bagian lain dari aplikasi mobile yang mungkin mencakup fitur tambahan seperti pengingat jadwal periksa, notifikasi, dan fitur-fitur lain yang meningkatkan kegunaan aplikasi.

### *Interaksi Antar Bagian*
1. *Data Source (MySQL) ke Data Processing (Endpoint)*:
   - MySQL menyimpan semua data yang diperlukan oleh aplikasi. Endpoint di data processing melakukan query ke database untuk mengambil atau memperbarui data sesuai dengan permintaan dari aplikasi mobile.

2. *Data Processing (Endpoint) ke Mobile Apps*:
   - Endpoint menyediakan berbagai API yang digunakan oleh aplikasi mobile untuk melakukan autentikasi pengguna dan mengakses data rekam medis. Ketika pengguna mengakses aplikasi mobile, aplikasi akan mengirim permintaan ke endpoint untuk autentikasi dan mengambil data yang relevan.

3. *Mobile Apps*:
   - Aplikasi mobile menggunakan data yang diterima dari endpoint untuk menampilkan informasi kepada pengguna. Aplikasi mobile memungkinkan pengguna untuk melihat dan mengedit profil, melihat rekam medis, dan menggunakan fitur tambahan lainnya.

## Tim dan Tugas

### *UI/UX Designer*
1. Mirta Chadhirotin Nachlah (3122500009)
2. Masyita Fahra Nabila (3122500023)

*Tugas:*
- Melakukan riset pengguna untuk memahami kebutuhan dan masalah pengguna (User, Admin, Dokter).
- Membuat wireframe untuk merancang struktur dasar layar dan navigasi aplikasi.
- Merancang elemen visual seperti tombol, ikon, dan tata letak sesuai dengan pedoman desain yang konsisten.
- Memastikan estetika desain yang menarik dan sesuai dengan identitas visual klinik PENS.
- Mengembangkan prototipe interaktif untuk menunjukkan alur pengguna dan fungsionalitas aplikasi.
- Merancang alur pengguna yang intuitif dan efisien untuk setiap peran (User, Admin, Dokter).
- Mengumpulkan umpan balik dari pengguna dan melakukan iterasi desain untuk meningkatkan pengalaman pengguna.
- Bekerja sama dengan tim pengembang untuk memastikan desain dapat diimplementasikan secara teknis.

### *FrontEnd Mobile*
1. Mohammad Ilham Ramadani (312250021)
2. Rifqi Rayita Dhiyaulhaq (3122500027)
3. Muhammad Syahrul Ramadhani (3122500030)
4. Mirta Chadhirotin Nachlah (3122500009)
5. Masyita Fahra Nabila (3122500023)

*Tugas:*
- Mengimplementasikan desain UI/UX ke dalam kode Flutter.
- Mengembangkan fitur-fitur antarmuka pengguna untuk aplikasi mobile.
- Bekerja sama dengan backend untuk mengintegrasikan API.
- Membantu melakukan pengujian aplikasi pada perangkat mobile.

### *BackEnd API & Mobile*
1. Mohammad Ilham Ramadani (312250021)
2. Rifqi Rayita Dhiyaulhaq (3122500027)

*Tugas:*
- Mengembangkan backend aplikasi menggunakan Laravel.
- Membuat API untuk berinteraksi dengan aplikasi mobile.
- Mengatur autentikasi pengguna dan manajemen sesi.
- Bekerja sama dengan tim database untuk memastikan data tersimpan dengan benar.

### *Consume API*
1. Mohammad Ilham Ramadani (312250021)
2. Rifqi Rayita Dhiyaulhaq (3122500027)

*Tugas:*
- Mengintegrasikan API dari backend ke aplikasi mobile.
- Mengelola permintaan dan respons data dari server.
- Menyelesaikan masalah terkait konsumsi API dan optimasi performa aplikasi.

### *Database*
1. Mohammad Ilham Ramadani (312250021)

*Tugas:*
- Mendesain dan mengimplementasikan struktur database menggunakan MySQL.
- Mengelola skema database dan tabel yang dibutuhkan untuk aplikasi.
- Melakukan optimasi query dan pengelolaan indeks untuk memastikan performa database yang baik.
- Memastikan integritas data dan keamanan akses ke database.
    
## Tahapan Pelaksanaan

<p align="center"><img src="images/timeline.jpg" alt="timeline_kerja"></p>

1. Pengerjaan UI/UX dan Database<br> 
    Pelaksanaan UI/UX yang diikuti dengan penyusunan database dilakukan dalam kurun waktu 1 minggu (25 April -  2 Mei 2024)<br>
    - Melakukan riset pengguna untuk memahami kebutuhan dan masalah pengguna (User, Admin, Dokter)
    - Membuat wireframe untuk merancang struktur dasar layar dan navigasi aplikasi.
    - Merancang elemen visual seperti tombol, ikon, dan tata letak sesuai dengan pedoman desain yang konsisten.
    - Memastikan estetika desain yang menarik dan sesuai dengan identitas visual klinik PENS.
    - Mendesain dan mengimplementasikan struktur database menggunakan MySQL yang berisi informasi terkait:
        - user
        - rekam medis
    - Mengelola skema database dan tabel yang dibutuhkan untuk aplikasi.

2. Proses slicing <br>
    Proses slicing selesai dalam kurun waktu 3 minggu
    (3 Mei 2024 - 23 Mei 2024)<br>
    - Mengimplementasikan desain UI/UX ke dalam kode Flutter.
    - Mengembangkan fitur-fitur antarmuka pengguna untuk aplikasi mobile.
    - Bekerja sama dengan backend untuk mengintegrasikan API.
    - Membantu melakukan pengujian aplikasi pada perangkat mobile.
    - Dalam proses slicing beberapa page(halaman) yang reuse-able diantaranya:
        - Profile
        - FAQ
        - Edit Profile
        - Riwayat Rekam Medis
        - Jadwal Dokter

3. Hosting<br>
    Hosting aplikasi E-Klink PENS untuk menyimpan dan menampilkan situs web aplikasi tersebut dengan pengerjaan dalam kurun waktu 1 hari (24 Mei 2024)

4. BackEnd API
    Proses penyusunan backend API dalam kurun waktu dua hari (25 Mei - 26 Mei 2024)<br>
    - Mengembangkan backend aplikasi menggunakan Laravel.
    - Membuat API untuk berinteraksi dengan aplikasi mobile.
    - Mengatur autentikasi pengguna dan manajemen sesi.
    - Bekerja sama dengan tim database untuk memastikan data tersimpan dengan benar.

5. Consume API<br>
    Consume API memerlukan estimasi waktu dalam kurun waktu tiga hari (26 Mei - 29 Mei 2024)<br>
    - Mengintegrasikan API dari backend ke aplikasi mobile.
    - Mengelola permintaan dan respons data dari server.
    - Menyelesaikan masalah terkait konsumsi API dan optimasi performa aplikasi.
    - Dalam tahapan consume API setelah menyusun databse meliputi:
        - Method get, post, patch. dan delete

## Sistem Testing

Dalam pengembangan aplikasi E-Klinik PENS, dua jenis pengujian penting yang perlu dilakukan adalah pengujian fungsional (functional testing) dan pengujian instalasi (installation testing). Berikut adalah rincian dari kedua jenis pengujian tersebut:

### VERSI DOCKER
<hr>

Dalam konteks menggunakan Docker untuk pengembangan dan pengujian aplikasi E-Klinik PENS, berikut adalah rincian fungsional testing dan installation testing:

### Fungsional Testing

*Tujuan*: Memastikan bahwa semua fitur dan fungsi aplikasi bekerja sesuai dengan spesifikasi dan kebutuhan pengguna.

1. *Unit Testing*:
   - Menggunakan container Docker untuk menjalankan unit test pada komponen-komponen aplikasi secara terisolasi.
   - Misalnya, menjalankan PHPUnit untuk backend Laravel dalam sebuah container yang memiliki semua dependensi yang dibutuhkan.

2. *Integration Testing*:
   - Menggunakan Docker Compose untuk mendefinisikan dan menjalankan layanan (MySQL, Laravel backend, dan API endpoint) dalam beberapa container yang terhubung.
   - Menguji integrasi antara aplikasi mobile (dalam container) dan backend (dalam container) melalui API.

3. *System Testing*:
   - Menjalankan seluruh aplikasi (frontend mobile, backend Laravel, dan database MySQL) dalam lingkungan container Docker untuk mensimulasikan lingkungan produksi.
   - Menguji semua fitur utama secara end-to-end di dalam lingkungan yang mirip dengan produksi.

4. *User Acceptance Testing (UAT)*:
   - Menyediakan environment Docker yang bisa digunakan oleh pengguna akhir untuk melakukan pengujian.
   - Menggunakan Docker untuk mengatur lingkungan pengujian yang konsisten dan mudah disebarluaskan kepada pengguna akhir untuk mendapatkan umpan balik.

*Contoh Proses Pengujian Fungsional*:
- Menjalankan docker-compose up untuk mengatur lingkungan pengujian yang mencakup semua layanan.
- Menjalankan skrip pengujian otomatis dalam container yang memverifikasi berbagai fitur aplikasi seperti login, pengelolaan rekam medis, dan penjadwalan dokter.

- Authentication
<p align="center"><img src="images/auth (1).png" alt="authentication"></p> <br>
<p align="center"><img src="images/auth (2).png" alt="authentication"></p>

- Clinic History
<p align="center"><img src="images/clinic_history (1).png" alt="clinic history"></p> <br
>
<p align="center"><img src="images/clinic_history (2).png" alt="clinic history"></p>

### Installation Testing

*Tujuan*: Memastikan bahwa aplikasi dapat diinstal dan dijalankan dengan benar di berbagai perangkat dan lingkungan.

1. *Container Build Verification*:
   - Memastikan bahwa Dockerfile untuk setiap komponen aplikasi (frontend mobile, backend, dan database) dapat membangun image yang berfungsi dengan baik.
   - Menguji proses build Docker image untuk setiap layanan dan memastikan bahwa image tersebut dapat berjalan tanpa error.

2. *Container Deployment Verification*:
   - Menggunakan Docker Compose untuk mengatur dan menjalankan seluruh stack aplikasi dalam beberapa container.
   - Memastikan bahwa setiap container dapat berkomunikasi dengan yang lain sesuai dengan definisi di docker-compose.yml.

3. *Configuration Testing*:
   - Menguji aplikasi dalam berbagai konfigurasi container untuk memastikan kompatibilitas dan kinerja.
   - Memastikan bahwa variabel lingkungan dan pengaturan konfigurasi lainnya diterapkan dengan benar dalam container.

4. *Update and Rollback Testing*:
   - Menguji proses update aplikasi dengan memperbarui Docker image dan memastikan bahwa aplikasi tetap berfungsi dengan baik.
   - Memastikan bahwa proses rollback ke versi sebelumnya dapat dilakukan tanpa kehilangan data atau mengganggu fungsionalitas aplikasi.

*Contoh Proses Pengujian Instalasi*:
- Menjalankan docker build untuk membuat Docker image dari Dockerfile yang ada.
- Menjalankan docker-compose up untuk memulai layanan dalam container.
- Memverifikasi bahwa setiap container (MySQL, backend Laravel, frontend mobile) berjalan dengan benar dan saling berkomunikasi.
- Menguji update Docker image dan melakukan rollback jika diperlukan.


- Docker Build
<p align="center"><img src="images/docker_build.png" alt="installation testing"></p>

- Docker Up
<p align="center"><img src="images/docker_up.png" alt="installation testing"></p>

- Docker Status
<p align="center"><img src="images/docker_status.png" alt="installation testing"></p>

- Docker Restart
<p align="center"><img src="images/docker_restart.png" alt="installation testing"></p>

- Result
<p align="center"><img src="images/result.png" alt="installation testing"></p>

- Dengan menggunakan Docker untuk fungsional dan installation testing, tim pengembang dapat memastikan bahwa aplikasi E-Klinik PENS tidak hanya berfungsi dengan baik, tetapi juga mudah diinstal, dikonfigurasi, dan diperbarui dalam lingkungan yang terkontainerisasi.

## Kesimpulan

E-Klinik PENS adalah aplikasi rekam medis berbasis mobile yang dikembangkan dengan Flutter, yang memfasilitasi akses online bagi pengguna untuk melihat rekam medis mereka. Aplikasi ini memiliki tiga peran utama: User, Admin, dan Dokter. Pengguna dapat melihat riwayat rekam medis dan jadwal dokter, Admin bertanggung jawab untuk mengelola data aplikasi, dan Dokter dapat mengisi rekam medis pasien. Backend aplikasi dikembangkan menggunakan framework Laravel untuk autentikasi dan interaksi dengan database, sementara MySQL digunakan sebagai database utama untuk penyimpanan data rekam medis. Server bertindak sebagai perantara yang memastikan komunikasi yang efisien antara aplikasi mobile, backend, dan database, sehingga menghasilkan pengalaman pengguna yang seamless dan efektif.

Desain sistem E-Klinik PENS terdiri dari tiga komponen utama: Data Source (MySQL), Data Processing (Endpoint), dan Mobile Apps. MySQL bertindak sebagai penyimpanan data, endpoint sebagai logika bisnis dan antarmuka API, serta aplikasi mobile sebagai antarmuka pengguna. Interaksi antar komponen ini memungkinkan pengguna untuk mengakses dan mengelola informasi medis secara online melalui perangkat mobile.
