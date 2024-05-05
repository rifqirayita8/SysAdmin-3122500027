# Telnet (Send mail from telnet)
![](https://lh7-us.googleusercontent.com/8x9hnk4WFzLFSi2qnVcUjNv33PnP35wT4cuIOhBvMEBR0GNwCEDvMMpz7FuR4TI7xoG-JKQAgLpT9VB5ktLhpEJ5TZpg5j33kO4cnPyU_gRK-YW5_5WfTZckwdU3gXUgHeKwvDiKKY_a_j_CSpVH6JA)
- Menghubungkan ke IP address 192.168.6.10 25 dengan 4 oktet pertama adalah IP dari server kelompok 6. Sementara 25 adalah port yang digunakan untuk service SMTP (Simple Mail Transfer Protocol) yang berfungsi untuk mengirim email. Command ini berfungsi untuk menghubungkan ke service email yang running di IP address tersebut.
- ehlo kelompok6.local merupakan command yang dikirim ke server untuk memulai sesi SMTP ketika menginisialisasi koneksi email.
- 250 merupakan respons server kelompok6.
- MAIL FROM adalah alamat email pengirim. Disini sendernya adalah [iqbal@mail.kelompok6.local](mailto:iqbal@mail.kelompok6.local) dengan respons 250 yang berarti alamat diterima.  
- RCPT TO adalah alamat email penerima. Disini receivernya adalah [arsyita@kelompok5.local](mailto:arsyita@kelompok5.local) dengan respons 250 yang berarti alamat diterima.
- DATA merupakan isi dari email tersebut yang terdiri dari sender, receiver, date, subject, dan isinya.
- 2.0.0 berarti email berhasil dikirim/diterima
- queued as xxxxxxxxx adalah unique ID yang dibuat server untuk pesan yang telah diterima olehnya.
#

# Pop3 With Telnet
![](https://lh7-us.googleusercontent.com/KU4nq6BLYlpjcg1lUZ1qWJ0nAyR5iqSZYEEu9N0zzfKUICpbnemcxRv_pYMd6PQ0yOLhmi9n5O8d8aMxvgwlwbxtYh3GDpykjxXpfBhF3zFoqalq7Ag93BzU6B1QGsMtvPnL27301NrmA0GEu0fVnbo)

- Menghubungkan ke IP address 192.168.6.10 dengan 110 adalah port yang digunakan oleh service POP3(Post Office Protocol Version 3). POP3 merupakan protokol yang digunakan untuk mengambil email dari server email ke komputer client.
- Dovecot adalah software yang digunakan untuk service emailnya.
- user iqbal login sebagai iqbal@mail.kelompok6.local dan memasukkan pw nya.
- LIST menampilkan daftar email dalam inbox dan menampilkan informasi ukuran masing2 pesan.

![](https://lh7-us.googleusercontent.com/VIuutuuLIjvjp9yXwScKnQNa7Jvm00cuMPxahKOPTId9pQAOoJz_7GUv7DZmZITX5ZN3KhwXGylLivuvP7_PcuxW_eJJVLOkqWvCGjWQ5W9r6pKFcDXTAwe3hRazLL-RmwJt0qdq3Niiv6zYG0ScfaA)

- RETR 44 digunakan untuk membaca pesan 44.
- Return-Path adalah email address sender, disini adalah user@kelompok2.local
- X-Original-To adalah email address recipient yang pertama atau asli, disini adalah iqbal@kelompok6.local
- Delivered-To adalah email address recipient yang akhir.
- From adalah nama pengirim.
- To adalah nama penerima.
- Date adalah tanggal dan waktu email dikirim.
- Subject adalah isi email.
- Body adalah isinya.
#

# Analisis Header MIME
![](https://lh7-us.googleusercontent.com/-aNcOrsF27tw0Ol4ZU2uC6Z6uFByqqwBAQf5HWy1tW6OtSlmLz47os5zm33xaWaw3STMqcFGA-QLsYdg0VLTd2yMhMKNHif51rA6IeXtWxGGLTqWpL1DiVCyye8jvIZzp8nutXWnFIVYrhbbRdWzT1o)
MIME (Multipurpose Internet Mail Extensions) adalah protokol tambahan yang memungkinkan kita mengirim data yang bukan ASCII (misalnya gambar, video, atau teks dengan karakter khusus) melalui email. Dasar-dasar email hanya bisa mengirim pesan dalam format teks ASCII 7-bit, tapi MIME mengubah data yang bukan ASCII menjadi format yang bisa dikirim melalui email. Jadi, ketika Anda mengirim email dengan lampiran gambar atau dokumen PDF, MIME akan merubahnya menjadi format yang bisa dikirimkan melalui email, dan di sisi penerima, data itu akan dikembalikan ke bentuk aslinya. Dengan MIME, kita bisa mengirim email dengan berbagai jenis konten, tidak hanya teks biasa.

-   Analisis header MIME dari gambar di atas :
	1.  Mime-version : mendefinisikan version dari MIME, yaitu pada gambar di atas menggunakan MIME version 1.0
	2.  Content-Type : mendefinisikan jenis data yang digunakan dalam isi pesan. Jenis dan subjenisnya dipisahkan oleh tanda slash. MIME memungkinkan tujuh jenis data yang berbeda, yaitu teks, multipart, pesan, gambar, video, audio, dan aplikasi (misalnya post-script dan stream). Artinya Content-Type menandai jenis data yang terkandung dalam email, misalnya apakah itu teks biasa, gambar, atau bahkan file audio atau video. Ini membantu program email dalam memahami dan menampilkan isi email dengan benar kepada penerima. Pada gambar diatas Content-Type nya adalah text/plain, yang berarti adalah text biasa.
	3.  Content-Transfer-Encoding : bagian dari header email yang mendefinisikan metode yang digunakan untuk mengubah pesan menjadi urutan angka 0 dan 1 (bit) untuk transportasi. Pada gambar di atas menggunakan metode 7bit, berarti menggunakan 7 bit ASCII untuk mentransfer data, dimana metode ini cocok untuk teks biasa.
	4.  Content Description : memberikan deskripsi singkat tentang isi dari pesan email, seperti apakah itu berupa gambar, audio, atau video.

-   Analisis header email :
Selain dari header MIME yang sudah disebutkan di atas, maka termasuk di dalam header email standar. Yaitu meliputi :
	1.  Date : Menunjukkan waktu ketika email terkirim.
	2.  From : Alamat email pengirim, menunjukkan siapa yang mengirim email tersebut.    
	3.  To : Alamat email penerima, menunjukkan kepada siapa email tersebut ditujukan. 
	4.  Subject : Subjek atau judul dari email, yang memberikan gambaran isi pesan. 
	5.  Message-ID : ID unik yang digunakan untuk mengidentifikasi email secara unik. Berguna dalam referensi balasan.
	6.  X-sender : Informasi tambahan tentang pengirim email, seperti alamat email atau nama pengirim tambahan.
#
