# Belajar Redis

## Sejarah Redis
- Redis singkatan dari Remote Dictionary Server adalah sistem basis data key-value berbasis memory
- Pertama kali rilis tahun 2009 sebagai project open source

## Apa itu Key-Value Database ?
- Redis adalah sistem basis data key-value
- Paradigma key-value adalah paradigma dimana data disimpan dalam bentuk pair (key-value)
- Key mirip dengan primary key dari data, sedangkan value adalah isi dari datanya

## Apa Itu In-Memory Database ?
- Redis menyimpan datanya di memory, namun kita bisa memintanya untuk menyimpan secara regular permanen di disk
- Data di disk hanya dijadikan backup ketika redis berjalan ulang, selama redis berjalan, redis hanya akan melakukan manipulasi data ke memory

## Kapan Butuh Redis ?
- Saat kita membuat aplikasi, tidak langsung wajib menggunakan redis
- Redis menggunakan memory sebagai penyimpanan utama, otomatis harga memory lebih mahal dibandingkan disk
- Untuk menggunakan redis, kita perlu lihat kasusnya secara detail, sebagai contoh:
  1. Ketika database utama lambat
  2. Ketika integrasi dengan aplikasi lain lambat (third party application)
  3. Ketika ada proses berat di aplikasi, misalnya melakukan kalkulasi data
  4. Ketika membuat delayed job, misalnya scheduler untuk mengirim email
- Rata - rata redis digunakan untuk mempercepat aplikasi yang lambat
- Dan juga redis biasa digunakan untuk caching, menyimpan data secara sementara

## Menginstall Redis
- https://redis.io/download/
- Redis adalah aplikasi yang dibuat menggunakan bahasa pemrograman C
- Untuk menggunakan redis, kita harus melakukan kompilasi kode program redis nya
- Disarankan menggunakan docker untuk menjalankan redis

## Menginstall Redis via Docker
- Docker image: https://hub.docker.com/_/redis
- Docker compose: https://github.com/Sandydht/belajar-redis

## Redis Server vs Redis CLI
- Saat kita menginstal redis, ada 2 aplikasi yang terinstal, Redis Server dan Redis CLI
- Redis Server adalah aplikasi server untuk redis itu sendiri
- Redis CLI adalah aplikasi command line untuk client, dimana digunakan untuk berkomunikasi dengan redis server

## Konek ke Redis Server via Redis CLI
- redis-cli -h host -p port

## Referensi
- https://redis.io/
- https://www.youtube.com/watch?v=YIBDd-nG3hc&list=PL-CtdCApEFH-7hBhz1Q-4rKIQntJoBNX3

# CATATAN
- DISARANKAN UNTUK MEMPELAJARI DOCKER TERLEBIH DAHULU
