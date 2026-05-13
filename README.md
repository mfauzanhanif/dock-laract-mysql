# PENGGUNAAN

## Instalasi Docker
Tarik repo
```bash
git clone https://github.com/mfauzanhanif/dock-laract-mysql.git .
```

jalankan `docker compose up -d --build`
```bash
docker compose up -d --build
```

## Akses Container
masuk ke container app berdasarkan docker-compose.yml atau custom sendiri
```bash
docker exec -it laravel_app bash
```

## Instalasi Laravel
buat project laravel
```bash
laravel new app
```

## Konfigurasi `vite.config.js` di Laravel
Nanti, setelah kamu berhasil menginstal Laravel (misal `laravel new app`) dan package frontend-nya, kamu wajib mengedit file `vite.config.js` (atau `.ts`) di dalam folder Laravel tersebut agar Vite mau menerima koneksi dari luar container Docker.

Ubah konfigurasinya menjadi seperti ini:

```javascript
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import react from '@vitejs/plugin-react';

export default defineConfig({
    plugins: [
        laravel({
            input: 'resources/js/app.jsx',
            refresh: true,
        }),
        react(),
    ],
    // ---> Tambahkan blok server ini
    server: {
        host: '0.0.0.0', 
        port: 5173,
        hmr: {
            host: 'localhost'
        }
    }
});
```