# rust-server

## Commit 1 Reflection Notes

Method handle_connection: 

- mem-print informasi mengenai setiap request yang dikirmkan ke server.
- BufReader: variabel untuk menampung stream. 
- http_request: variabel yang berisi baris-baris request yang dikirimkan browser ke server. 
- Vec<_> mengindikasikan bahwa baris-baris ini akan disimpan dalam vektor.
- .lines: salah satu method dari Bufreader, memisahkan data dari stream jika menemukan newline.
- .map dan .result: mendapatkan string dari masing-masing baris request.
