# High-Level Design (HLD)

**Sistem Informasi Ujian Online Tes Kemampuan Akademik (TKA) Berbasis Web Menggunakan Metode Algoritma Fisher-Yates Shuffle**

---

## 1. Diagram Arsitektur Sistem (C4 Model - Level 2: Container Diagram)

```mermaid
graph TD
    user([Siswa / Tentor / Pemilik Bimbel])
    
    subgraph Client Tier [Frontend - Next.js]
        ui[Web Application UI]
        state[Client State & Session Manager]
    end

    subgraph Application Tier [Backend - Express.js Node.js]
        apiGateway[REST API Gateway / Auth Middleware]
        examService[Exam & Assessment Service]
        fyEngine[Fisher-Yates Shuffle Engine ★]
        recapService[Evaluation & Recap Service]
    end

    subgraph Data Tier [Database - MySQL]
        db[(MySQL Database)]
    end

    user -->|HTTPS / REST| ui
    ui -->|Manage State| state
    ui -->|REST API Requests| apiGateway
    apiGateway --> examService
    apiGateway --> recapService
    examService -->|Trigger Pengacakan| fyEngine
    examService -->|Read/Write Exam Data| db
    recapService -->|Query Score & Recap| db
