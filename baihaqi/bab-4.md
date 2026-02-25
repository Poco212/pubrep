Dalam implementasi Network Bound Disk Encryption (NBDE), media penyimpanan yang digunakan harus terlebih dahulu menerapkan enkripsi Linux Unified Key Setup (LUKS). Mekanisme enkripsi ini dirancang khusus untuk sistem operasi berbasis Linux, sehingga penerapannya terbatas pada lingkungan yang menggunakan distribusi Linux sebagai platform operasionalnya. 
 
Pada penelitian ini, implementasi Linux Unified Key Setup (LUKS) dilakukan menggunakan sistem operasi Arch Linux. Pemilihan Arch Linux didasarkan pada tingkat fleksibilitas dan kemudahannya dalam melakukan konfigurasi serta modifikasi sistem sesuai dengan kebutuhan server. Karakteristik tersebut memungkinkan penyesuaian komponen dan layanan yang dijalankan sehingga mendukung proses implementasi enkripsi secara optimal dan terkontrol.

Selain menggunakan Linux Unified Key Setup (LUKS), implementasi Network Bound Disk Encryption (NBDE) juga memerlukan beberapa aplikasi pendukung, antara lain Tang sebagai server otentikasi, Clevis sebagai klien untuk proses binding dan dekripsi otomatis, serta Firewalld sebagai pengelola aturan keamanan jaringan. Berikut ini merupakan penjelasan mengenai penggunaan aplikasi pendukung tersebut dalam mendukung implementasi NBDE secara menyeluruh.

 # Tang server
Tang adalah layanan yang digunakan untuk menghubungkan kunci kriptografi dengan kondisi atau keberadaan jaringan tertentu sehingga pemanfaatannya bergantung pada lingkungan jaringan yang telah ditentukan (ArchLinux,2026). Mekanisme ini memungkinkan proses pembukaan kunci (dekripsi) dilakukan secara otomatis apabila sistem berada pada lingkungan jaringan yang telah ditentukan dan dipercaya.Pendekatan ini meningkatkan aspek keamanan karena akses terhadap data tidak hanya bergantung pada kunci enkripsi, tetapi juga pada validasi kondisi jaringan yang digunakan.

![install tang](/baihaqi/images/mkinitcpio/install-tangserver.png)

Aplikasi Tang pada dasarnya telah tersedia dalam repositori resmi pada beberapa sistem operasi berbasis Linux. Ketersediaan ini memudahkan administrator sistem dalam memperoleh paket instalasi yang terverifikasi dan terintegrasi dengan sistem manajemen paket distribusi yang digunakan.

Meskipun demikian, aplikasi tersebut tidak selalu terpasang secara bawaan pada saat instalasi awal sistem operasi. Oleh karena itu, diperlukan proses instalasi secara manual sebelum aplikasi dapat digunakan untuk mendukung implementasi Network Bound Disk Encryption (NBDE).

Proses instalasi dilakukan melalui mekanisme manajemen paket yang disediakan oleh masing-masing distribusi Linux. Setiap distribusi memiliki pengelola paket yang berbeda, sehingga perintah instalasi yang digunakan juga menyesuaikan dengan sistem yang diterapkan.

Pada sistem operasi Arch Linux, instalasi Tang dapat dilakukan menggunakan perintah manajemen paket sudo pacman -S tang. Perintah tersebut dijalankan melalui terminal dengan hak akses administratif untuk memastikan proses instalasi berjalan dengan baik.

Perintah tersebut berfungsi untuk mengunduh serta memasang paket Tang beserta seluruh dependensi yang dibutuhkan dari repositori resmi Arch Linux. Dengan demikian, sistem akan secara otomatis menyesuaikan kebutuhan pustaka dan komponen pendukung lainnya sehingga aplikasi dapat berjalan secara optimal sesuai dengan konfigurasi sistem yang digunakan.
 
![add port tang](/baihaqi/images/mkinitcpio/add-port-pada-tang.png)

Setelah proses instalasi layanan Tang server selesai dilakukan, langkah selanjutnya adalah melakukan konfigurasi agar layanan tersebut dapat berjalan melalui port yang telah diberikan izin pada server. Konfigurasi ini dilakukan untuk memastikan bahwa layanan Tang dapat diakses oleh klien yang membutuhkan, khususnya dalam implementasi Network Bound Disk Encryption (NBDE). Tanpa konfigurasi port yang tepat, layanan tidak akan dapat berkomunikasi secara optimal melalui jaringan.

Port itu sendiri merupakan jalur komunikasi logis yang digunakan oleh sistem operasi untuk mengidentifikasi dan mengelola lalu lintas data antar layanan dalam suatu jaringan komputer. Setiap layanan atau aplikasi jaringan berjalan pada nomor port tertentu sehingga sistem dapat membedakan satu layanan dengan layanan lainnya dalam satu alamat internet yang sama. 

Dalam konfigurasi server, pembukaan dan pemberian izin terhadap port tertentu dilakukan melalui pengaturan firewall atau sistem keamanan jaringan yang digunakan. Proses ini bertujuan untuk menjaga keamanan server dengan membatasi akses hanya pada layanan yang diperlukan. Oleh karena itu, selain memastikan port telah dibuka, peneliti juga perlu mempertimbangkan aspek keamanan agar layanan Tang dapat berjalan dengan aman dan terkontrol.

Pada penelitian ini port yang diberi akses merupakan 7500/tcp. Karena  secara teknis, layanan Tang secara default berjalan pada port 7500/TCP. Oleh karena itu, pembukaan port tersebut pada firewall server menjadi langkah yang diperlukan agar klien, seperti sistem operasi yang menggunakan Clevis, dapat terhubung dan melakukan proses Network Bound Disk Encryption (NBDE) tidak dapat berjalan.

![start tang](/baihaqi/images/mkinitcpio/restart%26enable-tangserver.png)

![add port tang firewalld](/baihaqi/images/mkinitcpio/add-porttang-pada-firewalld.png)

![reload firewalld]() 

# clevis

![install clevis client](/baihaqi/images/mkinitcpio/instal-clevis-client.png)

![test tang server](/baihaqi/images/mkinitcpio/test-tang-server.png)

# kernel parameter
![install hook clevis](/baihaqi/images/mkinitcpio/install-hook-clevis.png)
![install hook net](/baihaqi/images/mkinitcpio/install-net-hook.png)
![hook net clevis](/baihaqi/images/mkinitcpio/add-net%26clevis-hook.png)
![setup ip parameter](/baihaqi/images/mkinitcpio/setup-ip-parameter.png)

## binding
![cek ip address](/baihaqi/images/mkinitcpio/cek-ipaddress.png)
![cek list binding server](/baihaqi/images/mkinitcpio/cek-tangpadaserver.png)
![gagal binding](/baihaqi/images/mkinitcpio/gagal-binding.png)
![sukses binding](/baihaqi/images/mkinitcpio/berhasil-binding.png) 
![generate mkinitcpio](/baihaqi/images/mkinitcpio/generate-mkinitcpio.png) 
 
 
  
 

