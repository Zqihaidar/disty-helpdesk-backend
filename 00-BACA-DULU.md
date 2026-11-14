# disty-helpdesk-backend/ : folder induk back-end Disty HelpDesk

Berisi semua yang berkaitan dengan server: API Laravel, API Node.js, database, deploy, tes, dan dokumentasi. Tampilan ada di folder terpisah `../disty-helpdesk-frontend`.

| Folder | Isi |
|---|---|
| `laravel/` | Berkas yang dibutuhkan Laravel agar hidup (`artisan`, `vendor/`, `composer.json`, `.env`). `public/` hanya berisi `index.php`, `.htaccess`, `uploads/` |
| `auth/`, `api/`, `admin/`, `client/`, `teknisi/`, `bersama/` | Kode aplikasi Laravel per urusan (`api/api.php` berisi rute) |
| `config/`, `database/`, `tests/` | Konfigurasi Laravel, skema dan data contoh, tes PHPUnit |
| `deploy/` | Skrip dan contoh konfigurasi server |
| `node-backend/` | Versi Node.js dari API yang sama |
| `latihan/` | Latihan PHP murni (Modul 2) |
| `postman/`, `.postman/` | Koleksi Postman |

## Kaitan dengan silabus Pemrograman Back-End
| Modul silabus | Letaknya |
|---|---|
| 2. Bahasa Pemrograman Back-End (PHP) | `latihan/php/` |
| 3. Back-End Berbasis JavaScript | `node-backend/` |
| 4. Database dan SQL (MySQL) | `database/` |
| 5. Pemrograman API | `api/`, `auth/`, `postman/` |
| 6. Framework Laravel | `laravel/`, `admin/`, `client/`, `teknisi/`, `bersama/`, `config/` |
| 7. Integrasi dengan Layanan Cloud | `deploy/`, `Dockerfile`, `docker-compose.yml` |
| 8. Integrasi Back-End dengan Front-End | `config/cors.php`, `README.md` bagian Endpoint |
| 9. Version Control (Git) | Dikerjakan pada repositori proyek |
| 10. Uji Coba dan Implementasi | `tests/`, `node-backend/tests/` |
| 11. Dokumentasi dan Pelaporan | `README.md`, `CLAUDE.md`, `database/ERD_DISTY_1.drawio` |

## Setelah dipisah dari front-end
- `laravel/public/` tidak lagi berisi `index.html`, `login.html`, `helpdesk/`, `assets/`, `css/`, `vendor/`. Semuanya pindah ke `../disty-helpdesk-frontend`.
- Frontend di domain lain: isi `CORS_ORIGIN` di `laravel/.env` (atau `node-backend/.env`) dengan alamat frontend, lalu isi `config.js` di frontend dengan alamat API ini.
- Mau satu server seperti sebelumnya: salin ISI folder frontend (bukan folder-nya) ke `laravel/public/`. Dengan begitu `php artisan serve`, Nginx, Apache, skrip `deploy/`, dan Node (`PUBLIC_DIR`) bekerja seperti semula.
- Tes Node di `node-backend/tests/integrasi/api.test.js` (pemeriksaan berkas statis `/`, `/index.html`, `/login.html`) hanya lulus bila frontend sudah disalin ke `laravel/public/`.
- `README.md` dan `CLAUDE.md` masih menyebut struktur lama (`laravel/public/helpdesk/...` dan `../disty-helpdesk-frontend/docs/API-KONTRAK.md`). Isinya tidak diubah. `docs/` tidak ada di zip asli.
