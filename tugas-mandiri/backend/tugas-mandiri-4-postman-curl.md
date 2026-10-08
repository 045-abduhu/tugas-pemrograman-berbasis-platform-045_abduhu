# Tugas Mandiri 4 - Pengujian API dengan Postman dan curl

## Identitas

- Nama: **[abduhu]**
- NIM: **[2024520045]**
- Kelas: **[b]**
- Pertemuan: **02**

## Tujuan

Menguji API menggunakan Postman dan `curl`, kemudian membandingkan cara keduanya menampilkan request dan response.

# A. Pengujian Menggunakan Postman

## 1. GET

Method:

```text
GET
```

URL:

```text
https://httpbin.org/get
```

Klik **Send**.

Response yang diterima berupa JSON. Karena request GET tidak menggunakan body pada contoh ini, informasi utama berasal dari URL, header, dan parameter request.

## 2. POST

Method:

```text
POST
```

URL:

```text
https://httpbin.org/post
```

Pada tab **Body** pilih:

```text
raw → JSON
```

Masukkan:

```json
{
  "nama": "Umar",
  "kelas": "Informatika"
}
```

Header `Content-Type` sebaiknya:

```text
application/json
```

HTTPBin akan mengembalikan data JSON tersebut pada bagian `json` dalam response.

## Perbandingan GET dan POST

| Aspek | GET | POST |
|---|---|---|
| Endpoint | `/get` | `/post` |
| Data utama | URL/query/header | Body/header |
| Tujuan | Mengambil/menguji data | Mengirim data |
| Body pada contoh | Tidak digunakan | JSON |
| Hasil | Informasi request | Informasi request dan body JSON |

# B. Pengujian Menggunakan curl

## 1. curl GET

Jalankan:

```bash
curl -i https://httpbin.org/get
```

Opsi `-i` membuat header response ikut ditampilkan bersama body.

Contoh bagian yang perlu diperhatikan:

```text
HTTP/...
Content-Type: ...
Content-Length: ...
```

## 2. curl status 404

Jalankan:

```bash
curl -i https://httpbin.org/status/404
```

Perintah tersebut meminta HTTPBin mengembalikan status 404.

## C. Perbandingan `curl -s` dan `curl -i`

Jalankan:

```bash
curl -s https://httpbin.org/get
```

Kemudian:

```bash
curl -i https://httpbin.org/get
```

### Analisis

`curl -s` menggunakan mode silent sehingga informasi progres dari curl tidak ditampilkan dan output utama dapat difokuskan pada response. Opsi ini berguna ketika ingin mengambil response tanpa tampilan progres tambahan.

`curl -i` menampilkan HTTP response header sebelum response body. Karena itu opsi ini berguna ketika ingin memeriksa status code, Content-Type, Content-Length, dan header lain.

Perbedaannya adalah:

```text
curl -s → fokus pada output response tanpa progress meter
curl -i → response header + response body
```

## Bukti Pengujian

Lampirkan screenshot berikut:

```text
1. [Screenshot GET melalui Postman]
2. [Screenshot POST melalui Postman]
3. [Screenshot curl -i]
4. [Screenshot curl -s]
```

## Kesimpulan

Postman menyediakan antarmuka grafis sehingga request, header, body, status code, dan response mudah diperiksa. `curl` dapat digunakan melalui terminal dan cocok untuk pengujian cepat serta otomatisasi. Opsi `-s` digunakan untuk mode silent, sedangkan `-i` digunakan untuk menampilkan response header.

## Referensi

- curl documentation: https://curl.se/docs/
- HTTPBin: https://httpbin.org/
