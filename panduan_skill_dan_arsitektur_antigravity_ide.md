---
name: coding-efficacy-diagnostic-generator
description: Spesifikasi teknis, aturan UI/UX Clean Corporate, dan arsitektur aplikasi untuk membangun Generator Diagnostik Efikasi Diri & Kemampuan Koding di Antigravity IDE.
---

# SKILL & ARCHITECTURE RULES: CODING SELF-EFFICACY GENERATOR

Dokumen ini adalah instruksi utama (*Agent Skill*) bagi Antigravity IDE dalam merancang, menulis kode, dan memvalidasi aplikasi **Generator Diagnostik Efikasi Diri & Kemampuan Koding (Unplugged & Plugged)**.

## 1. ARSITEKTUR TEKNIS (SINGLE-FILE APPLICATION)
1. **Mandat Satu File (`index.html`):**
   - Seluruh struktur HTML5, konfigurasi gaya (Tailwind CSS via CDN), ikon (Lucide Icons via CDN), serta logika aplikasi dan pemanggilan AI (Vanilla JavaScript) wajib disatukan secara utuh di dalam satu file `index.html` yang siap di-deploy ke Netlify, Vercel, atau Cloudflare Pages.
2. **Injeksi API Key Otomatis:**
   - Pemanggilan model AI (Gemini API) untuk menyusun narasi diagnostik wajib mengambil kunci otorisasi secara langsung dari variabel lingkungan (*runtime environment*) tanpa menampilkan kolom input API Key manual pada antarmuka pengguna.
   - Sediakan juga mekanisme *Deterministic Fallback Generator* berbasis aturan psikometrik lokal apabila koneksi jaringan sedang luring (*offline*), sehingga aplikasi tetap berfungsi 100% tanpa hambatan.
3. **Dua Mode Penggunaan Terpadu:**
   - **Mode 1: Sesi Tes Interaktif Siswa:** Siswa memilih jenjang/level (**Level A - Unplugged** atau **Level B - Plugged**), mengerjakan soal berpikir komputasional, dan menggeser *Confidence Slider* (skala $1$ sampai $5$) pada setiap soal.
   - **Mode 2: Input Cepat / Kalkulator Diagnostik Guru:** Guru dapat memasukkan nama siswa, memilih level, mengisi skor domain berpikir komputasional serta skor rata-rata angket efikasi diri secara langsung untuk menghasilkan laporan instan.

## 2. STANDAR UI/UX: CLEAN CORPORATE & MINIMALIST SAAS
1. **Tata Letak (Layout):**
   - Gunakan struktur *Split-Screen Dashboard* proporsional: Panel Kiri untuk navigasi mode, kuis interaktif, atau input parameter guru; Panel Kanan untuk visualisasi matriks kuadran psikometrik dan lembar pratinjau laporan diagnostik.
2. **Palet Warna & Tipografi:**
   - Gunakan warna dasar netral yang bersih (`bg-slate-50`, permukaan kartu `bg-white`, garis tepi `border-slate-200`).
   - Gunakan aksen korporat tegas: `slate-900` untuk tajuk utama, `blue-600` untuk aksi primer, `emerald-600` untuk status *Mastery*, `amber-600` untuk peringatan kalibrasi (*Overconfident/Underconfident*), dan `rose-600` untuk intervensi dasar (*Struggling*).
   - Gunakan jenis huruf *sans-serif* modern (`Inter` atau `Plus Jakarta Sans`) untuk antarmuka, dan `JetBrains Mono` untuk potongan blok kode atau *pseudocode*.
3. **Pantangan Visual (Strict Anti-Slop Rules):**
   - **DILARANG** menggunakan gradasi warna ungu-magenta (*purple-to-pink gradients*).
   - **DILARANG** menggunakan gaya *Neo-Brutalism* (garis tepi hitam tebal dengan bayangan kasar).
   - **DILARANG** menggunakan karakter emoji di seluruh antarmuka maupun di dalam hasil laporan. Gunakan komponen *Lucide Icons* secara konsisten.

## 3. FITUR LAPORAN, PENYUNTINGAN LANGSUNG, & EKSPOR DOKUMEN
1. **Visualisasi Kuadran Psikometrik:**
   - Tampilkan grafik pemetaan posisi siswa pada *4-Quadrant Psychometric Grid* dimana sumbu horizontal ($X$) adalah Skor Kemampuan Aktual ($0 - 100$) dan sumbu vertikal ($Y$) adalah Skor Efikasi Diri ($0 - 100$).
2. **Penyuntingan Langsung (*Inline Editing*):**
   - Seluruh teks narasi hasil analisis AI pada lembar pratinjau laporan wajib dilengkapi atribut `contenteditable="true"` dengan indikator *hover* yang halus agar guru dapat menyunting kalimat secara langsung sebelum dokumen diunduh.
3. **Kesamaan Pratinjau dan Hasil Ekspor (100% Parity):**
   - Tata letak, tabel metrik, grafik kuadran, dan tipografi pada area pratinjau lembar kerja di layar aplikasi harus identik dengan hasil ekspor ke format **Microsoft Word (`.doc`)** maupun **Cetak PDF**.

## 4. KEPATUHAN TERMINOLOGI KURIKULUM & KEILMUAN
1. **Dimensi Profil Lulusan:**
   - Gunakan secara ketat istilah **Dimensi Profil Lulusan** (fokus pada dimensi **Penalaran Kritis**, **Kemandirian**, dan **Kreativitas**). Dilarang menggunakan istilah lama yang sudah tidak berlaku.
2. **Pemisahan Konstruk Psikometrik:**
   - Jangan pernah menyamakan skor keyakinan diri dengan bakat aktual. Laporan wajib menampilkan keduanya secara berdampingan beserta nilai **Indeks Kalibrasi Metakognitif ($I_{\text{cal}}$)**.