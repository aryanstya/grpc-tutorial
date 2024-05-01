## Module 9 Reflection

1.Dalam RPC Unary, klien mengirim satu permintaan dan mendapatkan satu tanggapan. Kasus penggunaan umum untuk RPC unary adalah saat mengambil data dari database atau menjalankan sesuatu di server. Dalam RPC streaming server, klien mengirim satu permintaan dan mendapatkan aliran sebagai tanggapan. Contoh penggunaannya adalah untuk mengambil data real-time seperti laporan cuaca atau harga saham. Dalam RPC streaming dua arah, baik klien maupun server akan mengirimkan aliran sebagai permintaan dan tanggapan masing-masing. Ini berguna untuk aplikasi obrolan, perangkat lunak yang menggunakan kolaborasi real-time, atau bahkan game.

2.Untuk otentikasi, teknologi yang paling umum digunakan adalah TLS/SSL dan JWT untuk memperkuat keamanan layanan gRPC. TLS/SSL digunakan untuk mengenkripsi data yang dikirim antara klien dan server. JWT (atau otentikasi berbasis token lainnya) dapat digunakan untuk mengotentikasi klien yang mengakses layanan.

3.Karena streaming dua arah menggunakan paralelisme dan konkurensi, layanan gRPC biasanya akan mewarisi masalah yang umum saat menggunakan konkurensi seperti kondisi perlombaan, bagian kritis, deadlock, dan lain-lain. Manajemen status juga sangat penting untuk ditangani dengan baik terutama dalam skenario aplikasi obrolan di mana sesi biasanya digunakan untuk melacak klien.

4.ReceiverStream berintegrasi dengan baik dengan tokio, di mana tokio umumnya digunakan untuk aplikasi asinkron yang ditulis dalam Rust. Tetapi jika Anda tidak menggunakan tokio, dapat sulit untuk menggunakan ReceiverStream dengan kerangka asinkron lainnya.

5.Kode server dan klien dapat dibagi menjadi fungsionalitas masing-masing (layanan pembayaran, layanan transaksi, layanan obrolan). Selain itu, itu dapat diorganisir lebih lanjut dengan menggunakan prinsip pemisahan kepentingan. Refaktorisasi juga bermanfaat untuk menghasilkan basis kode yang lebih dapat digunakan kembali sehingga pengembang lain dapat menambahkan fungsionalitas lebih banyak tanpa banyak masalah. Kita juga dapat menambahkan tes, penanganan kesalahan yang lebih kuat, dan dokumentasi untuk memperkuat basis kode secara keseluruhan.

6.Satu hal utama yang hilang adalah pemrosesan permintaan yang sebenarnya. Ini mencakup validasi input dan penanganan kesalahan jika permintaannya tidak sesuai yang diharapkan serta pemrosesan pembayaran menggunakan API pihak ketiga seperti Stripe misalnya.

7.Daya tarik utama dari gRPC adalah penggunaan HTTP/2 di mana ia menggunakan bagian terbaiknya, seperti multiplexing, kompresi header, dan pengkodean biner. gRPC juga menggunakan sistem serialisasi yang tidak tergantung bahasa dan netral platform yang disebut protobuf, lebih cepat dan ringan daripada JSON yang lebih umum digunakan. Alat-alat gRPC juga dapat menghasilkan kode untuk menghasilkan API yang aman tipe dalam banyak bahasa.
