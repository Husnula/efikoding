# DIAGRAM ARSITEKTUR & ALUR SISTEM (MERMAID.MD)
## PLATFORM EFIKODING: MODEL SISTEM, DATA, & LOGIKA KALIBRASI PSIKOMETRIK

**Versi Dokumen:** 1.0.0  
**Standar Diagram:** Mermaid.js Standard  

---

## 1. DIAGRAM ARSITEKTUR SISTEM (SYSTEM ARCHITECTURE)

Diagram berikut mengilustrasikan struktur arsitektur *Single-File Application* yang mandiri, menghubungkan dua peran antarmuka dengan modul komputasi psikometrik lokal dan mesin AI:

```mermaid
graph TB
    subgraph ClientApp["Aplikasi Mandiri (index.html)"]
        subgraph UILayer["Lapisan Antarmuka (Tailwind CSS & Lucide Icons)"]
            RoleSwitch["Pengalih Peran (Role Switcher)"]
            StudentPortal["Portal Siswa (User Role)"]
            AdminDashboard["Dashboard Guru (Admin Role)"]
        end

        subgraph CoreLogic["Mesin Logika & Psikometrik (Vanilla JS)"]
            SurveyEngine["Mesin Angket Efikasi Diri (12 Butir Likert)"]
            QuizEngine["Mesin Tes CT & Slider Kalibrasi (Level A/B)"]
            QuickCalc["Kalkulator Diagnostik Cepat Guru"]
            PsychometricMath["Kalkulator Formula Deterministik (S_skill, S_efficacy, I_cal)"]
            QuadrantClassifier["Klasifikator 4 Kuadran (Mastery, Underconfident, Overconfident, Struggling)"]
            FallbackEngine["Mesin Narasi Deterministik Lokal (Offline Engine)"]
            ReportEditor["Modul Penyuntingan Langsung (Inline Editing)"]
            ExportModule["Modul Ekspor (MS Word .doc & Cetak PDF)"]
        end

        subgraph VisualEngine["Mesin Visualisasi Grafis"]
            CanvasQuadrant["Kanvas Render Matriks 4 Kuadran"]
        end
    end

    subgraph ExternalServices["Layanan Eksternal & API"]
        GeminiAPI["Google Gemini REST API (JSON Mode)"]
        TailwindCDN["Tailwind CSS CDN"]
        LucideCDN["Lucide Icons CDN"]
    end

    RoleSwitch --> StudentPortal
    RoleSwitch --> AdminDashboard

    StudentPortal --> SurveyEngine
    StudentPortal --> QuizEngine
    QuizEngine --> PsychometricMath
    SurveyEngine --> PsychometricMath

    AdminDashboard --> QuickCalc
    QuickCalc --> PsychometricMath

    PsychometricMath --> QuadrantClassifier
    QuadrantClassifier --> CanvasQuadrant

    QuadrantClassifier --> FallbackEngine
    QuadrantClassifier --> GeminiAPI
    GeminiAPI -.->|Respon JSON Sukses| ReportEditor
    GeminiAPI -.->|Gagal / Luring| FallbackEngine
    FallbackEngine --> ReportEditor

    ReportEditor --> ExportModule
    CanvasQuadrant --> ExportModule

    TailwindCDN -.-> UILayer
    LucideCDN -.-> UILayer
```

---

## 2. DIAGRAM ALUR PENGGUNA SISWA (STUDENT USER JOURNEY)

Alur pengerjaan kuis siswa dari *onboarding*, pengisian angket efikasi baku, pengerjaan soal CT dengan slider keyakinan per soal, hingga penerimaan kartu refleksi *growth mindset*:

```mermaid
flowchart TD
    Start([Siswa Membuka Aplikasi]) --> InputData[Isi Nama Lengkap & Pilih Kelas]
    InputData --> SelectLevel{Pilih Paket Asesmen}
    
    SelectLevel -->|Level A: Unplugged| IntroA[Mulai Level A: Logika & Pola Dasar]
    SelectLevel -->|Level B: Plugged| IntroB[Mulai Level B: Algoritma & Pseudocode]
    
    IntroA --> Survey12[Sesi 1: Pengisian 12 Butir Angket Efikasi Diri]
    IntroB --> Survey12
    
    Survey12 --> CTQuestions[Sesi 2: Menjawab 4 Soal Berpikir Komputasional]
    
    subgraph LoopSoal["Perulangan Setiap Butir Soal CT"]
        PilihJawaban[Pilih Opsi Jawaban A, B, C, atau D]
        GeserSlider[Atur Task-Specific Confidence Slider 1-5: 20% s/d 100%]
        PilihJawaban --> GeserSlider
    end
    
    CTQuestions --> LoopSoal
    LoopSoal --> SelesaiSoal{Semua Soal Terjawab?}
    SelesaiSoal -->|Belum| LoopSoal
    SelesaiSoal -->|Sudah| HitungPsikometrik[Kalkulasi Otomatis S_skill, S_efficacy, I_cal]
    
    HitungPsikometrik --> StudentReport[Tampilkan Lembar Hasil Reflektif Siswa]
    StudentReport --> GrowthMindsetCard[Tampilkan Kartu Motivasi & Growth Mindset]
    GrowthMindsetCard --> Selesai([Siswa Menyelesaikan Sesi])
```

---

## 3. DIAGRAM ALUR GURU & LOGIKA GENERATOR (ADMIN WORKFLOW)

Alur komprehensif bagi guru pengampu saat menggunakan dashboard split-screen, melakukan input cepat (*fast calculator*), memicu AI atau *fallback*, menyunting teks, dan mencetak dokumen:

```mermaid
flowchart TD
    AdminStart([Guru Membuka Dashboard Admin]) --> PilihModeInput{Sumber Data Siswa}
    
    PilihModeInput -->|Hasil Sesi Siswa| MuatDataSiswa[Muat Data dari Sesi Tes Siswa]
    PilihModeInput -->|Input Kilat Guru| ManualInput[Masukkan Nama, Skor 4 Domain CT, & Rata-rata Angket]
    
    MuatDataSiswa --> KalkulasiLokal[Eksekusi Formula S_skill, S_efficacy, & I_cal]
    ManualInput --> KalkulasiLokal
    
    KalkulasiLokal --> PlotKuadran[Render Titik Koordinat pada Matriks 4 Kuadran]
    PlotKuadran --> CekJaringan{Pilih Mesin Narasi & Koneksi}
    
    CekJaringan -->|Gunakan Gemini API & Daring| CallGemini[Kirim Data JSON & SYSTEM_PROMPT ke Gemini]
    CekJaringan -->|Luring / Fallback Dipilih| RunFallback[Eksekusi Mesin Narasi Deterministik Lokal]
    
    CallGemini --> EvalResponse{Respon JSON Valid?}
    EvalResponse -->|Ya| ParseJSON[Ekstrak Ringkasan, Profil Lulusan, & Rekomendasi]
    EvalResponse -->|Tidak / Error| RunFallback
    
    ParseJSON --> RenderPreview[Tampilkan Lembar Pratinjau Dokumen Laporan Resmi]
    RunFallback --> RenderPreview
    
    RenderPreview --> InlineEdit[Guru Melakukan Inline Editing Teks Jika Diperlukan]
    InlineEdit --> ExportChoice{Pilihan Ekspor}
    
    ExportChoice -->|Unduh Dokumen Word| GenWord[Hasilkan Berkas .doc dengan Format Kop Resmi]
    ExportChoice -->|Cetak / Simpan PDF| PrintPDF[Cetak Dokumen A4 dengan CSS @media print]
    
    GenWord --> SelesaiAdmin([Laporan Resmi Siap Digunakan])
    PrintPDF --> SelesaiAdmin
```

---

## 4. POHON KEPUTUSAN KALIBRASI PSIKOMETRIK & 4 KUADRAN (DECISION TREE)

Logika deterministik yang menentukan kuadran dan strategi intervensi pedagogis:

```mermaid
flowchart TD
    Root([Mulai Evaluasi Psikometrik]) --> CheckSkill{Apakah S_skill >= 70?}
    
    CheckSkill -->|Ya: High Skill| CheckEffHigh{Apakah S_efficacy >= 70?}
    CheckSkill -->|Tidak: Low Skill| CheckEffLow{Apakah S_efficacy >= 70?}
    
    CheckEffHigh -->|Ya| Q1_Mastery["KUADRAN 1: MASTERY<br/>(High Skill, High Efficacy)<br/>Intervensi: Open-ended project & Peer Mentor"]
    CheckEffHigh -->|Tidak| Q2_Underconfident["KUADRAN 2: UNDERCONFIDENT<br/>(High Skill, Low Efficacy atau I_cal < -15)<br/>Intervensi: Validasi proses berpikir & Kurangi batas waktu"]
    
    CheckEffLow -->|Ya| Q3_Overconfident["KUADRAN 3: OVERCONFIDENT<br/>(Low Skill, High Efficacy atau I_cal > +15)<br/>Intervensi: Uji kasus batas (edge-case) & Trace table"]
    CheckEffLow -->|Tidak| Q4_Struggling["KUADRAN 4: STRUGGLING<br/>(Low Skill, Low Efficacy)<br/>Intervensi: Micro-scaffolding & Aktivitas Unplugged konkret"]

    Q1_Mastery --> CalCheck[Evaluasi Indeks Kalibrasi Metakognitif: I_cal = S_efficacy - S_skill]
    Q2_Underconfident --> CalCheck
    Q3_Overconfident --> CalCheck
    Q4_Struggling --> CalCheck

    CalCheck --> CalCat{-15 <= I_cal <= +15?}
    CalCat -->|Ya| WellCal[Status Kalibrasi: Akurat / Well-Calibrated]
    CalCat -->|I_cal > +15| BiasOver[Status Kalibrasi: Bias Keyakinan Berlebih / Overconfident]
    CalCat -->|I_cal < -15| BiasUnder[Status Kalibrasi: Bias Keraguan Diri / Underconfident]
```

---

## 5. DIAGRAM STATUS APLIKASI (STATE MACHINE)

Transisi status aplikasi selama sesi berlangsung:

```mermaid
stateDiagram-v2
    [*] --> IdleSelectRole : Aplikasi Dimuat

    state PortalSiswa {
        [*] --> StudentProfile
        StudentProfile --> SurveySession : Konfirmasi Identitas & Level
        SurveySession --> QuizSession : 12 Butir Angket Terisi
        QuizSession --> CalculatingResult : Soal CT & Slider Selesai
        CalculatingResult --> StudentResult : Skor & Refleksi Ditampilkan
        StudentResult --> [*]
    }

    state DashboardAdmin {
        [*] --> DashboardOverview
        DashboardOverview --> FastCalcMode : Buka Mode Input Kilat Guru
        DashboardOverview --> QuestionBankView : Buka Pratinjau Bank Soal
        
        FastCalcMode --> GeneratingAI : Klik Pemicu AI
        FastCalcMode --> GeneratingFallback : Klik Mesin Fallback Lokal
        
        GeneratingAI --> PreviewReport : Respon JSON Sukses
        GeneratingAI --> GeneratingFallback : Gagal / Timeout
        GeneratingFallback --> PreviewReport : Template Deterministik Terbentuk

        PreviewReport --> InlineEditingState : Guru Mengklik Teks Laporan
        InlineEditingState --> PreviewReport : Simpan Teks Lokal
        PreviewReport --> ExportingWord : Unduh File .doc
        PreviewReport --> PrintingPDF : Dialog Cetak Browser
    }

    IdleSelectRole --> PortalSiswa : Pilih Mode Siswa
    IdleSelectRole --> DashboardAdmin : Pilih Mode Guru
    PortalSiswa --> DashboardAdmin : Alihkan ke Mode Guru
    DashboardAdmin --> PortalSiswa : Alihkan ke Mode Siswa
```

---

## 6. DIAGRAM MODEL DATA & ENTITAS (ENTITY-RELATIONSHIP MODEL)

Struktur data internal yang dikelola di dalam memori lokal aplikasi:

```mermaid
erDiagram
    PROFIL_SISWA ||--o{ SESI_ANGKET : mengisi
    PROFIL_SISWA ||--o{ JAWABAN_SOAL_CT : menjawab
    PROFIL_SISWA ||--|| SKOR_PSIKOMETRIK : menghasilkan
    SKOR_PSIKOMETRIK ||--|| LAPORAN_DIAGNOSTIK : mendasari

    PROFIL_SISWA {
        string id_siswa
        string nama_lengkap
        string kelas_rombel
        string paket_level "Level A (Unplugged) / Level B (Plugged)"
        datetime tanggal_asesmen
    }

    SESI_ANGKET {
        int nomor_butir "1 sampai 12"
        string sub_skala "Reasoning | Debugging | Autonomy | SelfReg"
        int skor_likert "1 sampai 5"
    }

    JAWABAN_SOAL_CT {
        string kode_soal "A1-A4 atau B1-B4"
        string domain_ct "Decomposition | Pattern | Logic | Debugging"
        string opsi_terpilih "A | B | C | D"
        boolean status_kebenaran
        int skor_keyakinan "1 sampai 5 (20% - 100%)"
    }

    SKOR_PSIKOMETRIK {
        float skor_kemampuan_aktual "0.0 - 100.0"
        float skor_efikasi_diri "0.0 - 100.0"
        float indeks_kalibrasi "S_eff - S_skill"
        string kategori_kalibrasi "Well-Calibrated | Overconfident | Underconfident"
        string kode_kuadran "MASTERY | UNDERCONFIDENT | OVERCONFIDENT | STRUGGLING"
    }

    LAPORAN_DIAGNOSTIK {
        string ringkasan_eksekutif
        string evaluasi_penalaran_kritis
        string evaluasi_kemandirian
        string evaluasi_kreativitas
        string[] rekomendasi_intervensi_guru
        string pesan_umpan_balik_siswa
        boolean is_edited_manually
    }
```

---

## 7. DIAGRAM URUTAN GENERASI LAPORAN (SEQUENCE DIAGRAM)

Interaksi antar modul saat memproses narasi laporan diagnostik dengan jaminan *fallback*:

```mermaid
sequenceDiagram
    autonumber
    actor Guru as Guru / Admin
    participant UI as Dashboard Admin (UI)
    participant Engine as Mesin Psikometrik
    participant AIClient as Klien Gemini API
    participant Fallback as Mesin Fallback Lokal
    participant Report as Lembar Pratinjau Dokumen

    Guru->>UI: Klik tombol "Proses & Buat Laporan"
    UI->>Engine: Kirim data skor CT & efikasi diri
    Engine->>Engine: Hitung S_skill, S_efficacy, I_cal, & Tentukan Kuadran
    Engine-->>UI: Kembalikan koordinat kuadran & metrik

    alt Koneksi Daring & API Key Terpasang
        UI->>AIClient: Kirim JSON parameter + SYSTEM_PROMPT
        activate AIClient
        AIClient-->>UI: Respon JSON terstruktur valid
        deactivate AIClient
        UI->>Report: Muat narasi AI ke dalam template laporan
    else Koneksi Terputus / API Error
        UI->>Fallback: Panggil fungsi generateDeterministicReport(data)
        activate Fallback
        Fallback-->>UI: Kembalikan objek JSON narasi psikometrik baku
        deactivate Fallback
        UI->>Report: Muat narasi fallback ke dalam template laporan
    end

    Guru->>Report: Sunting teks secara langsung (Inline Edit)
    Report-->>UI: Simpan perubahan teks di memori sesi
    Guru->>UI: Klik "Unduh Word (.doc)" atau "Cetak Dokumen"
    UI-->>Guru: Unduh file dokumen resmi / Buka dialog cetak PDF
```
