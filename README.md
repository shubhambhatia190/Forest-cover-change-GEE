
# Forest Cover Change Detection Using Google Earth Engine (GEE)

This project leverages **Google Earth Engine (GEE)** and **Sentinel-2 imagery** to analyze and visualize forest cover changes over time in the **Dalma Wildlife Sanctuary**, India. The approach combines remote sensing, supervised classification, and temporal analysis to detect deforestation and forest loss from **2019 to 2023**.

> 🔗 [Open the GEE Script](https://code.earthengine.google.com/a83f96ed1a98086467c10db9a9001b7b)

---

## 📁 Folder Structure

```
Dalma_study_area/
└── AOI.shp   # Shapefile defining the Area of Interest (AOI)
```

The shapefile (`AOI`) should be uploaded as an **Earth Engine asset**. Make sure to update the script's `studyArea` variable with the asset path to this shapefile before running.

---

## 🗺️ Study Area

The analysis is focused on the **Dalma Wildlife Sanctuary**, located in **eastern India**, a region known for its ecological richness and diverse wildlife. This area has been under observation to study:

- Forest cover change between 2019 and 2023
- Deforestation hotspots
- Quantitative and visual summaries of changes

---

## 🛰️ Data Source

- **Satellite**: [Sentinel-2 Surface Reflectance Harmonised (S2 SR HARMONISED)](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- **Platform**: Google Earth Engine
- **Spatial Resolution**: 10 meters
- **Bands Used**:
  - `B2 (Blue)`
  - `B3 (Green)`
  - `B4 (Red)` – for true-color visualization
  - `B8 (NIR)` – for vegetation density
  - `B11, B12 (SWIR)` – for moisture and land cover separation

---

## 🧪 Methodology

1. **Data Preprocessing**
   - Cloud masking using `MSK_CLDPRB`, `MSK_SNWPRB`, and `SCL` bands
   - Year-wise median composite generation for 2019 and 2023

2. **Training Data**
   - Supervised classification using labeled samples (`Forest` = 1, `Other` = 0)
   - Training shapefiles stored as GEE assets

3. **Classification**
   - A decision tree classifier (`smileCart`) is trained and applied for both years
   - Outputs are classified land cover images

4. **Change Detection**
   - Post-classification comparison between 2019 and 2023
   - Change matrix and area statistics calculated to quantify forest loss

---

## 📊 Outputs

- Classified land cover maps for 2019 and 2023
- Change detection map highlighting forest gain/loss
- Area statistics for forest change over time
- Visuals and layers rendered in the Earth Engine Map panel

---

## 🔧 Instructions to Run

1. Upload the `AOI.shp` file (inside the `Dalma_study_area` folder) as an asset to your GEE account.
2. In the GEE script, replace the `studyArea` asset path with the one from your account:
   ```javascript
   var studyArea = ee.FeatureCollection("users/your_username/Dalma_AOI");
   ```
3. Run the script to generate composites, classify images, and visualize forest cover change.

---

## 📌 Author

- **Developed by**: Shubham Bhatia
- **Tools**: JavaScript API, Google Earth Engine, Sentinel-2

---

## 📜 License

This project is open for academic and non-commercial use. Please cite appropriately if used in publications.
