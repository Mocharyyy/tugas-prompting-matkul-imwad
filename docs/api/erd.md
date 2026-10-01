# Diagram Entity Relationship (ERD) Final

```mermaid
erDiagram
    USERS ||--o{ EXAM_RESULTS : "memiliki"
    EXAM_SCHEDULES ||--|{ EXAM_RESULTS : "menghasilkan"
    EXAM_SCHEDULES ||--|{ QUESTION_BANK : "mengandung"
    QUESTION_BANK ||--|{ QUESTION_OPTIONS : "memiliki"

    USERS {
        string id PK
        string name
        string username
        string password_hash
        enum role "SISWA, TENTOR, PEMILIK"
    }

    QUESTION_BANK {
        string id PK
        string exam_schedule_id FK
        text question_text
    }

    QUESTION_OPTIONS {
        string id PK
        string question_id FK
        text option_text
        boolean is_correct
    }

    EXAM_RESULTS {
        string id PK
        string user_id FK
        string exam_schedule_id FK
        decimal total_score
        datetime submitted_at
    }
