# Module 10 - Broadcast Chat

![Run 3 client with one server](./server_client.png)
![Sending message from clients](./send_msg.png)

Pada gambar di atas, dapat dilihat bahwa ketika seorang client mengirimkan sebuah pesan, pesan tersebut akan diterima oleh server kemudian server akan membagikan pesan tersebut ke semua client yang sedang terhubung ke server tersebut, termasuk client yang mengirimkan pesan tersebut. Hal ini terjadi karena setiap client yang menghubungkan diri ke server akan diingat oleh server dan server akan menunggu hingga salah satu client tersebut mengirimkan sebuah pesan ke server untuk server bagikan ke semua client yang terhubung padanya.

![Client server different port](./client_server_diff_port.png)

Pada gambar di atas, port dari client dan server berbeda, dimana server menunggu koneksi pada port `2000` sedangkan client ingin menghubungi sebuah `websocket` yang sedang berjalan pada port `8080`. Namun, karena tidak ada `websocket` yang sedang berjalan pada port `8080`, client mengalami error `ConnectionRefused`, yang menandakan bahwa client sudah mencoba beberapa kali untuk menghubungi `websocket` pada port `8080` tetapi hubungan tersebut tidak pernah berhasil.

![Client server same port](./client_server_same_port.png)

Setelah mengubah port server dari `2000` menjadi `8080`, client dapat berhubungan kembali dengan server seperti sebelumnya. Namun, berbeda dengan client yang menggunakan protokol `websocket` untuk menghubungi server, server hanya mendengarkan koneksi TCP yang terjadi pada port `8080`, dimana koneksi yang terjadi akan dijadikan sebuah stream `websocket` melalui code.
