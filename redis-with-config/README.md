# Configuration File
- Saat menjalankan redis, redis tidak butuh file konfigurasi
- Namun jika tidak menggunakan file konfigurasi, redis akan berjalan menggunakan konfigurasi default
- Ada baiknya kita membuat file konfigurasi agar pengaturannya bisa diubah
- https://github.com/antirez/redis/blob/6.0/redis.conf

# Menjalankan Redis dengan Docker
- Docker compose: https://github.com/Sandydht/belajar-redis/blob/master/redis-with-config/docker-compose.yaml

# Jalankan perintah
- docker compose -f docker-compose.yaml up -d