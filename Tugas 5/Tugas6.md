**LAPORAN WORKSHOP ADMINISTRASI JARINGAN**

![image15](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/33ad546a-b17e-4869-93e6-d2c3632722d9)

**Disusun Oleh:**

**Muhammad Iqbal Rahmatullah D3 IT A /3122500014**

**Mohammad Ilham Ramadani D3 IT A /3122500021**

**Rifqi Rayita Dhiyaulhaq D3 IT A /3122500027**

**Dosen Pembimbing :**

**Dr. Ferry Astika Saputra ST, M.Sc**

**Setup Konfigurasi**

![](./media/image4.png)

Hubungkan kabel ethernet pada device anda

![](./media/image18.png)

Custom wired dengan menambahkan Address, Netmask, Gateway, dan DNS
secara manual dan sudah ditentukan.

![](./media/image19.png)

Masuk dalam directory /etc/bind, dan masuk file **named.conf.options**
custom bagian forwaders menjadi dns, localhost, dan alamat ip yang sudah
kita custom sebelumnya. Ubah juga bagian allow-query, dan
allow-recursion yang awalnya internals menjadi any.

![](./media/image20.png)

Masuk dalam file **/etc/resolv.conf** dan custom NetworkManager,
diantaranya tambahkan search by namakelompok.local, nameserver alamat ip
kelompok, dan juga forwaders.

**Uji Coba**

- **Ping detik.com**

![](./media/image5.png)

> Kemudian coba ping ke detik.com apakah ada respon balik dari web
> tersebut, jika ada respon maka konfigurasi sudah benar, dan jika belum
> maka matikan firewall terlebih dahulu, agar nantinya bisa dicoba untuk
> ping.

- **Ping kelompok lain**

![](./media/image9.png)

> Test juga ping ke kelompok lain, dan jika ada respon dari ttl maka
> konfigurasi sudah benar dan terhubung.

- **Nslookup kelompok lain**

![](./media/image17.png)

> Cek nslookup dari kelompok lain, apakah bisa terhubung atau tidak,
> jika terhubung maka ada answer atau reply dari kelompok1.local dan
> jika tidak maka ada tulisan communicate timed out;;

- **Uji Client-Server**

![](./media/image16.png)

> Untuk memastikan dan mengujinya sebagai client, Coba hubungkan laptop
> / komputer lain yang terhubung langsung dengan koneksi ethernet. Ping
> ke alamat ip yang sudah di custom sebelumnya. Jika terhubung maka ada
> reply dari laptop/komputer yang dijadikan server

**Test RoundCube**

![](./media/image8.png)

Lihat bagian inbox, terdapat beberapa user yang sudah berhasil untuk
terhubung dan komunikasi dengan kelompok kamu, yaitu
@mail.kelompok6.local

![](./media/image6.png)

Gambar di atas adalah contoh pesan dari komunikasi di roundcube.

![](./media/image21.png)

Coba untuk mencoba kirim pesan antar user yang sudah terhubung

![](./media/image13.png)

Pesan sukses terkirim

![](./media/image12.png)

Gambar di atas adalah contoh pesan dari komunikasi di roundcube antara
user dan iqbal.

**Setup DNS Server via Winbox (Mikrotik)**

![](./media/image11.png)

- Hapus DHCP networks yang sudah terconfig sebelumnya dengan menekan
  tanda (-) yang tertera pada window DHCP Server.

![](./media/image7.png)

- Atur interface DHCP ke bridge 1

![](./media/image10.png)

- Atur network DHCP ke 192.168.6.0 dengan netmask 24.

![](./media/image3.png)

- Atur untuk DHCP ke 192.168.6.1

![](./media/image1.png)

- Relay isi 0.0.0.0

![](./media/image14.png)

- Untuk range DHCP address atur pada seluruh address di network
  192.168.6.0 kecuali address untuk gateway dan broadcast.

![](./media/image2.png)

- Tambahkan DNS Server untuk 10.10.10.1 (DNS Server Mikrotik kita) yang
  awalnya hanya ada satu,192.168.6.10
