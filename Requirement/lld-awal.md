### **2. Dokumen 2: `docs/lld-awal.md`**

Buat file bernama **`lld-awal.md`** di dalam folder **`docs/`** dan tempelkan teks berikut[cite: 6]:

```markdown
# Low-Level Design (LLD) Awal

**Sistem Informasi Ujian Online Tes Kemampuan Akademik (TKA) Berbasis Web Menggunakan Metode Algoritma Fisher-Yates Shuffle**

---

## 1. Desain Modul & Class (Fisher-Yates Engine & Exam Controller)

### Class `FisherYatesShuffle`
* **Tanggung Jawab**: Mengacak elemen larik array (soal/opsi) secara in-place dengan kompleksitas $O(n)$.
* **Method Utama**:
  * `shuffleArray<T>(items: T[]): T[]`: Mengambil array item dan melakukan iterasi dari indeks terakhir ke awal, menukar posisi secara acak menggunakan indeks berbasis `Math.random()`.

### Class `ExamController`
* **Tanggung Jawab**: Menangani request ujian dari siswa, memanggil modul pengacakan, dan menghitung koreksi.
* **Method Utama**:
  * `startExamSession(studentId: string, examId: string): Promise<ExamSessionPayload>`
  * `submitExamAnswers(sessionId: string, answers: StudentAnswerPayload): Promise<EvaluationResult>`

---

## 2. Skema Data (MySQL Database Schema)

```sql
CREATE TABLE users (
    id VARCHAR(36) PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    role ENUM('SISWA', 'TENTOR', 'PEMILIK') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE question_bank (
    id VARCHAR(36) PRIMARY KEY,
    question_text TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE question_options (
    id VARCHAR(36) PRIMARY KEY,
    question_id VARCHAR(36) NOT NULL,
    option_text TEXT NOT NULL,
    is_correct BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (question_id) REFERENCES question_bank(id) ON DELETE CASCADE
);

CREATE TABLE exam_results (
    id VARCHAR(36) PRIMARY KEY,
    student_id VARCHAR(36) NOT NULL,
    total_score DECIMAL(5,2) NOT NULL,
    submitted_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES users(id)
);
