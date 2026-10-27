# Tugas Mandiri 2 - Memahami HTTP Status Code

## Identitas

- Nama: **abduhu**
- NIM: **2024520045**
- Kelas: **b**
- Pertemuan: **02**

## Tujuan

Memahami arti kode status HTTP dan menghubungkannya dengan hasil pengujian.

## Endpoint Pengujian

Gunakan:

```text
https://httpbin.org/status/:code
```

Contoh:

```text
GET https://httpbin.org/status/200
GET https://httpbin.org/status/404
```

## Tabel Hasil Pengujian

| Status Code | Arti | Hasil Pengujian | Kapan Digunakan |
|---:|---|---|---|
| 200 | OK | Request berhasil | Membaca atau memproses request dengan sukses |
| 201 | Created | Resource berhasil dibuat | Setelah POST berhasil membuat resource |
| 400 | Bad Request | Request tidak valid | Data/body/parameter tidak sesuai |
| 401 | Unauthorized | Belum terautentikasi | Token/login diperlukan atau tidak valid |
| 403 | Forbidden | Akses ditolak | User sudah dikenal tetapi tidak memiliki izin |
| 404 | Not Found | Resource tidak ditemukan | URL/resource yang diminta tidak tersedia |
| 500 | Internal Server Error | Terjadi kesalahan server | Server gagal memproses request karena masalah internal |

## 1. Perbedaan 400 dan 404

`400 Bad Request` berarti server menerima request tetapi request tersebut tidak valid atau tidak dapat diproses karena masalah pada permintaan. Contohnya format JSON tidak sesuai atau parameter wajib tidak diberikan.

`404 Not Found` berarti server tidak menemukan resource atau route yang diminta. Contohnya meminta:

```text
GET /mahasiswa/999
```

ketika mahasiswa dengan ID 999 tidak ada.

Jadi, 400 berfokus pada **request yang tidak valid**, sedangkan 404 berfokus pada **resource atau route yang tidak ditemukan**.

## 2. Perbedaan 401 dan 403

`401 Unauthorized` berkaitan dengan autentikasi. Client belum memberikan identitas yang valid atau kredensial/token tidak valid.

`403 Forbidden` berarti server mengetahui client tetapi menolak akses karena client tidak mempunyai hak untuk melakukan operasi tersebut.

Contoh:

```text
401 → belum login / token tidak valid
403 → sudah login tetapi bukan admin
```

## 3. Mengapa 500 menunjukkan masalah pada server?

Status 500 menunjukkan bahwa server mengalami kondisi yang tidak diharapkan ketika memproses request. Contohnya terjadi exception yang tidak tertangani, konfigurasi server bermasalah, atau layanan pendukung mengalami kegagalan.

## 4. Apakah setiap error HTTP berarti server rusak?

Tidak. Kode 4xx menunjukkan masalah yang berkaitan dengan request atau akses dari client.

Contohnya:

```text
404 Not Found
```

belum tentu berarti server rusak. Server dapat berjalan normal tetapi resource yang diminta memang tidak ada.

Sebaliknya, 5xx menunjukkan kegagalan pada sisi server ketika memproses request.

## Bukti Pengujian

Lampirkan minimal tiga screenshot kode status berbeda.

```text
[Screenshot status 200]

[Screenshot status 404]

[Screenshot status 500]
```

## Kesimpulan

HTTP status code membantu client memahami hasil request. Kategori 2xx menunjukkan keberhasilan, 4xx umumnya menunjukkan masalah pada request atau akses client, dan 5xx menunjukkan kegagalan pemrosesan pada server.

## Referensi

- HTTP Semantics - RFC 9110: https://www.rfc-editor.org/rfc/rfc9110
- HTTPBin: https://httpbin.org/
