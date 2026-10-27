# Tugas Mandiri 1 — Perbandingan CSS Komponen dan Utility

## Tujuan
Membandingkan dua kartu biodata yang memiliki konten sama, tetapi memakai pendekatan styling berbeda.

## Ringkasan
- **Versi komponen:** gaya berada pada CSS di dalam `<style>` dengan class seperti `.card`, `.avatar`, dan `.btn`.
- **Versi utility:** gaya disusun melalui class Tailwind langsung di elemen HTML; file tidak menambahkan CSS buatan sendiri.

## Catatan pengukuran
Lengkapi kolom ini setelah membuka kedua file dan melakukan pengamatan sendiri.

| Aspek | Versi komponen | Versi utility |
|---|---|---|
| Baris CSS yang ditulis | Hitung baris aturan CSS pada bagian `<style>` | 0 baris CSS buatan sendiri |
| Jumlah class utility | Tidak berlaku sebagai pendekatan utama | Hitung class utility yang digunakan |
| Waktu pengerjaan aktual | Isi setelah mengukur | Isi setelah mengukur |
| Cara mengubah warna | Ubah aturan CSS pada `.btn`/`.card` | Ganti class warna pada elemen |
| Hasil pada viewport 360 px | Periksa dan catat | Periksa dan catat |

## Analisis
Versi komponen memisahkan tampilan dari struktur HTML sehingga satu aturan dapat dipakai ulang pada banyak kartu. Versi utility memungkinkan pengubahan tampilan secara langsung pada elemen tanpa membuat nama class CSS baru, tetapi atribut `class` dapat menjadi panjang. Untuk halaman dengan komponen berulang dan tema konsisten, pendekatan komponen membantu menjaga satu sumber aturan; untuk prototipe atau tata letak yang sering berubah, utility-first bisa lebih cepat.

## Bukti
- [ ] Screenshot versi komponen pada tampilan laptop.
- [ ] Screenshot versi komponen pada lebar 360 px.
- [ ] Screenshot versi utility pada tampilan laptop.
- [ ] Screenshot versi utility pada lebar 360 px.

**Catatan:** tempel screenshot hasil browser sendiri di bagian ini atau simpan di folder yang ditentukan dosen. Jangan mengisi waktu pengerjaan atau mengklaim screenshot yang belum dibuat.
