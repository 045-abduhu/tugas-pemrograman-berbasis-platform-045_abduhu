# Tugas Mandiri 3 — Matriks Authentication dan Authorization

## Konteks
Contoh proyek yang digunakan adalah e-library. Peran pengguna: Anggota, Pustakawan, dan Pimpinan. Sesuaikan peran dan endpoint jika proyek kelompok berbeda.

| Fitur | Anggota | Pustakawan | Pimpinan | Contoh endpoint |
|---|---:|---:|---:|---|
| Melihat katalog buku | ✅ | ✅ | ✅ | `GET /api/v1/buku` |
| Melihat detail buku | ✅ | ✅ | ✅ | `GET /api/v1/buku/:id` |
| Membuat peminjaman | ✅ | ✅ | ❌ | `POST /api/v1/peminjaman` |
| Melihat riwayat peminjaman sendiri | ✅ | ❌ | ❌ | `GET /api/v1/peminjaman/me` |
| Menambah katalog buku | ❌ | ✅ | ✅ | `POST /api/v1/buku` |
| Mengubah data katalog | ❌ | ✅ | ✅ | `PUT /api/v1/buku/:id` |
| Menghapus katalog | ❌ | ✅ | ❌ | `DELETE /api/v1/buku/:id` |
| Melihat rekap pengadaan | ❌ | ❌ | ✅ | `GET /api/v1/admin/rekap-pengadaan` |

Tanda ❌ berarti permintaan dari pengguna yang identitasnya sudah terverifikasi harus ditolak dengan 403 apabila fitur itu dilindungi oleh middleware peran.

## Perbedaan 401 dan 403
Kode **401** digunakan ketika permintaan ke endpoint terlindungi tidak menyertakan token atau token tidak valid/kedaluwarsa. Contohnya, `GET /api/v1/peminjaman/me` tanpa token harus ditolak karena identitas belum dapat diverifikasi.

Kode **403** digunakan ketika token valid tetapi peran pengguna tidak memiliki izin. Contohnya, anggota yang sudah login mencoba `POST /api/v1/buku` untuk menambah katalog; sistem mengetahui identitasnya, tetapi hak aksesnya tidak mencukupi.

## Jika hanya menggunakan `requireAuth`
Jika endpoint penambahan katalog hanya memakai `requireAuth`, sistem hanya memeriksa bahwa pengguna sudah login. Anggota yang telah login bisa mengakses fitur tersebut jika tidak ada pemeriksaan `requireRole`, sehingga hak akses tidak sesuai aturan aplikasi. Karena itu, route sensitif perlu memakai `requireAuth` terlebih dahulu, lalu `requireRole('PUSTAKAWAN', 'PIMPINAN')`.

Contoh:
```js
router.post(
  '/buku',
  requireAuth,
  requireRole('PUSTAKAWAN', 'PIMPINAN'),
  createBook
);
```
