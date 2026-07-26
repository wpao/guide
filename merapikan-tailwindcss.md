# Merapikan Class Tailwindcss

> 🏠 [Beranda](README.md)
---

<!-- Isi materi -->
Cara yang paling umum adalah menggunakan **Prettier + plugin Tailwind CSS**. Plugin ini akan **mengurutkan class Tailwind secara otomatis** setiap kali file disimpan.

Karena kita menggunakan **Vite + React + TypeScript + Tailwind CSS**, ini adalah solusi yang paling direkomendasikan.

## 1. Install Prettier dan plugin Tailwind

```bash
npm install -D prettier prettier-plugin-tailwindcss
```

atau

```bash
pnpm add -D prettier prettier-plugin-tailwindcss
```

---

## 2. Buat file `.prettierrc`

```json
{
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

Atau jika sudah punya konfigurasi Prettier:

```json
{
  "semi": false,
  "singleQuote": true,
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

---

## 3. VS Code

Install extension:

* **Prettier - Code formatter**

Lalu di `settings.json` tambahkan:

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true
}
```

Sekarang setiap menekan **Ctrl + S**, class Tailwind akan otomatis diurutkan.

---

## Contoh

Sebelum:

```tsx
<div className="text-white p-4 flex bg-blue-500 rounded font-bold hover:bg-blue-600 items-center justify-between">
```

Setelah Save:

```tsx
<div className="flex items-center justify-between rounded bg-blue-500 p-4 font-bold text-white hover:bg-blue-600">
```

Urutannya mengikuti standar yang dibuat oleh tim Tailwind.

---

# 4. Jika menggunakan ESLint

Install:

```bash
npm install -D eslint-plugin-tailwindcss
```

Tambahkan ke `eslint.config.js` atau `eslint.config.ts` (tergantung konfigurasi proyekmu).

Plugin ini dapat memberi peringatan jika:

* class bertabrakan
* class tidak valid
* urutan tidak sesuai

Namun untuk **mengurutkan otomatis**, Prettier tetap merupakan pilihan utama.

---

# 5. Bonus: Membuat class panjang lebih mudah dibaca

Misalnya daripada:

```tsx
<button className="flex items-center justify-center rounded-lg bg-blue-600 px-4 py-2 text-sm font-semibold text-white transition hover:bg-blue-700 disabled:cursor-not-allowed disabled:opacity-50">
```

Kamu bisa menggunakan `cn()` atau `clsx`.

Install:

```bash
npm install clsx
```

Contoh:

```tsx
import clsx from 'clsx'

<button
  className={clsx(
    'flex items-center justify-center',
    'rounded-lg bg-blue-600',
    'px-4 py-2',
    'text-sm font-semibold text-white',
    'transition hover:bg-blue-700',
    'disabled:cursor-not-allowed disabled:opacity-50'
  )}
>
  Simpan
</button>
```

Kode menjadi lebih mudah dibaca tanpa mengubah hasil akhirnya.

---

### Rekomendasi untuk stack Vite + React + TypeScript + Tailwind

Saya menyarankan kombinasi berikut:

* ✅ Prettier
* ✅ `prettier-plugin-tailwindcss`
* ✅ ESLint
* ✅ `clsx` (atau `classnames`) untuk class yang kondisional

Kombinasi ini adalah praktik yang umum dipakai pada proyek React modern dan akan membuat kode Tailwind tetap rapi secara otomatis.

---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#merapikan-class-tailwindcss)
