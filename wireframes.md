# SPESIFIKASI WIREFRAME & TATA LETAK ANTARMUKA (WIREFRAMES.MD)
## PLATFORM EFIKODING: DIAGNOSTIK EFIKASI DIRI & BERPIKIR KOMPUTASIONAL

**Versi Dokumen:** 1.0.0  
**Gaya Desain:** Clean Corporate & Minimalist SaaS  
**Grid Dasar:** 12-Column Responsive Layout (Desktop Split-Screen & Mobile Stacked)  

---

## 1. PETA ARSITEKTUR NAVIGASI & PERAN (SITE MAP)

```
                              ┌─────────────────────────────┐
                              │     HEADER NAVIGASI GLOBAL  │
                              │ [Logo] EfiKoding Diagnostic │
                              │ [Role Switch: SISWA | GURU] │
                              └──────────────┬──────────────┘
                                             │
                      ┌──────────────────────┴──────────────────────┐
                      ▼                                             ▼
       ┌───────────────────────────────┐             ┌───────────────────────────────┐
       │      MODUL USER (SISWA)       │             │      MODUL ADMIN (GURU)       │
       ├───────────────────────────────┤             ├───────────────────────────────┤
       │ 1. Onboarding & Profil Siswa  │             │ 1. Split-Screen Workspace     │
       │ 2. Sesi 1: Angket Efikasi     │             │    • Panel Kiri: Input Kilat, │
       │    (12 Butir Likert 1-5)      │             │      Parameter, Bank Soal     │
       │ 3. Sesi 2: Soal CT & Slider   │             │    • Panel Kanan: Grafik 4    │
       │    Keyakinan (Level A/B)      │             │      Kuadran & Pratinjau      │
       │ 4. Lembar Refleksi Diri       │             │ 2. Generator Narasi AI &      │
       │    (Growth Mindset Card)      │             │    Mesin Fallback Lokal       │
       │                               │             │ 3. Inline Editor Laporan      │
       │                               │             │ 4. Ekspor Word & Cetak PDF    │
       └───────────────────────────────┘             └───────────────────────────────┘
```

---

## 2. WIREFRAME MODUL USER (SISWA)

### 2.1 View U1: Onboarding, Identitas, & Pilihan Level
Tampilan bersih dan ramah anak, berfokus pada kejelasan petunjuk tanpa memicu stres ujian.

```
+-----------------------------------------------------------------------------------------+
| [Icon] EfiKoding                         [Mode Siswa (Aktif)]  [Beralih ke Mode Guru]   |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|       +-------------------------------------------------------------------------+       |
|       |                     SELAMAT DATANG DI EFIKODING                         |       |
|       |    Mari Mengenali Gaya Berpikir dan Membangun Keyakinan Kodingmu        |       |
|       +-------------------------------------------------------------------------+       |
|                                                                                         |
|       +-------------------------------------------------------------------------+       |
|       |  DATA PESERTA                                                           |       |
|       |  Nama Lengkap Siswa : [______________________________________]          |       |
|       |  Kelas / Rombel     : [ Pilih Kelas: 4 SD / 5 SD / 7 SMP / 8 SMP  v ]   |       |
|       +-------------------------------------------------------------------------+       |
|                                                                                         |
|       +-------------------------------------------------------------------------+       |
|       |  PILIH TANTANGAN ASESMEN HARI INI                                       |       |
|       |                                                                         |       |
|       |  [ ] LEVEL A: LOGIKA DASAR (UNPLUGGED)                                  |       |
|       |      Cocok untuk Fase A & B (SD Kelas 1-4) atau Pemula.                 |       |
|       |      Fokus: Pola robot, teka-teki logika harian, dan petunjuk langkah.  |       |
|       |                                                                         |       |
|       |  [*] LEVEL B: ALGORITMA & PSEUDOCODE (PLUGGED)                          |       |
|       |      Cocok untuk Fase C & D (SD Kelas 5-6 & SMP Kelas 7-9).             |       |
|       |      Fokus: Variabel nilai, kondisi logika JIKA/MAKA, dan perulangan.   |       |
|       +-------------------------------------------------------------------------+       |
|                                                                                         |
|                                       [ MULAI SESI ASESMEN -> ]                         |
|                                                                                         |
+-----------------------------------------------------------------------------------------+
```

---

### 2.2 View U2: Sesi 1 - Angket Efikasi Diri Baku (12 Butir Likert)
Pengukuran keyakinan afektif berdasarkan 4 sub-skala tervalidasi.

```
+-----------------------------------------------------------------------------------------+
| [Icon] EfiKoding | Sesi 1 dari 2: Angket Keyakinan Diri        [Progress: 40% ========] |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|   Petunjuk: Tidak ada jawaban benar atau salah. Pilihlah angka 1 sampai 5 yang paling   |
|   mencerminkan seberapa yakin kamu dengan kemampuan dirimu saat ini.                    |
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | Sub-Skala 1: Penalaran Algoritmik (Algorithmic Reasoning)                       |   |
|   +---------------------------------------------------------------------------------+   |
|   | 1. Saya yakin dapat memecah masalah yang rumit menjadi langkah-langkah kecil.   |   |
|   |    (1) Sangat Tidak Yakin   (2) Tidak   (3) Cukup   (4) Yakin   (*) Sangat (5)  |   |
|   |                                                                                 |   |
|   | 2. Saya yakin dapat menemukan pola atau kemiripan dari beberapa persoalan.      |   |
|   |    (1) Sangat Tidak Yakin   (2) Tidak   (3) Cukup   (*) Yakin   (5) Sangat (5)  |   |
|   |                                                                                 |   |
|   | 3. Saya yakin dapat menyusun instruksi secara runtut agar robot bergerak tepat. |   |
|   |    (1) Sangat Tidak Yakin   (2) Tidak   (*) Cukup   (4) Yakin   (5) Sangat (5)  |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | Sub-Skala 2: Ketekunan Pelacakan Kesalahan (Debugging & Persistence)            |   |
|   +---------------------------------------------------------------------------------+   |
|   | 4. Ketika instruksi atau kode saya error, saya yakin dapat mencari salahnya.    |   |
|   |    (1) Sangat Tidak Yakin   (2) Tidak   (3) Cukup   (*) Yakin   (5) Sangat (5)  |   |
|   | ... [Butir 5 sampai 12 berlanjut dengan opsi Likert seragam]                    |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|                   [ <- Kembali ke Profil ]        [ Lanjut ke Soal Koding -> ]          |
|                                                                                         |
+-----------------------------------------------------------------------------------------+
```

---

### 2.3 View U3: Sesi 2 - Pengerjaan Soal CT Diagnostik & Confidence Slider
Penyajian butir soal kognitif yang dipadukan dengan penggeser tingkat keyakinan tugas (*Task-Specific Confidence Slider*).

```
+-----------------------------------------------------------------------------------------+
| [Icon] EfiKoding | Sesi 2: Tantangan Logika (Soal 2 dari 4)    [Progress: 75% ========] |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | SOAL B2 - DOMAIN: CONDITIONALS & BOOLEAN LOGIC (PERCABANGAN)                    |   |
|   | Target Capaian: Mengevaluasi ekspresi logika majemuk operator DAN (AND)         |   |
|   +---------------------------------------------------------------------------------+   |
|   | Konteks:                                                                        |   |
|   | Sistem penyiram tanaman otomatis bekerja dengan aturan kode berikut:            |   |
|   | +-----------------------------------------------------------------------------+ |   |
|   | | JIKA (kelembapan < 40) DAN (status_hujan == SALAH) MAKA:                    | |   |
|   | |     pompa = "AKTIF"                                                         | |   |
|   | | SELAIN ITU:                                                                 | |   |
|   | |     pompa = "NONAKTIF"                                                      | |   |
|   | +-----------------------------------------------------------------------------+ |   |
|   |                                                                                 |   |
|   | Pertanyaan:                                                                     |   |
|   | Sensor membaca kelembapan = 30 dan status_hujan = BENAR. Apakah nilai pompa?    |   |
|   |                                                                                 |   |
|   |   ( ) A. "AKTIF"                                                                |   |
|   |   (*) B. "NONAKTIF"                                                             |   |
|   |   ( ) C. "ERROR"                                                                |   |
|   |   ( ) D. "AKTIF SEBENTAR"                                                       |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | [Icon Shield] TINGKAT KEYAKINANMU PADA SOAL INI (CONFIDENCE SLIDER)             |   |
|   | Seberapa yakin kamu bahwa jawaban dan alur logika pilihanmu di atas sudah tepat?|   |
|   |                                                                                 |   |
|   |     1 (20% Tebak)    2 (40% Ragu)    3 (60% Cukup)    [4] (80% Yakin)  5 (100%) |   |
|   |    [------------------------------------------------------O-----------]         |   |
|   |    Status Terpilih: "Skala 4: Yakin Benar (80%)"                                |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|                        [ <- Soal Sebelumnya ]    [ Soal Berikutnya / Selesai -> ]   |
|                                                                                         |
+-----------------------------------------------------------------------------------------+
```

---

### 2.4 View U4: Lembar Hasil Siswa (Growth Mindset Reflection)
Hasil psikometrik yang diterjemahkan menjadi bahasa apresiasi tanpa label negatif yang memicu kecemasan.

```
+-----------------------------------------------------------------------------------------+
| [Icon] EfiKoding | Hasil Diagnostik Belajar Siswa                                       |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | HEBAT, ARKAN! KAMU TELAH MENYELESAIKAN TANTANGAN KOMPUTASI HARI INI             |   |
|   | Tanggal Tes: 26 Oktober 2026 | Paket: Level B (Plugged)                         |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|   +-------------------------------+   +---------------------------------------------+   |
|   | SKOR PENALARAN LOGIKA         |   | TINGKAT KEYAKINAN DIRI                      |   |
|   |            75 / 100           |   |                 80%                         |   |
|   |       [Status: Sangat Baik]   |   |        [Status: Penuh Percaya Diri]         |   |
|   +-------------------------------+   +---------------------------------------------+   |
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | [Icon Sparkles] KARTU REFLEKSI PROSES BELAJAR (GROWTH MINDSET)                  |   |
|   |                                                                                 |   |
|   | "Logika pemecahan masalahmu sudah berjalan dengan sangat baik! Kamu mampu       |   |
|   | menganalisis kondisi kode yang rumit dengan teliti. Tetaplah berani mencoba     |   |
|   | tantangan baru, dan jangan ragu untuk memeriksa kembali alur kode saat kamu     |   |
|   | merasa sangat yakin. Kamu punya bakat komputasi yang luar biasa!"               |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|   +---------------------------------------------------------------------------------+   |
|   | KEKUATAN UTAMA YANG KAMU TUNJUKKAN:                                             |   |
|   | [Check] Menguasai Logika Percabangan (Conditionals)                             |   |
|   | [Check] Teliti dalam Menelusuri Nilai Variabel (State Tracking)                 |   |
|   | [Tips]  Latih ketelitian ekstra pada algoritma perulangan (Loops)               |   |
|   +---------------------------------------------------------------------------------+   |
|                                                                                         |
|               [ Unduh Rangkuman Saya ]           [ Selesai & Keluar ]                   |
|                                                                                         |
+-----------------------------------------------------------------------------------------+
```

---

## 3. WIREFRAME MODUL ADMIN / GURU (CLEAN CORPORATE SPLIT-SCREEN)

Struktur utama dashboard guru yang menyajikan kontrol di panel kiri dan kanvas analitik serta pratinjau lembar kerja resmi di panel kanan.

```
+---------------------------------------------------------------------------------------------------------------+
| [Icon] EfiKoding Admin | Diagnostik Psikometrik & Laporan Kurikulum        [Mode Guru Aktif]  [Switch: Siswa] |
+---------------------------------------------------------------------------------------------------------------+
| PANEL KIRI: KONTROL & INPUT CEPAT GURU            | PANEL KANAN: MATRIKS KUADRAN & LEMBAR LAPORAN RESMI       |
| (Width: 38% / 460px)                              | (Width: 62% / Flexible Canvas)                            |
|---------------------------------------------------|-----------------------------------------------------------|
| [Tab: Kalkulator Cepat] [Tab: Bank Soal] [Config] | +-------------------------------------------------------+ |
|                                                   | | VISUALISASI MATRIKS 4 KUADRAN PSIKOMETRIK             | |
| DATA SISWA DIAGNOSTIK:                            | |  Efikasi (Y)                                          | |
| Nama Siswa : [ Arkan Danendra               ]     | |  100 ^                                                | |
| Kelas/Fase : [ Fase D - Kelas 7 SMP         v ]   | |      |     [Q2: UNDERCONFIDENT] |  [Q1: MASTERY]      | |
| Paket Tes  : [*] Level B (Plugged) [ ] Level A    | |      |                          |      (*) Posisi     | |
|                                                   | |   70 |--------------------------+-------------------- | |
| KOMPONEN SKOR KEMAMPUAN AKTUAL (0-100):           | |      |     [Q4: STRUGGLING]     |  [Q3: OVERCONFIDENT]| |
| 1. Decomposition      : [========O-----] 80%      | |    0 +--------------------------+-------------------> | |
| 2. Pattern Recognition: [==========O---] 90%      | |      0                          70             100    | |
| 3. Sequencing / Logic : [=======O------] 75%      | |                                    Kemampuan Aktual(X)| |
| 4. Debugging          : [====O---------] 55%      | +-------------------------------------------------------+ |
| Skor Rata-rata Skill ($S_skill$) = 75.00          |                                                           |
|                                                   | METRIK INDEKS KALIBRASI METAKOGNITIF ($I_cal$):           |
| INPUT SKOR KEYAKINAN / EFIKASI DIRI:              | [$S_skill$: 75.0]  [$S_efficacy$: 82.0]  [$I_cal$: +7.0]      |
| Rata-rata Angket/Slider: [4.1  ] / 5.0            | Diagnosis: "TERKALIBRASI AKURAT (WELL-CALIBRATED)"        |
| Skor Efikasi ($S_efficacy$)    = 82.00            | Kuadran:   "KUADRAN 1: MASTERY (HIGH SKILL & EFFICACY)"   |
|                                                   |                                                           |
| AKSI GENERATOR:                                   | ACTION BAR RESMI:                                         |
| [*] Gunakan Gemini AI    [ ] Gunakan Local Engine | [ Sparkles: Generate AI ]  [ Word (.doc) ]  [ Cetak PDF ] |
|                                                   | --------------------------------------------------------- |
| API Key Runtime: [ Terkonfigurasi Otomatis v ]    | LEMBAR PRATINJAU DOKUMEN RESMI (INLINE EDITABLE):         |
| [ Tombol: PROSES & REFRESH LAPORAN ]              | +-------------------------------------------------------+ |
|                                                   | | KOP SEKOLAH / LEMBAGA ASESMEN DIAGNOSTIK              | |
| BANK SOAL PREVIEW (Accordion):                    | | LAPORAN EVALUASI DIAGNOSTIK BERPIKIR KOMPUTASIONAL    | |
| > Soal B1: Variables & State                      | | Identitas: Arkan Danendra | Kelas: 7 SMP | 26 Okt 2026| |
| > Soal B2: Conditionals & Logic                   | |                                                       | |
| > Soal B3: Loops & Efficiency                     | | 1. RINGKASAN EKSEKUTIF [Klik untuk menyunting]        | |
| > Soal B4: Code Debugging                         | | Siswa menunjukkan kemampuan berpikir komputasional    | |
|                                                   | | yang sangat solid dengan penguasaan seimbang pada...  | |
| LOG KALKULASI PSIKOMETRIK:                        | |                                                       | |
| • Formula $S_skill$ = (3/4) * 100 = 75            | | 2. CAPAIAN DIMENSI PROFIL LULUSAN                     | |
| • Formula $S_eff$   = (4.1/5) * 100 = 82          | | • Penalaran Kritis : Siswa cermat menguji kondisi...  | |
| • Formula $I_cal$   = 82 - 75 = +7 (Akurat)       | | • Kemandirian      : Regulasi diri dan daya juang...  | |
| • Status Kuadran    : MASTERY                     | | • Kreativitas      : Efisiensi algoritma berada...    | |
|                                                   | |                                                       | |
|                                                   | | 3. REKOMENDASI INTERVENSI PEDAGOGIS GURU              | |
|                                                   | | 1. Berikan proyek terbuka perancangan modul koding.   | |
|                                                   | | 2. Arahkan siswa menjadi tutor sebaya bagi kelompok...| |
|                                                   | | 3. Mulai perkenalkan tantangan Level B+ (Modular).    | |
|                                                   | +-------------------------------------------------------+ |
+---------------------------------------------------------------------------------------------------------------+
```

---

## 4. SPESIFIKASI MODAL & INTERAKSI KHUSUS

### 4.1 Mode Inline Editing (`contenteditable="true"`)
- Seluruh area narasi pada lembar pratinjau kanan memiliki batas halus bergaris putus-putus (`border-dashed border-slate-300`) saat kursor melintas (*hover*).
- Menampilkan *tooltip badge* kecil di pojok kanan atas: `[Icon Edit] Klik untuk menyunting teks secara langsung`.
- Perubahan teks langsung disimpan ke *state* memori lokal dan disinkronkan ke dokumen ekspor Word maupun cetak PDF.

### 4.2 Tata Letak Ekspor Presisi (100% Parity)
- Format lembar pratinjau dirancang dengan rasio dimensi lembar A4 portrait ($210\text{ mm} \times 297\text{ mm}$).
- Dilengkapi Kop Dokumen resmi, garis ganda pembatas, tabel skor dua kolom, grafik matriks kuadran beresolusi tinggi, narasi kurikulum, dan blok tanda tangan guru pengampu.
