# Quick Start Guide

Get the notebook running in under 5 minutes!

---

## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- **Git LFS** (untuk download file shapefile yang besar)

---

## Step 0: Install Git LFS (WAJIB!)

Repository ini menggunakan **Git Large File Storage (LFS)** untuk menyimpan file shapefile yang berukuran besar. Kamu **WAJIB** install Git LFS **SEBELUM** clone repository.

### Linux (Ubuntu/Debian)

```bash
# Install Git LFS
sudo apt-get update
sudo apt-get install git-lfs

# Aktifkan Git LFS di sistem
git lfs install
```

### Linux (Fedora/RHEL)

```bash
sudo dnf install git-lfs
git lfs install
```

### macOS

```bash
# Menggunakan Homebrew
brew install git-lfs
git lfs install
```

### Windows

```powershell
# Menggunakan winget
winget install GitHub.GitLFS

# Atau download dari: https://git-lfs.github.com/
# Setelah install, jalankan:
git lfs install
```

### Verifikasi Instalasi LFS

```bash
git lfs version
# Output: git-lfs/3.x.x (GitHub; linux amd64; go 1.x.x)
```

---

## Step-by-Step Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/DiversivikasiPangan.git
cd DiversivikasiPangan

# Jika LFS files tidak ter-download otomatis, jalankan:
git lfs pull
```

### Verifikasi LFS Files Sudah Ter-download

```bash
# Cek file mana yang di-track oleh LFS
git lfs ls-files

# Output yang diharapkan:
# xxxxxxxx - JenisTanahIndonesia/Jenis Tanah Indonesia.shp
# xxxxxxxx - SpotHeightIndonesia/Spot Height 250K.shp
# xxxxxxxx - SpotHeightIndonesia/Spot Height 50K.shp
```

### File LFS dalam Repository

| Folder                 | File                         | Ukuran (Approx) |
| ---------------------- | ---------------------------- | --------------- |
| `JenisTanahIndonesia/` | `*.shp, *.shx, *.dbf, *.prj` | ~50-100 MB      |
| `SpotHeightIndonesia/` | `Spot Height 250K.*`         | ~20-50 MB       |
| `SpotHeightIndonesia/` | `Spot Height 50K.*`          | ~100-200 MB     |

### 2. Create Virtual Environment

**Linux/macOS:**

```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Notebook

**Option A: Jupyter Notebook**

```bash
jupyter notebook diversifikasipangan_final.ipynb
```

**Option B: JupyterLab**

```bash
jupyter lab diversifikasipangan_final.ipynb
```

**Option C: VS Code**

1. Open VS Code
2. Install Python extension
3. Open `diversifikasipangan_final.ipynb`
4. Select Python interpreter (your venv)
5. Click "Run All"

---

## Verify Installation

Test that all packages are correctly installed:

```bash
python -c "
import pandas as pd
import numpy as np
import geopandas as gpd
import sklearn
import matplotlib.pyplot as plt
print(' All packages installed successfully!')
print(f'   pandas: {pd.__version__}')
print(f'   numpy: {np.__version__}')
print(f'   geopandas: {gpd.__version__}')
print(f'   scikit-learn: {sklearn.__version__}')
"
```

---

## Expected Output

After running the notebook, you will have:

1. **Console Output**: Cluster statistics and metrics
2. **Visualizations**: 15+ charts and maps
3. **CSV File**: `hasil_clustering_diversifikasi.csv`

---

## Quick Troubleshooting

| Issue                            | Solution                                               |
| -------------------------------- | ------------------------------------------------------ |
| `ModuleNotFoundError: geopandas` | `pip install geopandas`                                |
| `GDAL not found`                 | Install GDAL system package first                      |
| Shapefile not found              | Jalankan `git lfs pull`                                |
| File shapefile corrupt/kecil     | Re-download: `git lfs fetch --all && git lfs checkout` |
| Memory error                     | Use smaller dataset or increase RAM                    |
| Git LFS not installed warning    | Install LFS lalu `git lfs pull`                        |

---

## LFS Troubleshooting

### Problem: "File shapefile tidak ditemukan" atau "File corrupt/kecil"

Jika file shapefile berukuran sangat kecil (< 1KB) atau berisi text "version https://git-lfs.github.com/...", berarti LFS belum pull:

```bash
# Re-download LFS files
git lfs pull

# Atau fetch semua lalu checkout
git lfs fetch --all
git lfs checkout
```

### Problem: "Smudge error" atau "LFS object not found"

```bash
# Reset LFS pointer files
git lfs install --force
git lfs pull
```

### Problem: Clone tanpa LFS (sudah terlanjur)

Jika sudah clone sebelum install LFS:

```bash
# Install LFS
git lfs install

# Fetch dan checkout semua LFS files
git lfs fetch --all
git lfs checkout

# Atau re-clone dari awal
cd ..
rm -rf DiversivikasiPangan
git clone <repo-url>
```

---

## Need Help?

- Read the full [README.md](README.md)
- Check [DATA_DICTIONARY.md](DATA_DICTIONARY.md) for data descriptions
- Check [Git LFS Documentation](https://git-lfs.github.com/)
- Open an issue on GitHub

---

## TL;DR (Super Quick)

```bash
# 1. Install Git LFS (WAJIB sebelum clone!)
sudo apt install git-lfs && git lfs install   # Linux
brew install git-lfs && git lfs install       # macOS

# 2. Clone & pull LFS files
git clone <repo-url> && cd DiversivikasiPangan
git lfs pull

# 3. Setup Python
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt

# 4. Run notebook
jupyter notebook diversifikasipangan_final.ipynb
```

Selesai!
