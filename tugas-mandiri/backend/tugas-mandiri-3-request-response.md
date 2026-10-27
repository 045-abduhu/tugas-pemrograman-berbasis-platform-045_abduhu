# Tugas Mandiri 3 - Memahami Request dan Response

## Identitas

- Nama: **abduhu**
- NIM: **2024520045**
- Kelas: **b**
- Pertemuan: **02**

## Tujuan

Mengidentifikasi informasi yang dikirim client kepada server dan informasi yang dikembalikan server kepada client.

## Pengujian 1 - GET

Endpoint:

```text
GET https://httpbin.org/get?nama=Umar&kelas=TI
```

Query parameter yang dikirim:

```text
nama=Umar
kelas=TI
```

Pada response HTTPBin, parameter tersebut dapat dilihat pada bagian `args`.

Contoh:

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

## Pengujian 2 - Headers

Endpoint:

```text
GET https://httpbin.org/headers
```

Endpoint tersebut digunakan untuk melihat HTTP header yang diterima server.

Contoh bentuk response:

```json
{
  "headers": {
    "Accept": "...",
    "Host": "httpbin.org",
    "User-Agent": "..."
  }
}
```

Nilai header dapat berbeda tergantung client yang digunakan.

## 1. Apa yang dimaksud request dan siapa yang mengirimkannya?

Request adalah permintaan yang dikirimkan oleh client kepada server. Client dapat berupa browser, Postman, aplikasi mobile, atau program yang menggunakan HTTP client.

Pada pengujian ini, Postman atau browser bertindak sebagai client yang mengirim request kepada HTTPBin.

## 2. Apa yang dimaksud response dan siapa yang mengirimkannya?

Response adalah balasan dari server setelah menerima dan memproses request. Dalam pengujian ini HTTPBin bertindak sebagai server dan mengirimkan response kepada client.

## 3. Fungsi query parameter

Query parameter digunakan untuk memberikan informasi tambahan pada URL, biasanya untuk filtering, pencarian, pengurutan, atau parameter lain yang tidak perlu diletakkan pada body.

Contoh:

```text
?nama=Umar&kelas=TI
```

Artinya request membawa dua parameter, yaitu `nama` dengan nilai `Umar` dan `kelas` dengan nilai `TI`.

## 4. Fungsi HTTP header

HTTP header membawa metadata mengenai request atau response.

Contoh:

```text
User-Agent
```

Header tersebut dapat memberikan informasi mengenai client atau software yang melakukan request.

Header lain yang umum digunakan adalah:

```text
Content-Type
Accept
Authorization
Host
```

## 5. Perbedaan query parameter dan body

Query parameter diletakkan pada URL:

```text
GET /get?nama=Umar&kelas=TI
```

Sedangkan body diletakkan pada bagian isi request, misalnya:

```json
{
  "nama": "Umar",
  "kelas": "TI"
}
```

Query parameter sering digunakan untuk filter atau parameter sederhana, sedangkan body umum digunakan untuk mengirim data yang akan diproses, terutama pada POST, PUT, dan PATCH.

## Alur Request dan Response

```text
┌─────────────┐
│    Client   │
│  Postman    │
└──────┬──────┘
       │
       │ HTTP Request
       │ Method + URL + Header + Body
       ▼
┌─────────────┐
│   HTTPBin   │
│   Server    │
└──────┬──────┘
       │
       │ HTTP Response
       │ Status + Header + Body
       ▼
┌─────────────┐
│    Client   │
└─────────────┘
```

## Bukti Pengujian

Lampirkan screenshot response:

```text
[Screenshot GET /get]

[Screenshot GET /headers]
```

## Kesimpulan

Request adalah permintaan dari client ke server, sedangkan response adalah balasan dari server ke client. Request dapat membawa method, URL, query parameter, header, dan body. Response membawa status code, header, dan body.

## Referensi

- HTTPBin: https://httpbin.org/
- MDN HTTP Overview: https://developer.mozilla.org/en-US/docs/Web/HTTP
