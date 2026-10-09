# Dokumentasi Implementasi Backend & Algoritma (PTM-06)

## 1. Arsitektur Layanan Backend
Implementasi backend menggunakan Express.js/Next.js API Routes dengan arsitektur berlapis (Controller, Service, Repository) yang terintegrasi dengan Prisma ORM untuk akses database MySQL.

## 2. Modul Algoritma Fisher-Yates Shuffle Engine
* **Lokasi Kode**: `src/lib/fisherYates.ts`
* **Metode**: `shuffleArray<T>(array: T[]): T[]`
* **Kompleksitas**: Temporal $O(n)$, Spasial $O(1)$ (in-place modification).
* **Fungsi**: Mengacak urutan array soal dan opsi jawaban secara acak murni pada level backend sebelum dikirimkan sebagai payload ujian ke frontend.

## 3. Mekanisme Fallback & Error Handling
Apabila terjadi kegagalan pemprosesan algoritma atau keterbatasan sumber daya server, sistem secara otomatis mengaktifkan mode *fallback* dengan menyajikan urutan standar berdasarkan ID database tanpa menghentikan sesi ujian siswa.
