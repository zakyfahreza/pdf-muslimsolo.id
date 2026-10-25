# pdf.muslimsolo.id — Download Kitab Tajdidul Iman

Situs statis sederhana untuk membagikan kitab "Memperbaharui Iman (Tajdidul Iman)"
kepada peserta daurah. Saat peserta membuka link, mereka bisa langsung mengunduh
PDF ke penyimpanan HP.

## Isi folder

| File | Keterangan |
|------|------------|
| `index.html` | Halaman download |
| `tajdidul-iman.pdf` | File kitab |
| `CNAME` | Domain kustom: `pdf.muslimsolo.id` |
| `.nojekyll` | Menonaktifkan pemrosesan Jekyll di GitHub Pages |

---

## Cara deploy ke GitHub Pages

### 1. Buat repository baru di GitHub

Buka https://github.com/new, buat repo baru (mis. `pdf-muslimsolo`), set **Public**.
Jangan centang "Add a README".

### 2. Push project ini

Jalankan dari folder project (`c:\Users\asus\pdf-muslimsolo`):

```bash
git remote add origin https://github.com/<username>/pdf-muslimsolo.git
git branch -M main
git push -u origin main
```

Ganti `<username>` dengan username GitHub Anda.

### 3. Aktifkan GitHub Pages

1. Buka repo di GitHub → **Settings** → **Pages**.
2. Bagian **Build and deployment** → Source: **Deploy from a branch**.
3. Branch: **main**, folder: **/ (root)** → **Save**.
4. Tunggu 1–2 menit. GitHub akan memberi URL default
   `https://<username>.github.io/pdf-muslimsolo/`.

### 4. Pasang domain kustom

Pada halaman **Settings → Pages**, field **Custom domain** sudah otomatis
terisi `pdf.muslimsolo.id` (dari file `CNAME`). Centang **Enforce HTTPS**
setelah sertifikat selesai diterbitkan (bisa butuh beberapa menit sampai 1 jam).

---

## Pengaturan DNS (di pengelola domain muslimsolo.id)

Tambahkan satu record berikut di panel DNS domain `muslimsolo.id`:

| Type  | Name / Host | Value / Target              | TTL  |
|-------|-------------|-----------------------------|------|
| CNAME | `pdf`       | `<username>.github.io.`     | Auto |

- **Name** cukup `pdf` (bukan `pdf.muslimsolo.id`), karena sistem DNS
  otomatis menambahkan domain induk.
- **Value** adalah `<username>.github.io` (akhiri titik bila panel memintanya).

Setelah DNS menyebar (biasanya beberapa menit sampai beberapa jam),
`https://pdf.muslimsolo.id` akan menampilkan halaman download.

---

## Cara kerja download

Tombol pada `index.html` menggunakan atribut `download`, sehingga browser
langsung mengunduh PDF ke folder **Download** HP, bukan membuka pratinjau.
Pada beberapa browser HP (mis. Safari iOS lama), file mungkin terbuka sebagai
pratinjau; pengguna cukup menekan ikon simpan/bagikan untuk menyimpannya.

## Mengganti / memperbarui file PDF

Ganti `tajdidul-iman.pdf` dengan file baru (pakai nama sama), lalu:

```bash
git add tajdidul-iman.pdf
git commit -m "Update kitab"
git push
```
