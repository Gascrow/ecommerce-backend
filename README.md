# ecommerce-backend
# Dokumentasi Proyek Backend E-Commerce Kecil 🚀

## Prasyarat Sebelum Memulai
- Node.js (versi 14 atau lebih baru)
- PostgreSQL terinstal
- Git
- Postman (opsional, untuk testing API)

## Langkah-Langkah Instalasi Lengkap

### 1. Clone Repositori
```bash
# Buka terminal/command prompt
git clone [URL_REPOSITORY_GITHUB]
cd [nama-folder-project]
```

### 2. Persiapan Database PostgreSQL
#### 2.1 Buka PostgreSQL
```bash
# Masuk ke PostgreSQL
psql -U postgres
```

#### 2.2 Buat Database Baru
```sql
-- Di dalam PostgreSQL prompt
CREATE DATABASE "ecommerce-kecil";

-- Keluar dari PostgreSQL
\q
```

#### 2.3 Buat Tabel Produk
```sql
-- Masuk kembali ke database
psql -U postgres -d "ecommerce-kecil"

-- Jalankan query berikut:
CREATE TABLE produk (
    id SERIAL PRIMARY KEY,
    nama VARCHAR(255) NOT NULL,
    harga NUMERIC(10,2) NOT NULL
);
```

### 3. Konfigurasi Koneksi Database
#### Buka file `db.js` dan pastikan konfigurasi benar:
```javascript
const { Pool } = require("pg");

const pool = new Pool({
    user: "postgres",          // Username PostgreSQL
    host: "localhost",         // Host database
    database: "ecommerce-kecil", // Nama database yang dibuat
    password: "postgres",      // Password PostgreSQL
    port: 5432                 // Port default PostgreSQL
});

module.exports = pool;
```

### 4. Instalasi Dependensi
```bash
# Pastikan Anda di folder project
npm install
```

### 5. Jalankan Aplikasi
```bash
node index.js
# atau
npm start  # Jika sudah setting script di package.json
```

## Dokumentasi API 📡

### 1. Root Endpoint
- **URL**: `http://localhost:3001/`
- **Method**: GET
- **Deskripsi**: Endpoint percobaan
- **Response**: "Hello World from Express.js!"

### 2. Tambah Produk
- **URL**: `http://localhost:3001/produk`
- **Method**: POST
- **Body Request**:
```json
{
    "nama": "Nama Produk",
    "harga": 10000
}
```
- **Response**: Objek produk yang baru dibuat

### 3. Lihat Semua Produk
- **URL**: `http://localhost:3001/produk`
- **Method**: GET
- **Response**: Array dari semua produk

### 4. Update Produk
- **URL**: `http://localhost:3001/produk/:id`
- **Method**: PUT
- **Body Request**:
```json
{
    "nama": "Nama Produk Baru",
    "harga": 15000
}
```
- **Response**: Produk yang diupdate

### 5. Hapus Produk
- **URL**: `http://localhost:3001/produk/:id`
- **Method**: DELETE
- **Response**: `{ "message": "Produk dihapus" }`

## Troubleshooting 🛠️

### Masalah Umum
1. **Koneksi Database Gagal**
   - Periksa username dan password PostgreSQL
   - Pastikan PostgreSQL berjalan
   - Cek nama database

2. **Port Sudah Digunakan**
   - Ganti `PORT` di `index.js` jika perlu
   - Pastikan tidak ada aplikasi lain yang menggunakan port 3001

## Tips Tambahan
- Gunakan Postman untuk testing API
- Selalu jalankan `npm install` setelah pull repository
- Backup database secara berkala

## Kontributor
- Achmad Bayhaqi
- Muhammad Bagas Setiawan