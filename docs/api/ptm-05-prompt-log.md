# Log Prompting & Iterasi AI (PTM-05)

## 1. Riwayat Prompting

| No | Target Prompt | Alat AI & Versi | Ringkasan Prompt | Kualitas Output (1-5) | Revisi Manual |
|---|---|---|---|---|---|
| 1 | D.1 OpenAPI | ChatGPT / Gemini | Generasi draf `openapi.yaml` dari LLD PTM-04 untuk fitur TKA Fisher-Yates. | 5 | Menyesuaikan response code 400 dan tag `AI` pada endpoint pengacakan. |
| 2 | D.2 ERD / Prisma | ChatGPT / Gemini | Generasi ERD Mermaid dan `schema.prisma` yang konsisten dengan OpenAPI. | 5 | Menambahkan constraint cascade pada hapus opsi soal. |

## 2. Asumsi yang Ditandai [ASUMSI-XX]

| Kode Asumsi | Isi Asumsi | Verifikasi Tim |
|---|---|---|
| ASUMSI-01 | Pengacakan diproses secara in-memory di server Express.js. | Benar |
| ASUMSI-02 | Format nilai evaluasi menggunakan tipe skalar decimal (0.00-100.00). | Benar |
