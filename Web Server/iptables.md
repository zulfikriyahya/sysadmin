# Iptables: Pengertian, Fungsi dan Cara Menggunakannya

Oktober 19, 2021 5 min read

![[FI] Cara Menggunakan iptables](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/29203519/FI-Cara-Menggunakan-iptables.jpg)

Anda khawatir server Anda akan mendapat serangan kejahatan online? Jika iya, cobalah menggunakan iptables firewall untuk meningkatkan keamanan server tersebut.

Namun, Anda belum tahu bagaimana cara menggunakan iptables?

Tenang, Anda berada di halaman yang tepat! Artikel ini akan menjelaskan apa itu iptables dan fungsi iptables untuk server Anda, termasuk cara menggunakan iptables.

Yuk, simak pembahasan lengkapnya bawah ini!

**Daftar isi** [tutup](https://www.niagahoster.co.id/blog/tutorial-iptables/#)

[Apa Itu Iptables?](https://www.niagahoster.co.id/blog/tutorial-iptables/#Apa_Itu_Iptables)

[Cara Menggunakan iptables dalam 3 Langkah](https://www.niagahoster.co.id/blog/tutorial-iptables/#Cara_Menggunakan_iptables_dalam_3_Langkah)

[1\. Melakukan Instalasi iptables](https://www.niagahoster.co.id/blog/tutorial-iptables/#1_Melakukan_Instalasi_iptables)

[2\. Membuat Rules iptables](https://www.niagahoster.co.id/blog/tutorial-iptables/#2_Membuat_Rules_iptables)

[Mengaktifkan Trafik pada Localhost](https://www.niagahoster.co.id/blog/tutorial-iptables/#Mengaktifkan_Trafik_pada_Localhost)

[Mengaktifkan Koneksi pada Port HTTP, HTTPS dan SSH](https://www.niagahoster.co.id/blog/tutorial-iptables/#Mengaktifkan_Koneksi_pada_Port_HTTP_HTTPS_dan_SSH)

[Memfilter Koneksi berdasarkan Sumber Paket](https://www.niagahoster.co.id/blog/tutorial-iptables/#Memfilter_Koneksi_berdasarkan_Sumber_Paket)

[Memutus Koneksi Trafik Lainnya](https://www.niagahoster.co.id/blog/tutorial-iptables/#Memutus_Koneksi_Trafik_Lainnya)

[Menghapus Rules](https://www.niagahoster.co.id/blog/tutorial-iptables/#Menghapus_Rules)

[3\. Menyimpan Konfigurasi iptables secara Permanen](https://www.niagahoster.co.id/blog/tutorial-iptables/#3_Menyimpan_Konfigurasi_iptables_secara_Permanen)

[Kesimpulan](https://www.niagahoster.co.id/blog/tutorial-iptables/#Kesimpulan)

## Apa Itu Iptables?

Iptables adalah salah satu tools [firewall](https://www.niagahoster.co.id/blog/firewall-adalah/) pada sistem operasi Linux. Fungsi iptables adalah mengamankan jaringan dengan melakukan penyaringan trafik pada server [VPS tanpa panel](https://www.niagahoster.co.id/blog/panduan-vps-tanpa-panel/).

Dengan iptables, Anda dapat mengatur lalu lintas jaringan, termasuk mengizinkan atau memblokir koneksi yang masuk, keluar, atau sekedar melewati server.

Pada iptables, Anda bisa membuat aturan pada server untuk mengelola jenis paket yang dapat diterima, mengatur trafik berdasarkan asal dan tujuan data, mengelola port, dan lainnya.

iptables bekerja dengan membandingkan lalu lintas jaringan dengan serangkaian aturan yang telah dibuat. Jadi, semua paket dalam lalu lintas jaringan akan dicek.

Dalam pengaturan paket, iptables memiliki beberapa tabel yang berfungsi untuk menentukan arah putaran data. Setiap tabel tersebut memiliki rules atau kumpulan aturan yang disebut **chain**.

**Pertama**, tabel **FILTER**. Tabel ini digunakan untuk menyaring paket yang masuk, keluar, ataupun yang hanya lewat. Caranya. dengan menggunakan beberapa aturan, yaitu:

- **ACCEPT** : Menerima paket yang masuk
- **REJECT** : Menolak/Memblokir paket yang masuk
- **DROP** : Memutuskan koneksi paket
- **LOG** : Mencatat paket

Tabel FILTER memiliki tiga chain, yaitu:

- **INPUT** : Chain ini menangani semua paket yang masuk ke server.
- **OUTPUT** : Chain ini menangani semua paket yang keluar dari server.
- **FORWARD** : Chain ini menangani paket yang diteruskan melalui server.

**Kedua**, tabel **NAT (Network Address Translation)**. Tabel ini digunakan untuk mengubah alamat asal tujuan dari sebuah paket. Ada dua chain pada tabel NAT:

- **PRE-ROUTING (dstnat)** : Mengubah destination address pada sebuah paket data.
- **POST-ROUTING (srcnat)** : Mengubah source address dari sebuah paket data.

**Ketiga**, tabel **MANGLE**. Tabel ini digunakan untuk melakukan penghalusan pada proses pengaturan paket, dan memiliki kemampuan untuk menggunakan semua chain yang ada pada IPTABLES di atas.

Setelah mengetahui apa itu iptables dan fungsinya, saatnya untuk mengamankan firewall dengan iptables.

**Baca Juga :** [Konfigurasi Dasar VPS](https://www.niagahoster.co.id/blog/konfigurasi-dasar-vps/)

## Cara Menggunakan iptables dalam 3 Langkah

Sebelum mengikuti tutorial cara menggunakan iptables, pastikan Anda memiliki akses root ke server Anda. Jika sudah siap, Anda dapat langsung mengikuti tiga langkah berikut ini, yaitu:

1.  **Melakukan Instalasi iptables**
2.  **Membuat Rules iptables**
3.  **Menyimpan Konfigurasi iptables secara Permanen**

Nah, berikut ini merupakan penjelasan lengkapnya:

### 1\. Melakukan Instalasi iptables

Untuk mengecek versi iptables yang terinstall pada Linux, Anda perlu melakukan koneksi ke server dengan [cara menggunakan SSH](https://www.niagahoster.co.id/blog/cara-menggunakan-ssh/) terlebih dulu.

Caranya, login dengan username dan password yang dapat Anda temukan pada [detail SSH](https://www.niagahoster.co.id/kb/detail-ssh-pada-panel-vps-niagahoster) di panel VPS. Kemudian, jalankan perintah berikut:

sudo iptables -V

Jika perintah tersebut menampilkan output versi iptables seperti gambar di bawah ini, maka iptables memang sudah terinstall pada Linux.

![mengecek versi iptables](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110145/iptables-1.png)

![mengecek versi iptables](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110145/iptables-1.png)

Maka, Anda dapat langsung melanjutkan panduan ini ke langkah selanjutnya.

Namun,  jika outputnya berupa **command not found**, artinya iptables belum terinstall. Jadi, jalankan perintah berikut ini untuk menginstal iptables:

sudo apt-get update
sudo apt-get install iptables

Tunggu beberapa saat hingga proses instalasi iptables selesai dilakukan. Jika sudah berhasil, cek status konfigurasi dengan menjalankan perintah:

sudo iptables -L -v

Command `**-L**` pada perintah diatas digunakan untuk melihat list semua aturan yang ada. Sedangkan command **`-v`** digunakan untuk menunjukkan informasi list aturan tersebut secara detail. Contoh outputnya seperti ini:

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Iptables yang baru saja diinstall belum memiliki aturan apapun. Sehingga semua **paket yang masuk akan diterima tanpa filter**. Tentu saja hal ini masih sangat tidak aman, kan?

Tapi tenang saja, kami akan menjelaskan bagaimana cara membuat _rules_ pada iptables di langkah berikutnya.

**Baca juga:** [Cara Ganti Password VPS](https://www.niagahoster.co.id/blog/cara-ganti-password-vps/)

### 2\. Membuat Rules iptables

Rules iptables merupakan aturan untuk mengelola lalu lintas jaringan pada server. Rules ini akan ditambahkan pada suatu chain tertentu.

Iptables menggunakan perintah `-A` (**Append**) sebagai tanda bahwa ada rules yang ditambahkan:

sudo iptables -A

Namun, perintah di atas belum bisa dijalankan karena perintah **Append** tidak bisa berdiri sendiri. Perintah `-A` membutuhkan argumen pendukung untuk membuat suatu rules.

Berikut ini merupakan argumen yang bisa Anda gunakan untuk membuat rules:

- **\-i : Interface** merupakan antarmuka jaringan yang akan Anda filter, seperti **eth0**, **lo**, dll.
- **\-p : Protocol** adalah protokol jaringan yang akan di cek dalam suatu rule. Misalnya **tcp**, **udp**, **icmp**, dll.
- **\-s : Source** adalah alamat trafik berasal (IP address atau hostname)
- **\-dport : Destination Port** merupakan nomor port suatu protokol, seperti **22** untuk SSH dan **80** untuk HTTP. Perihal port SSH bisa Anda simak di artikel [cara ganti Port SSH di VPS](https://www.niagahoster.co.id/blog/cara-ganti-port-ssh-di-vps/).
- **\-j : Jump** merupakan nama target (**ACCEPT, DROP, RETURN** ) yang dituju ketika membuat rule yang baru.

Argumen di atas tidak harus digunakan satu persatu. Sesuaikan saja dengan kebutuhan Anda. Namun, kalau perlu digunakan semua, urutannya harus seperti ini:

sudo iptables -A <chain> -i <interface> -p <protocol (tcp/udp) > -s <source> --dport <port no.> -j <target>

Nah, sekarang mari coba membuat rules iptables dengan syntax di atas.

Sebagai contoh, di tutorial kali ini kami akan menambahkan rules pada chain **INPUT** untuk memfilter koneksi yang masuk dan mencegah koneksi yang dapat membahayakan server

Rules iptables yang akan kami gunakan sebagai contoh adalah:

1.  Mengaktifkan Trafik pada Localhost
2.  Mengaktifkan Koneksi pada Port HTTP, HTTPS dan SSH
3.  Memfilter Koneksi Berdasarkan Sumber Paket
4.  Memutus Koneksi Trafik Lainnya
5.  Menghapus Rules

**Baca juga:** [Cara Cek IP VPS](https://www.niagahoster.co.id/blog/cara-cek-ip-vps/)

#### **Mengaktifkan Trafik pada Localhost**

Untuk mengizinkan trafik pada localhost, jalankan perintah berikut ini:

sudo iptables -A INPUT -i lo -j ACCEPT

Perintah di atas memastikan koneksi antara database dan aplikasi web pada localhost bisa berjalan dengan baik.

**Baca juga:** [Cara Cek RAM VPS](https://www.niagahoster.co.id/blog/cara-cek-ram-vps/)

#### **Mengaktifkan Koneksi pada Port HTTP, HTTPS dan SSH**

Untuk memberikan izin akses ke port HTTP (**80**), HTTPS (**443**)  dan SSH (**22**), jalankan perintah di bawah ini:

sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

Jika sudah, Anda dapat mengecek rules yang baru saja Anda buat dengan perintah:

sudo iptables -L -v

Perintah tersebut akan menghasilkan output seperti gambar berikut:

![mengecek rules iptables yang baru dibuat](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110544/iptables-2.png)

![mengecek rules iptables yang baru dibuat](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110544/iptables-2.png)

Gambar di atas menunjukkan bahwa iptables akan menerima semua koneksi TCP dari port HTTP, HTTPS dan SSH.

**Baca juga:** [Cara Install WordPress di VPS](https://www.niagahoster.co.id/blog/cara-install-wordpress-di-vps/)

#### **Memfilter Koneksi berdasarkan Sumber Paket**

Untuk menyaring koneksi yang masuk berdasarkan IP address atau range IP address tertentu, tambahkan IP sumber paket berasal setelah perintah `-s` seperti ini:

sudo iptables -A INPUT -s 192.168.1.2 -j ACCEPT

Sebaliknya, untuk memutus koneksi IP tertentu, Anda bisa menjalankan perintah **DROP** berikut ini:

sudo iptables -A INPUT -s 192.168.1.2 -j DROP

Anda juga bisa memutus koneksi dari suatu range IP address dengan menambahkan perintah `-m` dan modul iprange. Kemudian, masukkan range IP address setelah perintah `--src-range`.

Jangan lupa gunakan tanda pisah tanpa spasi (-) untuk memisahkan range IP Address. Untuk lebih lengkapnya, silakan lihat perintah berikut:

sudo iptables -A INPUT -m iprange --src-range 192.168.1.130-192.168.1.180 -j DROP

Perintah di atas akan memutus koneksi dari range IP address **192.168.130** hingga **192.168.1.180**.

**Baca juga:** [Cara Upload File ke VPS](https://www.niagahoster.co.id/blog/cara-upload-file-ke-vps/)

#### **Memutus Koneksi Trafik Lainnya**

Setelah mengizinkan koneksi masuk dari port tertentu, bagaimana cara memutus semua paket dari trafik diluar rules yang telah Anda buat? Sebab, penting untuk mencegah koneksi asing mengakses server Anda melalui port yang terbuka, kan?

Caranya, jalankan perintah berikut ini:

sudo iptables -A INPUT -j DROP

Nah, sekarang semua trafik dari luar port yang ditentukan pada rules telah terputus.

#### **Menghapus Rules**

Ada kalanya Anda ingin menghapus semua rules untuk kembali membuat rules dari awal lagi. Untuk melakukannya, jalankan perintah **Flush** berikut ini:

sudo iptables -F

Anda juga bisa menghapus suatu rule secara spesifik dengan menggunakan perintah **Delete** atau `-D`.  Namun, Anda perlu tahu dulu nomor line dari rule yang akan Anda hapus. Jadi, jalankan perintah di bawah ini:

sudo iptables -L --line-numbers

Setelah dijalankan, Anda akan mendapat output yang mirip seperti ini:

![mengecek nomor line rule iptables](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110824/iptables-3.png)

![mengecek nomor line rule iptables](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18110824/iptables-3.png)

Pilih rule yang akan dihapus, kemudian ingatlah **chain** serta **nomornya**. Masukkan chain beserta nomor rule pada perintah delete sebagai berikut:

sudo iptables -D \[chain\] \[nomor rule\]

Sebagai contoh, Anda ingin menghapus rule nomor 2 pada chain INPUT. Maka, perintahnya adalah:

sudo iptables -D INPUT 2

**Baca juga:** [Cara Backup VPS](https://www.niagahoster.co.id/blog/cara-backup-vps/)

### 3\. Menyimpan Konfigurasi iptables secara Permanen

Rules iptables yang telah dibuat di atas akan hilang ketika server direstart. Jadi, pastikan  Anda menyimpan konfigurasi iptables secara permanen dengan perintah di bawah ini:

sudo /sbin/iptables-save

Jangan lupa jalankan perintah tersebut ketika ada perubahan pada rules iptables.

Misalnya, ketika Anda ingin menghapus semua rules iptables, maka Anda perlu menjalankan dua perintah berikut ini:

sudo iptables -F
sudo /sbin/iptables-save

Output yang akan dihasilkan adalah:

![menyimpan konfigurasi iptables secara permanen](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18111010/iptables-4.png)

![menyimpan konfigurasi iptables secara permanen](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2021/10/18111010/iptables-4.png)

**Baca Juga :** [Panduan Melakukan Reset Firewall dari SSH](https://www.niagahoster.co.id/blog/reset-firewall-vps/)

## Kesimpulan

Iptables bisa membantu Anda mengamankan server VPS. Cara menggunakan iptables juga cukup mudah. Asalkan Anda paham dengan basic syntaxnya, Anda sudah bisa membuat aturan atau rules iptables untuk keamanan server.

Namun, peningkatan keamanan menggunakan iptables saja tentu tidak cukup. Anda perlu menggunakan server VPS yang mumpuni dan memberikan perlindungan keamanan yang baik.

Layanan **[Cloud VPS Niagahoster](https://www.niagahoster.co.id/cloud-vps-hosting)** dapat menjadi salah satu pilihannya. Dengan tambahan fitur keamanan seperti DDoS Detection, Mod Security dan konfigurasi Firewall di VPS, Anda tidak perlu khawatir lagi dengan ancaman dari luar sistem.

Cloud VPS Niagahoster juga memungkinkan Anda untuk memilih **beragam sistem operasi** Linux untuk menginstall iptables di server Anda. Selain itu, dengan **Full Root Access** yang diberikan, Anda mempunyai kontrol penuh terhadap server dan konfigurasinya.
