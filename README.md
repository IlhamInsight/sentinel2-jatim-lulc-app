# Sistem Geospasial LULC Sentinel-2 Jawa Timur (Standalone Streamlit App)

Aplikasi web interaktif klasifikasi tutupan dan penggunaan lahan (*Land Use / Land Cover* - LULC) Provinsi Jawa Timur berbasis data spektral satelit Sentinel-2 L2A (12 band spektral + indeks NDVI/NDWI/NDBI) menggunakan model terbaik Machine Learning (LightGBM).

---

## Struktur Direktori Standalone

```
.
├── app.py                      # Aplikasi utama Streamlit
├── requirements.txt            # Dependensi Python untuk runtime cloud
├── .gitignore                  # Konfigurasi Git
├── models/
│   ├── model_terbaik.pkl       # Serialisasi model LightGBM (13.7 MB)
│   └── model_metadata.json     # Metadata performa & metrik evaluasi
├── prepared_data/
│   └── data_prepared_all.csv   # Dataset sampel pra-proses (1.000 titik)
└── sampling_geojson/           # Poligon ROI ground truth geospasial (5 kelas)
    ├── bangunan.geojson
    ├── pertanian.geojson
    ├── perairan.geojson
    ├── hutan.geojson
    └── mangrove.json
```

---

## Menjalankan Aplikasi Secara Lokal

1. Clone repositori ini atau masuk ke direktori:
   ```bash
   cd standalone_streamlit_app
   ```

2. Buat virtual environment (opsional namun direkomendasikan):
   ```bash
   python -m venv venv
   # Di Windows:
   venv\Scripts\activate
   # Di Linux/macOS:
   source venv/bin/activate
   ```

3. Pasang semua dependensi:
   ```bash
   pip install -r requirements.txt
   ```

4. Jalankan aplikasi Streamlit:
   ```bash
   streamlit run app.py
   ```

Aplikasi akan otomatis terbuka pada browser di `http://localhost:8501`.

---

## Deploy ke Streamlit Community Cloud (Gratis)

1. Buat repositori baru di GitHub (misal: `sentinel2-jatim-lulc-app`).
2. Masukkan semua isi folder ini ke repositori tersebut:
   ```bash
   git init
   git add .
   git commit -m "Deploy: Inisialisasi standalone LULC Streamlit app"
   git branch -M main
   git remote add origin https://github.com/USERNAME_ANDA/sentinel2-jatim-lulc-app.git
   git push -u origin main
   ```
3. Buka [Streamlit Community Cloud](https://share.streamlit.io/).
4. Klik **"New app"** dan isi:
   - **Repository**: `USERNAME_ANDA/sentinel2-jatim-lulc-app`
   - **Branch**: `main`
   - **Main file path**: `app.py`
5. Klik **"Deploy!"**.
