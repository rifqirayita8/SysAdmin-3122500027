<div align="center">
**LAPORAN WORKSHOP ADMINISTRASI JARINGAN**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/33ad546a-b17e-4869-93e6-d2c3632722d9)

**Disusun Oleh:**

**Muhammad Iqbal Rahmatullah D3 IT A /3122500014**

**Mohammad Ilham Ramadani D3 IT A /3122500021**

**Rifqi Rayita Dhiyaulhaq D3 IT A /3122500027**

**Dosen Pembimbing :**

**Dr. Ferry Astika Saputra ST, M.Sc**
</div>
<br><hr><br>

**Setup Konfigurasi**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/f68e8f02-a009-410b-9a3a-29ae3e64a6ec)

Hubungkan kabel ethernet pada device anda

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/edeb6194-8333-4324-be4e-d1113cd54d09)

Custom wired dengan menambahkan Address, Netmask, Gateway, dan DNS
secara manual dan sudah ditentukan.

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/0bef99a1-767b-464c-9ecf-0127cd0847f6)

Masuk dalam directory /etc/bind, dan masuk file **named.conf.options**
custom bagian forwaders menjadi dns, localhost, dan alamat ip yang sudah
kita custom sebelumnya. Ubah juga bagian allow-query, dan
allow-recursion yang awalnya internals menjadi any.

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/5924a4cf-9732-4e64-991f-5cdcc8fb919a)

Masuk dalam file **/etc/resolv.conf** dan custom NetworkManager,
diantaranya tambahkan search by namakelompok.local, nameserver alamat ip
kelompok, dan juga forwaders.

**Uji Coba**

- **Ping detik.com**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/fd7344d2-3e35-4c4c-95db-d73b1c1f5f91)

> Kemudian coba ping ke detik.com apakah ada respon balik dari web
> tersebut, jika ada respon maka konfigurasi sudah benar, dan jika belum
> maka matikan firewall terlebih dahulu, agar nantinya bisa dicoba untuk
> ping.

- **Ping kelompok lain**

![image9](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/0fe93844-d01a-44a7-af6c-fa2bfe64bac5)

> Test juga ping ke kelompok lain, dan jika ada respon dari ttl maka
> konfigurasi sudah benar dan terhubung.

- **Nslookup kelompok lain**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/c582ff1f-bb27-4291-a29e-f7c17f0b4df1)

> Cek nslookup dari kelompok lain, apakah bisa terhubung atau tidak,
> jika terhubung maka ada answer atau reply dari kelompok1.local dan
> jika tidak maka ada tulisan communicate timed out;;

- **Uji Client-Server**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/759e5878-0775-4a95-a640-65de66a47d16)

> Untuk memastikan dan mengujinya sebagai client, Coba hubungkan laptop
> / komputer lain yang terhubung langsung dengan koneksi ethernet. Ping
> ke alamat ip yang sudah di custom sebelumnya. Jika terhubung maka ada
> reply dari laptop/komputer yang dijadikan server

**Test RoundCube**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/52d54c01-8c80-493c-93c8-cdc9b1002f1a)

Lihat bagian inbox, terdapat beberapa user yang sudah berhasil untuk
terhubung dan komunikasi dengan kelompok kamu, yaitu
@mail.kelompok6.local

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/c91eb1d0-85c5-47c5-bb16-0afac4d3e365)

Gambar di atas adalah contoh pesan dari komunikasi di roundcube.

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/33a7901a-42fc-4fa7-93a1-55376cb22f73)

Coba untuk mencoba kirim pesan antar user yang sudah terhubung

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/bc3ef5bc-b54f-4f74-9052-3fc3079cc829)

Pesan sukses terkirim

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/4b606e67-9bd2-4789-8c41-7b0ef95c95db)

Gambar di atas adalah contoh pesan dari komunikasi di roundcube antara
user dan iqbal.

**Setup DNS Server via Winbox (Mikrotik)**

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/78bc90ab-ca3d-4a33-8284-10f8fa6e5f43)


- Hapus DHCP networks yang sudah terconfig sebelumnya dengan menekan
  tanda (-) yang tertera pada window DHCP Server.

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/c8eeed3e-4e08-47cb-93fa-ad65341d848e)

- Atur interface DHCP ke bridge 1

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/9a592e0e-9835-4747-8866-820b6cfe8e91)

- Atur network DHCP ke 192.168.6.0 dengan netmask 24.

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/a06eee57-7343-413a-9bda-e4289f66645a)

- Atur untuk DHCP ke 192.168.6.1

![](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/140db1f8-3eda-4cc4-a75d-c97495ad8df7)

- Relay isi 0.0.0.0

![image14](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/6a7645a1-7164-4000-8f08-0fd4ba68fe87)

- Untuk range DHCP address atur pada seluruh address di network
  192.168.6.0 kecuali address untuk gateway dan broadcast.

![image2](https://github.com/rifqirayita8/SysAdmin-3122500027/assets/114125588/ddec85bf-eb20-45f0-b554-8361cbc2ce09)

- Tambahkan DNS Server untuk 10.10.10.1 (DNS Server Mikrotik kita) yang
  awalnya hanya ada satu,192.168.6.10
