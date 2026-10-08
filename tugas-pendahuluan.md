# Tugas Pendahuluan - Pertemuan 02

## Identitas

- Nama: **abduhu**
- NIM: **2024520045**
- Kelas: **b**
- Mata Kuliah: **Pemrograman Berbasis Platform**
- Pertemuan: **02**

## 1. Perbandingan Struktur Data `/posts/1` dan `/users/1`

### `/posts/1`

Contoh data:

```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit..."
}
```

Field pada data post:

| Field | Fungsi |
|---|---|
| `userId` | Menunjukkan ID pengguna yang memiliki post |
| `id` | Identitas unik dari post |
| `title` | Judul post |
| `body` | Isi atau konten post |

### `/users/1`

Data user memiliki struktur yang lebih lengkap, misalnya:

```json
{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "sincere@april.biz",
  "address": {
    "street": "Kulas Light",
    "suite": "Apt. 556",
    "city": "Gwenborough",
    "zipcode": "92998-3874",
    "geo": {
      "lat": "-37.3159",
      "lng": "81.1496"
    }
  },
  "phone": "1-770-736-8031",
  "website": "hildegard.org",
  "company": {
    "name": "Romaguera-Crona",
    "catchPhrase": "Multi-layered client-server neural-net",
    "bs": "harness real-time e-markets"
  }
}
```

Field user digunakan untuk menyimpan identitas, informasi kontak, alamat, website, dan informasi perusahaan.

### Perbandingan

`/posts/1` berfokus pada data tulisan, sedangkan `/users/1` berfokus pada data pengguna. Post memiliki `userId` yang menghubungkan post dengan user. Dengan demikian, `userId` dapat dipandang sebagai referensi ke `users.id`.

**Kesimpulan:** struktur post lebih sederhana karena hanya menyimpan informasi tulisan, sedangkan struktur user lebih kompleks karena menyimpan identitas, alamat, kontak, dan perusahaan.

---

## 2. Analisis Struktur Tabel `/posts` dan `/users`

Jika data JSONPlaceholder dianggap sebagai struktur tabel relasional, tabel sederhananya dapat digambarkan sebagai berikut.

### Tabel `users`

| Kolom | Keterangan |
|---|---|
| `id` | Primary key pengguna |
| `name` | Nama pengguna |
| `username` | Nama pengguna/login |
| `email` | Email |
| `address` | Informasi alamat |
| `phone` | Nomor telepon |
| `website` | Website |
| `company` | Informasi perusahaan |

### Tabel `posts`

| Kolom | Keterangan |
|---|---|
| `id` | Primary key post |
| `userId` | Foreign key yang menunjuk `users.id` |
| `title` | Judul tulisan |
| `body` | Isi tulisan |

### Diagram Relasi Sederhana

```text
┌─────────────────────┐
│       users         │
├─────────────────────┤
│ PK id               │
│ name                │
│ username            │
│ email               │
│ address             │
│ phone               │
│ website             │
│ company             │
└──────────┬──────────┘
           │
           │ 1
           │
           │
           │ N
┌──────────▼──────────┐
│       posts         │
├─────────────────────┤
│ PK id               │
│ FK userId           │
│ title               │
│ body                │
└─────────────────────┘
```

Hubungan tersebut dapat dibaca sebagai **satu user dapat mempunyai banyak post**, sedangkan satu post dimiliki oleh satu user berdasarkan `userId`.

---

## 3. Hubungan URL, Method, dan Data pada `/posts`

URL menunjukkan resource yang ingin diakses, sedangkan HTTP method menunjukkan operasi yang dilakukan terhadap resource tersebut.

Contoh:

```text
GET https://jsonplaceholder.typicode.com/posts
```

Request tersebut berarti meminta daftar post.

Untuk satu post:

```text
GET https://jsonplaceholder.typicode.com/posts/1
```

Angka `1` merupakan route parameter yang digunakan untuk menentukan post dengan ID 1.

Untuk filter:

```text
GET https://jsonplaceholder.typicode.com/posts?userId=1
```

`userId=1` merupakan query parameter. Hasilnya adalah daftar post yang memiliki `userId` bernilai 1.

Untuk membuat post:

```text
POST https://jsonplaceholder.typicode.com/posts
```

Data dikirim melalui body JSON, misalnya:

```json
{
  "userId": 1,
  "title": "Post Baru",
  "body": "Isi post baru"
}
```

Jadi, hubungan ketiganya adalah:

```text
URL       → menentukan resource
Method    → menentukan operasi
Data      → menentukan parameter/body yang digunakan
Response  → berisi hasil operasi
```

---

## 4. Perbedaan `/posts/1` dan `?userId=1`

### `/posts/1`

```text
GET https://jsonplaceholder.typicode.com/posts/1
```

Digunakan untuk mengambil **satu post** berdasarkan ID.

Bentuk hasilnya adalah satu objek:

```json
{
  "userId": 1,
  "id": 1,
  "title": "...",
  "body": "..."
}
```

### `?userId=1`

```text
GET https://jsonplaceholder.typicode.com/posts?userId=1
```

Digunakan sebagai filter berdasarkan `userId`. Hasilnya berupa **array** yang berisi post milik user dengan ID 1.

```json
[
  {
    "userId": 1,
    "id": 1,
    "title": "...",
    "body": "..."
  }
]
```

### Kesimpulan

`/posts/1` menggunakan **path parameter** untuk memilih satu resource tertentu, sedangkan `?userId=1` menggunakan **query parameter** untuk memfilter kumpulan resource.

---

## 5. Perbandingan GET, POST, PUT, PATCH, dan DELETE

| Method | Tujuan | Contoh URL | Status umum | Perubahan data |
|---|---|---|---|---|
| GET | Membaca data | `/posts/1` | 200 | Tidak mengubah data |
| POST | Membuat data | `/posts` | 201 | Membuat resource baru |
| PUT | Mengganti/memperbarui resource | `/posts/1` | 200 | Mengubah resource |
| PATCH | Memperbarui sebagian field | `/posts/1` | 200 | Mengubah sebagian resource |
| DELETE | Menghapus resource | `/posts/1` | 200 | Menghapus resource secara simulasi |

Contoh POST:

```json
{
  "userId": 1,
  "title": "Post Baru",
  "body": "Isi post baru"
}
```

Contoh PUT:

```json
{
  "id": 1,
  "userId": 1,
  "title": "Judul Baru",
  "body": "Isi Baru"
}
```

Contoh PATCH:

```json
{
  "title": "Judul Saja Diubah"
}
```

Pada JSONPlaceholder klasik, operasi POST, PUT, PATCH, dan DELETE disimulasikan sehingga respons terlihat seperti operasi berhasil, tetapi perubahan tidak benar-benar tersimpan permanen di server.

**Kesimpulan:** GET digunakan untuk membaca, POST membuat, PUT mengganti/memperbarui resource, PATCH memperbarui sebagian, dan DELETE menghapus. Perbedaan method membuat maksud request dapat dipahami dengan jelas oleh server dan client.

## Referensi

1. JSONPlaceholder Guide - Typicode: https://github.com/typicode/jsonplaceholder
2. JSONPlaceholder API documentation: https://jsonplaceholder.typicode.com/
