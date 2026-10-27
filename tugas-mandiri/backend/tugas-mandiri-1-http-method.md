# Tugas Mandiri 1 - Mengenal HTTP Method dan Endpoint

## Identitas

- Nama: **abduhu**
- NIM: **2024520045**
- Kelas: **b**
- Pertemuan: **02**

## Tujuan

Memahami hubungan antara HTTP method, endpoint, parameter, request, dan response menggunakan HTTPBin.

## 1. GET

**Method:**

```text
GET
```

**URL:**

```text
https://httpbin.org/get?nama=Umar&kelas=TI
```

**Data yang dikirim:**

```text
nama=Umar
kelas=TI
```

**Tujuan:** mengambil data dan menguji query parameter.

**Hasil yang diharapkan:** HTTPBin mengembalikan response JSON yang menampilkan query parameter pada bagian `args`.

Contoh bentuk response:

```json
{
  "args": {
    "nama": "Umar",
    "kelas": "TI"
  },
  "headers": {},
  "origin": "...",
  "url": "https://httpbin.org/get?nama=Umar&kelas=TI"
}
```

## 2. POST

**Method:**

```text
POST
```

**URL:**

```text
https://httpbin.org/post
```

**Body:**

```json
{
  "nama": "Umar",
  "kelas": "TI"
}
```

**Tujuan:** menguji pengiriman data melalui request body.

HTTPBin akan mengembalikan data yang dikirim pada bagian `json` apabila body dikirim sebagai JSON.

## 3. PUT

**Method:**

```text
PUT
```

**URL:**

```text
https://httpbin.org/put
```

**Body:**

```json
{
  "nama": "Umar",
  "kelas": "TI",
  "status": "aktif"
}
```

**Tujuan:** menguji request PUT dan pengiriman data melalui body.

## 4. PATCH

**Method:**

```text
PATCH
```

**URL:**

```text
https://httpbin.org/patch
```

**Body:**

```json
{
  "status": "selesai"
}
```

**Tujuan:** menguji request PATCH untuk perubahan sebagian.

## 5. DELETE

**Method:**

```text
DELETE
```

**URL:**

```text
https://httpbin.org/delete
```

**Tujuan:** menguji request DELETE.

## Tabel Hasil Pengujian

Isi kolom status berdasarkan hasil pengujian Anda di Postman.

| No | Method | Endpoint | Data yang dikirim | Status | Hasil |
|---:|---|---|---|---:|---|
| 1 | GET | `/get` | Query `nama`, `kelas` | 200 | Request berhasil dan query tampil pada response |
| 2 | POST | `/post` | JSON `nama`, `kelas` | 200 | Request berhasil dan data body ditampilkan kembali |
| 3 | PUT | `/put` | JSON nama, kelas, status | 200 | Request berhasil dan body ditampilkan kembali |
| 4 | PATCH | `/patch` | JSON status | 200 | Request berhasil dan body ditampilkan kembali |
| 5 | DELETE | `/delete` | Tidak ada | 200 | Request DELETE berhasil |

## Analisis

GET digunakan untuk mengambil informasi dan pada contoh ini data tambahan dikirim melalui query parameter. POST digunakan untuk mengirim data baru melalui body. PUT biasanya digunakan untuk mengganti atau memperbarui resource secara keseluruhan, sedangkan PATCH digunakan untuk perubahan sebagian. DELETE digunakan untuk meminta penghapusan resource.

HTTPBin berfungsi sebagai layanan pengujian sehingga endpoint `/get`, `/post`, `/put`, `/patch`, dan `/delete` terutama digunakan untuk memperlihatkan informasi request yang diterima server.

## Bukti Pengujian

Tambahkan minimal dua screenshot hasil pengujian Postman di bagian ini.

```text
[Screenshot GET melalui Postman]

[Screenshot POST melalui Postman]
```

## Kesimpulan

HTTP method menunjukkan jenis operasi yang diminta client. Endpoint menunjukkan alamat resource atau fungsi yang dituju. Data dapat dikirim melalui query parameter, header, atau body tergantung kebutuhan request.

## Referensi

- HTTPBin: https://httpbin.org/
- JSONPlaceholder/REST API examples: https://github.com/typicode/jsonplaceholder
