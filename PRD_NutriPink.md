# Product Requirements Document (PRD)

## NutriPink — Web App Kalkulator Gizi & Pelacak Makro Harian

| Atribut | Detail |
|---|---|
| **Nama Produk** | NutriPink (*"Sahabat Nutrisi & Makro Sehatmu"*) |
| **Versi Dokumen** | 1.0 (Draft) |
| **Tanggal** | 20 Oktober 2026 |
| **Platform** | Web App responsif (mobile-first, desktop, tablet) |
| **Bahasa Utama** | Bahasa Indonesia (`lang="id"`), format angka `id-ID` |
| **Referensi Desain** | `DESIGN.md` (design system "Lush Nutrition") dan `code.html` (prototipe layar Kalkulator Harian) |
| **Status** | Draft untuk review |

---

## 1. Ringkasan Eksekutif

NutriPink adalah web app pelacak kalori dan makronutrien (karbohidrat, protein, lemak) harian. Pengguna mencatat makanan per sesi makan, lalu melihat sisa kalori, progres makro, dan asupan air secara langsung. Pengguna juga bisa menghitung target kalori dan makro pribadi dari data tubuh dan tujuan mereka.

Pendekatan produknya adalah **"micro-ritual"**: pencatatan harian dibuat cepat, ringan, dan menyenangkan, bukan klinis atau restriktif. Bahasa visual yang dipakai adalah palet rose/strawberry yang hangat, kartu bersudut membulat, dan visualisasi makro berwarna pastel.

### 1.1 Visi
> Menjadikan pelacakan nutrisi harian sesederhana mencatat satu kali makan dalam kurang dari 15 detik, dengan pengalaman yang memotivasi, bukan menghakimi.

### 1.2 Tujuan Produk
1. Memudahkan pengguna mengetahui **sisa kalori dan makro** harian secara *real-time*.
2. Menyediakan **kalkulator target** (BMR/TDEE → kalori & makro) yang akurat dan mudah dipahami.
3. Menyediakan **pencatatan makanan yang cepat** lewat pencarian, pilihan populer, dan input manual.
4. Membangun **kebiasaan konsisten** lewat riwayat, tren, dan umpan balik positif.
5. Menyajikan **konten dan basis data makanan lokal Indonesia** (nasi merah, tempe, ayam bakar, dll.).

### 1.3 Non-Tujuan (Out of Scope v1.0)
- Rekomendasi diagnosis atau terapi medis (bukan alat medis).
- Pemindaian barcode / pengenalan makanan dari foto (kandidat v2).
- Fitur sosial / komunitas / *leaderboard*.
- Integrasi wearable (Apple Health, Google Fit, dll.).
- Aplikasi native iOS/Android (v1.0 adalah web app/PWA).

---

## 2. Latar Belakang & Masalah

| Masalah Pengguna | Dampak | Respons NutriPink |
|---|---|---|
| Aplikasi pelacak kalori terasa rumit dan penuh angka | Pengguna berhenti mencatat dalam 1–2 minggu | UI kartu bersih, input minimal, pilihan populer satu-ketuk |
| Basis data makanan didominasi makanan Barat | Pengguna Indonesia harus input manual | Basis data makanan Indonesia + input manual fleksibel |
| Tidak tahu berapa target kalori dan makro yang tepat | Mengira-ngira, hasil tidak optimal | Kalkulator target berbasis rumus ilmiah |
| Tampilan klinis dan terasa menghakimi | Demotivasi, relasi negatif dengan makanan | Tone hangat, umpan balik positif, tanpa bahasa "gagal/dosa" |

---

## 3. Target Pengguna & Persona

### 3.1 Segmen Utama
- **Individu sadar kesehatan** yang ingin menjaga pola makan.
- **Penggiat kebugaran** yang menargetkan protein dan makro tertentu.
- **Pemakan sadar (*mindful eaters*)** yang ingin memahami komposisi makanan tanpa diet ekstrem.

### 3.2 Persona

**Persona 1 — Rara (26, karyawan kantoran)**
- *Tujuan:* menurunkan berat badan 4 kg secara sehat.
- *Pain point:* sibuk, sering lupa mencatat, bingung porsi.
- *Kebutuhan:* pencatatan cepat via HP, pengingat lembut, ringkasan sisa kalori yang jelas.

**Persona 2 — Dimas (30, penggiat gym)**
- *Tujuan:* menambah massa otot (*lean bulk*), target protein ≥ 1,8 g/kg.
- *Pain point:* sulit menghitung makro untuk masakan rumahan.
- *Kebutuhan:* input makro manual, target makro kustom, tren mingguan.

**Persona 3 — Bu Sari (42, ibu rumah tangga)**
- *Tujuan:* menjaga pola makan keluarga dan mengontrol gula.
- *Pain point:* tidak terbiasa dengan aplikasi rumit.
- *Kebutuhan:* UI sederhana, bahasa Indonesia, makanan lokal.

---

## 4. Ruang Lingkup Produk & Peta Navigasi

Prototipe desain memiliki tiga area navigasi utama (navbar desktop, *bottom nav* mobile):

| Menu | `data-path` | Ikon | Status di Desain | Status PRD |
|---|---|---|---|---|
| **Kalkulator Harian** | `kalkulator-harian` | `calculate` | ✅ Sudah didesain (`code.html`) | MVP |
| **Riwayat Makanan** | `riwayat-makanan` | `restaurant_menu` | ⚠️ Belum didesain | MVP |
| **Target & Goal** | `target-dan-goal` | `track_changes` | ⚠️ Belum didesain | MVP |

> **Catatan:** Dua halaman terakhir baru terdefinisi sebagai item navigasi. Spesifikasi fungsionalnya di PRD ini adalah **usulan** dan perlu didesain (lihat Bagian 12).

Elemen global:
- **Header tetap** (logo NutriPink, navigasi, *chip* ringkasan kalori `1,420 / 2,000 kkal`, avatar profil).
- **Footer** dengan tagline dan hak cipta.
- **Bottom navigation** (mobile < 768px).

---

## 5. Fitur & Kebutuhan Fungsional

Prioritas memakai skema **MoSCoW**: **M**ust, **S**hould, **C**ould, **W**on't. Status *(Ada di desain)* berarti sudah tergambar di `code.html`.

### 5.1 Modul A — Kalkulator Harian (Dashboard)

#### A1. Navigasi Tanggal — **Must** *(Ada di desain)*
- Pengguna dapat berpindah hari lewat tombol sebelumnya/berikutnya (`chevron_left` / `chevron_right`).
- Label tanggal memakai format lokal Indonesia, mis. "Rabu, 24 Mei".
- Label default "Hari Ini". Hari yang berbeda memuat data log harinya masing-masing.
- **Kriteria Penerimaan:**
  - Mengetuk tombol berikutnya/sebelumnya memuat data hari tersebut dalam ≤ 500 ms (dari cache lokal).
  - Tombol "berikutnya" dinonaktifkan atau diberi batas wajar untuk tanggal masa depan (usulan: boleh sampai +1 hari untuk perencanaan).
  - *(Usulan)* Mengetuk label tanggal membuka *date picker*.

#### A2. Kartu Target Nutrisi (Ring Kalori) — **Must** *(Ada di desain)*
- Menampilkan *radial gauge* (SVG, `stroke-linecap: round`) dengan angka **Sisa kkal** di tengah.
- Panel samping menampilkan: **Terpakai**, **Target**, dan **Persentase**.
- *Badge* "Goal: X kkal" di pojok kanan atas kartu.
- **Aturan perhitungan:**
  - `Sisa = Target − Terpakai` (tidak ditampilkan negatif di tengah ring; minimum `0`).
  - `Persentase = min(Terpakai / Target, 100%)`, dibulatkan 1 desimal.
  - Offset ring = `keliling − (progres × keliling)`, dengan `keliling = 2π × 50 ≈ 314,159`.
- **Kriteria Penerimaan:**
  - Ring dan angka diperbarui otomatis ≤ 100 ms setelah makanan ditambah atau dihapus, dengan animasi transisi ~700 ms (`ease-out`).
  - Angka memakai format `id-ID` (mis. `1.340 kkal`).
  - *(Usulan)* Jika Terpakai > Target, ring berubah ke state "melebihi target" dengan teks informatif dan netral (mis. "Melebihi 120 kkal dari target"), tanpa warna merah agresif.

#### A3. Bar Progres Makro — **Must** *(Ada di desain)*
- Tiga bar linear (tinggi 8px, ujung membulat): **Karbohidrat**, **Protein**, **Lemak**.
- Setiap baris menampilkan `gram terpakai / gram target` (mis. `165g / 240g`).
- Lebar bar = `min(round(terpakai/target × 100), 100)%`.
- **Kriteria Penerimaan:** Semua bar diperbarui bersamaan dengan ring kalori dalam satu siklus `recalculateAll`.

#### A4. Formulir "Catat Makanan" — **Must** *(Ada di desain)*

| Field | Tipe | Validasi | Catatan |
|---|---|---|---|
| Sesi Waktu Makan | `select` | Wajib | Sarapan / Makan Siang / Makan Malam / Camilan. Default sesuai jam saat ini *(usulan)*. |
| Nama Makanan / Minuman | `text` + ikon cari | Wajib, tidak kosong | Mendukung pencarian/autocomplete dari basis data *(Should)*. |
| Porsi (Gram/Satuan) | `number` + stepper − / + | Min 10, kelipatan 5 | Stepper ±25. Default 100. |
| Estimasi Kalori (kkal) | `number` | Wajib, ≥ 1 | Otomatis diskalakan saat porsi diubah (jika sudah terisi). |
| Karbo / Protein / Lemak (g) | `number` ×3 | ≥ 0, opsional | Opsional, default 0. |

- Tombol utama **"+ Tambah Makanan"** (tinggi 48px, `#FF4D8D`, `scale(0.98)` saat ditekan).
- **Perilaku:**
  - Setelah submit sukses: item masuk ke daftar sesi terkait, form di-*reset* (porsi kembali 100), dan seluruh kalkulasi dihitung ulang.
  - Input nama diberi *sanitasi* (`escapeHTML`) untuk mencegah XSS.
  - Mengubah porsi lewat stepper menskalakan kalori secara proporsional: `kalori_baru = kalori_lama / porsi_lama × porsi_baru`.
- **Kriteria Penerimaan:**
  - Form tidak bisa dikirim jika nama kosong atau kalori ≤ 0, dengan pesan error inline.
  - Item baru muncul dengan animasi *fade-in*.
  - Makro tidak terisi → dihitung sebagai 0 (tidak error).
  - *(Usulan)* Jika kalori kosong tetapi makro terisi, sistem menyarankan kalori otomatis: `4×karbo + 4×protein + 9×lemak`.

#### A5. Pilihan Populer Cepat (Quick Add) — **Must** *(Ada di desain)*
- *Chip* satu-ketuk yang mengisi otomatis form (nama, kalori, makro, porsi 150g, sesi yang disarankan).
- Contoh di desain: 🥣 Oatmeal Pisang (280k), 🍗 Nasi Merah + Ayam (450k), 🥑 Alpukat Segar (160k), 🫐 Greek Yogurt (130k).
- Pada mobile, layar menggulir halus ke form setelah chip dipilih.
- **Peningkatan (Should):** daftar populer menjadi dinamis berdasarkan **makanan yang sering/terakhir dicatat pengguna**.

#### A6. Diary Makanan per Sesi — **Must** *(Ada di desain)*
Empat kartu sesi: **Sarapan Pagi** (`wb_twilight`), **Makan Siang** (`light_mode`), **Makan Malam** (`dark_mode`), **Camilan & Minuman**.
- Header kartu: ikon, nama sesi, **subtotal** (`X kkal • K: Xg • P: Xg • L: Xg`), tombol **"+ Tambah"**.
- Baris item: ikon makanan, nama (terpotong jika panjang), deskripsi porsi, kalori tebal, *pill* makro `K / P / L`, tombol hapus.
- Tombol **"+ Tambah"** memilih sesi terkait pada form dan memberi fokus ke input nama.
- *Empty state*: teks ramah "Belum ada camilan yang dicatat hari ini."
- **Kriteria Penerimaan:**
  - Menghapus item langsung memperbarui subtotal sesi dan total harian.
  - Saat daftar kosong, *empty state* muncul kembali.
  - *(Should)* Konfirmasi atau *undo* (toast "Dibatalkan?" 5 detik) setelah hapus.
  - *(Should)* Item dapat **diedit** (porsi dan nilai gizi) lewat stepper `+/−` seperti spesifikasi design system ("swipe atau hover memunculkan stepper dan delete").
  - *(Could)* Salin item ke sesi/hari lain.

#### A7. Banner Motivasi — **Should** *(Ada di desain)*
- Banner gradasi dengan pesan dinamis berdasarkan persentase pencapaian (mis. "Kamu telah memenuhi 63% kebutuhan nutrisi harian. Pertahankan konsistensi!").
- Pesan bervariasi menurut kondisi: <30%, 30–90%, 90–110%, >110%, protein tercapai, dll. Tone selalu positif dan non-menghakimi.

#### A8. Pelacak Hidrasi (Air Minum) — **Must** *(Ada di desain)*
- Menampilkan `X ml dari target 2.000 ml (N gelas)` dan 8 ikon gelas (`local_drink`) yang terisi sesuai jumlah.
- Tombol `+` / `−` mengubah **±250 ml** per gelas; batas 0–3.500 ml.
- Gelas terisi: warna `primary`; kosong: `outline-variant`.
- **Aturan:** `gelas = round(ml / 250)`.
- **Peningkatan:** target air bisa dikustomisasi (default dihitung dari berat badan ≈ 30–35 ml/kg).

#### A9. Chip Ringkasan di Header — **Should** *(Ada di desain)*
- Chip `🔥 1,420 / 2,000 kkal` di header harus **sinkron** dengan data harian aktual (bukan angka statis).

---

### 5.2 Modul B — Target & Goal (Kalkulator Gizi)

*Halaman ini tertera di navigasi, tetapi belum didesain. Spesifikasi berikut adalah usulan.*

#### B1. Input Profil — **Must**
| Input | Tipe | Validasi |
|---|---|---|
| Jenis kelamin | Segmented toggle (Pria / Wanita) | Wajib |
| Usia | Angka | 15–100 tahun |
| Tinggi badan | Angka (cm) | 100–250 |
| Berat badan | Angka (kg) | 30–300 |
| Tingkat aktivitas | Pilihan | Wajib |
| Tujuan | Chip | Turun BB / Jaga BB / Naik BB (otot) |
| Kecepatan perubahan | Pilihan | Pelan / Sedang / Cepat (dengan batas aman) |
| Satuan energi | Segmented toggle | `kkal` ↔ `kJ` |

#### B2. Perhitungan Otomatis — **Must**

**BMR (Mifflin-St Jeor):**
- Pria: `BMR = 10×BB + 6,25×TB − 5×usia + 5`
- Wanita: `BMR = 10×BB + 6,25×TB − 5×usia − 161`

**TDEE = BMR × faktor aktivitas**

| Aktivitas | Faktor |
|---|---|
| Sedentari (minim gerak) | 1,2 |
| Ringan (olahraga 1–3×/minggu) | 1,375 |
| Sedang (3–5×/minggu) | 1,55 |
| Aktif (6–7×/minggu) | 1,725 |
| Sangat aktif (fisik berat/2×/hari) | 1,9 |

**Target kalori** = TDEE ± penyesuaian tujuan:
- Turun BB: defisit 10–20% (maks ≈ 500–750 kkal/hari).
- Jaga BB: 0%.
- Naik BB: surplus 5–15%.

**Pengaman (*guardrail*):** target kalori tidak boleh turun di bawah batas minimum aman (usulan: **1.200 kkal wanita / 1.500 kkal pria**), dengan pesan edukatif jika hasil perhitungan lebih rendah.

**Distribusi makro default** (dapat diubah pengguna; satuan `g` ↔ `%`):

| Tujuan | Karbo | Protein | Lemak |
|---|---|---|---|
| Turun BB | ~40% | ~30% | ~30% |
| Jaga BB | ~50% | ~20% | ~30% |
| Naik BB | ~50% | ~25% | ~25% |

Konversi ke gram: karbo & protein **4 kkal/g**, lemak **9 kkal/g**.

*Contoh validasi dari prototipe:* target 2.100 kkal ≈ Karbo 240 g (960) + Protein 130 g (520) + Lemak 65 g (585) = 2.065 kkal, mendekati target.

#### B3. Tampilan Hasil — **Must**
- Kartu hasil: BMR, TDEE, target kalori, target makro (gram dan persen), target air.
- Tombol **"Simpan Target"** (primary) dan opsi **"Sesuaikan Manual"** (override target).
- Target tersimpan langsung memperbarui Dashboard (ring, bar makro, header).

#### B4. Goal Tambahan — **Should**
- Target berat badan dan tenggat; estimasi waktu pencapaian.
- Pencatatan berat badan berkala dan grafik tren.
- Riwayat perubahan target.

---

### 5.3 Modul C — Riwayat Makanan

*Belum didesain. Spesifikasi usulan.*

#### C1. Daftar Riwayat Harian — **Must**
- Daftar hari (terbaru di atas) dengan ringkasan: total kkal, makro, % pencapaian target, dan indikator air.
- Mengetuk satu hari membuka diary hari itu (menuju Dashboard dengan tanggal tersebut).

#### C2. Tren & Statistik — **Should**
- Grafik mingguan/bulanan: kalori vs target, rata-rata makro, konsistensi pencatatan (*streak*).
- Filter rentang: 7 hari / 30 hari / kustom.
- Visual memakai warna makro dari design system.

#### C3. Makanan Sering Dimakan & Favorit — **Should**
- Daftar makanan terakhir/sering dan fitur **favorit** untuk *quick add*.

#### C4. Cari & Filter — **Could**
- Cari riwayat menurut nama makanan atau sesi makan.

#### C5. Ekspor Data — **Could**
- Ekspor CSV/PDF ringkasan mingguan.

---

### 5.4 Modul D — Basis Data Makanan & Pencarian

| ID | Kebutuhan | Prioritas |
|---|---|---|
| D1 | Pencarian makanan (nama, *fuzzy*, bahasa Indonesia) dengan *autocomplete* di field "Nama Makanan" | Should |
| D2 | Basis data awal makanan Indonesia (mis. bersumber dari **Tabel Komposisi Pangan Indonesia/TKPI** Kemenkes, bila lisensi memungkinkan) | Should |
| D3 | Pilihan satuan porsi (gram, mangkuk, butir, gelas, sendok) dengan konversi gram | Should |
| D4 | Makanan buatan pengguna (*custom food*) tersimpan dan dapat dipakai ulang | Should |
| D5 | Pembuat resep (*Recipe Builder*): gabungan beberapa bahan → nilai gizi per porsi | Could (disebut di design system, area kanan desktop) |
| D6 | Input manual sepenuhnya tetap tersedia (fallback, seperti di prototipe) | Must |

---

### 5.5 Modul E — Akun, Profil & Pengaturan

| ID | Kebutuhan | Prioritas |
|---|---|---|
| E1 | Mode tamu (data tersimpan lokal tanpa login) agar *onboarding* ringan | Must |
| E2 | Registrasi/login (email atau Google) untuk sinkronisasi lintas perangkat | Should |
| E3 | Avatar/profil di header membuka menu: Profil, Pengaturan, Keluar | Should |
| E4 | Pengaturan: satuan (kkal/kJ, ml/oz), bahasa, target air, pengingat | Should |
| E5 | Hapus akun dan data (kepatuhan privasi) | Must (jika ada akun) |
| E6 | *Onboarding* 3 langkah: profil → tujuan → target otomatis | Should |

---

## 6. Alur Pengguna Utama (User Flows)

### 6.1 Pengguna Baru
1. Membuka web app → *onboarding* singkat (profil, aktivitas, tujuan).
2. Sistem menghitung target kalori dan makro → pengguna meninjau → **Simpan Target**.
3. Masuk Dashboard dengan ring penuh (belum ada makanan).
4. Mencatat makanan pertama lewat *quick add*.
5. Melihat ring dan makro berubah, lalu menerima pesan motivasi pertama.

### 6.2 Mencatat Makanan (Alur Inti, target < 15 detik)
1. Dashboard → ketuk **chip populer** *atau* ketik nama makanan.
2. Form terisi otomatis → sesuaikan porsi (stepper) bila perlu.
3. Ketuk **+ Tambah Makanan**.
4. Item muncul di sesi → ring, bar makro, dan subtotal sesi diperbarui.

### 6.3 Meninjau Progres
1. Buka **Riwayat Makanan** → pilih rentang.
2. Lihat tren dan hari spesifik → buka diary hari tersebut.

### 6.4 Mengubah Target
1. Buka **Target & Goal** → ubah berat/aktivitas/tujuan.
2. Lihat hasil hitung baru → **Simpan Target** → Dashboard diperbarui.

---

## 7. Aturan Bisnis & Perhitungan (Ringkasan)

| Aturan | Rumus / Ketentuan |
|---|---|
| Kalori dari makro | `kkal = 4×K + 4×P + 9×L` (K=karbo, P=protein, L=lemak) |
| Sisa kalori | `max(Target − Terpakai, 0)` untuk tampilan ring |
| Persentase | `min(Terpakai/Target × 100, 100)`, 1 desimal |
| Skala porsi | `nilai_baru = nilai_per_gram × porsi_baru` |
| Gelas air | `round(ml / 250)`; target default 2.000 ml; maks 3.500 ml |
| Pembulatan tampilan | Kalori dan gram dibulatkan ke bilangan bulat; subtotal dijumlahkan dari nilai asli sebelum dibulatkan |
| Format angka | Locale `id-ID` (pemisah ribuan titik, desimal koma) |
| Batas aman target kalori | Minimum 1.200 (wanita) / 1.500 (pria) kkal/hari kecuali ada peringatan khusus |

---

## 8. Kebutuhan Desain & UX (Berdasarkan `DESIGN.md`)

### 8.1 Identitas Visual
- **Gaya:** *Organic Minimalism* + *Tactile Soft Glass*; hangat, bersih, berbasis kartu.
- **Font:** Plus Jakarta Sans (400/600/700/800). Angka metrik memakai *tabular figures*.
- **Ikon:** Material Symbols Outlined.

### 8.2 Palet Warna Utama

| Peran | Warna | Penggunaan |
|---|---|---|
| Primary | `#FF4D8D` (Strawberry) | Aksi utama, progres, tombol |
| Secondary | `#FF8A73` (Peach Coral) | **Karbohidrat** |
| Tertiary | `#E02E6C` (Rose Cherry) | **Protein** |
| Fats | `#F4A8B9` (Soft Blush) | **Lemak** |
| Neutral | `#544349` (Deep Fig) | Teks dan ikon (tanpa hitam murni) |
| Canvas | `#FFF5F7` | Latar halaman |
| Surface L1 | `#FFFFFF` | Kartu |
| Surface L2 | `#FDF2F4` | Input, chip, track |

### 8.3 Responsivitas

| Breakpoint | Layout |
|---|---|
| **Mobile < 768px** | Satu kolom; kartu ringkasan di atas; margin 16px; jarak antar kartu 12px; *bottom nav* |
| **Tablet 768–1024px** | Grid 8 kolom; banner ringkasan; log makanan 2 kolom |
| **Desktop > 1024px** | 12 kolom, maks. 1200px (prototipe memakai `max-w-7xl`); kiri 4–5 kolom *sticky* (ringkasan, form, air), kanan 7–8 kolom (diary, analisis) |

### 8.4 Komponen & Interaksi
- **Tombol primary:** tinggi 48px, hover/aktif ke `#E02E6C` + `scale(0.98)`.
- **Input:** tinggi 48px, radius 12px; fokus → latar putih + ring 2px `#FF4D8D`.
- **Chip:** tinggi 32px, pill; terpilih = latar `#FF4D8D`, teks putih.
- **Elevasi:** Level 1 kartu (glow rose lembut), Level 2 bar sticky (blur 16px), Level 3 modal/sheet pencarian makanan.
- **Animasi:** transisi ring 700 ms, bar 500 ms, *fade-in* item baru.

### 8.5 Tone of Voice
- Bahasa Indonesia santai-hangat, memakai "kamu".
- Positif dan mendukung. Hindari kata "gagal", "buruk", "dosa", dan "curang".

---

## 9. Kebutuhan Non-Fungsional

| Kategori | Kebutuhan |
|---|---|
| **Performa** | LCP < 2,5 dtk di 4G; interaksi (tambah/hapus makanan) memperbarui UI < 100 ms; bundle JS awal < 200 KB gzip |
| **Responsif** | Fungsional penuh di lebar 320 px s.d. 1920 px; area sentuh min. 40×40 px |
| **Aksesibilitas** | Target **WCAG 2.1 AA**: kontras teks, label form (`label for`), `aria-current` pada nav, `aria-live` untuk pembaruan sisa kalori, navigasi keyboard, fokus terlihat. Warna makro **tidak boleh menjadi satu-satunya pembeda** (selalu sertakan label teks) |
| **Kompatibilitas** | 2 versi terakhir Chrome, Safari, Firefox, Edge; iOS Safari 15+; Android Chrome |
| **Offline/PWA** | Dapat dipasang (PWA); pencatatan tetap berfungsi offline dan disinkronkan saat online (Should) |
| **Keamanan** | Sanitasi semua input (XSS); HTTPS; validasi sisi server; pembatasan laju (*rate limit*) API |
| **Privasi** | Data kesehatan = data sensitif. Persetujuan eksplisit, kebijakan privasi jelas, hak hapus data, kepatuhan **UU PDP (UU No. 27/2022)** |
| **Lokalisasi** | `id-ID` default; arsitektur siap i18n (EN sebagai kandidat) |
| **Ketersediaan** | Uptime ≥ 99,5% (jika memakai backend) |
| **Observabilitas** | Analitik penggunaan (anonim), pelacakan error |

---

## 10. Arsitektur & Catatan Teknis (Usulan)

> Prototipe `code.html` adalah **HTML statis + Tailwind CDN + JavaScript *vanilla***, dengan data tersimpan di atribut DOM (`data-kcal`, `data-c`, dll.) dan target hardcoded. Untuk produksi, ini perlu direfaktor.

### 10.1 Rekomendasi
| Aspek | Prototipe Saat Ini | Rekomendasi Produksi |
|---|---|---|
| Framework | HTML + JS inline | React/Next.js atau Vue/Nuxt (berbasis komponen) |
| Styling | Tailwind via CDN (runtime) | Tailwind dikompilasi (build-time) memakai *design tokens* dari `DESIGN.md` |
| State | Atribut DOM | State terpusat (store) + model data tipikal |
| Data | Hardcoded | LocalStorage/IndexedDB (tamu) + backend API (akun) |
| Target | Konstanta (2100/240/130/65) | Diambil dari profil pengguna |
| Font/ikon | Google Fonts (CDN) | *Self-host* dan subset untuk performa serta privasi |

### 10.2 Model Data (Konseptual)

```text
User            { id, nama, jenis_kelamin, tgl_lahir, tinggi_cm, berat_kg,
                  aktivitas, tujuan, satuan, dibuat_pada }
Target          { id, user_id, kkal, karbo_g, protein_g, lemak_g, air_ml,
                  berlaku_sejak }
Food            { id, nama, sumber(db|custom), per_gram, kkal, karbo_g,
                  protein_g, lemak_g, serat_g?, satuan_porsi[] }
LogEntry        { id, user_id, tanggal, sesi(sarapan|siang|malam|camilan),
                  food_id?, nama, porsi_g, kkal, karbo_g, protein_g, lemak_g,
                  dibuat_pada }
WaterLog        { id, user_id, tanggal, jumlah_ml }
WeightLog       { id, user_id, tanggal, berat_kg }
```

### 10.3 Titik Integrasi API (Konseptual)
- `GET /api/days/{tanggal}` — log dan ringkasan harian
- `POST /api/logs` · `PATCH /api/logs/{id}` · `DELETE /api/logs/{id}`
- `GET /api/foods?q=` — pencarian makanan
- `GET/PUT /api/targets` — target gizi
- `POST /api/water` — pencatatan air
- `GET /api/history?from=&to=` — riwayat dan tren

---

## 11. Metrik Keberhasilan (KPI)

| Metrik | Definisi | Target (3 bulan pasca-rilis) |
|---|---|---|
| **Aktivasi** | % pengguna baru yang mencatat ≥ 1 makanan di sesi pertama | ≥ 70% |
| **Waktu catat 1 makanan** | Median waktu dari buka form ke tombol tambah | ≤ 15 detik |
| **Retensi D7 / D30** | % pengguna aktif kembali hari ke-7 / ke-30 | ≥ 35% / ≥ 20% |
| **Konsistensi** | Rata-rata hari tercatat per minggu per pengguna aktif | ≥ 4 hari |
| **Penyelesaian target** | % pengguna yang menyelesaikan kalkulator target | ≥ 80% dari pengguna baru |
| **Pemakaian *quick add*** | % entri yang dibuat via chip/favorit | ≥ 40% |
| **Error form** | % submit form gagal validasi | < 10% |
| **Kinerja** | LCP p75 | < 2,5 dtk |
| **Kepuasan** | CSAT / NPS | CSAT ≥ 4,3/5 |

---

## 12. Kesenjangan Desain & Pertanyaan Terbuka

Hasil telaah `DESIGN.md` dan `code.html` menemukan hal-hal yang **perlu diputuskan atau diselaraskan** sebelum pengembangan:

### 12.1 Inkonsistensi yang Ditemukan
| # | Temuan | Rekomendasi |
|---|---|---|
| 1 | **Target kalori tidak konsisten:** chip header `1,420 / 2,000 kkal` vs kartu `Goal: 2.100 kkal` | Satu sumber kebenaran (target pengguna); header harus dinamis |
| 2 | **Nilai terpakai tidak konsisten:** header `1,420` vs kartu `1.340` kkal (hasil hitung dari item: 380+560+400 = 1.340) | Header disinkronkan dengan perhitungan riil |
| 3 | **Warna makro berbeda antara dokumen dan kode:** DESIGN.md menetapkan Protein = Tertiary `#E02E6C`, Lemak = `#F4A8B9`, tetapi kode memakai `primary` (`#b90a5a`) untuk bar protein dan `primary-fixed-dim` untuk lemak | Selaraskan token warna; putuskan satu palet makro final |
| 4 | **Warna primary ganda:** DESIGN.md menyebut Primary `#FF4D8D`, tetapi token `primary` di Tailwind = `#b90a5a` (`#FF4D8D` ada di `primary-container`) | Definisikan ulang token: peran dan nama harus jelas |
| 5 | **Subtotal sesi di HTML awal tidak cocok dengan jumlah item** (mis. subtotal Sarapan statis "380 kkal, K:52g, P:18g" vs item 220+156+4 = 380 kkal; ok, tetapi karbo dan protein statis perlu dicek ulang oleh `recalculateAll`) | Hapus nilai statis, hitung dari data |
| 6 | Label tombol "+ Tambah Makanan" memuat ikon `+` **dan** teks `+` (duplikat) | Hapus salah satu |
| 7 | Palet DESIGN.md menyebut warna Canvas `#FFF5F7`, tetapi kode memakai `bg-background` = `#fff8f8` | Selaraskan |
| 8 | Teks banner "63%" statis | Dinamis dari data |
| 9 | Kelas `animate-fadeIn` dipakai di JS, tetapi *keyframe* tidak didefinisikan | Tambahkan definisi animasi |
| 10 | Hitungan gelas memakai `round`, sehingga 1.400 ml tampil sebagai 6 gelas | Pastikan konsisten dengan tampilan "ml" |
| 11 | Ring tidak punya state "melebihi target" | Rancang state ini |
| 12 | Desain belum menampilkan *loading*, *error*, dan *offline state* | Tambahkan |

### 12.2 Layar yang Belum Didesain
- Halaman **Riwayat Makanan** (daftar, tren, grafik).
- Halaman **Target & Goal** (formulir profil, hasil kalkulator).
- **Onboarding**, **Login/Registrasi**, **Profil/Pengaturan**.
- **Modal pencarian makanan** (Level 3 elevasi di design system) dan **edit item**.
- State kosong, galat, dan *loading* seluruh halaman.
- Varian tablet (grid 8 kolom) belum divalidasi di prototipe.

### 12.3 Pertanyaan Terbuka untuk Pemilik Produk
1. Apakah v1.0 **wajib login**, atau cukup mode tamu berbasis lokal?
2. Sumber basis data makanan: TKPI Kemenkes, basis data komersial/API pihak ketiga, atau dikurasi sendiri? Bagaimana lisensinya?
3. Apakah ada **model bisnis** (gratis, *freemium*, langganan) yang memengaruhi cakupan fitur MVP?
4. Apakah serat, gula, dan natrium perlu dilacak? (design system menyebut "fiber" di area Karbohidrat.)
5. Perlukah **peringatan kesehatan** (disclaimer) khusus untuk kondisi tertentu (diabetes, hamil, di bawah 18 tahun)?
6. Kebijakan **batas usia** pengguna? Pelacakan kalori untuk remaja memerlukan kehati-hatian.
7. Apakah satuan **kJ** dan bahasa Inggris dibutuhkan sejak awal?

---

## 13. Risiko & Mitigasi

| Risiko | Dampak | Kemungkinan | Mitigasi |
|---|---|---|---|
| Data gizi makanan lokal tidak akurat/tidak lengkap | Kepercayaan menurun | Tinggi | Sumber resmi (TKPI), label "estimasi", izinkan koreksi pengguna |
| Pengguna mengembangkan relasi tidak sehat dengan makanan (obsesi kalori / gangguan makan) | Bahaya kesehatan, reputasi | Sedang | Batas minimum kalori, bahasa non-menghakimi, tanpa "streak" yang memicu rasa bersalah berlebihan, tautan sumber bantuan |
| Dianggap memberi saran medis | Risiko hukum | Sedang | *Disclaimer* jelas: bukan pengganti ahli gizi/dokter |
| Kebocoran/penyalahgunaan data kesehatan | Hukum & reputasi | Rendah–Sedang | Enkripsi, minimisasi data, kepatuhan UU PDP |
| Fatigue pencatatan, retensi rendah | KPI tidak tercapai | Tinggi | Quick add, favorit, pengingat lembut, input < 15 dtk |
| Ketergantungan CDN (Tailwind, Fonts) | Performa dan stabilitas | Sedang | Build lokal, *self-host* aset |

> **Disclaimer produk (wajib tampil di aplikasi):** *"NutriPink memberikan estimasi untuk tujuan informasi dan bukan pengganti saran medis atau ahli gizi. Konsultasikan kondisi kesehatan Anda kepada tenaga profesional."*

---

## 14. Rencana Rilis (Roadmap Usulan)

| Fase | Cakupan | Prioritas Utama |
|---|---|---|
| **MVP (v1.0)** | Dashboard (A1–A8), Kalkulator Target (B1–B3), Riwayat dasar (C1), input manual dan quick add (D6), mode tamu + penyimpanan lokal (E1), responsif penuh, disclaimer | Inti pencatatan dan target |
| **v1.1** | Pencarian makanan + basis data lokal (D1–D4), edit item, undo, tren mingguan (C2), favorit (C3), akun dan sinkronisasi (E2–E4), onboarding (E6) | Kemudahan dan retensi |
| **v1.2** | PWA offline, pengingat, pelacakan berat badan (B4), ekspor data (C5), Recipe Builder (D5) | Keterlibatan |
| **v2.0+** | Pemindai barcode, pengenalan makanan lewat foto, integrasi wearable, rekomendasi menu, bahasa Inggris | Diferensiasi |

---

## 15. Kriteria Penerimaan MVP (Definition of Done)

- [ ] Seluruh fitur **Must** di Bagian 5 berfungsi sesuai kriteria penerimaan.
- [ ] Perhitungan kalori, makro, ring, dan bar konsisten, tanpa angka *hardcoded* yang bertentangan.
- [ ] Tampilan sesuai `DESIGN.md` (token warna, tipografi, radius, elevasi) di mobile, tablet, dan desktop.
- [ ] Ketidakkonsistenan desain Bagian 12.1 sudah diselesaikan.
- [ ] Lolos audit aksesibilitas WCAG 2.1 AA (Lighthouse ≥ 90 + uji manual keyboard dan pembaca layar).
- [ ] Lighthouse Performance ≥ 85 di mobile.
- [ ] Input pengguna disanitasi; tidak ada celah XSS pada nama makanan.
- [ ] Disclaimer kesehatan dan kebijakan privasi tersedia.
- [ ] Data tetap ada setelah *refresh* halaman (penyimpanan lokal).
- [ ] Uji lintas browser sesuai Bagian 9 lulus.

---

## 16. Glosarium

| Istilah | Arti |
|---|---|
| **Makro** | Makronutrien: karbohidrat, protein, lemak |
| **kkal** | Kilokalori (satuan energi makanan) |
| **BMR** | *Basal Metabolic Rate*, energi minimum yang dibutuhkan tubuh saat istirahat |
| **TDEE** | *Total Daily Energy Expenditure*, total energi harian termasuk aktivitas |
| **Quick Add** | Penambahan makanan satu-ketuk dari daftar populer atau favorit |
| **TKPI** | Tabel Komposisi Pangan Indonesia |
| **MVP** | *Minimum Viable Product* |
| **PWA** | *Progressive Web App* |

---

*Dokumen ini disusun berdasarkan analisis `DESIGN.md` dan prototipe `code.html`. Bagian yang bertanda "usulan" adalah rekomendasi tambahan yang perlu divalidasi bersama tim produk dan desain.*
