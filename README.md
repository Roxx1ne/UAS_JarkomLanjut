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

![topologi](topologi.jpg)
