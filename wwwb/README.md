# WWWB → GitHub Pages Workflow

## Struktur Folder

```
misterhans77.github.io/
├── wwwb/                    ← Semua proyek WWWB di sini
│   ├── index.html           ← Landing page proyek WWWB
│   ├── website-kelas/       ← Contoh: website kelas 6
│   │   ├── index.html
│   │   ├── css/
│   │   └── js/
│   └── ppdb-online/         ← Contoh: PPDB online
├── blog-images/             ← Blogspot images (existing)
└── README.md
```

## Alur Workflow

```
1. HERMES: Chat → generate/edit konten
     ↓
2. WWWB: Build website (drag-drop)
     ↓
3. WWWB: Export → folder proyek di wwwb/
     ↓
4. HERMES: Push ke GitHub (auto-deploy)
     ↓
5. GitHub Pages: Live di misterhans77.github.io
```

## Perintah Cepat (dari Hermes chat)

### Push website WWWB baru
```
"push folder website-kelas ke github"
```

### Update website yang sudah ada
```
"update website-kelas di github"
```

### Cek status deploy
```
"cek status github pages"
```

## Manual Deploy (jika perlu)

```bash
cd ~/misterhans77.github.io
git add wwwb/
git commit -m "update: website WWWB baru"
git push origin main
```

## URL Hasil Deploy

- **Landing WWWB**: https://misterhans77.github.io/wwwb/
- **Proyek spesifik**: https://misterhans77.github.io/wwwb/nama-proyek/

## Integrasi WYSIWYG Web Builder

### Export dari WWWB ke folder proyek:

1. Buka WYSIWYG Web Builder 20
2. File → Export → Website
3. Pilih folder: `C:\Users\Eko Pujiyanto\misterhans77.github.io\wwwb\nama-proyek\`
4. Export

### lalu push ke GitHub:
```bash
cd ~/misterhans77.github.io
git add wwwb/nama-proyek
git commit -m "add: website nama-proyek"
git push
```

## Catatan

- GitHub Pages auto-deploy dalam ~1 menit setelah push
- WWWB export menghasilkan HTML/CSS/JS murni (static)
- Tidak perlu build step — langsung push file statis
