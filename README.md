# Agroecological Clustering for Carbohydrate Source Diversification in Indonesia

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **A Clustering-Based Agroecological Approach to Identify Potential Carbohydrate Source Diversification in Indonesia**

## Table of Contents

- [Overview](#overview)
- [Research Objectives](#research-objectives)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Data Sources](#data-sources)
- [Running the Notebook](#running-the-notebook)
- [Key Results](#key-results)
- [Citation](#citation)
- [Contributors](#contributors)
- [License](#license)

---

## Overview

This research project employs **unsupervised machine learning techniques** (K-Means clustering) to identify agroecological zones suitable for carbohydrate crop diversification across 34 Indonesian provinces. The study integrates multi-source geospatial and climatological data to classify regions based on environmental characteristics and maps appropriate carbohydrate crop functional groups to each identified cluster.

### Why This Matters

Indonesia's food security heavily relies on rice, making the country vulnerable to climate change and agricultural disruptions. This research provides a **data-driven framework** for recommending alternative carbohydrate sources based on local agroecological conditions.

---

## Research Objectives

1. **Identify distinct agroecological zones** across Indonesian provinces using clustering analysis
2. **Integrate multi-source environmental data** (soil, rainfall, elevation) for comprehensive zoning
3. **Map appropriate carbohydrate crop functional groups** to each identified zone
4. **Provide evidence-based diversification recommendations** for food security policy

## 📁 Project Structure

```
DiversivikasiPangan/
│
├── diversifikasipangan_final.ipynb    # Main analysis notebook
├── README.md                           # This documentation
├── methodology.md                      # Detailed methodology
├── requirements.txt                    # Python dependencies
│
├── Data Sources/
│   ├── Jumlah Curah Hujan dan Jumlah Hari Hujan di Stasiun
│   │   Pengamatan BMKG, 2011-2015.csv     # Rainfall data
│   │
│   ├── JenisTanahIndonesia/               # Soil classification shapefiles
│   │   ├── Jenis Tanah Indonesia.shp
│   │   ├── Jenis Tanah Indonesia.dbf
│   │   ├── Jenis Tanah Indonesia.shx
│   │   ├── Jenis Tanah Indonesia.prj
│   │   └── ...
│   │
│   └── SpotHeightIndonesia/               # Elevation data shapefiles
│       ├── Spot Height 250K.shp
│       ├── Spot Height 50K.shp
│       └── ...
│
└── Output/
    └── hasil_clustering_diversifikasi.csv  # Final clustering results
```

---

## Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Git (for cloning the repository)

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/DiversivikasiPangan.git
cd DiversivikasiPangan
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# Using venv
python -m venv venv

# Activate on Linux/macOS
source venv/bin/activate

# Activate on Windows
venv\Scripts\activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Verify Installation

```bash
python -c "import pandas, numpy, geopandas, sklearn; print('All packages installed successfully!')"
```

---

## Data Sources

### 1. Soil Classification Data

- **Source**: FAO-UNESCO Soil Map of the World
- **Format**: Shapefile (.shp)
- **Spatial Resolution**: 1:5,000,000
- **Location**: `JenisTanahIndonesia/`

### 2. Elevation Data

- **Source**: Indonesian Geospatial Agency (Badan Informasi Geospasial, BIG)
- **Format**: Shapefile (.shp)
- **Spatial Resolution**: 1:250,000 and 1:50,000
- **Location**: `SpotHeightIndonesia/`

### 3. Rainfall Data

- **Source**: Indonesian Meteorological, Climatological, and Geophysical Agency (BMKG)
- **Format**: CSV
- **Temporal Coverage**: 2011-2015 (5-year average)
- **Stations**: 34 observation stations across Indonesian provinces
- **Location**: Root directory

---

## Running the Notebook

### Option 1: Jupyter Notebook

```bash
jupyter notebook diversifikasipangan_final.ipynb
```

### Option 2: JupyterLab

```bash
jupyter lab diversifikasipangan_final.ipynb
```

### Option 3: VS Code

1. Open VS Code
2. Install the Python and Jupyter extensions
3. Open `diversifikasipangan_final.ipynb`
4. Select Python interpreter (your virtual environment)
5. Run all cells sequentially

### Execution Order

The notebook is organized into **15 sequential stages**. Execute cells in order:

| Stage | Description             | Cells         |
| ----- | ----------------------- | ------------- |
| 1-3   | Data Loading            | Cells 1-13    |
| 4-5   | Data Exploration        | Cells 14-22   |
| 6     | Feature Engineering     | Cells 23-35   |
| 7     | Preprocessing & PCA     | Cells 36-42   |
| 8     | Optimal k Determination | Cells 43-50   |
| 9     | K-Means Clustering      | Cells 51-55   |
| 10    | Hierarchical Validation | Cells 56-60   |
| 11    | Cluster Profiling       | Cells 61-70   |
| 12-13 | Crop Mapping            | Cells 71-85   |
| 14    | Visualization           | Cells 86-100  |
| 15    | Export Results          | Cells 101-117 |

### Expected Runtime

- **Full notebook execution**: ~2-5 minutes
- **Hardware requirements**: 4GB RAM minimum, 8GB recommended

---

## Key Results

### Identified Agroecological Zones (5 Clusters)

| Cluster | Zone Name                     | Provinces | Avg Rainfall | Primary Crops          |
| ------- | ----------------------------- | --------- | ------------ | ---------------------- |
| **C0**  | Dry–Moist Calcareous Sulawesi | 9         | 1,587 mm     | Maize, Sorghum, Millet |
| **C1**  | Humid Peat–Alluvial Sumatra   | 10        | 2,769 mm     | Sago, Rice             |
| **C2**  | Extreme Peat Kalimantan       | 7         | 2,758 mm     | Sago                   |
| **C3**  | Volcanic Intensive Java–Bali  | 7         | 2,016 mm     | Rice, Maize            |
| **C4**  | Equatorial Humid Maluku–Papua | 1         | 3,402 mm     | Sago                   |

### Carbohydrate Crop Functional Groups

| Functional Group  | Representative Crops        | Water Requirement    | Target Zones |
| ----------------- | --------------------------- | -------------------- | ------------ |
| Wetland Cereals   | Rice                        | High (>1500 mm)      | C1, C3       |
| Dryland Cereals   | Maize, Sorghum, Millet      | Low-Medium           | C0, C3       |
| Root & Tubers     | Cassava, Taro, Sweet Potato | Medium               | All zones    |
| Palms & Starch    | Sago, Sugar Palm            | Very High (>2500 mm) | C1, C2, C4   |
| Drought-Resilient | Porang, Ganyong, Arrowroot  | Low (<1000 mm)       | C0           |

### Clustering Quality Metrics (k=5)

| Metric                                | Value | Interpretation              |
| ------------------------------------- | ----- | --------------------------- |
| Silhouette Score                      | 0.414 | Good cluster cohesion       |
| Calinski-Harabasz Index               | 23.4  | Moderate cluster separation |
| Davies-Bouldin Index                  | 0.738 | Good (<1 is desirable)      |
| Adjusted Rand Index (vs Hierarchical) | 0.562 | Moderate method agreement   |

---

## Output Files

### `hasil_clustering_diversifikasi.csv`

The main output file containing clustering results and recommendations:

| Column                  | Description                                  |
| ----------------------- | -------------------------------------------- |
| `Provinsi`              | Province name                                |
| `Region`                | Geographic region (Sumatra, Java_Bali, etc.) |
| `Cluster_KMeans`        | Cluster assignment (0-4)                     |
| `Cluster_Name`          | Descriptive zone name                        |
| `Mean_Annual_Rainfall`  | Average rainfall (mm/year)                   |
| `Mean_Rainy_Days`       | Average rainy days per year                  |
| `Rainfall_Variability`  | Rainfall standard deviation                  |
| `Aridity_Index`         | Climate aridity indicator                    |
| `Climate_Zone`          | Climate classification                       |
| `Soil_Volcanic`         | Volcanic soil suitability (0-1)              |
| `Soil_Alluvial`         | Alluvial soil suitability (0-1)              |
| `Soil_Organic_Peat`     | Peat soil index (0-1)                        |
| `Soil_Calcareous`       | Calcareous soil index (0-1)                  |
| `Soil_Quality_Index`    | Composite soil quality score                 |
| `Primary_Crops`         | Recommended primary crops                    |
| `Diversification_Crops` | Recommended diversification crops            |

## Acknowledgments

- **Indonesian Geospatial Agency (BIG)** for elevation data
- **BMKG** for rainfall observation data
- **FAO-UNESCO** for soil classification data
- **Telkom University** for academic support

---

_Last Updated: December 2025_
