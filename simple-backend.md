# Judul Materi

> 🏠 [Beranda](README.md)
---

<!-- Isi materi -->
Baik. Kita akan membuat backend CRUD sederhana menggunakan:

* **Express**
* **TypeScript**
* **pnpm**
* Data disimpan sementara di memory (nanti bisa diganti ke database atau JSON).

## 1. Inisialisasi Project

```bash
mkdir backend
cd backend

pnpm init

pnpm add express cors

pnpm add -D typescript tsx @types/node @types/express @types/cors
```

Buat `tsconfig.json`

```bash
npx tsc --init
```

Lalu ubah menjadi:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src"]
}
```

---

## 2. Struktur Folder

```
backend
│
├── src
│   ├── index.ts
│   ├── routes
│   │     └── barang.route.ts
│   ├── controllers
│   │     └── barang.controller.ts
│   ├── data
│   │     └── barang.data.ts
│   └── types
│         └── barang.ts
│
├── package.json
└── tsconfig.json
```

---

## 3. package.json

Tambahkan script

```json
{
  "scripts": {
    "dev": "tsx watch src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js"
  }
}
```

---

## 4. Type

`src/types/barang.ts`

```ts
export interface Barang {
  id: string;
  nama: string;
  hargaBeli: number;
  hargaJual: number;
}
```

> Saya menggunakan `hargaBeli` dan `hargaJual` karena properti dengan tanda `-` (`harga-beli`) kurang nyaman digunakan di TypeScript/JavaScript.

---

## 5. Data

`src/data/barang.data.ts`

```ts
import { Barang } from "../types/barang";

export const barang: Barang[] = [
  {
    id: "1",
    nama: "Pulsa XL",
    hargaBeli: 9500,
    hargaJual: 10000,
  },
];
```

---

## 6. Controller

`src/controllers/barang.controller.ts`

```ts
import { Request, Response } from "express";
import { barang } from "../data/barang.data";
import { Barang } from "../types/barang";

export const getBarang = (_: Request, res: Response) => {
  res.json(barang);
};

export const getBarangById = (req: Request, res: Response) => {
  const data = barang.find((b) => b.id === req.params.id);

  if (!data) {
    return res.status(404).json({
      message: "Barang tidak ditemukan",
    });
  }

  res.json(data);
};

export const createBarang = (req: Request, res: Response) => {
  const body: Barang = req.body;

  barang.push(body);

  res.status(201).json(body);
};

export const updateBarang = (req: Request, res: Response) => {
  const index = barang.findIndex((b) => b.id === req.params.id);

  if (index === -1) {
    return res.status(404).json({
      message: "Barang tidak ditemukan",
    });
  }

  barang[index] = {
    ...barang[index],
    ...req.body,
  };

  res.json(barang[index]);
};

export const deleteBarang = (req: Request, res: Response) => {
  const index = barang.findIndex((b) => b.id === req.params.id);

  if (index === -1) {
    return res.status(404).json({
      message: "Barang tidak ditemukan",
    });
  }

  barang.splice(index, 1);

  res.json({
    message: "Barang berhasil dihapus",
  });
};
```

---

## 7. Route

`src/routes/barang.route.ts`

```ts
import { Router } from "express";
import {
  createBarang,
  deleteBarang,
  getBarang,
  getBarangById,
  updateBarang,
} from "../controllers/barang.controller";

const router = Router();

router.get("/", getBarang);
router.get("/:id", getBarangById);
router.post("/", createBarang);
router.put("/:id", updateBarang);
router.delete("/:id", deleteBarang);

export default router;
```

---

## 8. Server

`src/index.ts`

```ts
import express from "express";
import cors from "cors";
import barangRoute from "./routes/barang.route";

const app = express();

app.use(cors());
app.use(express.json());

app.use("/barang", barangRoute);

app.get("/", (_, res) => {
  res.json({
    message: "API berjalan 🚀",
  });
});

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

---

## 9. Jalankan

```bash
pnpm dev
```

Server akan berjalan di

```
http://localhost:3000
```

---

## Endpoint CRUD

### GET semua barang

```
GET /barang
```

---

### GET berdasarkan id

```
GET /barang/1
```

---

### POST

```
POST /barang
```

Body

```json
{
  "id": "2",
  "nama": "Pulsa Telkomsel",
  "hargaBeli": 19000,
  "hargaJual": 20000
}
```

---

### PUT

```
PUT /barang/2
```

Body

```json
{
  "nama": "Pulsa Telkomsel 20K",
  "hargaJual": 21000
}
```

---

### DELETE

```
DELETE /barang/2
```

## Pengembangan selanjutnya

Struktur ini sudah cukup rapi untuk berkembang. Tahap berikutnya yang biasanya ditambahkan adalah:

* validasi request menggunakan **Zod**,
* pemisahan menjadi **service layer** (`controller → service → repository`),
* penggunaan database seperti **SQLite**, **PostgreSQL**, atau **MySQL** melalui **Prisma ORM**,
* penanganan error terpusat (global error handler).

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#judul-materi)
