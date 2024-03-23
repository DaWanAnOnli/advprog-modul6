# rust-server

## Commit 1 Reflection Notes

Method handle_connection: 

- mem-print informasi mengenai setiap request yang dikirmkan ke server.
- BufReader: variabel untuk menampung stream. 
- http_request: variabel yang berisi baris-baris request yang dikirimkan browser ke server. 
- Vec<_> mengindikasikan bahwa baris-baris ini akan disimpan dalam vektor.
- .lines: salah satu method dari Bufreader, memisahkan data dari stream jika menemukan newline.
- .map dan .result: mendapatkan string dari masing-masing baris request.


## Commit 2 Reflection Notes
![commit2](https://github.com/DaWanAnOnli/advprog-modul6/assets/124868777/df86285d-2876-47dc-b419-f231fa0ebc85)

Method handle_connection:

- Menambahkan ```fs``` ke dalam ```use``` untuk meng-import modul filesystem.
- Menambahkan ```format!``` untuk memasukkan isi variabel ```status_line```, ```contents```, dan ```length``` ke dalam response.
Alur:
- Program menerima request html seperti sebelumnya.
- Program memasukkan informasi seperti file html, status line, dan length ke dalam response.
- Program mengirimkan response kepada user.
Pada program ini, request apapun akan tetap mendapatkan response yang sama. (tidak ada validasi jenis request).



## Commit 3 Reflection Notes
- Sebelumnya request apapun akan menghasilkan response yang sama.
- Buat file ```404.html``` untuk meng-handle request page not found
- Kita menambahkan if-else untuk validasi request. Jika Url pathnya kosong (root), akan mengembalikan halaman html seperti sebelumnya. Jika tidak, misal ditambahkan ```/hello``` akan mengembalikan halaman ```404.html``` (karena untuk sekarang belum ada implementasi untuk path tersebut).
- Tambahkan if else block pada code untuk memeriksa request line.

## Commit 4 Reflection Notes
- Mengganti ```if``` dengan ```match``` (semacam switch case) untuk case biasa, sleep, dan lain-lain.
- Untuk case sleep, server akan dibuat delay 5 detik untuk simulasi response yang lambat.
- Delay 5 detik bukan untuk setiap request, namun setiap request menambah delay 5 detik. Jadi jika ada 10 request bersamaan, akan ada yang menunggu 5 detik, 10 detik, dan seterusnya hingga 50 detik.
- Aplikasi menjadi tidak efisien karena dijalankan secara sekuensial. Jika dijalankan secara paralel, masing-masing user akan menunggu maksimal 5 detik.

## Commit 5 Reflection Notes
- Kita membuat implementasi thread pool agar server dapat berjalan secara concurrent
- Pertama kita buat agar setiap request akan diassign 1 thread. Namun ini tidak ideal karena rentan terhadap serangan Denial of Service
- Setelah itu kita implementasikan pembatasan jumlah thread dalam satu waktu.
- Langkah berikutnya adalah membuat tempat untuk menyimpan thread-thread yang akan digunakan.
- Lalu kita membuat mekanisme agar thread dapat langsung dibuat saat runtime dan menunggu sampai request datang
- Terakhir, kita membuat mekanisme untuk mengambil code dari queue yang ada di thread pool dan meng-assignnya menggunakan channel ke thread yang tersedia.

