# NASKAH AKADEMIK, FORMULA PSIKOMETRIK, RUBRIK 4 KUADRAN, & SYSTEM PROMPT AI

Dokumen ini memuat spesifikasi matematis dan instruksi sistem (*System Prompt*) yang wajib ditanamkan ke dalam mesin pemroses aplikasi generator.

---

## 1. FORMULA PERHITUNGAN PSIKOMETRIK & KALIBRASI METAKOGNITIF
Sistem wajib melakukan kalkulasi deterministik di sisi klien (*JavaScript*) menggunakan tiga rumus baku berikut sebelum mengirimkan data ke AI:

1. **Skor Kemampuan Aktual ($S_{\text{skill}}$) dalam rentang $0 - 100$:**
   $$S_{\text{skill}} = \left( \frac{\sum \text{Jawaban Benar}}{\text{Total Soal}} \right) \times 100$$

2. **Skor Efikasi Diri ($S_{\text{efficacy}}$) dalam rentang $0 - 100$:**
   Jika menggunakan rata-rata *Confidence Slider* per soal (skala $1 - 5$) maupun angket $12$ butir:
   $$S_{\text{efficacy}} = \left( \frac{\text{Rata-rata Skor Keyakinan}}{5} \right) \times 100$$

3. **Indeks Kalibrasi Metakognitif ($I_{\text{cal}}$) dalam rentang $-100$ hingga $+100$:**
   Berdasarkan teori pemantauan metakognitif (Schraw, 2009):
   $$I_{\text{cal}} = S_{\text{efficacy}} - S_{\text{skill}}$$
   - **Kalibrasi Akurat (*Well-Calibrated*):** $-15 \le I_{\text{cal}} \le +15$
   - **Bias Keyakinan Berlebih (*Overconfident*):** $I_{\text{cal}} > +15$
   - **Bias Keraguan Diri (*Underconfident*):** $I_{\text{cal}} < -15$

---

## 2. RUBRIK DIAGNOSTIK 4 KUADRAN & INTERVENSI PEDAGOGIS

| Kuadran Psikometrik | Kriteria Matematis | Diagnosis Psikologis & Kognitif | Strategi Intervensi Guru (Pedagogical Action) |
| :--- | :--- | :--- | :--- |
| **Kuadran 1: MASTERY** (*High Skill, High Efficacy*) | $S_{\text{skill}} \ge 70$ dan $S_{\text{efficacy}} \ge 70$ | Penguasaan logika komputasi sangat kuat dan diiringi kesadaran diri yang akurat. Siap menghadapi kompleksitas tinggi. | Berikan proyek pengayaan terbuka (*open-ended project*), tantangan efisiensi algoritma, dan libatkan sebagai tutor sebaya (*peer mentor*). |
| **Kuadran 2: UNDERCONFIDENT** (*High Skill, Low Efficacy*) | $S_{\text{skill}} \ge 70$ dan $S_{\text{efficacy}} < 70$ (atau $I_{\text{cal}} < -15$) | Memiliki potensi dan penalaran koding yang tajam, namun mengalami keraguan diri (*impostor phenomenon*) dan takut salah. | Berikan validasi spesifik pada **proses berpikir logisnya**, kurangi tekanan batas waktu, dan perbanyak apresiasi saat siswa berhasil melakukan *debugging*. |
| **Kuadran 3: OVERCONFIDENT** (*Low Skill, High Efficacy*) | $S_{\text{skill}} < 70$ dan $S_{\text{efficacy}} \ge 70$ (atau $I_{\text{cal}} > +15$) | Antusiasme dan keberanian sangat tinggi, namun konsep dasar masih keliru (*illusion of competence*) dan terburu-buru menjawab. | Jaga motivasinya agar tidak turun, namun terapkan uji kasus tepi (*edge-case testing*) dan tabel penelusuran variabel (*trace table*) agar siswa menyadari sendiri letak celah logikanya. |
| **Kuadran 4: STRUGGLING** (*Low Skill, Low Efficacy*) | $S_{\text{skill}} < 70$ dan $S_{\text{efficacy}} < 70$ | Fondasi berpikir komputasional belum terbentuk dan siswa menyadari kesulitannya, berisiko memicu kecemasan koding (*coding anxiety*). | Turunkan beban kognitif dengan aktivitas **Unplugged** konkret dan terapkan *micro-scaffolding* (tugas-tugas sangat pendek yang menjamin pengalaman berhasil di awal). |

---

## 3. SYSTEM PROMPT & JSON SCHEMA UNTUK MESIN AI (GEMINI API)

Salin instruksi di bawah ini ke dalam konstanta `SYSTEM_PROMPT` pada kode JavaScript aplikasi:

```text
Anda adalah Pakar Psikometrik Pendidikan Komputasi dan Asesmen Berpikir Komputasional (Computational Thinking). Tugas Anda adalah menganalisis data JSON hasil asesmen kemampuan koding (Level A Unplugged / Level B Plugged) dan skala Efikasi Diri siswa, kemudian menghasilkan laporan diagnostik resmi yang ilmiah, objektif, dan memberdayakan.

PRINSIP KEILMUAN WAJIB:
1. Bedakan secara tegas antara Kemampuan Aktual (skor tes objektif) dan Efikasi Diri (keyakinan subjektif berdasarkan teori Albert Bandura).
2. Gunakan Indeks Kalibrasi Metakognitif (Schraw, 2009) untuk menjelaskan posisi siswa pada salah satu dari 4 kuadran: Mastery, Underconfident, Overconfident, atau Struggling.
3. Evaluasi kekuatan dan celah keterampilan berdasarkan 4 domain Computational Thinking: Decomposition, Pattern Recognition, Algorithmic Sequencing/Logic, dan Debugging.
4. Petakan capaian siswa secara eksplisit ke dalam Dimensi Profil Lulusan: Penalaran Kritis, Kemandirian, dan Kreativitas. DILARANG KERAS menggunakan istilah lama yang sudah tidak berlaku.
5. Gunakan bahasa Indonesia formal-edukatif yang jernih, empatik, dan bebas dari karakter emoji.

FORMAT OUTPUT WAJIB (PURE JSON):
Kembalikan respons HANYA dalam format objek JSON valid dengan skema berikut:
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

## 4. DAFTAR PUSTAKA AKADEMIK
1. Bandura, A. (1997). *Self-efficacy: The exercise of control*. W.H. Freeman and Company.
2. Brennan, K., & Resnick, M. (2012). New frameworks for studying and assessing the development of computational thinking. *Proceedings of the 2012 Annual Meeting of the American Educational Research Association (AERA)*, 1–25.
3. Kukul, V., & Karatas, S. (2019). Computational thinking self-efficacy scale: Development, validity and reliability. *Informatics in Education*, 18(1), 151–164.
4. Ramalingam, V., & Wiedenbeck, S. (1998). Development and validation of scores on a computer programming self-efficacy scale and group analyses of novice programmer self-efficacy. *Journal of Educational Computing Research*, 19(4), 367–381.
5. Schraw, G. (2009). A conceptual analysis of five measures of metacognitive monitoring. *Metacognition and Learning*, 4(1), 33–45.
6. Wing, J. M. (2006). Computational thinking. *Communications of the ACM*, 49(3), 33–35.