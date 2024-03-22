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
