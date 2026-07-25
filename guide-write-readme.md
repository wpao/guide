Karena GitHub README tidak mendukung **navbar** seperti HTML/CSS, biasanya dokumentasi menggunakan **navigation bar berbasis Markdown** di bagian atas setiap file.

Saya sarankan template seperti ini.

```md
# Judul Materi

> 🏠 [Beranda](README.md) | 📚 [Daftar Dokumentasi](README.md) | ⬅️ [Sebelumnya](../javascript/array.md) | ➡️ [Selanjutnya](use-effect.md)

---

<!-- Isi materi -->

## Apa itu?

...

---

> 🏠 [Beranda](README.md) | ⬆️ [Kembali ke Atas](#judul-materi)
```

---

Atau jika ingin lebih sederhana dan bersih:

```md
[🏠 Home](README.md) • [⬅ Previous](../javascript/array.md) • [Next ➡](use-effect.md)

---

# useMemo

...

---

[⬆ Back to Top](#usememo)
```

---

Kalau dokumentasimu akan banyak (50+ file), saya lebih menyarankan template berikut agar konsisten.

```md
[🏠 Home](README.md) • [📖 Index](README.md) • [⬆ Top](#judul-materi)

---

# Judul Materi

> Deskripsi singkat mengenai materi.

---

## Daftar Isi

- [Apa itu?](#apa-itu)
- [Sintaks](#sintaks)
- [Contoh](#contoh)
- [Best Practice](#best-practice)
- [Kesalahan Umum](#kesalahan-umum)
- [Referensi](#referensi)

---

## Apa itu?

...

## Sintaks

...

## Contoh

...

## Best Practice

...

## Kesalahan Umum

...

## Referensi

...

---

### Navigasi

- ⬅️ Sebelumnya:
- ➡️ Selanjutnya:
- 🏠 [Kembali ke Beranda](README.md)
- ⬆️ [Kembali ke Atas](#judul-materi)
```

Template ini rapi, konsisten di setiap file, dan memudahkan pembaca berpindah antar topik maupun kembali ke halaman utama.
