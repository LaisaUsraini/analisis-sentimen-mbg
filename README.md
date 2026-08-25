# Analisis Sentimen MBG

Analisis Sentimen Opini Publik terhadap Program Makan Bergizi Gratis (MBG) di Media Sosial X Menggunakan Naïve Bayes Classifier dan Support Vector Machine.

## Deskripsi

Penelitian ini menganalisis sentimen opini publik terhadap program Makan Bergizi Gratis (MBG) pada media sosial X. Penelitian membandingkan dua algoritma klasifikasi, yaitu Naïve Bayes Classifier (NBC) dan Support Vector Machine (SVM), tidak hanya dari sisi kinerja klasifikasi, tetapi juga dari sisi efisiensi komputasi yang diukur melalui training time dan inference time.

Penelitian menggunakan kerangka kerja SEMMA dan diimplementasikan dengan Python pada Google Colaboratory.

## Dataset

Data dikumpulkan dari media sosial X menggunakan Tweet-Harvest oleh Helmi Satria (https://github.com/helmisatria/tweet-harvest). Data dikumpulkan menggunakan tiga kata kunci terkait program MBG dengan filter bahasa Indonesia.

Tahapan pembersihan data:
- Data mentah awal: 7.922 baris
- Setelah pembuangan duplikat eksak: 6.147 baris
- Setelah cleansing dan pembuangan duplikat tersembunyi: 4.732 baris
- Data akhir setelah seluruh preprocessing: 4.666 baris

Distribusi label:
- Positif: 2.258 tweet
- Negatif: 2.059 tweet
- Netral: 349 tweet

### Skema Kolom Dataset Final

| Kolom | Keterangan |
|-------|-----------|
| full_text | Teks tweet asli |
| text_final | Teks setelah preprocessing |
| skor_sentimen | Skor sentimen dari leksikon InSet |
| label | Label sentimen akhir (positif, negatif, netral) |

Struktur folder data:
- `dataset_mentah.csv` — data gabungan hasil Tweet-Harvest (kolom full_text)
- `dataset_final_berlabel.csv` — data setelah preprocessing dan pelabelan

## Metode

Tahapan preprocessing: cleansing, case folding, tokenisasi, normalisasi, stopword removal, dan stemming. Pembobotan kata menggunakan TF-IDF. Pelabelan menggunakan pendekatan berbasis leksikon InSet.

Model dievaluasi menggunakan tiga rasio pembagian data (70:30, 80:20, 90:10) dan K-Fold Cross Validation (k=10).

## Hasil

Berdasarkan hasil rata-rata K-Fold Cross Validation:

| Metrik | NBC | SVM |
|--------|-----|-----|
| Akurasi | 69,22% | 81,20% |
| Precision | 46,88% | 67,19% |
| Recall | 49,54% | 59,05% |
| F1-Score | 47,65% | 57,44% |

Dari sisi efisiensi komputasi, SVM membutuhkan waktu pelatihan sekitar 270 kali lebih lama dan waktu prediksi sekitar 555 kali lebih lama dibandingkan NBC.

Temuan menunjukkan adanya trade-off, yaitu SVM unggul dari sisi akurasi, sedangkan NBC unggul dari sisi efisiensi komputasi.

## Struktur Repositori

- `data/` — dataset mentah dan dataset final berlabel
- `notebooks/` — notebook penelitian
- `requirements.txt` — daftar pustaka yang digunakan

## Pustaka

Penelitian ini menggunakan Python dengan pustaka utama seperti pandas, scikit-learn, Sastrawi, NLTK, dan WordCloud. Daftar lengkap terdapat pada requirements.txt.

## Catatan

Dataset yang dibagikan tidak menyertakan informasi identitas pengguna demi menjaga privasi.
