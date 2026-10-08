# Tugas Mandiri 5 - Membandingkan SQL Mentah dan ORM

## Identitas

- Nama: **abduhu**
- NIM: **2024520045**
- Kelas: **b**
- Pertemuan: **02**

## Tujuan

Membandingkan operasi database menggunakan SQL secara langsung dengan ORM.

Contoh tabel:

```text
jadwal
```

Struktur sederhana:

| Kolom | Tipe | Keterangan |
|---|---|---|
| `id` | INT | Primary key |
| `mata_kuliah` | VARCHAR | Nama mata kuliah |
| `status` | VARCHAR | Status jadwal |

## Operasi yang Dipilih

Operasi yang digunakan adalah **mengambil satu data berdasarkan ID**.

Kondisi:

```text
id = 1
```

# A. SQL Mentah

Contoh SQL:

```sql
SELECT *
FROM jadwal
WHERE id = ?;
```

Nilai parameter:

```text
1
```

Jika menggunakan Node.js dengan library seperti `mysql2`, konsepnya dapat ditulis:

```javascript
const [rows] = await connection.execute(
  'SELECT * FROM jadwal WHERE id = ?',
  [1]
);

console.log(rows);
```

Penggunaan parameter `?` membuat nilai input dikirim sebagai parameter query, bukan digabungkan langsung ke string SQL.

# B. ORM dengan Prisma

Contoh Prisma:

```javascript
const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});

console.log(jadwal);
```

Pada ORM, developer bekerja dengan model dan method yang disediakan Prisma. Prisma kemudian menangani penerjemahan operasi tersebut menjadi operasi database.

# C. Perbandingan

| Aspek | SQL Mentah | ORM |
|---|---|---|
| Penulisan | SQL langsung | Method/API ORM |
| Kontrol query | Sangat langsung | Melalui abstraksi ORM |
| Pemahaman SQL | Sangat diperlukan | Tetap penting |
| Integrasi model aplikasi | Lebih manual | Lebih terstruktur |
| Portabilitas | Tergantung SQL database | Dibantu abstraksi ORM |
| Kompleksitas sederhana | Relatif mudah | Relatif mudah setelah memahami ORM |
| Query kompleks | Dapat sangat fleksibel | Kadang perlu raw query |

## 1. Perbedaan cara penulisan SQL dan ORM

SQL mentah menuliskan perintah database secara langsung:

```sql
SELECT *
FROM jadwal
WHERE id = ?;
```

Sedangkan ORM menggunakan model dan method:

```javascript
prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});
```

SQL berkomunikasi langsung menggunakan bahasa SQL, sedangkan ORM memberikan lapisan abstraksi antara kode aplikasi dan database.

## 2. Kelebihan SQL mentah

Kelebihan SQL mentah adalah kontrol terhadap query lebih langsung. Developer dapat menggunakan fitur SQL secara spesifik sesuai database yang digunakan. SQL juga berguna untuk query yang kompleks dan analisis database.

## 3. Kelebihan ORM

ORM membantu developer bekerja dengan model yang lebih dekat dengan struktur kode aplikasi. ORM dapat menyediakan validasi tipe, autocomplete, relasi model, dan operasi CRUD melalui API yang konsisten.

## 4. Apa itu SQL Injection?

SQL injection adalah serangan ketika input pengguna dimanfaatkan untuk mengubah atau menyisipkan perintah SQL yang tidak seharusnya dijalankan.

Contoh pola yang berbahaya adalah ketika input langsung digabungkan ke query:

```javascript
const sql = "SELECT * FROM jadwal WHERE id = " + userInput;
```

Jika `userInput` berasal dari pengguna tanpa validasi atau parameterisasi, query dapat dimanipulasi.

Dampaknya dapat berupa pembacaan data yang tidak seharusnya, perubahan data, penghapusan data, atau tindakan lain sesuai hak akses database.

## 5. Mengapa parameter query mengurangi risiko SQL Injection?

Parameter query memisahkan nilai input dari struktur perintah SQL.

Contoh:

```sql
SELECT *
FROM jadwal
WHERE id = ?;
```

Nilai `1` diberikan sebagai parameter:

```javascript
connection.execute(
  'SELECT * FROM jadwal WHERE id = ?',
  [1]
);
```

Dengan cara tersebut, input diperlakukan sebagai nilai data, bukan sebagai bagian dari sintaks SQL.

Parameterisasi tetap harus dipakai bersama validasi input, hak akses database yang tepat, dan praktik keamanan lainnya.

## 6. Bagaimana ORM membantu pengembang?

ORM menyediakan abstraksi untuk mengakses database melalui model dan method. Pada contoh Prisma:

```javascript
const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});
```

Developer tidak perlu menulis SQL SELECT secara langsung untuk operasi sederhana tersebut. ORM mengelola penerjemahan operasi model ke query database.

Namun, ORM tidak berarti developer tidak perlu memahami SQL. Pemahaman SQL tetap diperlukan untuk memahami relasi, indeks, performa query, transaksi, dan kasus ketika query kompleks membutuhkan SQL secara langsung.

## Kesimpulan

SQL mentah memberikan kontrol langsung terhadap database, sedangkan ORM memberikan abstraksi yang membuat pengolahan data lebih terintegrasi dengan kode aplikasi. Keduanya memiliki kelebihan dan dapat digunakan sesuai kebutuhan. Parameterized query penting untuk mencegah input pengguna dianggap sebagai bagian dari sintaks SQL.

## Referensi

- Prisma Documentation: https://www.prisma.io/docs
- OWASP SQL Injection Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html
- MySQL Documentation: https://dev.mysql.com/doc/
