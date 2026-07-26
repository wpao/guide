# Judul Materi

> 🏠 [Beranda](README.md)
membuat database menggunakan docker compose
```
# for local ==================================================
services:
  database:
    image: postgres:latest
    container_name: database # nama container
    restart: always
    env_file:
      - .env
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}
    ports:
      - "${POSTGRES_PORT}:5432" # expose:container
    volumes:
      - backend_pgdata:/var/lib/postgresql/data

volumes:
  backend_pgdata:

```
---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#judul-materi)
