# Tugas Mandiri 4 — Menganalisis Struktur dan Validitas JWT

## 1. Klaim pada payload
Pada JWT praktikum, klaim `sub` digunakan untuk mengidentifikasi subjek/pengguna. Klaim `role` menyatakan peran pengguna yang dipakai server untuk memeriksa hak akses. Klaim `iat` menunjukkan waktu token diterbitkan, sedangkan `exp` menunjukkan waktu kedaluwarsa token.

Contoh payload ilustratif dari modul (bukan hasil login saya):
```json
{
  "sub": "2",
  "nim": "2026002",
  "role": "MAHASISWA",
  "iat": 1791320400,
  "exp": 1791324000
}
```
Selisih `exp` dan `iat` pada contoh tersebut adalah 3.600 detik atau satu jam. Dalam laporan akhir, cocokkan nama klaim dan nilai dengan token yang benar-benar diterbitkan oleh API praktikum.

## 2. Mengapa perubahan payload membuat token gagal?
JWT ditandatangani oleh server menggunakan secret. Jika satu karakter pada payload diubah tanpa membuat tanda tangan baru, isi token tidak lagi cocok dengan signature yang dibuat server. Karena verifikasi gagal, endpoint yang memerlukan token harus menolak permintaan dengan status 401.

## 3. Tabel hasil pengujian
Isi kolom hasil aktual setelah menjalankan API sendiri.

| Pengujian | Hasil yang diharapkan | Hasil aktual saya |
|---|---|---|
| `GET /api/v1/auth/me` dengan token asli | 200 | Isi setelah mencoba |
| `GET /api/v1/auth/me` dengan token yang diubah | 401 | Isi setelah mencoba |

## 4. Cara pengujian
1. Nyalakan backend praktikum.
2. Login menggunakan akun praktikum dan salin token yang dihasilkan.
3. Periksa payload di jwt.io. Gunakan hanya token dari lingkungan praktikum.
4. Kirim `GET http://localhost:3000/api/v1/auth/me` dengan header `Authorization: Bearer TOKEN_ASLI`; catat status.
5. Ubah satu karakter token, lalu kirim lagi ke endpoint yang sama; catat status yang benar-benar diterima.
6. Ambil screenshot payload serta kedua hasil request. Samarkan token lengkap dan jangan menaruh token di repository.

## 5. Bukti
- [ ] Screenshot payload JWT (token lengkap disamarkan).
- [ ] Screenshot respons token asli (seharusnya 200).
- [ ] Screenshot respons token yang diubah (seharusnya 401).

**Catatan:** jangan mengisi kolom hasil aktual sebelum pengujian dilakukan.
