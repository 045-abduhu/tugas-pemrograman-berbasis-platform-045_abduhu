# Tugas Mandiri 2 — Tata Letak Responsif dengan Tailwind

## Bagian halaman
Halaman berisi navbar (Beranda, Profil, Kontak), hero “Selamat Datang”, tiga kartu (Biodata, Jadwal Kuliah, Kegiatan), dan footer.

## Class utama dan fungsinya
| Class | Fungsi |
|---|---|
| `flex` | Menyusun item navbar secara fleksibel |
| `flex-col sm:flex-row` | Navbar bertumpuk pada layar kecil dan menyamping pada layar lebih lebar |
| `grid grid-cols-1` | Menyusun hero/kartu dalam satu kolom pada layar kecil |
| `md:grid-cols-2` | Mengubah hero menjadi dua kolom pada ukuran md |
| `md:grid-cols-3` | Mengubah kumpulan kartu menjadi tiga kolom pada ukuran md |
| `gap-4` / `gap-6` | Memberi jarak antar elemen |
| `p-5`, `px-4`, `py-8` | Mengatur padding |
| `rounded-xl`, `rounded-2xl` | Membuat sudut membulat |
| `shadow-sm` | Memberi bayangan halus |
| `hover:text-blue-700` | Mengubah warna teks saat kursor diarahkan ke tautan |

## Analisis
Utility memudahkan saya mengatur jarak, warna, dan perubahan responsif langsung pada elemen HTML. Bagian yang paling mudah disusun adalah kumpulan kartu karena `grid-cols-1 gap-4 md:grid-cols-3` sudah menjelaskan susunannya. Namun, daftar class yang panjang pada satu elemen dapat membuat HTML lebih sulit dibaca sehingga perlu dirapikan.

## Bukti yang perlu ditambahkan
- [ ] Screenshot tampilan laptop.
- [ ] Screenshot tampilan viewport 360 px.

Buka file HTML di browser, lalu gunakan Developer Tools/Responsive Design Mode untuk mengatur lebar viewport ke 360 px. Tempel screenshot yang benar-benar diambil dari browser.
