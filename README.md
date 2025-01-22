# Naufal Aulio Sopian
# 20210801018
# UAS_JarkomLanjut


# SOAL
Buatlah topologi dan konfigurasi ruang lab praktikum Universitas Esa Unggul untuk masing - masing kampus (CR,KHI,KJ), bagaimana agar mereka bisa terhubung dan terkoneksi dengan memanfaatkan routing statik, routing dynamic(RIP,BGP,OSPF).Kumpulkan semua ke github masing - masing. 

# Penjelasan

# pengertian routing statik
Routing statis adalah metode pengaturan rute dalam jaringan di mana rute yang digunakan untuk pengiriman data ditentukan secara manual oleh administrator jaringan. Dengan kata lain, setiap rute yang digunakan dalam jaringan ditulis langsung ke dalam tabel routing perangkat jaringan (seperti router), dan tidak berubah kecuali administrator melakukan perubahan manual.

# pengertian routing dynamic
Routing dinamis adalah metode pengaturan rute di mana rute ditentukan oleh protokol routing yang dapat berkomunikasi antar perangkat jaringan untuk menentukan jalur terbaik secara otomatis berdasarkan kondisi jaringan yang selalu berubah. Protokol routing dinamis secara otomatis akan menyesuaikan jalur-jalur rute ketika ada perubahan dalam topologi jaringan (seperti perangkat baru yang ditambahkan atau jalur yang terputus).

# pengertian OSPF
OSPF adalah protokol routing dinamis yang bersifat link-state (berbasis status tautan). OSPF mengumpulkan informasi tentang status tautan (link state) di dalam jaringan dan membangun topologi jaringan berdasarkan informasi tersebut. Setiap router yang menjalankan OSPF akan saling bertukar informasi mengenai status tautan untuk memperoleh informasi lengkap mengenai jaringan.

# pengertian RIP
RIP adalah protokol routing dinamis yang menggunakan metode distance-vector untuk menentukan jalur terbaik. Setiap router yang menjalankan RIP akan berbagi informasi mengenai rute yang dimiliki dan menghitung jumlah hop (perantara router yang dilalui) untuk mencapai tujuan.

# Pengertian BGP
BGP adalah protokol routing yang digunakan untuk pertukaran informasi routing antar autonomous systems (AS) di internet. BGP bekerja dengan cara path-vector, di mana setiap router BGP berbagi informasi mengenai jalur atau path yang tersedia untuk mencapai tujuan tertentu, beserta dengan rute AS yang dilalui.

# Penjelasan IP Addressing yang dipakai
1.1. Lokasi CR

    Router CR:
        ETH0 (Public): 192.168.1.1/24 (Terhubung ke Internet)
        ETH1 (Subnet Internal 1): 10.1.1.1/24
        ETH2 (Subnet Internal 2): 14.1.1.1/24

    Switch 1:
        Mengelola koneksi perangkat di subnet 10.1.1.0/24.
        Contoh IP perangkat:
            PC1: 10.1.1.2
            PC2: 10.1.1.3
            PC3: 10.1.1.4

    Switch 2:
        Mengelola koneksi perangkat di subnet 14.1.1.0/24.
        Contoh IP perangkat:
            PC4: 14.1.1.2
            PC5: 14.1.1.3
            PC6: 14.1.1.4

1.2. Lokasi KJ

    Router KJ:
        ETH0 (Public): 192.168.2.1/24 (Terhubung ke Internet)
        ETH1 (Subnet Internal 1): 10.2.1.1/24
        ETH2 (Subnet Internal 2): 14.2.1.1/24

    Switch 1:
        Mengelola koneksi perangkat di subnet 10.2.1.0/24.
        Contoh IP perangkat:
            Laptop1: 10.2.1.2
            Laptop2: 10.2.1.3
            Laptop3: 10.2.1.4

    Switch 2:
        Mengelola koneksi perangkat di subnet 14.2.1.0/24.
        Contoh IP perangkat:
            Laptop4: 14.2.1.2
            Laptop5: 14.2.1.3
            Laptop6: 14.2.1.4

1.3. Lokasi KHI

    Router KHI:
        ETH0 (Public): 192.168.3.1/24 (Terhubung ke Internet)
        ETH1 (Subnet Internal 1): 10.3.1.1/24
        ETH2 (Subnet Internal 2): 14.3.1.1/24

    Switch 1:
        Mengelola koneksi perangkat di subnet 10.3.1.0/24.
        Contoh IP perangkat:
            Laptop1: 10.3.1.2
            Laptop2: 10.3.1.3
            Laptop3: 10.3.1.4

    Switch 2:
        Mengelola koneksi perangkat di subnet 14.3.1.0/24.
        Contoh IP perangkat:
            Laptop4: 14.3.1.2
            Laptop5: 14.3.1.3
            Laptop6: 14.3.1.4

# penjelasan routing yang dipakai
2.1. Routing pada Router CR

    Ke subnet KJ (10.2.1.0/24) melalui 192.168.2.1.
    Ke subnet KHI (10.3.1.0/24) melalui 192.168.3.1.

2.2. Routing pada Router KJ

    Ke subnet CR (10.1.1.0/24) melalui 192.168.1.1.
    Ke subnet KHI (10.3.1.0/24) melalui 192.168.3.1.

2.3. Routing pada Router KHI

    Ke subnet CR (10.1.1.0/24) melalui 192.168.1.1.
    Ke subnet KJ (10.2.1.0/24) melalui 192.168.2.1.

# penjelasan protokol routing yang dipakai
# OSPF
# ROUTER CR
router ospf 1
 network 10.1.1.0 0.0.0.255 area 0
 network 14.1.1.0 0.0.0.255 area 0
 network 192.168.1.0 0.0.0.255 area 0

 # ROUTER KJ 
 router ospf 1
 network 10.2.1.0 0.0.0.255 area 0
 network 14.2.1.0 0.0.0.255 area 0
 network 192.168.2.0 0.0.0.255 area 0

 # ROUTER KHI
 router ospf 1
 network 10.3.1.0 0.0.0.255 area 0
 network 14.3.1.0 0.0.0.255 area 0
 network 192.168.3.0 0.0.0.255 area 0

 # BGP
 # ROUTER CR
 router bgp 65001
 network 10.1.1.0 mask 255.255.255.0
 network 14.1.1.0 mask 255.255.255.0
 neighbor 192.168.2.1 remote-as 65002
 neighbor 192.168.3.1 remote-as 65003

 # ROUTER KJ
 router bgp 65002
 network 10.2.1.0 mask 255.255.255.0
 network 14.2.1.0 mask 255.255.255.0
 neighbor 192.168.1.1 remote-as 65001
 neighbor 192.168.3.1 remote-as 65003

 # ROUTER KHI
 router bgp 65003
 network 10.3.1.0 mask 255.255.255.0
 network 14.3.1.0 mask 255.255.255.0
 neighbor 192.168.1.1 remote-as 65001
 neighbor 192.168.2.1 remote-as 65002

 # KESIMPULAN
Topologi jaringan untuk ruang lab praktikum di Universitas Esa Unggul telah dirancang dengan menggunakan pendekatan routing statik dan dinamis (OSPF, RIP, dan BGP). Routing statik digunakan untuk menentukan jalur antar subnet secara manual pada router masing-masing kampus (CR, KJ, KHI), sehingga cocok untuk jaringan kecil dengan struktur topologi tetap. OSPF diterapkan sebagai protokol routing dinamis berbasis link-state untuk lingkungan dalam satu Autonomous System (AS), karena memungkinkan setiap router membangun peta jaringan lengkap dan memilih jalur terbaik berdasarkan metrik. Sementara itu, BGP digunakan untuk koneksi antar AS dalam skenario jaringan yang lebih kompleks, memungkinkan pertukaran informasi rute antar kampus yang berbeda. Dengan pembagian IP Address yang terstruktur, subnet masing-masing kampus dapat terhubung melalui router dan switch, serta dapat saling berkomunikasi melalui VPN Tunnel untuk keamanan data. Pendekatan ini menjamin fleksibilitas, skalabilitas, dan keamanan dalam jaringan laboratorium Universitas Esa Unggul.


![topologi](topologi.jpg)
