# RENCANA PENGEMBANGAN SISTEM (DEVELOPMENT PLAN)
## PLATFORM DIAGNOSTIK EFIKASI DIRI & BERPIKIR KOMPUTASIONAL (EFIKODING / CALIBRATIKA)

**Status Dokumen:** Disetujui untuk Implementasi  
**Target Rilis:** v1.0.0 (Production-Ready Single-File Architecture)  
**Lingkup:** Arsitektur Peran Ganda (*Admin / Guru* & *User / Siswa*), Mesin Psikometrik Deterministik, Integrasi AI Generatif, dan Modul Ekspor Berstandar Resmi  

---

## 1. IKHTISAR PROYEK & REKOMENDASI NAMA APLIKASI

Berdasarkan empat pilar dokumen spesifikasi (Instrumen Baku Psikometrik, Matriks Kurikulum CP KKA & Dimensi Profil Lulusan, Naskah Akademik Kalibrasi Metakognitif, serta Panduan Desain Antigravity IDE), platform ini dirancang untuk menjembatani evaluasi kemampuan berpikir komputasional (*actual skill*) dengan keyakinan diri siswa (*self-efficacy*).

### Rekomendasi Nama Aplikasi

Berikut adalah 5 opsi nama dengan filosofi keilmuan dan penjenamaan korporat-edukatif:

| No | Opsi Nama | Tagline Rekomendasi | Filosofi & Alasan Pemilihan |
| :--- | :--- | :--- | :--- |
| **1** | **EfiKoding** *(Sangat Direkomendasikan)* | *Platform Diagnostik Efikasi Diri & Logika Komputasional* | Memadukan dua kata kunci utama: **Efikasi** (Bandura, 1997) dan **Koding** (CP KKA Kurikulum Nasional). Bersuara ramah, mudah diingat oleh guru dan siswa di Indonesia, serta tegas dalam merepresentasikan tujuan aplikasi. |
| **2** | **Calibratika** | *Metacognitive Calibration for Computational Thinking* | Diambil dari kata **Kalibrasi** (Schraw, 2009) dan **Informatika**. Menekankan keunggulan sistem dalam memetakan bias metakognitif (*overconfidence* dan *underconfidence*). |
| **3** | **Kognitika** | *Asesmen Diagnostik Kognitif & Efikasi Diri Komputasi* | Gabungan dari **Kognisi**, **Efikasi**, dan **Informatika**. Memberikan kesan akademis yang berwibawa untuk lingkungan sekolah dasar, menengah, maupun dinas pendidikan. |
| **4** | **Metakod Diagnostic** | *Pemetaan Metakognisi & Keterampilan Pemrograman* | Menonjolkan aspek metakognisi sebagai fondasi pembentukan *growth mindset* siswa dalam menyelesaikan tantangan algoritma. |
| **5** | **CT-Efficacy Navigator** | *Empowering Computational Thinking through Self-Efficacy Diagnostics* | Pilihan bernuansa internasional untuk sekolah berstandar SPK atau kurikulum berbasis dwibahasa. |

> **Rekomendasi Utama yang Dipilih:** **EfiKoding** (dengan modul kalibrasi metakognitif **Calibratika Engine**).

---

## 2. DIFERENSIASI DUA PERAN PENGGUNA (ROLE ARCHITECTURE)

Sistem mengadopsi pemisahan peran yang tegas (*separation of concerns*) antara kebutuhan evaluasi instruksional guru dan pengalaman reflektif siswa:

```
                          ┌──────────────────────────────┐
                          │   PORTAL UTAMA EFIKODING     │
                          └──────────────┬───────────────┘
                                         │
                 ┌───────────────────────┴───────────────────────┐
                 ▼                                               ▼
   ┌───────────────────────────┐                   ┌───────────────────────────┐
   │    ROLE 1: USER / SISWA   │                   │    ROLE 2: ADMIN / GURU   │
   ├───────────────────────────┤                   ├───────────────────────────┤
   │ 1. Pengisian Angket Baku  │                   │ 1. Mode Input Cepat Guru  │
   │    (12 Butir Likert 1-5)  │                   │    (Fast Diagnostic Calc) │
   │ 2. Pemilihan Level Tes    │                   │ 2. Matriks Analisis Kelas │
   │    (Level A / Level B)    │                   │    (Distribusi 4 Kuadran) │
   │ 3. Pengerjaan Soal CT     │                   │ 3. Engine Analisis AI     │
   │    + Confidence Slider    │                   │    (Gemini + Fallback)    │
   │ 4. Lembar Refleksi Diri   │                   │ 4. Inline Editing Laporan │
   │    & Growth Mindset Card  │                   │ 5. Ekspor Word & Cetak PDF│
   │ 5. Visualisasi Kuadran    │                   │ 6. Manajemen Bank Soal    │
   └───────────────────────────┘                   └───────────────────────────┘
```

### A. Peran User (Siswa)
- **Tujuan Utama:** Menjalani asesmen kognitif tanpa rasa takut (*low-stakes diagnostic*), mengukur keyakinan subjektif pada instrumen baku, dan memperoleh umpan balik yang membangun kepercayaan diri.
- **Fitur Spesifik:**
  1. *Onboarding & Personalization:* Pengisian nama, kelas, dan pemilihan jenjang asesmen (Level A - Unplugged untuk Fase A-B/Pemula C, Level B - Plugged untuk Fase C-D).
  2. *Sesi 1 - Angket Efikasi Diri Baku:* 12 butir instrumen terstandardisasi (Kukul & Karatas 2019; CPSES 1998) mencakup 4 sub-skala (*Algorithmic Reasoning*, *Debugging & Persistence*, *Autonomy*, dan *Self-Regulation*).
  3. *Sesi 2 - Tantangan Berpikir Komputasional:* Pengerjaan 4 butir soal diagnostik interaktif per level dengan *Task-Specific Confidence Slider* ($1-5$) untuk mengukur keyakinan per butir soal.
  4. *Refleksi & Student Dashboard:* Tampilan kartu pertumbuhan (*Growth Mindset Card*), apresiasi pencapaian domain, dan visualisasi titik posisi diri di dalam kuadran psikometrik tanpa terminologi yang menghakimi.

### B. Peran Admin (Guru / Instruktur / Asesor)
- **Tujuan Utama:** Mengelola asesmen, melakukan penginputan cepat data observasi kelas (*quick-calculator*), menghasilkan laporan diagnostik pedagogis formal, menyunting rekomendasi secara langsung (*inline-editing*), dan mengunduh berkas laporan berstandar kedinasan.
- **Fitur Spesifik:**
  1. *Dashboard Diagnostik Kelas:* Ringkasan persebaran siswa pada 4 Kuadran Psikometrik (*Mastery, Underconfident, Overconfident, Struggling*) dengan indikator peringatan metakognitif.
  2. *Kalkulator Diagnostik Cepat (Fast-Track Guru):* Antarmuka input instan tanpa mengharuskan siswa membuka aplikasi. Guru memasukkan nama, skor domain CT ($0-100$), dan rata-rata skor angket ($1-5$) untuk langsung mengkalkulasi $S_{\text{skill}}$, $S_{\text{efficacy}}$, $I_{\text{cal}}$, dan memetakan kuadrannya.
  3. *Pemrosesan Narasi AI & Deterministic Fallback:* Pemicu generasi analisis AI (skema JSON murni) menggunakan Gemini API dengan perlindungan 100% *Deterministic Fallback Rule-Based Engine* saat jaringan luring atau tanpa kuota API.
  4. *Penyuntingan Laporan Langsung (Inline WYSIWYG):* Fitur `contenteditable="true"` pada seluruh blok teks laporan (ringkasan eksekutif, capaian dimensi profil lulusan, dan rekomendasi intervensi) dengan penanda visual interaktif.
  5. *Ekspor Laporan Presisi (100% Parity):* Ekspor ke dokumen **Microsoft Word (`.doc`)** berbasis HTML Blob terformat dan opsi **Cetak Dokumen / Simpan PDF** dengan tata letak lembar kerja A4 profesional.
  6. *Manajemen Data & Bank Soal:* Pratinjau dan penyesuaian butir soal Level A & B serta parameter rubrik.

---

## 3. TAHAPAN PENGEMBANGAN (PHASE-BY-PHASE ROADMAP)

```
[FASE 1: FONDASI & SPESIFIKASI] ──► [FASE 2: ENGINE PSIKOMETRIK] ──► [FASE 3: UI/UX & ROLE ENGINE]
           │                                      │                                      │
           ▼                                      ▼                                      ▼
 Dokumen PRD, Desain,             Formula Matematis Deterministik,       Komponen Clean Corporate,
 Wireframes, & Mermaid            Aturan 4 Kuadran, & Fallback AI        Split-Screen, & State Flow
           │                                      │                                      │
           └──────────────────────────────────────┴──────────────────────────────────────┘
                                                  │
                                                  ▼
                                    [FASE 4: INTEGRASI AI & EKSPOR]
                                                  │
                                                  ▼
                                    [FASE 5: VALIDASI & AUDIT AKHIR]
```

### Fase 1: Spesifikasi & Dokumentasi Arsitektur (Milestone Saat Ini)
- **Output:**
  1. `plan.md`: Roadmap pengembangan, arsitektur peran ganda, strategi teknis.
  2. `prd.md`: Spesifikasi fungsional, formula matematika, integrasi kurikulum, skema JSON AI, dan batasan operasional.
  3. `wireframes.md`: Blueprint antarmuka teks/ASCII untuk portal siswa dan dashboard admin.
  4. `design-system.md`: Desain sistem korporat (palet warna netral, tipografi, komponen kartu, grafik kuadran, anti-slop rules).
  5. `mermaid.md`: Visualisasi alur logika, state machine, arsitektur sistem, dan ERD.

### Fase 2: Pembangunan Mesin Psikometrik & Logika Deterministik
- **Aktivitas:**
  1. Implementasi fungsi kalkulasi $S_{\text{skill}}$ (persentase skor aktual $0-100$).
  2. Implementasi fungsi kalkulasi $S_{\text{efficacy}}$ (konversi skala Likert 1-5 ke rentang $0-100$).
  3. Implementasi fungsi kalkulasi Indeks Kalibrasi Metakognitif $I_{\text{cal}} = S_{\text{efficacy}} - S_{\text{skill}}$.
  4. Implementasi logika deterministik pengelompokan 4 Kuadran (*Mastery, Underconfident, Overconfident, Struggling*).
  5. Pembangunan *Deterministic Narrative Fallback Engine* yang menghasilkan narasi utuh berstruktur standar jika AI tidak aktif.

### Fase 3: Pembangunan Antarmuka Pengguna (Single-File Application `index.html`)
- **Aktivitas:**
  1. Integrasi Tailwind CSS v3 via CDN dan Lucide Icons via CDN (tanpa dependensi build kompleks).
  2. Implementasi tata letak *Clean Corporate Split-Screen Dashboard*.
  3. Pembangunan modul alur pengerjaan tes siswa (Sesi Angket 12 Butir + Sesi Tes Soal CT Unplugged/Plugged dengan Slider Kalibrasi).
  4. Pembangunan modul Admin/Guru (Fast Diagnostic Input, Analitik Kuadran, Ringkasan Siswa).
  5. Pembangunan komponen interaktif Kanvas Grafik Matriks 4 Kuadran Psikometrik ($X: S_{\text{skill}}, Y: S_{\text{efficacy}}$).

### Fase 4: Integrasi AI, Inline Editing, & Modul Ekspor
- **Aktivitas:**
  1. Integrasi pemanggilan Gemini REST API (model `gemini-1.5-flash` / `gemini-2.5-flash`) dengan injeksi otomatis `SYSTEM_PROMPT` dan pemrosesan JSON terstruktur.
  2. Implementasi atribut `contenteditable="true"` dengan penanda visual interaktif pada seluruh blok narasi hasil analisis.
  3. Implementasi tombol *Export to Microsoft Word (.doc)* yang membungkus lembar kerja ke dalam format MIME HTML Office yang rapi.
  4. Implementasi stylesheet `@media print` untuk *Cetak Dokumen / Simpan PDF* dengan margin presisi dan pemisah halaman resmi.

### Fase 5: Pengujian, Validasi Kepatuhan, & Dokumentasi Penggelaran
- **Aktivitas:**
  1. Pengujian batas nilai (*edge-case testing*): skor 0, skor 100, selisih ekstrem $I_{\text{cal}} = \pm 100$.
  2. Validasi aturan *Strict Anti-Slop*: bebas gradasi ungu-pink, bebas gaya neo-brutalism, bebas karakter emoji.
  3. Validasi kepatuhan terminologi Kurikulum Nasional: memastikan terminologi **Dimensi Profil Lulusan** (Penalaran Kritis, Kemandirian, Kreativitas) digunakan secara konsisten.
  4. Verifikasi portabilitas berkas tunggal (`index.html`) pada berbagai peramban web modern tanpa instalasi paket node lokal.

---

## 4. STRUKTUR TEKNOLOGI & DEPENDENSI

Aplikasi mematuhi standar *Zero-Build Single-File Architecture*:
- **Struktur Berkas:** 1 file mandiri `index.html` (berisi HTML5, Tailwind CSS, Lucide Icons, dan skrip Vanilla JS terpadu).
- **Styling Engine:** Tailwind CSS via CDN (`https://cdn.tailwindcss.com`) dengan konfigurasi kustom palet `slate`, `blue`, `emerald`, `amber`, dan `rose`.
- **Ikonografi:** Lucide Icons via CDN (`https://unpkg.com/lucide@latest`).
- **Mesin Grafik Kuadran:** HTML5 Native Canvas / SVG Rendering (ringan, tajam di layar Retina, dan dapat langsung diekspor/dicetak).
- **Mesin AI:** Google Gemini API (REST Endpoint) + Local Deterministic Expert Engine (Fallback).
- **Mesin Ekspor:** Blob Data URI untuk `.doc` dan CSS Print Framework untuk PDF.

---

## 5. KRITERIA KEBERHASILAN (ACCEPTANCE CRITERIA)

| Parameter | Kriteria Keberhasilan |
| :--- | :--- |
| **Portabilitas** | Dapat dijalankan langsung dengan klik dua kali pada `index.html` di peramban apa pun (Chrome, Edge, Firefox, Safari) tanpa server lokal. |
| **Presisi Matematis** | Formula $S_{\text{skill}}$, $S_{\text{efficacy}}$, dan $I_{\text{cal}}$ menghitung nilai secara akurat 100% sesuai naskah akademik psikometrik. |
| **Keandalan AI & Luring** | Jika API Key tersedia dan jaringan daring, AI menghasilkan JSON valid. Jika jaringan luring atau API gagal, sistem otomatis beralih ke *Fallback Engine* lokal tanpa *crash* atau *error prompt*. |
| **Dua Peran Terintegrasi** | Pengguna dapat berpindah dengan mulus antara Portal Siswa (pengerjaan kuis lengkap) dan Dashboard Admin/Guru (analisis cepat dan cetak laporan). |
| **Kemudahan Penyuntingan** | Guru dapat mengedit teks laporan hasil analisis langsung di lembar pratinjau sebelum diekspor. |
| **Kesesuaian Ekspor** | Dokumen Word dan PDF memiliki tata letak, kop surat, tabel skor, dan grafik kuadran yang identik dengan pratinjau antarmuka. |
