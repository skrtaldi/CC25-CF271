# SMART - Stunting Monitoring Alert Response Tools
<p align="center"> <img src="https://img.shields.io/badge/status-In%20Progress-yellow" /> <img src="https://img.shields.io/badge/Team-CC25--CF271-blue" /> </p>

SMART (Stunting Monitoring Alert Response Tools) adalah solusi digital berbasis machine learning yang dirancang untuk membantu pemangku kebijakan dan tenaga kesehatan dalam memantau dan merespons potensi risiko stunting pada anak secara dini. Proyek ini dikembangkan dalam konteks Capstone Project Dicoding. 

---

## 📌 Daftar Isi
  - Latar Belakang
  - Tujuan
  - Fitur Utama
  - Arsitektur Sistem
  - Struktur
  - Anggota Tim

---

## 📖 Latar Belakang
Stunting merupakan permasalahan kesehatan masyarakat yang mendesak di Indonesia, dengan dampak jangka panjang terhadap perkembangan kognitif, fisik, dan produktivitas anak di masa depan. Berdasarkan data dari Badan Kependudukan dan Keluarga Berencana Nasional (BKKBN) dan Kementerian Kesehatan, prevalensi stunting di Indonesia masih cukup tinggi meskipun telah terjadi penurunan dalam beberapa tahun terakhir.

Penyebab utama dari kondisi ini seringkali berakar pada kurangnya pemantauan pertumbuhan anak secara berkelanjutan, terutama di tingkat pelayanan dasar seperti Posyandu dan Puskesmas. Salah satu kendala signifikan dalam upaya pencegahan stunting adalah masih manualnya proses pencatatan dan pelaporan data pertumbuhan anak. Data yang tersimpan secara konvensional sulit untuk dianalisis secara cepat, sehingga identifikasi anak dengan risiko stunting sering terlambat.

Di sisi lain, tenaga kesehatan di lapangan memerlukan sistem yang tidak hanya mencatat data, tetapi juga mampu memberikan wawasan dan rekomendasi berbasis analisis cerdas untuk mendukung pengambilan keputusan yang tepat dan cepat.

---

## 🎯 Tujuan
Kondisi ini menjadi dasar tim kami untuk merancang solusi berbasis teknologi yang dapat meningkatkan efektivitas pemantauan pertumbuhan anak. Melalui pendekatan design thinking, kami melakukan eksplorasi kebutuhan pengguna langsung, terutama petugas di Posyandu dan Puskesmas, dan menemukan adanya kebutuhan nyata akan sistem digital yang:
- Intuitif dan mudah digunakan oleh tenaga kesehatan di lapangan,
- Mampu mencatat dan memvisualisasikan data pertumbuhan anak secara efisien,
- Dilengkapi dengan kemampuan prediktif untuk mengidentifikasi risiko stunting secara otomatis,
- Memberikan rekomendasi berbasis data untuk mendukung intervensi dini yang tepat sasaran.

---

## ⚙️ Fitur Utama

- 🔍 Prediksi klasifikasi risiko stunting berbasis model Machine Learning (Dense Neural Network, Decision Tree)
- 🧪 Eksplorasi & preprocessing dataset (SSGI, WHO)
- 🛠️ Integrasi RESTful API untuk komunikasi frontend–backend
- 📱 Web app responsif untuk berbagai ukuran perangkat
- 🧠 Inference real-time menggunakan model TensorFlow
- 🧾 Validasi input & interpretasi hasil prediksi
- 🖥️ Dashboard input data oleh pengguna (Puskesmas)

---

## 🏗 Arsitektur Sistem


## 📂 Struktur Proyek (Unfinished)  
- File(Machine Learning): model, dataset kaggle, capstone
by MC525D5X0112, MC525D5Y0147, MC525D5X0133
Proyek ini bertujuan untuk memprediksi status stunting pada anak berdasarkan data pemeriksaan antropometri dan dataset eksternal. Model dikembangkan menggunakan data real dan dataset eksternal dari Kaggle, disimpan dalam format `.h5`, serta dikonversi ke TensorFlow.js untuk prediksi berbasis web.

---

## 📁 Struktur Direktori

```bash
├── data_pemeriksaan/
│   ├── data_pemeriksaan.csv
│   ├── data_pemeriksaan_real.csv
│   ├── data_pemeriksaan_scale.csv
│   └── data_pemeriksaan_with_status.csv
│
├── dataset_training/
│   ├── stunting_dataset.csv
│   └── stunting_dataset_with_status.csv
│
├── model_h5/
│   ├── best_model.h5
│   └── model_stunting.h5
│
├── model-tfjs/
│   ├── group1-shard1of1.bin
│   └── model.json
│
└── predict_stunting.ipynb
```

---

## 📂 Penjelasan Folder & File

### `data_pemeriksaan/`

Berisi 831 riwayat pemeriksaan dari 50 anak.

- **`data_pemeriksaan.csv`**  
  Dataset real awal.

- **`data_pemeriksaan_realXX.csv`**  
  Variasi dataset real untuk percobaan (filter, gabung, dsb).

- **`data_pemeriksaan_scale.csv`**  
  Hasil transformasi fitur `Gender`, `Age`, `Weight`, `Height`.

- **`data_pemeriksaan_with_status.csv`**  
  Dataset dengan penambahan label status: `berpotensi stunting`, `normal`, atau `stunting`.

---

### `dataset_training/`

Berisi data latih dari Kaggle sebanyak 100.000 data.

- **`stunting_dataset.csv`**  
  Dataset mentah dari Kaggle.

- **`stunting_dataset_with_status.csv`**  
  Dataset yang telah:
  - Ditambahkan kolom ID
  - Dikonversi gender (`L=0`, `P=1`)
  - Dihitung HAZ berdasarkan standar WHO
  - Diberi label status stunting

---

### `model_h5/`

Model dalam format `.h5`:

- **`best_model.h5`**  
  Model dengan akurasi validasi terbaik.

- **`model_stunting.h5`**  
  Model lain yang digunakan untuk evaluasi.

---

### `model-tfjs/`

Model versi **TensorFlow.js** untuk digunakan di frontend/web:

- **`model.json`** – Arsitektur model.
- **`group1-shard1of1.bin`** – Bobot model.

---

### `predict_stunting.ipynb`

Notebook prediksi untuk data real dan data dummy:
- Preprocessing data
- Prediksi menggunakan model
- Visualisasi & evaluasi hasil

---

## ⚙️ Teknologi

- Python (Pandas, Scikit-learn, TensorFlow)
- TensorFlow.js
- Jupyter Notebook
- WHO Child Growth Standards (untuk HAZ)

---

## 🧠 Kategori Status

Model mengklasifikasikan status anak menjadi:

| Kategori              | Syarat HAZ        |
|-----------------------|-------------------|
| **Stunting**          | HAZ < -2          |
| **Berpotensi Stunting** | -2 ≤ HAZ < -1     |
| **Normal**            | HAZ ≥ -1          |

- BackEnd & FrontEnd
https://github.com/Faizz-spec/BackEnd-stunting
by FC525D5Y0158
https://github.com/AchmadMuchtaromZaydi/front_end_stunting/tree/main
by FC525D5Y0159, FC525D5Y0433

## 👥 Anggota Tim (CC25-CF271)
- FC-27 ACHMAD MUCHTAROM ZAYDI FC525D5Y0159
- MC-36 AJENG NINA RISKI MC525D5X0112
- MC-47 MOH. ALDI ROHMATULLOH MC525D5Y0147
- FC-42 ADAM RIKY PRATAMA FC525D5Y0433
- FC-26 AHMAD NUR FAIZIN FC525d5Y0158
- MC-45 ALVINA AULIA NISA MC525D5X0133





