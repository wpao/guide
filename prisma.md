# Judul Materi

> 🏠 [Beranda](README.md)

---

<!-- Isi materi -->
ORM Prisma

backend
│
├── prisma
│   ├── schema.prisma
├── src
├── .env
├── package.json
└── tsconfig.json

<!-- 
.env
-->
isi .env
```
DATABASE_URL="postgresql://postgresuser:postgres@localhost:5434/mydatabase?schema=public"
```
```
DATABASE_URL="postgresql://{POSTGRES_USER}:{POSTGRES_PASSWORD}@localhost:{POSTGRES_PORT}/{POSTGRES_DB}?schema=public"
```


> pastikan database sudah terbuat.

```
pnpm prisma generate
pnpm prisma migrate
```

---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#judul-materi)
