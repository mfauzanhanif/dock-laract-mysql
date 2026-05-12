# PENGGUNAAN

Tarik repo
```bash
git clone https://github.com/mfauzanhanif/dock-laract-mysql.git .
```

jalankan `docker compose up -d --build`
```bash
docker compose up -d --build
```

masuk ke container app berdasarkan docker-compose.yml atau custom sendiri
```bash
docker exec -it laravel_13_app bash
```

buat project laravel
```bash
laravel new temp-app
cp -a temp-app/. .
rm -rf temp-app
```

jalankan `npm install`
```bash
npm install
```

jalankan `npm run dev`
```bash
npm run dev
```