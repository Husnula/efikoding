# SISTEM DESAIN KORPORAT & PANDUAN GAYA (DESIGN SYSTEM)
## PLATFORM EFIKODING: CLEAN CORPORATE & MINIMALIST SAAS

**Versi Dokumen:** 1.0.0  
**Filosofi Desain:** *Clean Corporate, Objective Educational SaaS, & High-Legibility Typography*  
**Prinsip Utama:** Ketelitian Keilmuan, Antarmuka Minimalis Bebas Distraksi, serta Kepatuhan Mutlak Aturan Anti-Slop.  

---

## 1. PANDUAN ANTI-SLOP KETAT (STRICT ANTI-SLOP RULES)

Sistem antarmuka EfiKoding wajib mematuhi tiga larangan estetika berikut:
1. **DILARANG GRADASI UNGU-PINK (*NO PURPLE-TO-PINK GRADIENTS*):**
   - Hindari penggunaan efek *glow* kecerdasan buatan sintetis berlebihan seperti kombinasi `indigo-600` ke `fuchsia-500` atau gradasi ungu-magenta.
   - Gunakan warna tunggal korporat yang kokoh (*solid corporate blue & deep slate*).
2. **DILARANG GAYA NEO-BRUTALISM (*NO NEO-BRUTALISM*):**
   - Hindari garis batas hitam tebal berlebih (`border-4 border-black`) dan bayangan kaku 90 derajat (`shadow-[4px_4px_0px_#000]`).
   - Gunakan garis tepi halus (`border-slate-200`), permukaan kartu putih murni (`bg-white`), dan bayangan mikroskopis (*subtle elevation*).
3. **DILARANG KARAKTER EMOJI DI SELURUH ANTARMUKA & LAPORAN:**
   - Dilarang keras menaruh karakter emoji (seperti 🚀, 💡, 🔥, 👍, 🧠) baik pada tombol, label metrik, kartu ringkasan, maupun teks laporan resmi yang dihasilkan AI.
   - Gunakan secara konsisten ikon vektor terstandardisasi dari **Lucide Icons** (`lucide-react` atau pustaka CDN Lucide).

---

## 2. PALET WARNA SISTEM (COLOR PALETTE & DESIGN TOKENS)

### 2.1 Warna Netral & Fondasi Layar (Neutral Foundation)

| Token Nama | Nilai HEX | Kelas Tailwind | Penggunaan Spesifik |
| :--- | :--- | :--- | :--- |
| `surface-ground` | `#F8FAFC` | `bg-slate-50` | Latar belakang kanvas aplikasi |
| `surface-card` | `#FFFFFF` | `bg-white` | Kartu panel, kontainer formulir, lembar pratinjau |
| `surface-subtle` | `#F1F5F9` | `bg-slate-100` | Latar belakang input non-aktif, *header* tabel skor |
| `border-default` | `#E2E8F0` | `border-slate-200` | Garis pembatas kartu, sel tabel, pemisah panel |
| `border-hover` | `#CBD5E1` | `border-slate-300` | Garis pembatas saat kursor mendekat (*hover state*) |
| `text-primary` | `#0F172A` | `text-slate-900` | Tajuk utama, nilai skor numerik besar, kop dokumen |
| `text-secondary` | `#475569` | `text-slate-600` | Teks penjelasan, label formulir, narasi deskriptif |
| `text-muted` | `#94A3B8` | `text-slate-400` | *Placeholder*, unit metrik, indikator non-aktif |

### 2.2 Warna Aksi Korporat (Brand Corporate)

| Token Nama | Nilai HEX | Kelas Tailwind | Penggunaan Spesifik |
| :--- | :--- | :--- | :--- |
| `brand-primary` | `#2563EB` | `bg-blue-600` | Tombol utama, pemicu proses, bilah progres aktif |
| `brand-hover` | `#1D4ED8` | `bg-blue-700` | Kondisi *hover* tombol utama |
| `brand-surface` | `#EFF6FF` | `bg-blue-50` | Latar belakang kartu sorotan, *badge* status aktif |
| `brand-border` | `#BFDBFE` | `border-blue-200` | Garis tepi elemen terpilih (*selected state*) |

### 2.3 Warna Status 4 Kuadran Psikometrik & Kalibrasi Metakognitif

| Kuadran / Status | Warna Utama | Permukaan Lembut | Garis Tepi | Representasi Keilmuan |
| :--- | :--- | :--- | :--- | :--- |
| **Q1: MASTERY** | `#059669` (`emerald-600`) | `#ECFDF5` (`emerald-50`) | `#A7F3D0` (`emerald-200`) | Kemampuan tinggi & keyakinan tinggi |
| **Q2: UNDERCONFIDENT** | `#D97706` (`amber-600`) | `#FFFBEB` (`amber-50`) | `#FDE68A` (`amber-200`) | Kemampuan tinggi namun ragu diri ($I_{\text{cal}} < -15$) |
| **Q3: OVERCONFIDENT** | `#EA580C` (`orange-600`) | `#FFF7ED` (`orange-50`) | `#FED7AA` (`orange-200`) | Keyakinan tinggi namun konsep keliru ($I_{\text{cal}} > +15$) |
| **Q4: STRUGGLING** | `#E11D48` (`rose-600`) | `#FFF1F2` (`rose-50`) | `#FECDD3` (`rose-200`) | Membutuhkan intervensi konkret dasar |
| **Well-Calibrated** | `#0284C7` (`sky-600`) | `#F0F9FF` (`sky-50`) | `#BAE6FD` (`sky-200`) | Kalibrasi akurat ($-15 \le I_{\text{cal}} \le +15$) |

---

## 3. SISTEM TIPOGRAFI (TYPOGRAPHY SYSTEM)

Sistem menggunakan font *sans-serif* dengan tingkat legibilitas tinggi untuk UI dan font *monospace* berjarak tetap untuk ekspresi kode/pseudocode:

- **Font Antarmuka & Laporan:** `Inter`, `Plus Jakarta Sans`, atau `system-ui, -apple-system, sans-serif`
- **Font Kode & Pseudocode:** `JetBrains Mono`, `Fira Code`, atau `ui-monospace, monospace`

### Skala Ukuran Teks (Type Scale)

| Level Hirarki | Ukuran / Line Height | Bobot (*Weight*) | Penggunaan |
| :--- | :--- | :--- | :--- |
| **Display 1** | `28px / 36px` (`text-2xl` / `text-3xl`) | `font-bold` (700) | Judul laporan, kop dokumen resmi |
| **Heading 1** | `20px / 28px` (`text-xl`) | `font-semibold` (600) | Judul panel split-screen, nama siswa utama |
| **Heading 2** | `16px / 24px` (`text-base`) | `font-semibold` (600) | Sub-judul bagian laporan, judul domain CT |
| **Heading 3** | `14px / 20px` (`text-sm`) | `font-medium` (500) | Label kartu metrik, header tabel |
| **Body Text** | `14px / 22px` (`text-sm`) | `font-normal` (400) | Teks narasi laporan, petunjuk soal |
| **Body Small** | `12px / 18px` (`text-xs`) | `font-normal` (400) | Catatan kaki, petunjuk slider, indikator formula |
| **Code Block** | `13px / 20px` (`text-xs font-mono`) | `font-medium` (500) | Potongan *pseudocode*, variabel program |

---

## 4. SPESIFIKASI KOMPONEN UTAMA (COMPONENT TOKENS)

### 4.1 Tombol (Button Components)
- **Tombol Utama (Primary Button):**
  `bg-blue-600 hover:bg-blue-700 text-white font-medium px-4 py-2.5 rounded-lg shadow-sm transition-colors flex items-center justify-center gap-2 focus:ring-2 focus:ring-blue-500 focus:ring-offset-1`
- **Tombol Sekunder (Secondary Button):**
  `bg-white hover:bg-slate-50 text-slate-700 border border-slate-200 font-medium px-4 py-2.5 rounded-lg shadow-sm transition-colors flex items-center justify-center gap-2`
- **Tombol Sukses / Cetak (Action Button):**
  `bg-emerald-600 hover:bg-emerald-700 text-white font-medium px-4 py-2.5 rounded-lg shadow-sm transition-colors flex items-center justify-center gap-2`

### 4.2 Slider Kalibrasi Keyakinan (Confidence Slider)
- **Struktur Trek:** Garis trek `h-2 bg-slate-200 rounded-lg` dengan pengisi progres aktif `bg-blue-600`.
- **Thumb:** Lingkaran pemilih `w-5 h-5 bg-white border-2 border-blue-600 rounded-full shadow cursor-pointer`.
- **Indikator Skala:** 5 penanda diskrit ($1$ s/d $5$) dilengkapi keterangan verbal:
  - Skala 1: *Menebak (20%)*
  - Skala 2: *Kurang Yakin (40%)*
  - Skala 3: *Cukup Yakin (60%)*
  - Skala 4: *Yakin Benar (80%)*
  - Skala 5: *Sangat Yakin & Terbukti (100%)*

### 4.3 Matriks 4 Kuadran Grafik Kanvas (Canvas & SVG Grid)
- **Dimensi Kanvas:** Rasio aspek $1:1$ (standar $360\text{px} \times 360\text{px}$ pada desktop).
- **Latar Kuadran:**
  - Kuadran 1 (Kanan Atas): Latar `rgba(16, 185, 129, 0.05)` (Emerald)
  - Kuadran 2 (Kiri Atas): Latar `rgba(245, 158, 11, 0.05)` (Amber)
  - Kuadran 3 (Kanan Bawah): Latar `rgba(249, 115, 22, 0.05)` (Orange)
  - Kuadran 4 (Kiri Bawah): Latar `rgba(244, 63, 94, 0.05)` (Rose)
- **Garis Sumbu Silang ($X=70, Y=70$):** Garis putus-putus berbobot `1.5px` dengan warna `#94A3B8` (`slate-400`).
- **Titik Koordinat Siswa:** Lingkaran ganda dengan radius inti `6px` warna `#2563EB` dan lingkaran halo `12px` beropasitas `30%`.

### 4.4 Penanda Interaktif Penyuntingan Langsung (Inline Editing)
Elemen laporan yang dapat diedit langsung menggunakan atribut `contenteditable="true"` memiliki panduan visual:
- **Kondisi Normal:** Tampilan teks biasa tanpa garis yang mengganggu pembacaan dokumen.
- **Kondisi Sorot (*Hover State*):** `border border-dashed border-blue-400 bg-blue-50/30 rounded p-1.5 transition-all cursor-text`.
- **Kondisi Fokus (*Active Focus*):** `outline-none ring-2 ring-blue-500/30 border border-blue-500 bg-white rounded p-1.5`.

---

## 5. STANDAR EKSPOR & GAYA CETAK (@MEDIA PRINT)

Agar lembar kerja pratinjau di layar memiliki kesesuaian identik (*100% parity*) dengan hasil cetak fisik maupun dokumen Word:

```css
@media print {
  body {
    background-color: #FFFFFF !important;
    color: #0F172A !important;
    font-size: 11pt !important;
  }
  
  /* Sembunyikan elemen navigasi dan panel kiri */
  header, nav, #panel-kiri-kontrol, .no-print {
    display: none !important;
  }
  
  /* Bentangkan panel laporan menjadi satu halaman A4 penuh */
  #panel-kanan-laporan {
    width: 100% !important;
    margin: 0 !important;
    padding: 0 !important;
    box-shadow: none !important;
    border: none !important;
  }
  
  /* Cegah pemotongan tabel atau diagram di tengah halaman */
  .print-avoid-break {
    page-break-inside: avoid;
    break-inside: avoid;
  }
  
  /* Pastikan warna latar kartu dan border tetap tercetak */
  * {
    -webkit-print-color-adjust: exact !important;
    print-color-adjust: exact !important;
  }
}
```
