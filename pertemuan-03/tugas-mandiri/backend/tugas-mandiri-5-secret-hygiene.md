# Tugas Mandiri 5 — Pemeriksaan Secret Hygiene

## Tujuan
Memeriksa agar file rahasia seperti `backend/.env` tidak terlacak Git dan token JWT lengkap tidak tersimpan di laporan atau kode client.

## 1. Periksa apakah `.env` dilacak Git
Jalankan dari folder utama repository:

```bash
git ls-files --error-unmatch backend/.env 2>/dev/null && echo "BAHAYA: .env terlacak" || echo "AMAN: .env tidak terlacak"
```

Hasil aman yang diharapkan adalah:
```text
AMAN: .env tidak terlacak
```

Jika `.env` ternyata sudah terlacak, tambahkan `backend/.env` ke `.gitignore`, lalu hentikan pelacakan tanpa menghapus file lokal:
```bash
git rm --cached backend/.env
```
Setelah itu commit perubahan `.gitignore` dan penghapusan dari index. Jika rahasia pernah dipublikasikan, ganti `JWT_SECRET` karena rahasia lama harus dianggap bocor.

## 2. Periksa pola token JWT pada dokumentasi dan client
Jalankan:
```bash
git grep -nE 'eyJ[A-Za-z0-9_-]+\\.[A-Za-z0-9_-]+\\.[A-Za-z0-9_-]+' -- docs web mobile || echo "AMAN: tidak ada JWT di laporan atau client"
```

Perintah ini mencari pola token JWT pada file yang dilacak Git di folder `docs`, `web`, dan `mobile`. Jika ditemukan token, hapus token lengkap dari laporan, source code client, dan screenshot. Gunakan placeholder seperti `[TOKEN DISAMARKAN]` untuk dokumentasi.

## 3. Contoh `.gitignore`
Pastikan aturan berikut ada pada `.gitignore` yang sesuai dengan struktur repository:
```gitignore
.env
.env.*
!.env.example
backend/.env
```

`backend/.env.example` boleh berisi nama variabel dan nilai dummy, tetapi jangan berisi secret asli. Contoh:
```env
PORT=3000
JWT_SECRET=ganti_dengan_secret_lokal_yang_kuat
```

## 4. Catatan hasil pemeriksaan
Lengkapi tabel ini dengan hasil yang benar-benar muncul di terminal.

| Pemeriksaan | Hasil aktual | Tindakan jika ditemukan masalah |
|---|---|---|
| `backend/.env` tidak terlacak | Isi setelah menjalankan perintah | Tambahkan ke `.gitignore` dan `git rm --cached` jika sudah terlacak |
| Token JWT tidak ditemukan di `docs`, `web`, `mobile` | Isi setelah menjalankan perintah | Hapus token dan gunakan placeholder |
| Secret tidak tampil di screenshot/laporan | Periksa secara manual | Samarkan atau hapus |
| `JWT_SECRET` yang pernah terpapar sudah diganti | Isi setelah memeriksa | Ganti secret dan terbitkan token baru |

## 5. Kesimpulan
Secret hygiene penting karena file `.env` dapat berisi kunci yang digunakan untuk menandatangani JWT. Jika kunci tersebut bocor, pihak lain berpotensi membuat token palsu yang tampak sah. Token juga tidak boleh disimpan utuh dalam laporan atau kode client; gunakan placeholder dan samarkan bukti.

## Bukti yang perlu dilampirkan
- [ ] Screenshot hasil pemeriksaan `.env` tidak terlacak.
- [ ] Screenshot hasil pencarian token (pastikan token asli tidak tampak).
- [ ] Catatan tindakan perbaikan jika ditemukan masalah.

**Peringatan:** perintah pemeriksaan belum dijalankan oleh paket ini. Isi hasil aktual setelah menjalankannya di repository sendiri.
