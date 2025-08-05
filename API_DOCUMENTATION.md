# API Documentation - Uas2210018

## Overview
API ini dibuat untuk mengelola data tabel `uas2210018` dengan kolom `nama` dan `nobp`.

## Database Migration
File migration telah dibuat: `database/migrations/2025_08_05_170545_create_uas2210018_table.php`

### Struktur Tabel
```sql
CREATE TABLE uas2210018 (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    nama VARCHAR(255) NOT NULL,
    nobp VARCHAR(255) NOT NULL,
    created_at TIMESTAMP NULL,
    updated_at TIMESTAMP NULL
);
```

## Model
File model: `app/Models/Uas2210018.php`

### Fillable Fields
- `nama` (string)
- `nobp` (string)

## Controller
File controller: `app/Http/Controllers/Uas2210018Controller.php`

## API Endpoints

### 1. GET /api/uas2210018
**Menampilkan semua data**

**Response Success:**
```json
{
    "success": true,
    "data": [
        {
            "id": 1,
            "nama": "John Doe",
            "nobp": "2210018",
            "created_at": "2025-08-05T17:05:45.000000Z",
            "updated_at": "2025-08-05T17:05:45.000000Z"
        }
    ]
}
```

### 2. POST /api/uas2210018
**Menambah data baru**

**Request Body:**
```json
{
    "nama": "John Doe",
    "nobp": "2210018"
}
```

**Response Success (201):**
```json
{
    "success": true,
    "message": "Data berhasil ditambahkan",
    "data": {
        "id": 1,
        "nama": "John Doe",
        "nobp": "2210018",
        "created_at": "2025-08-05T17:05:45.000000Z",
        "updated_at": "2025-08-05T17:05:45.000000Z"
    }
}
```

**Response Error (422):**
```json
{
    "message": "The nama field is required.",
    "errors": {
        "nama": ["The nama field is required."],
        "nobp": ["The nobp field is required."]
    }
}
```

### 3. GET /api/uas2210018/{id}
**Menampilkan data berdasarkan ID**

**Response Success:**
```json
{
    "success": true,
    "data": {
        "id": 1,
        "nama": "John Doe",
        "nobp": "2210018",
        "created_at": "2025-08-05T17:05:45.000000Z",
        "updated_at": "2025-08-05T17:05:45.000000Z"
    }
}
```

**Response Error (404):**
```json
{
    "success": false,
    "message": "Data tidak ditemukan"
}
```

### 4. PUT /api/uas2210018/{id}
**Mengupdate data berdasarkan ID**

**Request Body:**
```json
{
    "nama": "Jane Doe",
    "nobp": "2210019"
}
```

**Response Success:**
```json
{
    "success": true,
    "message": "Data berhasil diperbarui",
    "data": {
        "id": 1,
        "nama": "Jane Doe",
        "nobp": "2210019",
        "created_at": "2025-08-05T17:05:45.000000Z",
        "updated_at": "2025-08-05T17:10:30.000000Z"
    }
}
```

**Response Error (404):**
```json
{
    "success": false,
    "message": "Data tidak ditemukan"
}
```

### 5. DELETE /api/uas2210018/{id}
**Menghapus data berdasarkan ID**

**Response Success:**
```json
{
    "success": true,
    "message": "Data berhasil dihapus"
}
```

**Response Error (404):**
```json
{
    "success": false,
    "message": "Data tidak ditemukan"
}
```

## Routes
File routes: `routes/api.php`

```php
Route::apiResource('uas2210018', Uas2210018Controller::class);
```

## Setup Instructions

### 1. Install Dependencies
```bash
composer install
```

### 2. Setup Environment
Copy file `.env.example` ke `.env` dan sesuaikan konfigurasi database.

### 3. Generate Application Key
```bash
php artisan key:generate
```

### 4. Run Migration
```bash
php artisan migrate
```

### 5. Start Server
```bash
php artisan serve
```

## Testing API

### Menggunakan cURL

**Get All Data:**
```bash
curl -X GET http://localhost:8000/api/uas2210018
```

**Create Data:**
```bash
curl -X POST http://localhost:8000/api/uas2210018 \
  -H "Content-Type: application/json" \
  -d '{"nama":"John Doe","nobp":"2210018"}'
```

**Get Data by ID:**
```bash
curl -X GET http://localhost:8000/api/uas2210018/1
```

**Update Data:**
```bash
curl -X PUT http://localhost:8000/api/uas2210018/1 \
  -H "Content-Type: application/json" \
  -d '{"nama":"Jane Doe","nobp":"2210019"}'
```

**Delete Data:**
```bash
curl -X DELETE http://localhost:8000/api/uas2210018/1
```

### Menggunakan Postman

1. Import collection dengan endpoint di atas
2. Set header `Content-Type: application/json` untuk POST dan PUT
3. Set body raw JSON untuk POST dan PUT requests

## Validation Rules

- `nama`: required, string, max 255 characters
- `nobp`: required, string, max 255 characters

## Error Handling

API ini menggunakan standard HTTP status codes:
- 200: Success
- 201: Created
- 404: Not Found
- 422: Validation Error
- 500: Server Error

Semua response menggunakan format JSON dengan struktur yang konsisten. 