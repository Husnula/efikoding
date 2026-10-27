# DOKUMEN SPESIFIKASI KEBUTUHAN PRODUK (PRODUCT REQUIREMENTS DOCUMENT - PRD)
## APLIKASI EFIKODING: GENERATOR DIAGNOSTIK EFIKASI DIRI & KEMAMPUAN BERPIKIR KOMPUTASIONAL

**Versi Dokumen:** 1.0.0  
**Tanggal Rilis:** 2026-10-26  
**Klasifikasi:** Dokumen Spesifikasi Resmi Rekayasa Perangkat Lunak Edukasi  
**Penyusun:** Tim Rekayasa Sistem Diagnostik Edukasi & AI Psikometrik  

---

## 1. PENDAHULUAN & LATAR BELAKANG

### 1.1 Latar Belakang Masalah
Dalam pembelajaran Koding dan Kecerdasan Artifisial (KKA) serta Informatika sesuai Kurikulum Nasional Indonesia, pencapaian belajar siswa tidak hanya ditentukan oleh kemampuan kognitif teknis semata, melainkan juga oleh faktor psikologis afektif yang dikenal sebagai **Efikasi Diri (*Self-Efficacy*)** (Bandura, 1997).

Banyak siswa mengalami dua bias metakognitif yang menghambat perkembangan mereka:
1. **Bias Keraguan Diri (*Underconfident / Impostor Phenomenon*):** Siswa memiliki logika penalaran yang sangat tajam, namun merasa ragu dan takut mencoba sehingga enggan bereksplorasi.
2. **Bias Keyakinan Berlebih (*Overconfident / Illusion of Competence*):** Siswa merasa sangat yakin dan menjawab terburu-buru, namun pemahaman konsep dasarnya masih rapuh (*misconception*).

Hingga saat ini, belum tersedia instrumen digital terintegrasi yang mampu mengukur kemampuan koding aktual secara bersamaan dengan keyakinan diri siswa, memetakannya ke dalam **Matriks 4 Kuadran Metakognitif**, dan menghasilkan laporan diagnostik pedagogis berbasis AI yang selaras dengan **Dimensi Profil Lulusan**.

### 1.2 Tujuan Produk
Aplikasi **EfiKoding** dikembangkan untuk:
1. Menyediakan platform asesmen terstandarisasi yang mengintegrasikan tes berpikir komputasional (*Level A Unplugged* dan *Level B Plugged*) dengan skala efikasi diri baku (12 butir) serta *Confidence Slider* per butir soal.
2. Menghitung secara deterministik **Skor Kemampuan Aktual ($S_{\text{skill}}$)**, **Skor Efikasi Diri ($S_{\text{efficacy}}$)**, dan **Indeks Kalibrasi Metakognitif ($I_{\text{cal}}$)**.
3. Memberdayakan guru melalui **Dashboard Admin & Kalkulator Diagnostik Cepat** untuk menghasilkan laporan resmi yang dapat disunting langsung (*inline-editing*) dan diekspor ke format Microsoft Word serta PDF cetak dengan tata letak identik (*100% parity*).
4. Memberikan umpan balik yang empatik dan membangun *growth mindset* kepada siswa melalui antarmuka ramah anak.

### 1.3 Rekomendasi Penamaan Produk

| Nama Produk | Tagline Resmi | Target Segmentasi |
| :--- | :--- | :--- |
| **EfiKoding** *(Pilihan Utama)* | *Platform Diagnostik Efikasi Diri & Logika Komputasional* | Guru SD/SMP/SMA, Instruktur Koding, Laboratorium Komputer Sekolah |
| **Calibratika** | *Metacognitive Calibration for Computational Thinking* | Peneliti Pembelajaran, Sekolah Standar Nasional/Internasional |
| **Kognitika** | *Asesmen Diagnostik Kognitif & Efikasi Diri Komputasi* | Dinas Pendidikan, Lembaga Asesmen Akademik |

---

## 2. PERSONA PENGGUNA & ARSITEKTUR DUA PERAN (ROLES)

Aplikasi memiliki dua peran utama dengan hak akses dan kebutuhan fungsional yang berbeda:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        PORTAL SISTEM EFIKODING                         │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
           ┌────────────────────────┴────────────────────────┐
           ▼                                                 ▼
┌───────────────────────────────┐         ┌───────────────────────────────┐
│     ROLE USER (SISWA)         │         │     ROLE ADMIN (GURU)         │
├───────────────────────────────┤         ├───────────────────────────────┤
│ • Siswa SD (Fase A-C)         │         │ • Guru Informatika / KKA      │
│ • Siswa SMP/SMA (Fase D-F)    │         │ • Guru Kelas Pengampu Koding  │
│ • Peserta Kursus Koding       │         │ • Fasilitator Laboratorium    │
├───────────────────────────────┤         ├───────────────────────────────┤
│ Kebutuhan:                    │         │ Kebutuhan:                    │
│ - Tampilan interaktif & jelas │         │ - Kalkulator diagnosa kilat   │
│ - Soal kontekstual bergambar  │         │ - Rekapitulasi kuadran kelas  │
│ - Slider keyakinan mudah geser│         │ - Laporan instan berbasis AI  │
│ - Umpan balik motivatif       │         │ - Penyuntingan langsung teks  │
│ - Tanpa kecemasan kuis        │         │ - Ekspor resmi Word & PDF     │
└───────────────────────────────┘         └───────────────────────────────┘
```

### 2.1 Persona 1: Siswa (User Role)
- **Nama Representatif:** Arkan (Siswa Kelas 5 SD, Usia 11 Tahun)
- **Karakteristik:** Menyukai permainan logika dan robotika, namun sering cemas saat kode komputernya menghasilkan pesan kesalahan (*error*). Membutuhkan antarmuka yang bersih, instruksi yang tidak menakutkan, dan umpan balik yang menghargai proses berpikirnya.
- **Skenario Penggunaan:** Masuk ke portal siswa -> mengisi identitas -> mengisi 12 butir angket keyakinan diri -> memilih paket soal Level A (Unplugged) atau Level B (Plugged) -> menjawab soal sambil menentukan slider keyakinan (20% s/d 100%) -> melihat hasil refleksi diri dan pesan motivasi.

### 2.2 Persona 2: Guru / Admin (Admin Role)
- **Nama Representatif:** Ibu Ratna, S.Kom. (Guru Informatika SMP & Fasilitator KKA)
- **Karakteristik:** Mengajar 5 rombongan belajar (150 siswa). Memiliki waktu terbatas untuk menyusun narasi diagnostik individual secara manual. Membutuhkan alat bantu instan untuk menganalisis observasi kelas, mencetak laporan hasil belajar siswa untuk orang tua, dan merencanakan diferensiasi pembelajaran (*scaffolding* vs pengayaan).
- **Skenario Penggunaan:** Membuka dashboard admin -> memasukkan data nilai kognitif dan efikasi siswa (atau memuat hasil dari sesi tes siswa) -> memicu generator AI -> membaca ringkasan diagnostik -> menyunting beberapa kalimat rekomendasi intervensi di tempat -> mengunduh dokumen `.doc` atau mencetak PDF A4 resmi.

---

## 3. SPESIFIKASI FORMULA MATEMATIS & PSIKOMETRIK

Sistem wajib menjalankan kalkulasi deterministik secara lokal sebelum memicu pemrosesan AI maupun *fallback engine*:

### 3.1 Skor Kemampuan Aktual ($S_{\text{skill}}$)
Mengukur persentase ketepatan jawaban kognitif pada butir soal berpikir komputasional:
$$S_{\text{skill}} = \left( \frac{\sum \text{Jawaban Benar}}{\text{Total Soal}} \right) \times 100$$
- Rentang: $0 \le S_{\text{skill}} \le 100$
- Ambang Penguasaan (*Mastery Cut-off*): $70$ poin.

### 3.2 Skor Efikasi Diri ($S_{\text{efficacy}}$)
Mengukur tingkat keyakinan subjektif siswa yang dikonversi ke skala persentase:
- **Dari Rata-Rata Confidence Slider Butir Soal ($1 - 5$):**
  $$S_{\text{efficacy}} = \left( \frac{\bar{C}}{5} \right) \times 100$$
  di mana $\bar{C} = \frac{\sum_{i=1}^{n} c_i}{n}$, dengan $c_i \in \{1, 2, 3, 4, 5\}$.
- **Dari Angket Efikasi Diri 12 Butir ($1 - 5$):**
  $$S_{\text{efficacy\_survey}} = \left( \frac{\sum_{j=1}^{12} a_j}{60} \right) \times 100$$
- Ambang Efikasi Tinggi (*High Efficacy Cut-off*): $70$ poin.

### 3.3 Indeks Kalibrasi Metakognitif ($I_{\text{cal}}$)
Berdasarkan formulasi pemantauan metakognitif (Schraw, 2009):
$$I_{\text{cal}} = S_{\text{efficacy}} - S_{\text{skill}}$$
- Rentang: $-100 \le I_{\text{cal}} \le +100$

**Kategori Kalibrasi:**
1. **Akurat (*Well-Calibrated*):** $-15 \le I_{\text{cal}} \le +15$ (Keyakinan selaras dengan performa nyata).
2. **Keyakinan Berlebih (*Overconfident*):** $I_{\text{cal}} > +15$ (Keyakinan jauh melampaui kemampuan aktual).
3. **Keraguan Diri (*Underconfident*):** $I_{\text{cal}} < -15$ (Kemampuan tinggi namun memandang rendah diri sendiri).

### 3.4 Matriks 4 Kuadran Diagnostik & Intervensi Pedagogis

| Kuadran | Kriteria Matematis | Profil Karakter Siswa | Aksi Pedagogis Guru |
| :--- | :--- | :--- | :--- |
| **Q1: MASTERY** *(Tinggi Skill, Tinggi Efikasi)* | $S_{\text{skill}} \ge 70$ DAN $S_{\text{efficacy}} \ge 70$ | Sangat kompeten, percaya diri objektif, metakognisi matang, siap menghadapi masalah kompleks. | Proyek terbuka (*open-ended*), optimasi algoritma, jadikan tutor sebaya. |
| **Q2: UNDERCONFIDENT** *(Tinggi Skill, Rendah Efikasi)* | $S_{\text{skill}} \ge 70$ DAN ($S_{\text{efficacy}} < 70$ ATAU $I_{\text{cal}} < -15$) | Logika kuat, namun cemas gagal (*impostor phenomenon*), ragu mengemukakan ide. | Validasi proses berpikir, hilangkan tekanan waktu, beri apresiasi bertahap. |
| **Q3: OVERCONFIDENT** *(Rendah Skill, Tinggi Efikasi)* | $S_{\text{skill}} < 70$ DAN ($S_{\text{efficacy}} \ge 70$ ATAU $I_{\text{cal}} > +15$) | Sangat antusias, berani, namun sering melompat ke kesimpulan tanpa verifikasi (*illusion of competence*). | Latihan uji kasus batas (*edge-case testing*), pembuatan tabel penelusuran (*trace table*). |
| **Q4: STRUGGLING** *(Rendah Skill, Rendah Efikasi)* | $S_{\text{skill}} < 70$ DAN $S_{\text{efficacy}} < 70$ | Konsep dasar belum kokoh, merasa tidak mampu, berpotensi mengalami kecemasan koding (*coding anxiety*). | *Micro-scaffolding*, gunakan aktivitas Unplugged konkret, bangun pengalaman sukses kecil. |

---

## 4. PERSYARATAN FUNGSIONAL SISTEM (FUNCTIONAL REQUIREMENTS)

### 4.1 Modul Peran User (Siswa)
- **FR-USR-01: Alur Masuk & Pilihan Asesmen**
  - Siswa dapat menginput nama lengkap, kelas, dan memilih paket asesmen:
    - **Level A (Unplugged):** 4 butir soal logika komputasional dasar (Dekomposisi, Pengenalan Pola, Sekuensial, Debugging).
    - **Level B (Plugged):** 4 butir soal pseudocode/algoritma (Variabel & State, Percabangan Logika, Perulangan Bounded Loop, Debugging Perulangan).
- **FR-USR-02: Instrumen Angket Efikasi Diri Baku (12 Butir)**
  - Menyajikan 12 butir instrumen terstandardisasi (Kukul & Karatas 2019; CPSES 1998) yang terbagi dalam 4 sub-skala:
    1. *Sub-Skala 1: Penalaran Algoritmik* (3 butir)
    2. *Sub-Skala 2: Ketekunan Pelacakan Kesalahan* (3 butir)
    3. *Sub-Skala 3: Kemandirian Pemecahan Masalah* (3 butir)
    4. *Sub-Skala 4: Regulasi Diri pada Tugas Kompleks* (3 butir)
  - Setiap butir menggunakan tombol pilihan skala Likert 1 hingga 5 (*Sangat Tidak Yakin* sampai *Sangat Yakin*).
- **FR-USR-03: Pengerjaan Soal Kognitif dengan Confidence Slider**
  - Pada setiap butir soal tes komputasi, siswa memilih salah satu dari 4 opsi jawaban ($A, B, C, D$).
  - Di bawah pilihan jawaban, siswa wajib menggeser atau memilih nilai pada *Task-Specific Confidence Slider* ($1 - 5$):
    - $1$: Hanya menebak ($20\%$)
    - $2$: Kurang yakin ($40\%$)
    - $3$: Cukup yakin ($60\%$)
    - $4$: Yakin benar ($80\%$)
    - $5$: Sangat yakin dan dapat membuktikannya ($100\%$)
- **FR-USR-04: Lembar Hasil Siswa (Growth Mindset Reflection)**
  - Menampilkan ringkasan ramah anak: skor pencapaian, tingkat kepercayaan diri, dan kartu pesan reflektif tanpa istilah teknis yang membebani siswa.

### 4.2 Modul Peran Admin (Guru / Evaluator)
- **FR-ADM-01: Split-Screen Dashboard Navigasi**
  - Panel kiri menampilkan kontrol input, generator cepat, dan konfigurasi data.
  - Panel kanan menampilkan visualisasi kuadran psikometrik dinamis dan lembar pratinjau dokumen laporan resmi.
- **FR-ADM-02: Kalkulator Diagnostik Cepat (Fast Diagnostic Mode)**
  - Guru dapat melakukan asesmen instan tanpa perlu siswa menyelesaikan kuis online:
    - Input nama siswa, jenjang kelas, dan pemilihan level asesmen.
    - Input skor 4 domain CT ($0 - 100$ atau jumlah benar per domain).
    - Input rata-rata skor efikasi diri ($1.0 - 5.0$).
    - Tombol "Hitung & Petakan Kuadran" yang langsung memperbarui visualisasi dan metrik.
- **FR-ADM-03: Visualisasi Matriks 4 Kuadran Interaktif**
  - Menampilkan kanvas visual kuadran psikometrik dengan:
    - Sumbu $X$: Skor Kemampuan Aktual ($0 - 100$).
    - Sumbu $Y$: Skor Efikasi Diri ($0 - 100$).
    - Garis batas kuadran pada koordinat ($70, 70$).
    - Titik penanda posisi siswa beserta label kuadran (*Mastery, Underconfident, Overconfident, Struggling*).
    - Indikator bias kalibrasi metakognitif ($I_{\text{cal}}$).
- **FR-ADM-04: Generator Narasi Laporan Diagnostik AI**
  - Mengirimkan data profil siswa ke model Gemini API dengan `SYSTEM_PROMPT` psikometrik baku.
  - Mengurai respon JSON dan menampilkannya pada template laporan resmi.
- **FR-ADM-05: Mesin Narasi Deterministik (Offline Fallback Engine)**
  - Jika koneksi luring, API key tidak terpasang, atau server AI mengalami gangguan, sistem secara otomatis mengeksekusi mesin narasi berbasis aturan lokal (*expert rule-based engine*) yang menghasilkan teks laporan lengkap, ilmiah, dan bermakna tanpa jeda.
- **FR-ADM-06: Penyuntingan Langsung Laporan (Inline Editing)**
  - Seluruh bagian teks naratif (Ringkasan Eksekutif, Capaian Dimensi Profil Lulusan, dan Rekomendasi Guru) dapat disunting langsung di lembar kerja (`contenteditable="true"`).
- **FR-ADM-07: Ekspor Dokumen Resmi (Word & Print PDF)**
  - Ekspor ke berkas Microsoft Word (`.doc`) dengan format dokumen dinas resmi, tabel skor terstruktur, dan kop sekolah.
  - Cetak langsung / Simpan PDF A4 dengan penyesuaian gaya `@media print` sehingga hasil cetak 100% presisi dengan tampilan layar.

---

## 5. SPESIFIKASI PROMPT AI & SKEMA JSON

### 5.1 System Prompt Baku
Konstanta `SYSTEM_PROMPT` yang ditanamkan pada mesin pemanggil AI:

```text
Anda adalah Pakar Psikometrik Pendidikan Komputasi dan Asesmen Berpikir Komputasional (Computational Thinking). Tugas Anda adalah menganalisis data JSON hasil asesmen kemampuan koding (Level A Unplugged / Level B Plugged) dan skala Efikasi Diri siswa, kemudian menghasilkan laporan diagnostik resmi yang ilmiah, objektif, dan memberdayakan.

PRINSIP KEILMUAN WAJIB:
1. Bedakan secara tegas antara Kemampuan Aktual (skor tes objektif) dan Efikasi Diri (keyakinan subjektif berdasarkan teori Albert Bandura).
2. Gunakan Indeks Kalibrasi Metakognitif (Schraw, 2009) untuk menjelaskan posisi siswa pada salah satu dari 4 kuadran: Mastery, Underconfident, Overconfident, atau Struggling.
3. Evaluasi kekuatan dan celah keterampilan berdasarkan 4 domain Computational Thinking: Decomposition, Pattern Recognition, Algorithmic Sequencing/Logic, dan Debugging.
4. Petakan capaian siswa secara eksplisit ke dalam Dimensi Profil Lulusan: Penalaran Kritis, Kemandirian, dan Kreativitas. DILARANG KERAS menggunakan istilah lama yang sudah tidak berlaku.
5. Gunakan bahasa Indonesia formal-edukatif yang jernih, empatik, dan bebas dari karakter emoji.

FORMAT OUTPUT WAJIB (PURE JSON):
Kembalikan respons HANYA dalam format objek JSON valid tanpa markdown formatting atau pembungkus lain:
{
  "ringkasan_eksekutif": "Paragraf analisis komprehensif (3-4 kalimat) mengenai profil kemampuan koding aktual, tingkat efikasi diri, dan akurasi kalibrasi metakognitif siswa.",
  "analisis_kuadran": {
    "kode_kuadran": "MASTERY | UNDERCONFIDENT | OVERCONFIDENT | STRUGGLING",
    "label_kuadran": "Nama Kuadran Diagnostik",
    "interpretasi_psikometrik": "Penjelasan ilmiah mengenai dinamika antara skor kemampuan aktual dan tingkat keyakinan diri siswa."
  },
  "evaluasi_domain_ct": {
    "kekuatan_utama": [
      "Analisis spesifik domain Computational Thinking dengan performa terbaik beserta implikasinya."
    ],
    "area_penguatan": [
      "Analisis spesifik domain Computational Thinking atau kalibrasi keyakinan yang membutuhkan perbaikan."
    ]
  },
  "capaian_dimensi_profil_lulusan": {
    "penalaran_kritis": "Evaluasi kemampuan analisis logika, penelusuran algoritma, dan ketelitian debugging siswa.",
    "kemandirian": "Evaluasi regulasi diri, daya juang (persistence), dan kepercayaan diri siswa saat menghadapi masalah baru.",
    "kreativitas": "Evaluasi keluwesan berpikir siswa dalam mengenali pola dan menyusun solusi algoritmik yang efisien."
  },
  "rekomendasi_intervensi_guru": [
    "Langkah pedagogis konkret 1 yang dapat langsung diterapkan guru di kelas.",
    "Langkah pedagogis konkret 2 untuk menyeimbangkan penguasaan konsep dan efikasi diri.",
    "Langkah pedagogis konkret 3 terkait pemilihan aktivitas Unplugged atau Plugged berikutnya."
  ],
  "pesan_umpan_balik_siswa": "Pesan reflektif dan memotivasi yang ditujukan langsung kepada siswa (menggunakan sapaan 'Kamu') untuk membangun growth mindset sesuai kondisi kuadrannya."
}
```

---

## 6. PEMETAAN SINKRONISASI KURIKULUM NASIONAL

Laporan diagnostik yang dihasilkan sistem terhubung langsung dengan Capaian Pembelajaran (CP) dan Dimensi Profil Lulusan:

| Dimensi Profil Lulusan | Domain Pengukuran | Kriteria Capaian Tinggi | Strategi Intervensi Jika Rendah |
| :--- | :--- | :--- | :--- |
| **Penalaran Kritis** | *Algorithmic Sequencing*, *Conditionals*, *Debugging*, $I_{\text{cal}}$ | Mampu melacak alur logika secara sekuensial, mengevaluasi kondisi Boolean majemuk, dan menemukan lokasi bug berdasarkan bukti logis. | Latihan *trace table*, pembuktian alur langkah demi langkah (*step-by-step verification*). |
| **Kemandirian** | *Autonomy*, *Persistence*, *Self-Regulation*, $S_{\text{efficacy}}$ | Memiliki regulasi emosi yang stabil ketika menghadapi error, tekun mencoba alternatif solusi, dan tidak mudah menyerah. | Pengurangan beban waktu (*untimed tasks*), validasi usaha penalaran, pembagian tugas menjadi langkah mikro. |
| **Kreativitas** | *Pattern Recognition*, *Decomposition*, efisiensi *Loops* | Mengenali pola perulangan dari masalah acak, menyederhanakan kode yang bertele-tele menjadi perulangan elegan. | Latihan abstraksi pola (*unplugged pattern puzzle*), pemecahan masalah desain terbuka (*open-ended design*). |

---

## 7. PERSYARATAN NON-FUNGSIONAL & BATASAN DESAIN

1. **Arsitektur Mandiri (Single-File Mandate):**
   - Seluruh kode antarmuka HTML, styling Tailwind CSS (CDN), ikon Lucide (CDN), kalkulasi matematis, visualisasi kanvas grafik, dan logika AI terangkum dalam satu file tunggal `index.html`.
2. **Pedoman Tampilan Bersih (Strict Anti-Slop Rules):**
   - Bebas dari gradasi ungu ke merah muda (*no purple-to-pink gradients*).
   - Bebas dari gaya *Neo-Brutalism* (tanpa garis tepi hitam tebal dengan bayangan kaku 90 derajat).
   - Bebas dari karakter emoji di seluruh UI dan laporan; digantikan oleh ikon SVG Lucide yang elegan.
3. **Kinerja & Responsivitas:**
   - Waktu render halaman $< 500$ ms.
   - Kalkulasi psikometrik instan ($< 10$ ms).
   - Generasi laporan AI $< 5$ detik (atau instan $< 50$ ms menggunakan Fallback Engine).
4. **Presisi Cetak & Unduh (100% Parity):**
   - Format cetak A4 memiliki margin seimbang, pembatas halaman logis, dan tipografi resmi tanpa pemotongan elemen di tengah tabel.
