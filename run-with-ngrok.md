# Run Ngrok

> 🏠 [Beranda](README.md)

---
# Menjalankan project menggunakan Ngrok
## cara 1
contoh project kita di buat menggunakan vite
```bash
pnpm run dev
```
maka akan menghasilkan 
```bash
http://localhost:5173/
```
lalu buat base baru dan jalankan
```bash
ngrok http 5173
```
maka akan menghasilkan 
```bash
Account                       xxx (Plan: Free)                                                                  
Version                       3.39.1-msix-stable                                                                        
Region                        Asia Pacific (ap)                                                                         
Web Interface                 http://127.0.0.1:4040                                                                     
Forwarding                    https://650b-110-136-219-171.ngrok-free.app -> http://localhost:5173 
```
ini adalah link yang bisa anda bagikan ke semua orang 
```base 
https://650b-110-136-219-171.ngrok-free.app
```
tekan (visit site) jika mengunjungi web

jika anda menemukan pesan 
```bash
Blocked request. This host ("c15a-110-136-219-171.ngrok-free.app") is not allowed.
To allow this host, add "c15a-110-136-219-171.ngrok-free.app" to `server.allowedHosts` in vite.config.js.
```
artinya kita perlu setting file vite.config.ts untuk memberi access pada ```c15a-110-136-219-171.ngrok-free.app```
```bash
export default defineConfig({
  plugins: [react(), tailwindcss()],

  // ngrok
  server: {
    // ngrok local tes
    host: true,
    port: 5173,
    allowedHosts: true,
    // allowedHosts: [
    //   "650b-110-136-219-171.ngrok-free.app",
    // ],
  },
});
```
---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#run-ngrok)
