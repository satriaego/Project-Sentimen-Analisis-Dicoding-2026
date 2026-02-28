# Play Store Review Sentiment Analysis (Deep Learning)

Proyek ini bertujuan untuk melakukan klasifikasi sentimen (Positif, Negatif, Netral) terhadap ulasan aplikasi di Play Store menggunakan teknik **Natural Language Processing (NLP)** dan **Deep Learning**. Seluruh kriteria submission, termasuk kriteria opsional, telah terpenuhi dengan hasil yang memuaskan.

## Highlights & Achievements
* **Custom Dataset:** Menggunakan data hasil *scraping* mandiri dari Play Store dengan total **>10.000 sampel**.
* **Preprocessing & Labeling:** Data telah melalui tahap pembersihan dan pelabelan ke dalam 3 kelas kategori.
* **Multi-Scheme Experiment:** Melakukan 3 skema pelatihan berbeda untuk membandingkan performa berbagai algoritma Deep Learning.
* **Superior Accuracy:** Model berbasis **LSTM** berhasil mencapai akurasi **92.20%** pada testing set (melampaui target minimal 85%).
* **Inference Ready:** Model telah diuji dengan data baru dan memberikan output prediksi yang konsisten.

## Modeling Experiments

Kami melakukan eksperimen dengan tiga skema arsitektur yang berbeda untuk menemukan model dengan kemampuan generalisasi terbaik:

### Model A: Hybrid CNN-BiLSTM (Data Split 80:20)
* **Feature Extractor:** Menggunakan **Conv1D** untuk menangkap pola kata kunci lokal (*n-gram*).
* **Contextual Processing:** **Bidirectional LSTM** untuk memahami konteks temporal dua arah.
* **Regularization:** Kombinasi *SpatialDropout1D* dan *Dropout* standar.
* **Optimization:** Adam Optimizer dengan *Early Stopping*.

### Model B: Deep BiLSTM with Strict Regularization (Data Split 80:20)
* **Architecture:** Fokus pada **Bidirectional LSTM** murni untuk memori jangka panjang yang mendalam.
* **Strict Regularization:** Menerapkan **L2 Regularization (0.01)** pada layer LSTM dan Dense untuk menekan *noise*.
* **Robustness:** *SpatialDropout1D (0.5)* memberikan perlindungan ganda terhadap overfitting.
* **Optimization:** Adam dengan *Learning Rate* rendah (0.0001) berbasis *Validation Loss*.

### Model C: Efficient BiGRU (Data Split 70:30)
* **Architecture:** Menggunakan **Bidirectional GRU** yang lebih efisien secara komputasi namun tetap kuat menangkap konteks kalimat.
* **High Testing Portion:** Menguji ketangguhan model pada porsi data testing yang lebih besar (30%).
* **Adaptivity:** Menggunakan **ReduceLROnPlateau** untuk menjaga stabilitas konvergensi saat training.

## Model Performance
| Model Scheme | Accuracy (Testing Set) |
| :--- | :--- |
| **Model A** | **92.20%** |
| Model B | 91.61% |
| Model C | 91.29% |


## Inference Result
Model mampu memprediksi sentimen ulasan secara akurat sesuai dengan input yang diberikan.
<p align="center">
  <img src="https://lh3.googleusercontent.com/u/0/d/18MbDQ8J4y5NjWvmbPZyp3mPR2Dno3n4I" width="600" title="Accuracy Plot">
</p>

---
*Project ini dikembangkan sebagai bagian dari Submission Dicoding dengan pemenuhan seluruh kriteria wajib dan saran pengembangan.*
