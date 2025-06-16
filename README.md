# MLflow Project CI

Ini adalah proyek eksperimen Supervised Machine Learning (SML) yang mengotomatiskan re-training model dan packaging Docker image menggunakan MLflow dan GitHub Actions.

---

## Struktur Proyek

```
Eksperimen_SML_Nama-siswa/
├── .github/
│   └── workflows/
│       └── ci_mlflow_retrain.yaml   # Konfigurasi workflow GitHub Actions
├── MLproject/
│   ├── modelling.py                 # Skrip utama untuk pelatihan model MLflow
│   ├── requirements.txt             # Dependensi Python untuk proyek
│   ├── conda.yaml                   # Definisi lingkungan Conda (opsional, untuk reproduktifitas)
│   └── employee_preprocessing.csv   # Dataset input yang sudah diproses
└── README.md                      # File README ini
```

---

## Gambaran umum

Proyek ini mengimplementasikan alur Continuous Integration (CI) untuk model Machine Learning. Setiap kali ada perubahan pada branch main, GitHub Actions akan secara otomatis:

1. Menjalankan proyek MLflow Anda, yang akan melatih kembali model dan mencatat hasilnya secara lokal.
2. Membangun Docker image dari model yang baru dilatih.
3. Mendorong Docker image tersebut ke Docker Hub.
4. Mengunggah artifact MLflow (seperti model, metrik, parameter) sebagai artifact GitHub Actions.

---

## Running di Lokal

Untuk menjalankan proyek MLflow secara lokal:

1. **Klon repositori ini ke komputer Anda.** Pastikan Anda memiliki Python 3.12.7, Conda (jika menggunakan conda.yaml), dan Docker terinstal. Instal dependensi Python:
    ```bash
    pip install -r MLproject/requirements.txt
    ```
2. **Navigasi ke direktori root proyek di terminal Anda.** Jalankan proyek MLflow:
    ```bash
    mlflow run MLproject --env-manager=local
    ```
    (Ini akan mencatat run Anda ke direktori mlruns/ lokal.)