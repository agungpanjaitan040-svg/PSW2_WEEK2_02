# Catatan Pengujian Praktikum Sesi 02

**Mata Kuliah:** Pengembangan Situs Web I (41426012)  
**Topik:** Struktur Dokumen dan Elemen Semantik HTML

---

## 1. Pemeriksaan Melalui DevTools (Nomor 9)

Pemeriksaan dilakukan menggunakan DevTools (F12 / Ctrl+Shift+I) pada tab Elements dan pengujian navigasi secara interaktif di peramban.

| Pemeriksaan           | Bukti yang Dicatat                                                                                            | Hasil |
| :-------------------- | :------------------------------------------------------------------------------------------------------------ | :---- |
| **Bahasa dokumen**    | Tag `<html>` memiliki atribut `lang="id"` pada awal baris kode.                                               | Lulus |
| **Judul halaman**     | Teks `<title>` muncul dengan benar pada tab peramban ("Profil Organisasi Mahasiswa").                         | Lulus |
| **Hierarki heading**  | Urutan heading tersusun secara berjenjang dan logis dari `<h1>`, `<h2>`, hingga `<h3>`.                       | Lulus |
| **Landmark semantik** | Elemen semantik `<header>`, `<nav>`, `<main>`, `<aside>`, dan `<footer>` terletak langsung di dalam `<body>`. | Lulus |
| **Navigasi halaman**  | Tautan menu navigasi bergerak/menggulir langsung ke elemen dengan atribut `id` yang bersesuaian saat diklik.  | Lulus |

---

## 2. Hasil Validasi HTML (Nomor 10)

Pengujian validasi struktur kode menggunakan W3C Nu HTML Checker (`https://validator.w3.org/nu/`).

- **Hasil Awal (Sebelum Perbaikan):**
  - _Status:_ Ditemukan peringatan/error kecil pada penutupan tag serta kesesuaian atribut tautan saat pertama kali diuji.
  - _Tindakan:_ Membaca baris dan pesan kesalahan yang tertera pada validator, lalu memperbaikinya pada berkas `index.html`.
- **Hasil Akhir (Setelah Perbaikan):**
  - _Status:_ **"Document checking completed. No errors or warnings to show."**
  - _Keterangan:_ Seluruh dokumen HTML5 telah memenuhi standar sintaks dan semantik yang valid.
    _(Tangkapan layar hasil awal dan akhir disimpan pada folder dokumentasi)._

---

## 3. Eksperimen Terarah (Nomor 11)

Tabel berikut mendokumentasikan pengujian sengaja (merusak struktur untuk melihat perilaku peramban/validator) beserta analisis penyebab dan solusinya:

| Gejala                                          | Bukti                                                                                        | Penyebab                                                                | Perbaikan                                                                                     | Hasil    |
| :---------------------------------------------- | :------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------- | :------- |
| Struktur pohon DOM menjadi tidak beraturan      | Pada tab Elements di DevTools, elemen-elemen setelahnya masuk/bersarang ke dalam `<article>` | Tag penutup `</article>` dihapus secara sengaja                         | Menambahkan kembali tag penutup `</article>` pada akhir blok artikel                          | Berhasil |
| Tautan navigasi tidak merespons posisi tujuan   | URL peramban berubah memuat `#kegiatan`, tetapi tampilan layar tidak berpindah               | Nilai atribut `href="#kegiatan"` tidak cocok karena `id` section diubah | Mengembalikan nilai atribut `id` pada `<section>` agar persis sama dengan nilai `href`        | Berhasil |
| Tingkatan heading melompat/tidak berurutan      | Ditemukan elemen `<h4>` langsung di bawah `<h2>` tanpa tingkatan `<h3>`                      | Melewatkan tingkatan hierarki heading tingkat 3                         | Mengubah struktur heading agar bertingkat secara runtut (`<h2>` -> `<h3>` -> `<h4>`)          | Berhasil |
| Validator W3C menampilkan pesan galat (_Error_) | Pesan validator menyatakan elemen `main` tidak boleh menjadi turunan dari `header`           | Tag `<main>` disarangkan ke dalam tag `<header>`                        | Memindahkan tag `<main>` keluar dari `<header>` dan menempatkannya langsung di bawah `<body>` | Berhasil |
