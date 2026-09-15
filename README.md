# PMR Wira Skansa — Cek Kelulusan

![HTML5](https://img.shields.io/badge/HTML5-single_file-orange)
![No Build](https://img.shields.io/badge/build-tidak_perlu-blue)
![Bilingual](https://img.shields.io/badge/bahasa-ID_%2F_EN-green)

Halaman web satu file untuk cek kelulusan calon anggota PMR Wira Skansa: masukkan nama dan kelas, lalu sistem menampilkan status kelulusan — lengkap dengan hitung mundur, tampilan bilingual Indonesia/Inggris, dan tombol gabung grup bagi yang lolos.

Seluruh aplikasi (markup, styling, logika) hidup dalam satu `index.html` — tanpa build, tanpa dependensi npm, tanpa gambar eksternal (logo dan ikon murni CSS).

## Daftar isi

- [Fitur](#fitur)
- [Alur tampilan](#alur-tampilan)
- [Struktur](#struktur)
- [Cara menjalankan](#cara-menjalankan)
- [Catatan](#catatan)

## Fitur

| Fitur | Keterangan |
|---|---|
| **Cek kelulusan** | Input Nama + Kelas → lookup data peserta: Lolos (biru) / Tidak Lolos (merah) / data tidak ditemukan. |
| **Countdown 3-2-1** | Transisi dramatis sebelum hasil tampil. |
| **Bilingual** | Indonesia default, Inggris via `changeLanguage()` + objek `translations`. |
| **Responsif** | Media query hingga layar ≤ 480px. |
| **Aman dari XSS** | Input di-escape via `escapeHTML()`. |

## Alur tampilan

```text
homeView (hero + info + CTA) → formView (Nama + Kelas) → countdownView (3-2-1)
  → resultView (Lolos → tombol WA grup / Tidak Lolos / tidak ditemukan)
```

SPA via `showView()` (toggle `.view.active`); lookup exact `dataPeserta["Nama|Kelas"]`; render hasil via `renderResult()`.

## Struktur

```text
└── index.html   # semuanya (±486 baris CSS inline + ±287 baris JS inline)
    ├── homeView      # hero, navigasi, info 4 kartu, tentang, CTA, footer
    ├── formView      # form Nama + Kelas → lookup dataPeserta
    ├── countdownView # animasi hitung mundur
    └── resultView    # render hasil Lolos / Tidak Lolos
```

Font diambil dari Google Fonts (Inter, Poppins, dsb. — butuh internet sekali saat muat).

## Cara menjalankan

```bash
npx serve .
```

atau buka `index.html` langsung di browser; deploy statis ke GitHub Pages/Netlify/Vercel.

## Catatan

Data kelulusan tersimpan di sisi klien (terlihat lewat View Source) — cocok untuk pengumuman internal kasual, bukan untuk data yang wajib rahasia.
