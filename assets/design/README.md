# MY DESIGN PORTFOLIO — cara mengganti foto

Folder ini berisi 6 foto untuk section **Designs → My Design Portfolio**
(di halaman utama, section nomor 03).

## 1. Ganti fotonya
Timpa file berikut dengan karya desain Anda (nama file HARUS sama):

    01.jpg  02.jpg  03.jpg  04.jpg  05.jpg  06.jpg

- Format: JPG / PNG / WEBP — kalau formatnya beda, ubah juga nama
  ekstensinya di `index.html` (cari `assets/design/01.jpg`).
- Rasio paling pas: **4:5** (portrait) karena grid memakai rasio 4:5.
  Rasio lain tetap aman — gambar otomatis `object-fit: cover`
  jadi tidak akan gepeng.
- Disarankan lebar ±1200 px, ukuran file di bawah 300 KB supaya
  halaman tetap ringan.

Urutan tampil di grid (2 kolom di desktop): baris demi baris —
01 | 02, lalu 03 | 04, lalu 05 | 06. Di mobile jadi 1 kolom: 01–06.

## 2. Ganti teksnya (judul, kategori, deskripsi)
Buka `index.html`, cari tiap `<figure class="work-item">`:

- `data-work-index`  → urutan (0–5) untuk lightbox, jangan diduplikasi
- `data-title`       → judul karya (tampil di lightbox)
- `data-cat-label`   → kategori, mis. "Poster", "Branding"
- `data-year`        → tahun
- `data-client`      → klien / "Personal Project"
- `data-desc`        → deskripsi singkat
- `data-tools`       → daftar alat, dipisah tanda `|`
- `<figcaption>`     → nomor + judul + kategori di bawah foto
- `alt="..."`        → teks alternatif untuk aksesibilitas

## 3. Kalau file foto belum ada
Frame tidak akan rusak — muncul placeholder gelap bertuliskan
nama file yang harus ditaruh di sana.

## 4. Marquee (auto-scroll)
Galeri berjalan otomatis ke atas terus-menerus. Isinya di-duplikat
JavaScript (`buildClones()`) supaya loop-nya mulus tanpa jeda.
Interaksi pengguna (wheel / sentuh / seret / tombol) menahan
auto-scroll selama ±2,2 detik, lalu jalan lagi.

- Kecepatan: `speed` di fungsi `feedTick()` — 30 px/detik desktop,
  20 px/detik mobile.
- Matikan sama sekali kalau pengguna memakai *reduced motion*.

## 5. Parallax
Tiap foto ada di dalam `.work-media` (di dalam `.work-frame`).
JavaScript menggesernya dengan `transform: translate3d(0, y, 0)`
plus smoothing, maksimal ±6% tinggi kotak — jadi foto bergerak
lebih lambat daripada scroll halaman. Atur amplitudanya di
`parallaxTick()` (`fr.height * 0.06`).
