# 🌐 Sistem Informasi Frontpage
Fullstack Application (Next.js + Express.js + MySQL + Prisma)

## 📘 Deskripsi Proyek
Proyek ini merupakan aplikasi berbasis web yang terdiri atas dua komponen utama:

1. Frontend — dibangun menggunakan Next.js (TypeScript) untuk menampilkan antarmuka pengguna.
2. Backend — menggunakan Express.js (TypeScript) yang terhubung ke basis data MySQL melalui Prisma ORM.

Struktur proyek ini mendukung pengembangan modular di mana frontend dan backend dikelola secara terpisah dalam subfolder tersendiri.

## 🧩 Struktur Direktori
project-root/
├── frontend/     → Next.js (TypeScript)
├── backend/      → Express.js (TypeScript + Prisma)
└── docker-compose.yml

## 🚀 Bagian 1 — Menjalankan dengan Docker (Direkomendasikan)

### 1. Instalasi Awal
a. Unduh dan Instal Docker
- Buka situs resmi Docker: https://www.docker.com/products/docker-desktop
- Pilih versi sesuai sistem operasi (Windows / macOS / Linux)
- Setelah instalasi selesai login dengan akun yang ingin  digunakan
- pastikan Docker Desktop sudah berjalan

b. Verifikasi Instalasi
```
docker --version
```
Jika muncul versi Docker, instalasi berhasil.

### 2. Kloning Repositori
```
git clone git clone --recurse-submodules https://github.com/HowdyHowe/frontpage.git
cd project-root
```

Repositori ini berisi dua folder utama: frontend dan backend.

### 3. Menjalankan Seluruh Sistem dengan Docker Compose
Pastikan Anda berada di folder project-root, lalu jalankan:
```
docker-compose -f docker-compose.dev.yml up --build
```

Perintah ini akan melakukan beberapa hal otomatis:
1. Membangun image backend dan frontend
2. Menginstal semua dependensi (npm install)
3. Menjalankan database MySQL, backend, dan frontend dalam container terpisah

### 4. Akses Aplikasi
- Frontend (Next.js): http://localhost:3000
- Backend (Express.js API): http://localhost:5000
- Database (MySQL): localhost:3306

### 5. Penghentian Layanan
```
docker compose down
```

## 🧰 Bagian 2 — Alternatif Manual (Tanpa Docker)

Jika tidak ingin menggunakan Docker, jalankan frontend dan backend secara manual.

### 1. Persiapan Awal
Pastikan telah menginstal:
- Node.js (versi 22 atau lebih baru) → https://nodejs.org
- npm (biasanya sudah terpasang bersama Node.js)
- XAMPP → https://www.apachefriends.org/download.html

### 2. Mengatur MySQL di XAMPP
1. Jalankan XAMPP Control Panel
2. Aktifkan modul Apache dan MySQL
3. Klik tombol Admin di MySQL untuk membuka phpMyAdmin
4. Buat database baru bernama: frontpage
   Port default MySQL di XAMPP adalah 3306

### 3. Menjalankan Backend Secara Manual

```
cd backend
npm install
```

Buat file .env di folder backend:
DATABASE_URL="mysql://root:@localhost:3306/frontpage"
PORT=5000

Generate Prisma Client dan sinkronkan database:

```
npm run prisma:generate
npm run prisma:push
```

Jalankan server backend:
```
npm run dev
```

Backend berjalan di: http://localhost:5000

### 4. Menjalankan Frontend Secara Manual
cd ../frontend

```
npm install
```

Buat file .env.local:
NEXT_PUBLIC_API_URL=http://localhost:5000

Jalankan frontend:
```
npm run dev
```

Frontend berjalan di: http://localhost:3000

## 🧠 Ringkasan Jalur Akses
Komponen | Alamat Lokal | Deskripsi
----------|---------------|-----------
Frontend | http://localhost:3000 | Tampilan antarmuka utama pengguna
Backend  | http://localhost:5000 | API utama aplikasi
Database | localhost:3306 | Server MySQL (via XAMPP atau Docker)

## ⚙️ Tips dan Pemecahan Masalah
- Jika @prisma/client error, jalankan ulang: npm run prisma:generate
- Pastikan MySQL aktif sebelum menjalankan backend
- Jika port 3000 atau 5000 sudah digunakan, ubah di file .env masing-masing proyek

## 🧾 Lisensi
Proyek ini dikembangkan untuk tujuan pembelajaran dan pengembangan sistem informasi berbasis web.
Anda dapat memodifikasi dan menggunakan proyek ini untuk kebutuhan pribadi atau penelitian.

© 2025 - Fullstack Frontpage Application
