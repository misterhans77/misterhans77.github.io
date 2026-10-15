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

Setiap proyek di dalam `wwwb/` harus punya `index.html` di root-nya, supaya URL
folder (`/wwwb/nama-proyek/`) langsung terbuka. Hermes menyiapkan folder,
commit, dan push; langkah Publish dari editor dijalankan manual oleh user.

## Alur Workflow

```
1. HERMES: Chat → scaffold folder wwwb/nama-proyek/
     ↓
2. WWWB: Build website (drag-drop blocks)
     ↓
3. WWWB: File → Publish → Local Folder → wwwb/nama-proyek/
     ↓
4. HERMES: commit + push ke GitHub
     ↓
5. GitHub Pages: live di misterhans77.github.io/wwwb/nama-proyek/
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

## Publish dari WYSIWYG Web Builder

Jangan pakai menu Export — WWWB memakai menu **Publish**.

1. Buka project di WYSIWYG Web Builder 20.
2. **`Menu → File → Publish`**
3. Klik **New** untuk membuat lokasi publish baru.
4. Isi **Description** (nama bebas, mis. `github-pages-kelas6`).
5. Pilih **Type = `Local Folder`**.
6. Isi **Folder** dengan path absolut tujuan:

   ```
   C:\Users\Eko Pujiyanto\misterhans77.github.io\wwwb\nama-proyek\
   ```

7. Klik **OK**, lalu klik **Publish**.

### Opsi yang berguna di jendela Publish

| Opsi | Fungsi |
|---|---|
| *Entire website* | Publish semua halaman (default) |
| *Select page only* | Publish satu halaman saja |
| *Publish all files* | Semua file termasuk gambar |
| *Publish changed files only* | Hanya file yang berubah — lebih cepat saat re-publish |

### Catatan penting soal setelan Publish

Setelan publish **tidak disimpan di dalam project file**, tapi global di:

```
Documents\WYSIWYG Web Builder\system\publish.dat
```

Artinya: kalau project `.wbs` dipindah ke komputer lain, target publish-nya
tidak ikut terbawa dan harus dipilih ulang. Kalau ada masalah publish, aktifkan
log di **`Menu → Tools → Options → Publish`** — log muncul di
`Documents\WYSIWYG Web Builder\system\publish.log`.

## Push ke GitHub

```bash
cd ~/misterhans77.github.io
git add wwwb/nama-proyek
git commit -m "add: website nama-proyek"
git push origin main
```

> **Beri timeout yang cukup.** Push pertama via HTTPS bisa lewat dari 60 detik
> di mesin ini. Kalau `git push` terlihat timeout, jangan langsung commit ulang —
> cek dulu `git log --oneline -1` dan `git status` untuk memastikan apakah push
> sebenarnya sudah masuk.

## URL Hasil Deploy

- **Root hub**: https://misterhans77.github.io/
- **Folder WWWB**: https://misterhans77.github.io/wwwb/
- **Proyek spesifik**: https://misterhans77.github.io/wwwb/nama-proyek/

## Catatan

- GitHub Pages auto-deploy ~1 menit setelah push. Deploy pertama kali bisa lebih lama — jangan anggap gagal saat masih 404.
- WWWB Publish menghasilkan HTML/CSS/JS murni (static) — tidak perlu build step.
- Hosting Pages itu case-sensitive (Linux): `Logo.PNG` dan `logo.png` berbeda. Pastikan penamaan file konsisten.
- Jangan publish file project `.wbs` ke folder web — file itu source yang bisa diedit dan akan ikut terunduh publik.

---

Skill Hermes terkait: `wwwb-to-github-pages` (pipeline ini), `publish-site`
(deploy multi-provider dengan versioning/rollback).
