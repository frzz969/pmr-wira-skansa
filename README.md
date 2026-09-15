# PMR Wira Skansa — Cek Kelulusan

Halaman web satu file untuk cek kelulusan calon anggota PMR Wira Skansa: masukkan nama dan kelas, lalu sistem menampilkan status kelulusan — lengkap dengan hitung mundur, tampilan bilingual Indonesia/Inggris, dan tombol gabung grup bagi yang lolos.

Seluruh aplikasi (markup, styling, logika) hidup dalam satu `index.html` — tanpa build, tanpa dependensi npm, tanpa gambar eksternal (logo dan ikon murni CSS).

## Fitur

- **Cek kelulusan** — input Nama + Kelas, lookup data peserta: Lolos (biru) / Tidak Lolos (merah) / data tidak ditemukan.
- **Countdown 3-2-1** — transisi dramatis sebelum hasil tampil.
- **Bilingual** — Indonesia default, Inggris via `changeLanguage()`.
- **Responsif** — media query hingga layar ≤ 480px.
- **Aman dari XSS** — input di-escape via `escapeHTML()`.

## Struktur

```text
└── index.html   # semuanya: (±486 baris CSS inline + ±287 baris JS inline)
    ├── homeView      # hero, navigasi, info 4 kartu, tentang, CTA, footer
    ├── formView      # form Nama + Kelas → lookup dataPeserta
    ├── countdownView # animasi hitung mundur
    └── resultView    # render hasil Lolos / Tidak Lolos
```

## Cara menjalankan

```bash
npx serve .
```

atau buka `index.html` langsung di browser; bisa di-deploy statis ke GitHub Pages/Netlify/Vercel. Font diambil dari Google Fonts (butuh internet sekali saat muat).

## Catatan

Data kelulusan tersimpan di sisi klien (terlihat lewat View Source) — cocok untuk pengumuman internal kasual, bukan untuk data yang wajib rahasia.
