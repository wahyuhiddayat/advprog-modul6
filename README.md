# Reflection Module 6

## Commit 1 
Fungsi handle_connection memproses koneksi TCP yang masuk dengan cara membaca permintaan HTTP melalui TcpStream menggunakan BufReader. Prosesnya melibatkan iterasi atas baris-baris yang dibaca, dengan setiap baris yang berhasil dibaca diubah menjadi string. Proses iterasi ini berlangsung sampai menemui baris kosong, yang menandakan akhir dari header permintaan HTTP, dan kemudian mengumpulkan baris-baris yang dibaca ke dalam sebuah Vec<String>. Setelah itu, program akan print hasilnya.