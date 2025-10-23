# 🌐 Sistem Informasi Frontpage

Fullstack Application (Next.js + Express.js + MySQL + Prisma)

---

## 📘 Deskripsi Proyek

Proyek ini merupakan aplikasi berbasis web yang terdiri atas dua komponen utama:

1. Frontend — dibangun menggunakan Next.js (TypeScript) untuk menampilkan antarmuka pengguna.
2. Backend — menggunakan Express.js (TypeScript) yang terhubung ke basis data MySQL melalui Prisma ORM.

Struktur proyek ini mendukung pengembangan modular di mana frontend dan backend dikelola secara terpisah dalam subfolder tersendiri.

---

## 🖼️ Tampilan Halaman
-  Login
   ![Image 1](/image/image1.png)

-  Login & Signup versi mobile
   ![Image 2](/image/image2.png)
   ![Image 3](/image/image3.png)

-  Dashboard
   ![Image 4](/image/image4.png)
   ![Image 5](/image/image5.png)

-  Dashboard versi mobile
   ![Image 6](/image/image6.png)
   ![Image 7](/image/image7.png)
   ![Image 8](/image/image8.png)

-  Dashboard darkmode
   ![Image 9](/image/image9.png)
   ![Image 10](/image/image10.png)

-  Dashboard darkmode versi mobile
   ![Image 11](/image/image11.png)
   ![Image 12](/image/image12.png)
   ![Image 13](/image/image13.png)

---

## 🧩 Struktur Direktori

```
project-root/
├── frontend/     → Next.js (TypeScript)
├── backend/      → Express.js (TypeScript + Prisma)
└── docker-compose.yml
```

---

## 🚀 Bagian 1 — Menjalankan dengan Docker (Direkomendasikan)

### 1. Instalasi Awal

a. Unduh dan Instal Docker

- Buka situs resmi Docker: https://www.docker.com/products/docker-desktop
- Pilih versi sesuai sistem operasi (Windows / macOS / Linux)
- Setelah instalasi selesai login dengan akun yang ingin digunakan
- pastikan Docker Desktop sudah berjalan

> Anda juga harus menginstal WSL (Windows Subsystem for Linux), jika ketika anda menginstall docker kemudian diminta untuk menginstall WSL, anda harus menerima permintaan tersebut atau juga bisa dilakukan instalasi WSL secara manual yang dapat diakses pada link berikut: https://learn.microsoft.com/en-us/windows/wsl/install.

b. Verifikasi Instalasi

```
docker --version
```

Jika muncul versi Docker, instalasi berhasil.

### 2. Kloning Repositori

```
git clone --recurse-submodules https://github.com/HowdyHowe/frontpage.git
cd frontpage
```

Repositori ini berisi dua folder utama: frontend dan backend.

### 3. Menjalankan Seluruh Sistem dengan Docker Compose

Pastikan Anda berada di folder "/frontpage", lalu jalankan:

```
docker-compose -f docker-compose.dev.yml up --build
```

Perintah ini akan melakukan beberapa hal otomatis:

1. Membangun image backend dan frontend
2. Menginstal semua dependensi (npm install)
3. Menjalankan database MySQL, backend, dan frontend dalam container terpisah

> catatan: Waktu yang digunakan untuk membangun project bervariasi, dan sangat bergantung dengan kecepatan jaringan atau performa device yang digunakan, estimasi waktu untuk membangun project adalah 10-20 menit dalam kondisi normal. Dan juga perfoma dari website juga sangat bergantung dengan performa dari device yang digunakan.

### 4. Akses Aplikasi

Akses frontend dari aplikasi untuk melihat website.

- Frontend (Next.js): http://localhost:3000
- Backend (Express.js API): http://localhost:5000
- Database (MySQL): localhost:3306

> catatan: Beberapa halaman mungkin akan terasa berat dan memuat sedikit lama, itu dikarenakan penggunaan docker dalam mode development. Tetapi biasanya setelah dimuat halaman tersebut, maka saat kembali lagi akan lebih cepat karena sudah masuk ke cache.

### 5. Penghentian Layanan

```
docker compose down
atau
ctrl + c
```

---

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

---

## 🧠 Ringkasan Jalur Akses

| Komponen | Alamat Lokal          | Deskripsi                            |
| -------- | --------------------- | ------------------------------------ |
| Frontend | http://localhost:3000 | Tampilan antarmuka utama pengguna    |
| Backend  | http://localhost:5000 | API utama aplikasi                   |
| Database | localhost:3306        | Server MySQL (via XAMPP atau Docker) |

---

## 🧠 Tech Stack

Frontend:

- Next.js (TypeScript)
- TailwindCSS
- Axios (untuk komunikasi API)

Backend:

- Express.js (TypeScript)
- Prisma ORM
- MySQL (melalui XAMPP atau Docker)
- dotenv, cors, morgan

Tools & Infrastruktur:

- Docker & Docker Compose
- Git Submodules
- Node.js v22.x

---

## 🏗️ Arsitektur Sistem

Proyek ini menggunakan arsitektur client-server di mana:

Frontend (Client):
Bertanggung jawab menampilkan antarmuka pengguna dan mengirimkan permintaan HTTP ke server backend.

Backend (Server):
Menerima permintaan dari frontend, mengelola logika bisnis, dan melakukan interaksi dengan database MySQL.

Database (MySQL):
Menyimpan data utama seperti pengguna, artikel, dan kategori film (atau konten terkait aplikasi).

Alur data:
Frontend (Next.js) → Backend (Express.js) → Database (MySQL)

---

## ✅ Kesimpulan

Anda dapat memilih dua cara untuk menjalankan proyek:

1. Menggunakan Docker — direkomendasikan untuk kemudahan setup.
2. Manual Setup dengan XAMPP — jika Docker tidak berfungsi.

---

## ⚙️ Tips dan Pemecahan Masalah

- Jika @prisma/client error, jalankan ulang: npm run prisma:generate.
- Pastikan MySQL aktif sebelum menjalankan backend.
- Jika port 3000 atau 5000 sudah digunakan, ubah di file .env masing-masing proyek.
- "npm error code ECONNRESET" adalah error yang terjadi dikarenakan masalah pada jaringan internet anda.

---

## 🧾 Lisensi

Anda dapat memodifikasi dan menggunakan proyek ini untuk kebutuhan pribadi atau penelitian.

© 2025 - Fullstack Frontpage Application
