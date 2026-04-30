Modul Pertemuan 9: API(CRUD)
=====================================================================

**Tujuan Pembelajaran**
Materi ini bertujuan untuk mengetahui bagaimana cara membuat CRUD API Laravel 

1\. Pengenalan API
--------------
1. Apa itu API?
API (Application Programming Interface) adalah jembatan komunikasi yang memungkinkan dua aplikasi atau sistem yang berbeda untuk saling bertukar data.
    ![erd](/screenshoot/pertemuan-9/api-analogy.jpeg)
Analogi: Bayangkan Anda di restoran. Anda (sebagai aplikasi Frontend) tidak mungkin masuk ke dapur (sebagai Database/Backend) untuk memasak sendiri. Anda memanggil pelayan (API) untuk mencatat pesanan, pelayan membawanya ke dapur, lalu pelayan kembali membawa makanan ke meja Anda.

2. Perbedaan Route Biasa vs Route API
Di Laravel, perbedaan utamanya terletak pada output yang dihasilkan:
- Route Biasa (routes/web.php): Mengembalikan halaman web utuh (HTML/CSS/JS) yang siap dilihat mata.
- Route API (routes/api.php): Hanya mengembalikan data mentah tanpa desain, biasanya dalam format JSON (JavaScript Object       Notation). Aplikasi pemanggil yang akan mendesain sendiri bagaimana data tersebut ditampilkan.

3. Mengapa Kita Menggunakan API?
 - Satu Backend, Banyak Platform: Dengan menyediakan API, satu sistem backend Laravel dapat digunakan secara bersamaan oleh Website (misal: React/Next.js) dan Aplikasi Mobile (misal: Flutter).
 - Pembagian Kerja (Separation of Concerns): Tim Backend bisa fokus pada logika data dan keamanan, sementara tim Frontend fokus pada tampilan tanpa saling mengganggu kode satu sama lain.

2\. Standar HTTP Status Code
Berikut adalah format balasan status API yang akan kita gunakan dalam praktik:
- 200 OK: Request berhasil, server mengembalikan data (Digunakan untuk Read/Search).
- 201 Created: Request berhasil, data baru berhasil disimpan (Digunakan untuk Create).
- 204 No Content: Request berhasil, tapi tidak ada data untuk dikembalikan (Misal: setelah Delete).
- 400 Bad Request: Request ditolak karena input tidak valid.
- 401 Unauthorized: Client belum login atau tidak menyertakan token autentikasi.
- 403 Forbidden: Client login, tetapi tidak punya hak akses ke data tersebut.
- 404 Not Found: Data atau endpoint tidak ditemukan.
- 405 Method Not Allowed: Salah menggunakan metode HTTP (misal: rute POST ditembak dengan GET).
- 500 Internal Server Error: Terjadi error pada kode sistem/server.

3\. Persiapan dan Instalasi API