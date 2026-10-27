# INSTRUMEN ANGKET EFIKASI DIRI BAKU & BANK SOAL DIAGNOSTIK KODING

Dokumen ini berisi instrumen pengukuran psikometrik dan bank soal berpikir komputasional (*Computational Thinking*) yang menjadi data awal (*seed data*) di dalam aplikasi generator.

---

## BAGIAN 1: SKALA EFIKASI DIRI UMUM (12 BUTIR TERVALIDASI)
Diadaptasi dari *Computational Thinking Self-Efficacy Scale* (Kukul & Karatas, 2019) dan *Computer Programming Self-Efficacy Scale / CPSES* (Ramalingam & Wiedenbeck, 1998).

**Rentang Skala Likert ($1$ sampai $5$):**
- $1$ = Sangat Tidak Yakin
- $2$ = Tidak Yakin
- $3$ = Ragu-ragu / Cukup Yakin
- $4$ = Yakin
- $5$ = Sangat Yakin

### Sub-Skala 1: Penalaran Algoritmik (*Algorithmic Reasoning*)
1. Saya yakin dapat memecah masalah yang rumit menjadi langkah-langkah kecil yang lebih mudah diselesaikan (*Decomposition*).
2. Saya yakin dapat menemukan pola atau kemiripan dari beberapa permasalahan untuk mempercepat pencarian solusi (*Pattern Recognition*).
3. Saya yakin dapat menyusun urutan instruksi secara runtut dari awal hingga akhir agar sistem atau robot dapat menjalankan perintah dengan tepat (*Algorithmic Sequencing*).

### Sub-Skala 2: Ketekunan Pelacakan Kesalahan (*Debugging & Persistence*)
4. Ketika susunan instruksi atau kode yang saya buat tidak berjalan sesuai harapan, saya yakin dapat menemukan letak kesalahannya sendiri.
5. Saya tidak mudah menyerah dan yakin dapat memperbaiki kesalahan logika (*bug*) meskipun harus mencoba beberapa kali.
6. Saya yakin dapat menguji apakah solusi algoritma yang saya susun sudah benar-benar bebas dari kesalahan.

### Sub-Skala 3: Kemandirian Pemecahan Masalah (*Autonomy*)
7. Saya yakin dapat menyelesaikan tantangan logika atau pemrograman baru meskipun belum pernah melihat contoh yang persis sama sebelumnya.
8. Saya yakin dapat memahami petunjuk persoalan logika dan mengerjakannya secara mandiri tanpa harus selalu bergantung pada bantuan orang lain.
9. Saya yakin dapat menjelaskan alasan logis di balik langkah-langkah solusi yang saya buat kepada guru atau teman.

### Sub-Skala 4: Regulasi Diri pada Tugas Kompleks (*Self-Regulation*)
10. Saya tetap tenang dan fokus berpikir ketika menghadapi persoalan logika atau blok kode yang terlihat panjang.
11. Saya yakin dapat memilih cara yang paling efisien (paling ringkas dan tepat) dari beberapa alternatif solusi yang ada.
12. Saya yakin kemampuan saya dalam menyusun logika pemrograman akan terus berkembang melalui latihan yang konsisten.

---

## BAGIAN 2: TASK-SPECIFIC CONFIDENCE SLIDER (KALIBRASI PER SOAL)
Setiap kali siswa memilih jawaban pada butir soal tes (baik Level A maupun Level B), aplikasi wajib meminta input tingkat keyakinan spesifik tugas:

- **Pertanyaan Kalibrasi:** *"Seberapa yakin kamu bahwa jawaban dan alur logika yang kamu pilih pada soal ini sudah tepat?"*
- **Nilai Input ($1 - 5$):**
  - Skala $1$: Hanya menebak ($20\%$)
  - Skala $2$: Kurang yakin ($40\%$)
  - Skala $3$: Cukup yakin ($60\%$)
  - Skala $4$: Yakin benar ($80\%$)
  - Skala $5$: Sangat yakin dan dapat membuktikannya ($100\%$)

---

## BAGIAN 3: BANK SOAL LEVEL A (UNPLUGGED - LOGIKA DASAR)

### Soal A1 - Domain: Decomposition (Dekomposisi)
- **Konteks:** Rani ingin merancang instruksi untuk robot pembuat roti lapis otomatis. Sebelum menulis instruksi detail, ia harus memecah tugas besar "Membuat Roti Lapis" menjadi tahapan-tahapan kecil yang logis.
- **Pertanyaan:** Manakah pembagian sub-tugas yang paling runtut dan valid di bawah ini?
- **Opsi Jawaban:**
  - `A`: (1) Sajikan roti, (2) Siapkan bahan, (3) Oleskan selai, (4) Tutup roti.
  - `B`: (1) Siapkan dua lembar roti dan selai, (2) Oleskan selai pada permukaan roti pertama, (3) Tangkupkan roti kedua di atasnya, (4) Letakkan di piring saji.
  - `C`: (1) Oleskan selai di atas piring, (2) Ambil dua lembar roti, (3) Masukkan ke kotak bekal.
  - `D`: (1) Siapkan piring saji, (2) Tangkupkan kedua roti, (3) Buka tutup botol selai.
- **Kunci Jawaban:** `B`
- **Indikator Kompetensi:** Menguraikan proses kompleks menjadi sub-proses sekuensial yang tidak saling tumpang tindih.

### Soal A2 - Domain: Pattern Recognition (Pengenalan Pola)
- **Konteks:** Sebuah lampu indikator pada panel robot menyala secara bergantian mengikuti pola siklus berikut:
  `Merah -> Biru -> Biru -> Hijau -> Merah -> Biru -> Biru -> Hijau -> Merah -> ...`
- **Pertanyaan:** Jika pola siklus tersebut terus berulang secara konsisten, warna apakah yang akan menyala pada urutan ke-$11$ dan ke-$12$?
- **Opsi Jawaban:**
  - `A`: Merah dan Biru
  - `B`: Biru dan Hijau
  - `C`: Biru dan Biru
  - `D`: Hijau dan Merah
- **Kunci Jawaban:** `B`
- **Indikator Kompetensi:** Mengidentifikasi siklus berulang berukuran $4$ elemen untuk memprediksi keadaan pada indeks ke-$n$.

### Soal A3 - Domain: Algorithmic Sequencing (Urutan Algoritma Spasial)
- **Konteks:** Sebuah robot kurir berada di petak koordinat $(1,1)$ pada lantai berukuran $4 \times 4$ dan sedang menghadap ke arah **TIMUR (Kanan)**. Titik paket berada di koordinat $(3,2)$ (dua petak ke kanan, satu petak ke atas/utara). Instruksi `MAJU` menggerakkan robot $1$ petak sesuai arah hadapnya.
- **Pertanyaan:** Rangkaian instruksi manakah yang membawa robot tepat berhenti di petak $(3,2)$?
- **Opsi Jawaban:**
  - `A`: `MAJU` -> `MAJU` -> `HADAP KIRI (UTARA)` -> `MAJU`
  - `B`: `MAJU` -> `HADAP KANAN (SELATAN)` -> `MAJU` -> `MAJU`
  - `C`: `HADAP KIRI (UTARA)` -> `MAJU` -> `MAJU` -> `MAJU`
  - `D`: `MAJU` -> `MAJU` -> `MAJU` -> `HADAP KIRI (UTARA)`
- **Kunci Jawaban:** `A`
- **Indikator Kompetensi:** Melakukan penelusuran langkah (*spatial tracing*) berdasarkan orientasi arah dan perpindahan koordinat.

### Soal A4 - Domain: Debugging (Pelacakan Kesalahan Urutan)
- **Konteks:** Perhatikan algoritma mencuci tangan otomatis yang disusun oleh Budi:
  1. Buka keran air
  2. Basahi kedua tangan
  3. Keringkan tangan menggunakan handuk bersih
  4. Gosok seluruh permukaan tangan dengan sabun selama $20$ detik
  5. Bilas tangan dengan air mengalir hingga bersih
  6. Tutup keran air
- **Pertanyaan:** Algoritma di atas mengandung satu kesalahan logika (*bug*). Perbaikan manakah yang paling tepat?
- **Opsi Jawaban:**
  - `A`: Langkah 1 seharusnya diletakkan di urutan paling akhir.
  - `B`: Langkah 3 seharusnya dipindahkan ke urutan paling akhir setelah Langkah 6.
  - `C`: Langkah 4 seharusnya dijalankan sebelum Langkah 1.
  - `D`: Langkah 5 tidak diperlukan dan harus dihapus.
- **Kunci Jawaban:** `B`
- **Indikator Kompetensi:** Mendeteksi anomali urutan prasyarat (*precondition violation*) dan merumuskan koreksi yang tepat.

---

## BAGIAN 4: BANK SOAL LEVEL B (PLUGGED - ALGORITMA & PEMROGRAMAN)

### Soal B1 - Domain: Variables & State Mutation (Variabel & Data)
- **Konteks:** Perhatikan potongan *pseudocode* berikut ini:
  ```text
  skor = 10
  bonus = 5
  skor = skor + bonus
  skor = skor - 3
  ```
- **Pertanyaan:** Berapakah nilai akhir yang tersimpan di dalam variabel `skor` setelah seluruh baris kode dieksekusi?
- **Opsi Jawaban:**
  - `A`: $10$
  - `B`: $15$
  - `C`: $12$
  - `D`: $8$
- **Kunci Jawaban:** `C`
- **Indikator Kompetensi:** Melacak perubahan nilai variabel (*variable state tracking*) secara sekuensial.

### Soal B2 - Domain: Conditionals & Boolean Logic (Percabangan)
- **Konteks:** Sistem penyiram tanaman otomatis bekerja dengan aturan kode berikut:
  ```text
  JIKA (kelembapan < 40) DAN (status_hujan == SALAH) MAKA:
      pompa = "AKTIF"
  SELAIN ITU:
      pompa = "NONAKTIF"
  ```
- **Pertanyaan:** Apabila sensor membaca `kelembapan = 30` dan `status_hujan = BENAR`, apakah nilai variabel `pompa`?
- **Opsi Jawaban:**
  - `A`: `"AKTIF"`
  - `B`: `"NONAKTIF"`
  - `C`: `"ERROR"`
  - `D`: `"AKTIF SEBENTAR"`
- **Kunci Jawaban:** `B`
- **Indikator Kompetensi:** Mengevaluasi ekspresi logika majemuk menggunakan operator konjungsi (`DAN` / `AND`).

### Soal B3 - Domain: Loops & Efficiency (Perulangan)
- **Konteks:** Untuk menggambar persegi, sebuah pena robot menjalankan instruksi berikut:
  `GarisMaju(50) -> PutarKanan(90) -> GarisMaju(50) -> PutarKanan(90) -> GarisMaju(50) -> PutarKanan(90) -> GarisMaju(50) -> PutarKanan(90)`
- **Pertanyaan:** Struktur blok perulangan manakah yang menghasilkan gambar yang **identik** namun paling efisien?
- **Opsi Jawaban:**
  - `A`: `ULANGI 2 KALI { GarisMaju(50); PutarKanan(90); }`
  - `B`: `ULANGI 4 KALI { GarisMaju(50); PutarKanan(90); }`
  - `C`: `ULANGI 4 KALI { GarisMaju(50); } -> PutarKanan(90)`
  - `D`: `ULANGI SELAMANYA { GarisMaju(50); PutarKanan(90); }`
- **Kunci Jawaban:** `B`
- **Indikator Kompetensi:** Mengabstraksi sekuens instruksi repetitif ke dalam struktur perulangan terbatas (*bounded loop*).

### Soal B4 - Domain: Code Debugging (Pelacakan Kesalahan Kode)
- **Konteks:** Program berikut dirancang untuk menampilkan hitungan mundur dari $5$ hingga $1$, lalu berhenti:
  ```text
  angka = 5
  SELAMA (angka > 0) LAKUKAN:
      Tampilkan(angka)
      angka = angka + 1
  ```
- **Pertanyaan:** Saat dijalankan, program mengalami perulangan tak terbatas (*infinite loop*). Apa penyebab dan solusi perbaikannya?
- **Opsi Jawaban:**
  - `A`: Nilai awal `angka` seharusnya diatur menjadi $0$.
  - `B`: Kondisi `angka > 0` seharusnya diganti menjadi `angka == 5`.
  - `C`: Baris `angka = angka + 1` membuat nilai terus bertambah menjauhi batas berhenti; seharusnya diubah menjadi `angka = angka - 1`.
  - `D`: Baris `Tampilkan(angka)` harus dihapus dari dalam blok perulangan.
- **Kunci Jawaban:** `C`
- **Indikator Kompetensi:** Menganalisis kondisi terminasi perulangan (*loop termination condition*) dan memperbaiki kesalahan pembaruan variabel pencacah.