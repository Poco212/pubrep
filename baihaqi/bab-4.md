 Dalam implementasi Network Bound Disk Encryption (NBDE), media penyimpanan yang digunakan harus terlebih dahulu menerapkan enkripsi Linux Unified Key Setup (LUKS). Mekanisme enkripsi ini dirancang khusus untuk sistem operasi berbasis Linux, sehingga penerapannya terbatas pada lingkungan yang menggunakan distribusi Linux sebagai platform operasionalnya. 
 
 Pada penelitian ini, implementasi Linux Unified Key Setup (LUKS) dilakukan menggunakan sistem operasi Arch Linux. Pemilihan Arch Linux didasarkan pada tingkat fleksibilitas dan kemudahannya dalam melakukan konfigurasi serta modifikasi sistem sesuai dengan kebutuhan server. Karakteristik tersebut memungkinkan penyesuaian komponen dan layanan yang dijalankan sehingga mendukung proses implementasi enkripsi secara optimal dan terkontrol.

Selain menggunakan Linux Unified Key Setup (LUKS), implementasi Network Bound Disk Encryption (NBDE) juga memerlukan beberapa aplikasi pendukung, antara lain Tang sebagai server otentikasi, Clevis sebagai klien untuk proses binding dan dekripsi otomatis, serta Firewalld sebagai pengelola aturan keamanan jaringan. Berikut ini merupakan penjelasan mengenai penggunaan aplikasi pendukung tersebut dalam mendukung implementasi NBDE secara menyeluruh.
 # Tang server

 
 
 ![hook net clevis](/baihaqi/images/mkinitcpio/add-net%26clevis-hook.png)
 ![add port tang](/baihaqi/images/mkinitcpio/add-port-pada-tang.png)
 ![add port tang firewalld](/baihaqi/images/mkinitcpio/add-porttang-pada-firewalld.png)
 ![sukses binding](/baihaqi/images/mkinitcpio/berhasil-binding.png)
 ![cek ip address](/baihaqi/images/mkinitcpio/cek-ipaddress.png)
 ![cek list binding server](/baihaqi/images/mkinitcpio/cek-tangpadaserver.png)
 ![gagal binding](/baihaqi/images/mkinitcpio/gagal-binding.png)
 ![generate mkinitcpio](/baihaqi/images/mkinitcpio/generate-mkinitcpio.png)
 ![install clevis client](/baihaqi/images/mkinitcpio/instal-clevis-client.png)
 ![install hook clevis](/baihaqi/images/mkinitcpio/install-hook-clevis.png)
 ![install hook net](/baihaqi/images/mkinitcpio/install-net-hook.png)
 ![install tang](/baihaqi/images/mkinitcpio/install-tangserver.png)
 ![start tang](/baihaqi/images/mkinitcpio/restart%26enable-tangserver.png)
 ![setup ip parameter](/baihaqi/images/mkinitcpio/setup-ip-parameter.png)
 ![test tang server](/baihaqi/images/mkinitcpio/test-tang-server.png)

