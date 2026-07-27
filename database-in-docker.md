# Judul Materi

> 🏠 [Beranda](README.md)

---

<!-- Isi materi -->
Jika nama file Docker Compose Anda **bukan** `docker-compose.yml` atau `compose.yml`, maka Anda harus menentukan nama filenya dengan opsi `-f`.

Misalnya file Anda bernama:

```text
docker-compose.db.yml
```

Jalankan dengan perintah:

```bash
docker compose -f docker-compose.db.yml up -d
```

Penjelasan:

* `-f docker-compose.db.yml` → menggunakan file compose tersebut.
* `up` → membuat dan menjalankan container.
* `-d` → menjalankan di background (detached).

### Jika hanya ingin membuat container

```bash
docker compose -f docker-compose.db.yml up --build -d
```

### Melihat container yang berjalan

```bash
docker ps
```

### Melihat log database

```bash
docker compose -f docker-compose.db.yml logs -f
```

### Menghentikan container

```bash
docker compose -f docker-compose.db.yml down
```

### Jika ingin menghapus volume database juga

> **Perhatian:** Ini akan menghapus seluruh data PostgreSQL yang tersimpan di volume.

```bash
docker compose -f docker-compose.db.yml down -v
```

---

Jika struktur project Anda seperti berikut:

```text
project/
├── docker-compose.db.yml
├── .env
├── prisma/
├── src/
└── package.json
```

Maka cukup jalankan dari folder `project`:

```bash
docker compose -f docker-compose.db.yml up -d
```

---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#judul-materi)
