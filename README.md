# Eksperimen Operasi Dasar pada Sinyal

**M. Faridh Maulana** — 452024611065

## Deskripsi Singkat

Proyek ini merupakan eksperimen akademik dalam ranah Pengolahan Sinyal Digital (DSP) yang mengeksplorasi empat operasi dasar pada sinyal waktu-diskrit 1D dan citra digital 2D. Implementasi menggunakan Python dalam lingkungan Jupyter Notebook.

## Library yang Digunakan

- Python 3.14
- NumPy — operasi matriks dan sinyal
- OpenCV (`opencv-python`) — pemrosesan citra
- Matplotlib — visualisasi grafik dan citra
- Jupyter Notebook — lingkungan eksperimen interaktif

## Cara Menjalankan Notebook

```bash
# Install UV jika belum ada
# macOS and Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# Install dependencies
uv sync

# Jalankan notebook server
uv run jupyter lab
```

Buka file `notebook/operasi_sinyal_citra.ipynb` di browser dan jalankan seluruh sel secara berurutan, atau pilih menu `Kernel > Run All Cells`.

Untuk eksekusi headless:
```bash
uv run jupyter nbconvert --to notebook --execute notebook/operasi_sinyal_citra.ipynb --output executed.ipynb
```

## Struktur Folder

```
.
├── notebook/
│   └── operasi_sinyal_citra.ipynb   # Notebook utama (seluruh eksperimen)
├── images/
│   ├── img.png                      # Citra uji 1
│   └── img2.jpg                     # Citra uji 2
├── report/
│   └── laporan.tex                  # Laporan LaTeX (8 seksi)
├── pyproject.toml                   # Konfigurasi proyek dan dependensi
├── uv.lock                          # Lock file dependensi
├── .python-version                  # Versi Python (3.14)
└── README.md                        # File ini
```

## Ringkasan Hasil Eksperimen

| Operasi | Sinyal 1D | Citra 2D |
|---|---|---|
| **Penjumlahan** | Superposisi sinus + unit step; DC offset, perubahan rentang | Clipping (cv2.add) vs modulo (numpy+); efek overexposure |
| **Pergeseran** | Time delay ($k>0$) / advance ($k<0$); hubungan $\tau = k/f_s$ | Translasi affine; area kosong hitam; augmentasi data ML |
| **Amplifikasi** | $\alpha=0.5,1,2,-1$; inversi fase saat $\alpha<0$ | $\alpha=0.5\!-\!2.0$; clipping & integer overflow |
| **Uji Linier** | $T(x)=2x$ : lulus homogenitas & aditivitas (linier) | $T(x)=x^2$ : gagal kedua uji (non-linier) |

## Kesimpulan Singkat

Empat operasi dasar sinyal (penjumlahan, pergeseran, amplifikasi, translasi/amplifikasi citra) berhasil diimplementasikan dan dianalisis. Sistem $T(x) = 2x$ terverifikasi sebagai sistem linier melalui uji homogenitas dan aditivitas. Operasi-operasi ini merupakan fondasi DSP modern termasuk konvolusi, filtering, dan transformasi Fourier.
