# Prapemrosesan Data Harian NASA POWER Kota Semarang

Repositori ini berisi kode prapemrosesan, data hasil prapemrosesan, indeks pembagian data, dan konfigurasi model
untuk artikel:

> A. Putri dan R. A. Pramunendar, "Klasifikasi Curah Hujan Harian Semarang Menggunakan XGBoost dengan Penanganan
> Class Imbalance dan Seleksi Fitur," *Building of Informatics, Technology and Science (BITS)*.

## Isi repositori

```
├── data/
│   └── DATAFINAL1.csv                  data mentah NASA POWER (3.653 hari)
├── hasil/
│   ├── data_prapemrosesan_1mm.csv      17 fitur, PRECTOTCORR, label, dan subset
│   ├── indeks_pembagian_data.csv       tanggal dan subset (latih/validasi/uji)
│   ├── distribusi_prectotcorr.png
│   └── matriks_korelasi.png
├── prapemrosesan_nasa_power.ipynb      kode prapemrosesan
├── konfigurasi_model.json              konfigurasi tuning, ambang, fitur terpilih, dan model final
└── requirements.txt
```

## Tahapan dalam notebook

1. Membaca dan meninjau data
2. Pemeriksaan kualitas: nilai kosong, nilai -999, duplikasi baris dan tanggal, kelengkapan kalender
3. Validasi fisik: rentang setiap parameter dan konsistensi antarparameter. WD2M dan WD10M dikeluarkan karena seluruh
   nilainya berada di luar rentang 0–360°, sehingga tersisa 17 fitur
4. Statistik deskriptif, *outlier* (metode IQR), dan *skewness*
5. Korelasi antarfitur
6. Pelabelan: Hujan (1) jika PRECTOTCORR ≥ 1 mm, Tidak Hujan (0) jika < 1 mm
7. Pembagian data kronologis: latih 2016–2022 (2.557 hari), validasi 2023–2024 (731 hari), uji 2025 (365 hari)
8. Menyimpan hasil ke folder `hasil/`

## Sumber data

NASA POWER Data Access Viewer (https://power.larc.nasa.gov), data harian pada koordinat 7,06° LS dan 110,45° BT,
periode 1 Januari 2016–31 Desember 2025.

## Cara menjalankan

```bash
pip install -r requirements.txt
jupyter notebook prapemrosesan_nasa_power.ipynb
```

Di Google Colab, unggah folder `data/` beserta notebook ke direktori kerja yang sama, lalu jalankan semua sel.

## Sitasi

Jika memakai kode atau data dalam repositori ini, mohon sitasi artikel di atas.
