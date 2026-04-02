# Jekyll App Portfolio Theme

GitHub Pages theme untuk developer yang ingin menampilkan portofolio aplikasi mobile.

---

## ⚡ Quick Start

### 1. Setup Repository

```bash
# Clone / fork repo ini, atau push langsung ke repo GitHub Pages Anda
# Nama repo untuk user page: username.github.io
# Nama repo untuk project page: nama-repo (baseurl perlu disesuaikan)
```

### 2. Konfigurasi Awal

Edit `_config.yml`:

```yaml
title: "Nama Anda"
tagline: "Android Developer"
author: "Nama Lengkap Anda"
email: "email@example.com"
url: "https://username.github.io"
github_username: username
playstore_developer: "https://play.google.com/store/apps/developer?id=NamaAnda"
```

### 3. Install & Jalankan Lokal (Opsional)

```bash
bundle install
bundle exec jekyll serve
# Buka http://localhost:4000
```

---

## 📱 Menambah App Baru

Setiap kali rilis app baru, ikuti 3 langkah ini:

### Langkah 1 — Tambah Data di `_data/apps.yml`

```yaml
- id: nama-app-baru          # Huruf kecil, gunakan tanda hubung
  name: "Nama App Baru"
  tagline: "Slogan singkat aplikasi"
  description: "Deskripsi 1-2 kalimat untuk card di homepage."
  status: "released"          # released | development | draft
  category: "Productivity"
  version: "1.0.0"
  release_date: "2026-06-01"  # Format: YYYY-MM-DD
  last_update: "2026-06-01"
  playstore_url: "https://play.google.com/store/apps/details?id=com.example.app"
  privacy_url: "/privacy/nama-app-baru/"
  icon: "/assets/images/apps/nama-app-baru/icon.png"
  screenshots:
    - "/assets/images/apps/nama-app-baru/screen1.png"
    - "/assets/images/apps/nama-app-baru/screen2.png"
  downloads: "1K+"
  rating: "4.8"
  highlights:
    - "Fitur unggulan pertama"
    - "Fitur unggulan kedua"
    - "Fitur unggulan ketiga"
```

### Langkah 2 — Buat Halaman Detail

Salin `_apps/_TEMPLATE.md` → `_apps/nama-app-baru.md`

```markdown
---
app_id: nama-app-baru
title: "Nama App Baru"
description: "Deskripsi untuk SEO."
---

## Tentang Aplikasi
...

## Fitur Utama
...

## Changelog
...
```

### Langkah 3 — Buat Privacy Policy

Salin `_privacy/_TEMPLATE.md` → `_privacy/nama-app-baru.md`

```markdown
---
app_id: nama-app-baru
title: "Privacy Policy — Nama App Baru"
last_updated: "1 Juni 2026"
---

...isi privacy policy...
```

> **URL Privacy Policy untuk Play Store**: `https://username.github.io/privacy/nama-app-baru/`

### Langkah 4 — Upload Aset

```
assets/images/apps/nama-app-baru/
├── icon.png          # 512x512px, format PNG
├── screen1.png       # Screenshot portrait
├── screen2.png
└── screen3.png
```

### Langkah 5 — Push ke GitHub

```bash
git add .
git commit -m "feat: tambah nama-app-baru"
git push
```

GitHub Pages akan otomatis build dan deploy dalam 1-2 menit.

---

## 🔄 Update Status App

Status di `_data/apps.yml` otomatis mempengaruhi tampilan di homepage:

| Status | Tampilan |
|--------|----------|
| `released` | Section pertama, badge hijau, tombol Play Store aktif |
| `development` | Section kedua, badge kuning, tanpa tombol Play Store |
| `draft` | Section ketiga, badge abu-abu |

---

## 🎨 Kustomisasi Warna

Edit CSS variable di `assets/css/main.scss`:

```scss
:root {
  --accent: #4ade80;        /* Warna aksen utama (default: hijau) */
  --bg:     #0a0a0f;        /* Warna background utama */
}
```

Contoh warna aksen alternatif:
- Biru: `#60a5fa`
- Ungu: `#a78bfa`
- Oranye: `#fb923c`
- Merah muda: `#f472b6`

---

## 📁 Struktur Direktori

```
.
├── _config.yml              # Konfigurasi Jekyll
├── _data/
│   └── apps.yml             # ← DATA SEMUA APP (edit ini)
├── _apps/                   # ← KONTEN DETAIL APP (1 file per app)
│   ├── _TEMPLATE.md         # Template untuk app baru
│   └── sample-app.md
├── _privacy/                # ← PRIVACY POLICY (1 file per app)
│   ├── _TEMPLATE.md         # Template untuk privacy policy baru
│   └── sample-app.md
├── _layouts/
│   ├── default.html         # Layout dasar (header + footer)
│   ├── home.html            # Layout halaman utama
│   ├── app.html             # Layout detail app
│   └── privacy.html         # Layout privacy policy
├── _includes/
│   ├── head.html            # <head> tag
│   ├── header.html          # Navigasi
│   ├── footer.html          # Footer
│   └── app-card.html        # Komponen card app
├── assets/
│   ├── css/main.scss        # Stylesheet utama
│   └── images/apps/         # ← Letakkan icon & screenshot di sini
├── index.md                 # Halaman utama
├── about.md                 # Halaman about
└── Gemfile
```

---

## ❓ FAQ

**Q: Bagaimana cara mengubah urutan app?**  
Ubah urutan entry di `_data/apps.yml`. App ditampilkan sesuai urutan dalam file.

**Q: Bisa pakai custom domain?**  
Ya. Tambahkan file `CNAME` berisi domain Anda di root repo, lalu konfigurasikan DNS.

**Q: Bagaimana cara preview lokal?**  
Install Ruby + Bundler, jalankan `bundle install` lalu `bundle exec jekyll serve`.

**Q: App baru tidak muncul setelah push?**  
Tunggu 1-2 menit untuk GitHub Actions selesai build. Cek tab Actions di repo untuk status.
