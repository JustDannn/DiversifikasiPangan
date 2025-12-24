# Food Diversification Analysis Based on Agro-Ecological Clustering in Indonesia

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Overview

This research project analyzes **carbohydrate food diversification potential** across Indonesian provinces using **agro-ecological clustering** based on climate, soil, and geographical data. The study aims to identify optimal crop recommendations for each agro-ecological zone to enhance food security and agricultural resilience.

### Research Objectives

1. **Characterize agro-ecological zones** across Indonesian provinces based on rainfall, soil types, and elevation data
2. **Apply clustering algorithms** (K-Means and Hierarchical) to identify distinct agricultural zones
3. **Map functional crop groups** to each cluster for targeted food diversification strategies
4. **Provide data-driven recommendations** for carbohydrate crop diversification

---

## Repository Structure

```
Diversifikasi/
├── diversifikasipangan_final.ipynb    # Main analysis notebook
├── README.md                           # This documentation
├── .gitattributes                      # Git LFS configuration for shapefiles
│
├── Jumlah Curah Hujan dan Jumlah Hari Hujan di Stasiun Pengamatan   BMKG 2011-2015.csv
│   └── Rainfall data from BMKG weather stations (2011-2015)
│
├── JenisTanahIndonesia/               # Soil type shapefile data
│   └── Jenis Tanah Indonesia.shp      # FAO soil classification for Indonesia
│
└── SpotHeightIndonesia/               # Elevation shapefile data
    ├── Spot Height 250K.shp           # 1:250,000 scale elevation points
    └── Spot Height 50K.shp            # 1:50,000 scale elevation points
```

---

## Data Sources

| Dataset              | Description                                                 | Source         | Format           |
| -------------------- | ----------------------------------------------------------- | -------------- | ---------------- |
| **Rainfall Data**    | Annual rainfall and rainy days by BMKG stations (2011-2015) | BMKG Indonesia | CSV              |
| **Soil Types**       | FAO soil classification polygons                            | BIG Indonesia  | Shapefile (.shp) |
| **Elevation (250K)** | Spot heights at 1:250,000 scale                             | BIG Indonesia  | Shapefile (.shp) |
| **Elevation (50K)**  | Spot heights at 1:50,000 scale                              | BIG Indonesia  | Shapefile (.shp) |

### Data Attributes

#### Rainfall CSV Columns

- `Provinsi` - Province name
- `Stasiun_BMKG` - Weather station name
- `CH_YYYY` - Annual rainfall (mm) for year YYYY
- `HH_YYYY` - Number of rainy days for year YYYY

#### Soil Shapefile Attributes

- `FAOSOIL` - FAO soil classification code
- `DOMSOI` - Dominant soil type
- `Sub_Group_` - Soil subgroup classification
- `SQKM` - Area in square kilometers
- `geometry` - Polygon geometry

#### Elevation Shapefile Attributes

- `ELEVAS` - Elevation in meters
- `geometry` - Point geometry

---

## Prerequisites & Installation

### System Requirements

- **Python**: 3.8 or higher
- **RAM**: Minimum 8GB recommended
- **Storage**: ~500MB for data and outputs

### Required Python Packages

```bash
# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # Linux/macOS
# or
venv\Scripts\activate     # Windows

# Install required packages
pip install -r requirements.txt
```

### Package List

Create a `requirements.txt` file with:

```txt
pandas>=1.5.0
numpy>=1.21.0
geopandas>=0.12.0
shapely>=2.0.0
matplotlib>=3.5.0
seaborn>=0.12.0
scikit-learn>=1.1.0
scipy>=1.9.0
jupyter>=1.0.0
notebook>=6.5.0
```

Or install directly:

```bash
pip install pandas numpy geopandas shapely matplotlib seaborn scikit-learn scipy jupyter
```

## Running the Notebook

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd Diversifikasi
```

> **Note:** This repository uses Git LFS for shapefile storage. Ensure Git LFS is installed:
>
> ```bash
> git lfs install
> git lfs pull
> ```

### Step 2: Activate Environment & Install Dependencies

```bash
# Activate virtual environment
source venv/bin/activate  # Linux/macOS

# Install packages
pip install -r requirements.txt
```

### Step 3: Launch Jupyter Notebook

```bash
jupyter notebook diversifikasipangan_final.ipynb
```

Or use JupyterLab:

```bash
pip install jupyterlab
jupyter lab
```

### Step 4: Run All Cells

Execute cells sequentially from top to bottom. The notebook is organized into these sections:

1. **Library Imports** (Cell 1)
2. **Data Loading** (Cells 2-19)
3. **Exploratory Data Analysis** (Cells 20-36)
4. **Feature Engineering** (Cells 37-51)
5. **Clustering Analysis** (Cells 52-72)
6. **Crop Recommendation Mapping** (Cells 73-104)

## 🗺️ Results: Agro-Ecological Clusters

The analysis identifies **5 distinct agro-ecological zones**:

### Cluster 0: Dry–Moist Calcareous Sulawesi Zone

- **Provinces:** Sulawesi regions
- **Characteristics:** Moderate-low rainfall (~1,587 mm), calcareous soils
- **Primary Crops:** Maize, Sorghum, Foxtail Millet
- **Diversification:** Porang, Ganyong, Drought-tolerant Cassava

### Cluster 1: Humid Peat–Alluvial Sumatra Zone

- **Provinces:** Sumatra regions
- **Characteristics:** High rainfall (~2,769 mm), peat and alluvial soils
- **Primary Crops:** Sago, Wetland Rice
- **Diversification:** Cassava, Taro, Sweet Potato

### Cluster 2: Extreme Peat Kalimantan Wet Zone

- **Provinces:** Kalimantan regions
- **Characteristics:** Very high rainfall (~2,758 mm), extreme peat soils
- **Primary Crops:** Sago
- **Diversification:** Taro, Wild Yams

### Cluster 3: Volcanic Intensive Java–Bali Zone

- **Provinces:** Java, Bali, DKI Jakarta, DI Yogyakarta
- **Characteristics:** Moderate rainfall (~2,016 mm), highly fertile volcanic soils
- **Primary Crops:** Rice, Maize
- **Diversification:** Potato, Sweet Potato, Cassava

### Cluster 4: Equatorial Humid Core (Maluku–Papua)

- **Provinces:** Maluku, Papua regions
- **Characteristics:** Extreme rainfall (~3,402 mm), high variability
- **Primary Crops:** Sago
- **Diversification:** Taro, Sweet Potato

---

## Functional Crop Groups

| Group                       | Crops                               | Water Requirement           | Soil Preference      |
| --------------------------- | ----------------------------------- | --------------------------- | -------------------- |
| **Wetland Cereals**         | Rice                                | High (>1,500 mm)            | Alluvial, Volcanic   |
| **Dryland Cereals**         | Maize, Sorghum, Millet              | Low-Moderate (600-1,200 mm) | Volcanic, Calcareous |
| **Root & Tubers (Humid)**   | Cassava, Taro, Sweet Potato, Potato | Moderate (1,000-2,000 mm)   | Volcanic, Alluvial   |
| **Palms & Starch Trees**    | Sago, Aren, Enau                    | Very High (>2,500 mm)       | Organic/Peat, Swamp  |
| **Drought-Resilient Roots** | Ganyong, Porang, Garut, Uwi         | Low (<1,000 mm)             | Calcareous, Sandy    |

---

## Key Findings

1. **Volcanic regions (Java-Bali)** have the highest agricultural potential for intensive rice-maize systems

2. **Peatland regions (Kalimantan, Sumatra)** require focus on sago and wetland-adapted crops

3. **Eastern Indonesia (Maluku-Papua)** should prioritize sago as primary carbohydrate source

4. **Sulawesi and drier regions** benefit from drought-resilient crops like sorghum and porang

5. **Diversification strategies** should be tailored to each agro-ecological zone for resilience

---

## Acknowledgments

- **BMKG Indonesia** for rainfall data
- **BIG (Badan Informasi Geospasial)** for geospatial data
- **FAO** for soil classification standards
