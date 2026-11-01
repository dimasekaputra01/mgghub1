# Peluang Magang

Website statis untuk menjelajahi lowongan MagangHub Kemnaker: pencarian, filter (jurusan, lokasi, jenjang, kategori, wawancara, disabilitas), skor peluang, dan simpan lowongan favorit. Tanpa framework dan tanpa build step.

## Isi folder

| File | Fungsi |
| --- | --- |
| `index.html` | Seluruh tampilan dan logika |
| `data.json` | Data lowongan (hasil olahan CSV) |
| `build_data.py` | Mengubah CSV baru menjadi `data.json` |

## Hosting di GitHub Pages

1. Buat repository baru di GitHub, lalu upload `index.html`, `data.json`, dan `README.md`.
2. Buka **Settings → Pages**. Pada **Build and deployment**, pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu **Save**.
3. Tunggu satu sampai dua menit. Situs aktif di `https://USERNAME.github.io/NAMA-REPO/`.

Untuk mencoba di komputer sendiri, jalankan `python -m http.server` di folder ini lalu buka `http://localhost:8000`. Membuka `index.html` langsung dengan klik dua kali tidak akan memuat data karena batasan browser.

## Memperbarui data

```bash
pip install pandas
python build_data.py maganghub_semua_lowongan_TANGGAL.csv
```

Commit `data.json` yang baru, dan situs ikut diperbarui.

## Cara membaca peluang

Peluang = kuota ÷ jumlah pelamar saat data diambil (maksimal 100%).

| Label | Arti |
| --- | --- |
| Terbuka | Kuota sama atau lebih banyak dari pelamar |
| Tinggi | 50–99% |
| Sedang | 25–49% |
| Ketat | 10–24% |
| Sangat ketat | Di bawah 10% |

Ini perkiraan kasar. Jumlah pelamar terus naik, dan angka ini bukan jaminan diterima.
