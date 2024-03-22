# Reflection Module 6

## Commit 1 
Fungsi handle_connection memproses koneksi TCP yang masuk dengan cara membaca permintaan HTTP melalui TcpStream menggunakan BufReader. Prosesnya melibatkan iterasi atas baris-baris yang dibaca, dengan setiap baris yang berhasil dibaca diubah menjadi string. Proses iterasi ini berlangsung sampai menemui baris kosong, yang menandakan akhir dari header permintaan HTTP, dan kemudian mengumpulkan baris-baris yang dibaca ke dalam sebuah Vec<String>. Setelah itu, program akan print hasilnya.

## Commit 2
<img width="1440" alt="Screenshot 2024-03-22 at 4 20 28 PM" src="https://github.com/wahyuhiddayat/advprog-modul6/assets/119432989/ac9dc69e-f0c1-422d-83ef-27199b5e9118">

## Commit 3
<img width="1440" alt="Screenshot 2024-03-22 at 4 48 46 PM" src="https://github.com/wahyuhiddayat/advprog-modul6/assets/119432989/e8df4799-2772-48ee-bcb9-66e704011fcc">

Saya memodifikasi method handle_connection untuk mengecek dan melakukan pembagian response berdasarkan path. Selain itu, saya membuat file html baru bernama 404.html. Server akan mengecek path dari permintaan HTTP dan menentukan konten yang akan dikirim sebagai response. Jika path adalah /, maka server akan merespons dengan konten dari file hello.html. Jika path tidak dikenali, maka server akan merespons dengan konten dari file 404.html, yang merupakan halaman error. 

## Commit 4
Dengan menambahkan thread::sleep(Duration::from_secs(10)); pada route /sleep, saya mensimulasikan delay dalam menangani permintaan. Hasilnya, ketika dua permintaan dibuat hampir bersamaan—satu ke /sleep dan satunya lagi ke /—permintaan kedua harus menunggu sampai permintaan pertama selesai. Ini menunjukkan bahwa server seperti ini tidak bisa menangani permintaan secara paralel.

## Commit 5
ThreadPool berfungsi untuk mengelola sejumlah thread yang dapat bekerja secara simultan. Dengan menetapkan ThreadPool sebanyak 4 worker, server mampu mengatasi kelemahan sebelumnya, yaitu ketidakmampuan dalam menangani lebih dari satu permintaan secara bersamaan. Setiap permintaan yang masuk kini dialihkan ke sebuah worker yang ada dalam ThreadPool. Ini memungkinkan permintaan yang berbeda diproses secara paralel. Misalnya, permintaan ke rute /sleep yang membutuhkan waktu 10 detik sekarang tidak lagi menghambat proses permintaan lain yang masuk. Mekanisme ThreadPool menggunakan channel untuk memfasilitasi komunikasi antara threads. Saat sebuah job dikirim, ia masuk ke dalam antrian dan worker yang tersedia akan mengambil job tersebut untuk dieksekusi. Dengan penggunaan ThreadPool, server menjadi lebih efisien dan dapat diandalkan dalam menangani beban kerja yang lebih berat dan permintaan yang datang secara bersamaan. Hal ini menunjukkan pentingnya arsitektur yang baik dalam pengembangan server untuk mengoptimalkan kemampuan dalam melayani permintaan secara concurrent dan meningkatkan kinerja server secara keseluruhan.
