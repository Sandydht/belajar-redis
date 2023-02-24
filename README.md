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
- redis-cli -h (host) -p (port)

## Configuration File
- Saat menjalankan redis, redis tidak butuh file konfigurasi
- Namun jika tidak menggunakan file konfigurasi, redis akan berjalan menggunakan konfigurasi default
- Ada baiknya kita membuat file konfigurasi agar pengaturannya bisa diubah
- https://github.com/antirez/redis/blob/6.0/redis.conf

## Menjalankan Redis dengan Docker
- Docker compose: https://github.com/Sandydht/belajar-redis/blob/master/redis-with-config/docker-compose.yaml
- Jalankan perintah: docker compose -f docker-compose.yaml up -d

## Database
- Redis memiliki konsep database seperti pada relational database mysql atau postgre
- Di redis kita bisa membuat database dan menggunakan database nya
- Namun sedikit berbeda, jika di relational database kita bisa membuat database dengan menggunakan nama database, di redis kita hanya bisa menggunakan angka sebagai database
- Secara default database di redis adala 0 (nol)
- Kita bisa menggunakan database sejumlah maksimal sesuai dengan konfigurasi yang kita gunakan di file konfigurasi

## Operasi Database
- select database -> Selecting database number

## Struktur Data Redis
- Redis mendukung struktur data yang banyak, seperti String, List, Set, dan lain - lain
- Namun yang paling sering digunakan adalah struktur data String

## Operasi Data String
- set key value -> Set the string value of a key
- get key -> Get the value of a key
- exists key -> Determine if a key exists
- del key [key...] -> Delete a key
- append key value -> Append a value to a key
- key pattern -> Find all keys matching the given pattern

## Operasi Range Data String
- setrange key offset value -> Overwrite part of a string at key starting at the specified offset
- getrange key start end -> Get a substring of the string stored at a key

## Operasi Multiple Data String
- mget key [key...] -> Get the values of all the given keys
- mset key value [key value...] -> Set multiple keys to multiple values

## Expiration
- Secara default saat kita menyimpan data ke redis, redis akan menyimpannya secara permanen sampai kita menghapusnya
- Kadang kita mendapatkan kasus ingin menghapus data di redis secara otomatis dalam waktu tertentu
- Misal kita menyimpan data cache di redis selama 10 menit, setelah 10 menit kita akan query ulang ke database untuk mendapatkan data terbaru
- Hal ini bisa dilakukan di redis, redis memiliki fitur expiration secara otomatis pada data yang kita simpan di redis

## Operasi Expiration Data String
- expire key seconds -> Set a key's time to live in seconds
- setex key seconds value -> Set the value and expiration of a key
- ttl key -> Get the time to live for a key

## Increment && Decrement
- Operasi increment & decrement sekilas sangat mudah dilakukan, hanya tinggal mengupdate data yang di redis dengan data baru (data lama ditambah 1)
- Namun jika operasi dilakukan secara paralel dan dalam waktu yang sangat cepat, hal ini bisa memungkinkan race condition
- Untungnya redis memiliki operasi untuk melakukan increment & decrement

## Manual Increment & Decrement (Tidak Aman)
- value = GET key
- value = value + 1
- SET key value

## Operasi Increment & Decrement
- incr key -> Increment the integer value of a key by one
- decr key -> Decrement the integer value of a key by one
- incrby key increment -> Increment the integer value of a key by the given amount
- decrby key decrement -> Decrement the integer value of a key by the given amount

## Flush
- Kadang kita perlu mengosongkan seluruh data di redis, misal ketika terjadi kesalahan kode sehingga menyebabkan data di redis salah
- Menghapus data di redis satu - satu menggunakan operasi delete bukanlah hal yang bijak
- Redis memiliki fitur untuk menghapus seluruh data di database redis, yaitu operasi flush

## Operasi Flush
- flushdb -> Remove all keys from the current database
- flushall -> Remove all keys from all databases



# Referensi
- https://redis.io/
- https://www.youtube.com/watch?v=YIBDd-nG3hc&list=PL-CtdCApEFH-7hBhz1Q-4rKIQntJoBNX3

# CATATAN
- DISARANKAN UNTUK MEMPELAJARI DOCKER TERLEBIH DAHULU
