# Dokumentasi Kontrak REST API & Keputusan Desain

## 1. Ringkasan API
Desain API dikembangkan dengan pendekatan **API-First Approach** berstandar OpenAPI 3.0. Menggunakan jalur penamaan noun jamak dan format standar JSON.

## 2. Endpoint Algoritma (Tagged: AI/Algoritma)
* **Endpoint**: `POST /api/v1/exams/:id/start`
* **Mekanisme**: Menjalankan pengacakan array soal dan opsi jawaban berbasis *Fisher-Yates Shuffle Engine* pada backend sebelum dikirim ke pengguna.
* **Fallback**: Apabila proses pengacakan bermasalah, sistem menyajikan urutan standar database secara otomatis.
