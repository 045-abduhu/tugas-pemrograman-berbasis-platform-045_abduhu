# Tugas Pendahuluan — Pertemuan 3
## Component-based CSS/UI Framework vs Utility-first CSS & Authentication vs Authorization

### Soal 1 — Bandingkan Bootstrap dan Tailwind
Bootstrap menyediakan komponen dengan class yang sudah memiliki gaya, misalnya `card`, `card-body`, `btn`, dan `btn-primary`. Tailwind menggunakan class utility seperti `rounded-xl`, `p-4`, `bg-white`, `text-gray-800`, dan `bg-blue-600` untuk menyusun tampilan langsung pada HTML. Menurut saya, Bootstrap lebih mudah bagi pemula yang ingin cepat mendapatkan tampilan jadi, sedangkan Tailwind lebih fleksibel ketika ingin mengatur detail desain.

### Soal 2 — Kartu biodata dengan dua pendekatan
Sketsa kartu: foto di bagian atas, nama lengkap dan NIM di bawah foto, lalu tombol **Lihat Profil**.

**Versi komponen**
```html
<div class="card">
  <img src="foto.jpg" alt="Foto mahasiswa">
  <h2>abduh</h2>
  <p>NIM: 2024520045</p>
  <button class="btn">Lihat Profil</button>
</div>
```

**Versi utility-first**
```html
<div class="mx-auto max-w-sm rounded-xl bg-white p-6 text-center shadow">
  <img class="mx-auto h-24 w-24 rounded-full object-cover"
       src="foto.jpg" alt="Foto mahasiswa">
  <h2 class="mt-4 text-xl font-bold text-gray-800">abduhu</h2>
  <p class="mt-2 text-gray-600">NIM: 2024520045</p>
  <button class="mt-4 rounded-lg bg-blue-600 px-4 py-2 text-white hover:bg-blue-700">
    Lihat Profil
  </button>
</div>
```

Pada versi komponen, aturan CSS ditulis untuk `.card`, gambar, teks, dan `.btn`; jumlah pastinya mengikuti CSS yang benar-benar dibuat. Pada versi utility, gaya disusun dari class utility pada elemen HTML. Menurut saya, warna lebih cepat diubah pada utility-first untuk satu elemen, sedangkan perubahan seragam untuk banyak kartu lebih mudah dikelola melalui satu aturan komponen bersama.

### Soal 3 — Amati isi token JWT
JWT pada contoh terdiri atas **tiga bagian** yang dipisahkan tanda titik: header, payload, dan signature. Payload contoh menampilkan klaim `sub`, `name`, dan `iat`. Password tidak boleh disimpan di payload karena payload JWT dapat dibaca oleh siapa pun yang memperoleh token; tanda tangan menjaga integritas token, bukan menyembunyikan isi payload.

### Soal 4 — Analogi gerbang kampus
Pemeriksaan di gerbang UNIRA merupakan authentication, misalnya petugas memeriksa kartu identitas untuk memastikan siapa yang masuk. Pemeriksaan di depan ruang server merupakan authorization, yaitu memastikan apakah orang yang identitasnya sudah diketahui memang memiliki izin memasuki ruangan tersebut. Mahasiswa dapat lolos pemeriksaan identitas tetapi tetap ditolak dari ruang server karena tidak memiliki hak akses.

### Soal 5 — Peran pada aplikasi nyata
Contoh aplikasi: e-library.
- **Anggota:** mencari buku dan melihat riwayat peminjaman.
- **Pustakawan:** menambah atau memperbarui katalog dan memproses peminjaman.
- **Pimpinan:** melihat laporan serta rekap pengadaan.

Jika pengguna belum login atau tidak menyertakan token yang valid, endpoint terlindungi mengembalikan **401 Unauthorized** karena identitas belum berhasil diverifikasi. Jika pengguna sudah login dengan token valid tetapi perannya tidak diizinkan menggunakan fitur tertentu, respons yang tepat adalah **403 Forbidden**.
