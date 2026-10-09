# Log Prompting Implementasi & Unit Testing (PTM-06)

## 1. Catatan Prompting

| No | Target Prompt | Alat AI & Versi | Ringkasan Prompt | Kualitas Output (1-5) | Revisi Manual |
|---|---|---|---|---|---|
| 1 | Implementasi Fisher-Yates | ChatGPT / Gemini 1.5 | Buat fungsi TypeScript untuk algoritma Fisher-Yates Shuffle yang mengacak array soal dan opsi. | 5 | Menambahkan clone array agar tidak memutasi array asli secara langsung. |
| 2 | Integration & Fallback Test | ChatGPT / Gemini 1.5 | Buat skenario pengujian unit test dan penanganan fallback saat array kosong. | 5 | Memastikan tipe generik `<T>` mendukung struktur objek soal dan opsi. |

## 2. Ringkasan Asumsi
- **ASUMSI-01**: Proses pengacakan dilakukan pada server Express.js sebelum payload dikirimkan ke frontend.
- **ASUMSI-02**: Penanganan kegagalan algoritma diarahkan langsung ke mode fallback standar database.
