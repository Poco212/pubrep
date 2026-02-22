# IMPLEMENTASI MODEL NETWORK BOUND DISK ENCRYPTION UNTUK PENINGKATAN KEAMANAN ARSIP DIGITAL DI PT X

## BAB 1
Latar belakang

Menurut Undang – Undang No.43 Tahun 2009 pasal 1 ayat (2), definisi arsip merupakan rekaman kegiatan atau peristiwa arsip dalam berbagai bentuk dan media sesuai dengan perkembangan teknologi informasi dan komunikasi yang dibuat dan diterima oleh lembaga negara, pemerintahan daerah, lembaga pendidikan, perusahaan, organisasi politik, organisasi kemasyarakatan, dan perorangan dalam pelaksanaan kehidupan bermasyarakat, berbangsa, dan bernegara.
Menurut Peraturan Kepala Arsip Nasional Republik Indonesia No.7 Tahun 2016 tentang petunjuk pelaksanaan sistem klasifikasi keamanan dan akses arsip dinamis, klasifikasi keamanan arsip adalah kategori kerahasiaan informasi arsip berdasarkan pada tingkat keseriusan dampak yang ditimbulkannya terhadap kepentingan dan keamanan negara, masyarakat dan perorangan. Untuk mengklasifikasikan akses arsip, arsip dapat dikategorikan berdasarkan bagaimana arsip dapat digunakan untuk tujuan tertentu. Program pengamanan arsip melindungi data dan arsip secara fisik berdasarkan kategori keamanannya (Khariroh, 2021).
Dalam konteks perusahaan, arsip berfungsi sebagai aset informasi yang memiliki nilai hukum, administratif, dan strategis. Oleh karena itu, pengelolaan arsip yang baik menjadi bagian integral dari tata kelola organisasi yang efektif. Seiring berkembangnya teknologi informasi, bentuk arsip juga mengalami transformasi dari fisik menuju digital.
Transformasi arsip menuju format digital didorong oleh kebutuhan efisiensi, kemudahan akses, dan penghematan sumber daya. Namun, perubahan format ini juga menimbulkan tantangan baru terutama dalam aspek keamanan data dan keaslian arsip. Arsip digital rentan terhadap kerusakan perangkat, kehilangan data, dan serangan siber yang dapat mengancam integritas informasi. Dengan demikian, pengelolaan arsip digital menuntut penerapan strategi keamanan informasi yang terencana.
Keamanan arsip digital merupakan isu strategis dalam tata kelola arsip di era digitalisasi industri. Perusahaan harus memastikan bahwa arsip digital terlindungi dari risiko kebocoran, manipulasi, maupun kehilangan akibat akses yang tidak sah. Untuk itu, diperlukan penerapan kebijakan keamanan yang mencakup aspek kerahasiaan, integritas, dan ketersediaan data. Penerapan keamanan arsip digital bukan hanya tanggung jawab teknis, tetapi juga menjadi bagian dari manajemen risiko informasi secara menyeluruh. Oleh karena itu, sistem penyimpanan arsip digital perlu dirancang dengan pendekatan keamanan berlapis.
Dalam konteks penyimpanan digital, keamanan arsip digital bergantung pada mekanisme proteksi data di tingkat perangkat keras dan perangkat lunak. Salah satu pendekatan umum adalah dengan menerapkan sistem enkripsi pada media penyimpanan agar data tidak dapat diakses tanpa izin atau wewenang.
Ancaman terhadap arsip digital dapat muncul dari berbagai bentuk seperti ransomware, phishing, hingga serangan brute force pada sistem penyimpanan. Serangan-serangan ini sering memanfaatkan celah keamanan pada perangkat lunak atau kesalahan konfigurasi pengguna. Dalam konteks perusahaan, dampak serangan tersebut dapat menyebabkan kerugian finansial, reputasi, bahkan gangguan operasional (Raj, 2023).Karena itu, penerapan sistem keamanan berbasis enkripsi menjadi salah satu cara yang paling efektif untuk mengurangi risiko kebocoran data.
Implementasi teknologi enkripsi telah menjadi praktik standar dalam keamanan penyimpanan digital modern. Namun, satu sisi metode enkripsi masih terdapat kelemahan dalam kecepatan proses data yang cukup besar (Judijanto et al., 2025).  Oleh karena itu, pemilihan metode enkripsi yang tepat menjadi hal fundamental bagi keamanan arsip digital.
Salah satu implementasi enkripsi yang populer dalam sistem operasi berbasis Linux adalah LUKS (Linux Unified Key Setup). LUKS dikembangkan sebagai standar untuk mengelola enkripsi disk pada sistem Linux untuk manajemen kunci enkripsi. LUKS menyimpan informasi header yang memungkinkan pengguna mengelola beberapa kunci enkripsi pada satu volume penyimpanan (Onishchenko et al., 2024). Tantangan utama dalam sistem enkripsi adalah pengelolaan kunci yang aman dan efisien. Ketika sistem menggunakan satu kunci utama untuk seluruh media penyimpanan, maka seluruh data dapat diakses pihak luar. Dalam beberapa skenario, LUKS bergantung pada input manual pengguna untuk membuka partisi terenkripsi saat proses booting. Hal ini menimbulkan keterbatasan bagi sistem yang membutuhkan proses otomatis, seperti server atau sistem penyimpanan terpusat.
Salah satu pendekatan yang berkembang untuk mengatasi masalah pengelolaan kunci enkripsi adalah Network Bound Disk Encryption (NBDE). NBDE memungkinkan perangkat terenkripsi melakukan proses dekripsi hanya jika terkoneksi dengan jaringan dan server otentikasi yang sah (Red Hat, 2022). Dengan demikian, walaupun media penyimpanan dipindahkan ke sistem lain, data di dalamnya tetap tidak dapat diakses tanpa koneksi ke server kunci. Konsep ini memperluas keamanan LUKS dengan menambahkan lapisan verifikasi berbasis jaringan. Hal ini relevan bagi organisasi yang mengelola arsip digital pada lingkungan multi-server atau sistem terdistribusi.
Penerapan NBDE biasanya melibatkan dua komponen utama, yaitu Tang Server sebagai penyedia kunci dan Clevis Client sebagai agen dekripsi otomatis. Clevis melakukan proses binding terhadap volume terenkripsi dan secara otomatis meminta kunci dari Tang saat sistem boot . Desain ini memastikan bahwa sistem dapat berjalan tanpa intervensi manual namun tetap mempertahankan keamanan. Dengan mekanisme ini, NBDE memberikan keseimbangan antara keamanan dan efisiensi operasional.
Dalam konteks PT X, arsip digital menjadi aset informasi penting yang harus dijaga kerahasiaannya. Perusahaan yang bergerak di bidang media dan penerbitan ini menyimpan berbagai data strategis, termasuk naskah, kontrak, dan arsip digital hasil produksi. Dengan meningkatnya ketergantungan terhadap sistem penyimpanan digital, risiko kebocoran dan kehilangan data juga meningkat. Oleh karena itu, diperlukan pendekatan teknologi yang mampu mengamankan data dari akses tidak sah, baik dari internal maupun eksternal. NBDE menawarkan potensi untuk mengamankan arsip tersebut melalui kontrol berbasis jaringan.
Pengembangan model dan implementasi NBDE untuk perusahaan seperti PT X harus mempertimbangkan struktur jaringan internal dan pola akses data pengguna.Desain sistem harus mampu menjamin keamanan tanpa menurunkan kinerja akses arsip digital. Selain itu, integrasi dengan sistem autentikasi perusahaan harus dilakukan secara tertutup agar tidak mengganggu operasional.
Namun, penerapan NBDE juga memiliki tantangan tertentu, khususnya dalam hal desain server otentikasi dan pemulihan sistem. Apabila Tang Server mengalami kegagalan, maka seluruh sistem terenkripsi tidak dapat diakses hingga server dipulihkan. Oleh karena itu, diperlukan rancangan yang mempertimbangkan redundansi server dan kebijakan failover. Strategi ini akan menjamin ketersediaan sistem meskipun terjadi gangguan. 
PT X sebagai subjek penelitian memiliki kebutuhan khusus yang menjadikan NBDE relevan untuk diterapkan. Infrastruktur digital perusahaan melibatkan sistem penyimpanan terpusat untuk arsip media, yang diakses oleh banyak unit kerja melalui jaringan internal. Hal ini menimbulkan tantangan dalam menjaga kontrol akses dan otorisasi pengguna. Dengan NBDE, sistem penyimpanan dapat dibatasi hanya untuk perangkat yang berada dalam jaringan resmi perusahaan. Oleh karena itu, model yang diusulkan diharapkan dapat meningkatkan keamanan arsip digital perusahaan secara signifikan.
Berdasarkan latar belakang yang telah dijelaskan diatas, maka penulis ingin melakukan penelitian lebih lanjut terkait keamanan arsip digital pada lapisan fisik media penyimpanan yang ada di PT X. Adapun judul dalam penelitian ini adalah Implementasi Model Network Bound Disk Encryption Untuk Peningkatan Keamanan Arsip Digital di PT X.

Identifikasi masalah

Berdasarkan uraian pada latar belakang yang sudah dijelaskan bahwa, belum adanya model perancangan Network Bound Disk Encryption (NBDE) yang terstruktur dan sesuai dengan kebutuhan infrastruktur PT X. Kondisi ini menimbulkan potensi kesalahan dalam implementasi keamanan arsip digital, seperti ketidakefisienan manajemen kunci, ketergantungan terhadap server tunggal, serta belum optimalnya integrasi antara sistem enkripsi LUKS dengan otorisasi jaringan perusahaan.

Batasan masalah

untuk memperjelas ruang lingkup penelitian agar lebih terarah dan tidak melebar sehingga fokus pada tujuan utama yang ingin dicapai. Dengan adanya batasan masalah, penelitian dapat dilakukan secara lebih sistematis, mendalam, dan sesuai dengan kebutuhan perusahaan.

Batasan masalah dalam penelitian ini adalah sebagai berikut:
Penelitian difokuskan pada keamanan arsip digital yang disimpan dalam sistem penyimpanan internal perusahaan.
Model enkripsi yang diteliti terbatas pada penerapan Network Bound Disk Encryption (NBDE) dengan kombinasi metode enkripsi LUKS.
Ruang lingkup penelitian hanya mencakup perancangan model NBDE, tanpa membahas aspek implementasi infrastruktur jaringan secara detail di seluruh unit perusahaan.
Pengunaan sistem operasi Archlinux

Rumusan Masalah

Adapun rumusan masalah berdasarkan batasan masalah dan latar belakang yang telah dijelaskan di atas, maka peneliti merumuskan masalah penelitian ini yaitu “Bagaimana rancangan model enkripsi media penyimpanan dengan menggunakan Network Bound Disk Encryption Untuk Peningkatan Keamanan Arsip Digital di PT X.”

Tujuan dan Manfaat Penelitian

Adapun tujuan dan manfaat penelitian yang ingin dicapai oleh peneliti berdasarkan permasalahan yang telah dijelaskan atas adalah sebagai berikut:

Tujuan Penelitian
Tujuan penelitian ini adalah untuk mengetahui model enkripsi perangkat penyimpanan dengan menggunakan Network Bound Disk Encryption untuk meningkatkan keamanan arsip digital.

Manfaat Penelitian

Manfaat teoritis                                      
Penelitian ini diharapkan dapat memberi wawasan pengetahuan mengenai model pengamanan pada perangkat keras yang digunakan untuk menyimpan data digital dan dapat dijadikan sumber rujukan untuk penelitian selanjutnya.

Manfaat Praktis
Dapat menambah pengalaman langsung serta wawasan tentang merancang model enkripsi perangkat penyimpanan dengan menggunakan Networks Bound Disk Encryption.
Dapat memberikan masukan bagi PT Lektor Media Utama dalam meningkatkan keamanan pada perangkat keras untuk menyimpan arsip digital.

