# Case-Based Reasoning untuk Analisis Putusan Perdata Merek

Repositori ini berisi implementasi sistem *Case-Based Reasoning* (CBR) untuk menganalisis putusan pengadilan perdata khusus merek. Sistem ini menggunakan pendekatan berbasis teks dengan representasi dokumen menggunakan TF-IDF dan evaluasi kinerja klasifikasi menggunakan algoritma SVM dan Naive Bayes.

## 📚 Latar Belakang

Putusan pengadilan merupakan sumber data penting yang dapat dimanfaatkan untuk mendukung pengambilan keputusan hukum berbasis kasus sebelumnya. Dalam proyek ini, pendekatan CBR digunakan untuk membangun sistem yang mampu mengidentifikasi, merepresentasikan, dan mencocokkan kasus hukum berdasarkan kemiripan isi dokumen.

## ⚙️ Tahapan Proyek

### 1. Membangun Case Base

* **Pengumpulan Dokumen**: Data dikumpulkan melalui proses scraping dari situs Mahkamah Agung, dengan fokus pada perkara perdata merek.
* **Ekstraksi Teks**: Dokumen dalam format PDF dikonversi menjadi teks menggunakan `pdfminer`.
* **Pembersihan Data**: Melibatkan penghapusan watermark, disclaimer, dan elemen non-konten lainnya, serta normalisasi teks.
* **Logging & Validasi**: Proses didokumentasikan secara sistematis untuk menjamin integritas data.

> 🔹 Output: 70 dokumen berhasil dikonversi dan disimpan di `data/raw/`, log pembersihan disimpan di `logs/cleaning.log`.

### 2. Representasi Kasus

* **Ekstraksi Metadata**: Mengambil elemen penting dari dokumen (nomor perkara, tanggal, fakta hukum).
* **Representasi TF-IDF**: Setiap dokumen direpresentasikan sebagai vektor berdasarkan kemunculan term.
* **Visualisasi**: Distribusi fitur divisualisasikan untuk memahami karakteristik data.

### 3. Retrieval & Klasifikasi

* **Similarity Matching**: Mengukur kemiripan antar kasus menggunakan cosine similarity.
* **Klasifikasi**: Implementasi dan evaluasi model SVM dan Naive Bayes terhadap vektor TF-IDF.
* **Evaluasi**: Metrik akurasi, precision, recall, dan F1-score dihitung untuk menilai kinerja model.

## 📁 Struktur Direktori

```
.
├── data/
│   ├── raw/                # Dokumen hasil ekstraksi teks
│   └── eval/               # Hasil evaluasi model klasifikasi
├── logs/
│   └── cleaning.log        # Catatan proses pembersihan dokumen
├── Merek_PDF/              # PDF asli hasil scraping
├── casebase.ipynb          # Notebook utama
└── README.md               # Dokumentasi ini
```

## 🛠️ Dependensi

Proyek ini dikembangkan dengan Python 3.x dan membutuhkan pustaka berikut:

* `pandas`, `numpy`
* `scikit-learn`
* `pdfminer.six`
* `matplotlib`, `seaborn`
* `nltk`, `re`

Instalasi dapat dilakukan melalui:

### 1. Clone the Repository
```bash
git clone https://github.com/AdamKurnia313/CBR_PDK-Merek
cd CBR_PDK-Merek
```
### 2. Create and Activate a Virtual Environment
```bash
python -m venv venv

# For Windows
venv\Scripts\activate

# If PowerShell policy error:
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

# For macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

If `requirements.txt` is still empty, you can generate it automatically:
```bash
pip install pipreqs
pipreqs . --force
```

> 📌 Catatan: Pastikan folder `Merek_PDF/` dan `data/raw/` sudah tersedia sebelum menjalankan notebook.

## 📊 Hasil Evaluasi

Model klasifikasi menunjukkan bahwa pendekatan berbasis TF-IDF efektif dalam membedakan kategori putusan dengan akurasi memuaskan. Evaluasi lebih lanjut terdapat dalam folder `data/eval/`.

## 👨‍💻 Kontributor

* Adam Kurniawan — 202210370311211
* Wafiq Azizah - 202210370311247
  Tugas Besar Mata Kuliah Penalaran Komputer (B)
