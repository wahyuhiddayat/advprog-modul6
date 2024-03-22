# Reflection Module 6

## Commit 1 
Fungsi handle_connection memproses koneksi TCP yang masuk dengan cara membaca permintaan HTTP melalui TcpStream menggunakan BufReader. Prosesnya melibatkan iterasi atas baris-baris yang dibaca, dengan setiap baris yang berhasil dibaca diubah menjadi string. Proses iterasi ini berlangsung sampai menemui baris kosong, yang menandakan akhir dari header permintaan HTTP, dan kemudian mengumpulkan baris-baris yang dibaca ke dalam sebuah Vec<String>. Setelah itu, program akan print hasilnya.

## Commit 2
<img width="1440" alt="Screenshot 2024-03-22 at 4 20 28 PM" src="https://github.com/wahyuhiddayat/advprog-modul6/assets/119432989/ac9dc69e-f0c1-422d-83ef-27199b5e9118">

## Commit 3
Saya memodifikasi method handle_connection untuk mengecek dan melakukan pembagian response berdasarkan path. Selain itu, saya membuat file html baru bernama 404.html. Server akan mengecek path dari permintaan HTTP dan menentukan konten yang akan dikirim sebagai response. Jika path adalah /, maka server akan merespons dengan konten dari file hello.html. Jika path tidak dikenali, maka server akan merespons dengan konten dari file 404.html, yang merupakan halaman error. 