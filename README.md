# Play Store Review Sentiment Analysis: Gemini App (Deep Learning)

Proyek ini melakukan klasifikasi sentimen (**Positif, Negatif, Netral**) terhadap ulasan pengguna aplikasi **Gemini** di Google Play Store. Fokus utama adalah membandingkan tiga arsitektur Deep Learning (CNN, LSTM, GRU) dalam memahami konteks bahasa alami dari data hasil *scraping* mandiri.

## 🚀 Highlights & Achievements
* **Custom Dataset:** >10.000 ulasan aplikasi Gemini yang diambil secara mandiri melalui *scraping*.
* **Preprocessing:** Pembersihan teks (cleansing), pelabelan otomatis/manual ke dalam 3 kelas, dan ekstraksi fitur NLP.
* **Multi-Scheme Experiment:** Implementasi 3 arsitektur berbeda dengan teknik regularisasi ketat.
* **High Accuracy:** Model terbaik mencapai akurasi **92.20%** pada testing set.
* **Inference Ready:** Validasi model menggunakan data baru (unseen data) dengan import **SavedModel**.

---

## 🏗️ Modeling Experiments



### Model A: Hybrid CNN-BiLSTM (Data Split 80:20)
* **Feature Extractor:** Menggunakan **Conv1D** untuk menangkap pola kata kunci lokal (*n-gram*).
* **Contextual Processing:** **Bidirectional LSTM** untuk memahami konteks temporal dua arah.
* **Regularization:** *SpatialDropout1D* dan *Dropout* standar.
* **Optimization:** Adam Optimizer dengan *Early Stopping*.



### Model B: Deep BiLSTM with Strict Regularization (Data Split 80:20)
* **Architecture:** Bidirectional LSTM murni untuk memori jangka panjang yang mendalam.
* **Strict Regularization:** **L2 Regularization (0.01)** pada layer LSTM dan Dense.
* **Robustness:** *SpatialDropout1D (0.5)* dan *Dropout (0.5)* untuk mencegah overfitting.
* **Optimization:** Adam dengan *Learning Rate* rendah (0.0001).



### Model C: Efficient BiGRU (Data Split 70:30)
* **Architecture:** **Bidirectional GRU** yang lebih efisien komputasi untuk menangkap konteks dua arah.
* **High Testing Portion:** Pengujian ketangguhan pada porsi data testing 30%.
* **Adaptivity:** Menggunakan **ReduceLROnPlateau** untuk stabilitas konvergensi.

---

## 📊 Performance Summary
| Model Scheme | Architecture | Accuracy (Testing Set) |
| :--- | :--- | :--- |
| **Model A** | **Hybrid CNN-BiLSTM** | **92.20%** |
| **Model B** | **Deep BiLSTM** | **91.61%** |
| **Model C** | **BiGRU** | **91.29%** |

## 🧪 Inference Result
Tahap inferensi menggunakan import **SavedModel** untuk memvalidasi model pada data baru. Model mampu memprediksi sentimen ulasan secara akurat sesuai dengan input yang diberikan.

<p align="center">
  <img src="https://lh3.googleusercontent.com/u/0/d/18MbDQ8J4y5NjWvmbPZyp3mPR2Dno3n4I" width="600" title="Inference Result">
</p>

---
*Project ini memenuhi seluruh kriteria wajib dan saran pengembangan submission.*
