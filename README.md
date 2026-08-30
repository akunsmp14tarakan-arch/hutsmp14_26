# Situs Informasi HUT ke-7 SMP Negeri 14 Tarakan

Situs statis satu halaman berisi informasi acara (tema, tanggal, lokasi, rundown, jadwal persiapan) dan tautan unduh seluruh dokumen panitia. Tidak memerlukan backend atau build step — murni HTML/CSS statis, siap di-deploy ke Vercel.

## Struktur folder

```
index.html          -> halaman utama
assets/style.css     -> styling
dokumen/              -> seluruh dokumen panitia (docx, pdf, xlsx, pptx)
vercel.json           -> konfigurasi ringan untuk Vercel
```

## Cara deploy ke Vercel

**Opsi A — lewat situs Vercel (tanpa terminal):**
1. Buat akun/login di https://vercel.com
2. Klik "Add New" -> "Project" -> "Deploy from a template"/"Import" -> pilih opsi upload folder, lalu unggah folder ini apa adanya (atau unggah dulu ke repo GitHub, lalu import repo tersebut).
3. Framework Preset pilih **Other** (situs statis biasa). Tidak perlu Build Command maupun Output Directory khusus — biarkan default/kosong, karena `index.html` ada di root.
4. Klik Deploy. Selesai dalam hitungan detik.

**Opsi B — lewat CLI (jika sudah punya Node.js terpasang):**
```
npm install -g vercel
cd hut-smp14-site
vercel
```
Ikuti prompt-nya (login, pilih scope, konfirmasi direktori). Untuk deploy ke produksi: `vercel --prod`.

**Opsi C — lewat GitHub:**
1. Push folder ini ke repository GitHub baru.
2. Di Vercel, "Add New" -> "Project" -> Import repo tersebut.
3. Deploy — tidak perlu setting tambahan.

## Yang perlu diisi/disesuaikan sebelum publish

- **Alamat sekolah**: cari teks `[Alamat Sekolah]` di `index.html` (bagian hero) dan ganti dengan alamat lengkap.
- **Kontak panitia**: tambahkan nomor WA/email panitia di footer bila diperlukan.
- Nama-nama koordinator seksi, nomor SK, dsb. yang masih placeholder `[Nama]`/`[diisi]` ada di dalam dokumen `.docx` di folder `dokumen/` — bisa diedit langsung di Word sebelum dibagikan ulang (file di situs tidak otomatis ikut berubah, perlu diunggah ulang dokumen yang sudah direvisi).

## Memperbarui dokumen di kemudian hari

Jika ada revisi dokumen, cukup timpa file yang bersangkutan di folder `dokumen/` dengan nama file yang sama, lalu deploy ulang (`vercel --prod` atau push ulang ke GitHub bila memakai Opsi C). Tautan unduh di halaman tidak perlu diubah selama nama file dipertahankan.
