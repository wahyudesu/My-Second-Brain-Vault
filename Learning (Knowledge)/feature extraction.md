#machinelearning 
Feature extraction dalam machine learning adalah proses mengubah data mentah menjadi fitur numerik yang dapat diproses sambil mempertahankan informasi dalam set data asli⁴. Ini adalah proses reduksi dimensi di mana set data mentah awal dikurangi menjadi kelompok yang lebih mudah dikelola untuk pemrosesan³. Fitur extraction sangat berguna ketika Anda perlu mengurangi jumlah sumber daya yang diperlukan untuk pemrosesan tanpa kehilangan informasi penting atau relevan. Tujuan ekstraksi fitur adalah untuk meringkas sebagian besar informasi yang terkandung dalam kumpulan fitur asli sambil mengurangi dimensi dataset.

Berikut adalah beberapa teknik feature extraction yang umum digunakan:
1. **Principal Components Analysis (PCA)**: Salah satu teknik reduksi dimensi linear yang paling banyak digunakan.
2. **Independent Component Analysis (ICA)**: Metode reduksi dimensi linear yang mengambil data sebagai input.
3. **Linear Discriminant Analysis (LDA)**: Teknik reduksi dimensi pembelajaran yang diawasi.
4. **Locally Linear Embedding (LLE)**: Metode seperti PCA dan LDA, yang mampu melakukan kinerja yang sangat baik.
5. **Autoencoders**: Digunakan di sini untuk mengidentifikasi fitur kunci dalam data untuk pengkodean dengan belajar dari pengkodean set data asli untuk mendapatkan yang baru¹.

Source: 
(1) Feature Extraction Explained - MATLAB & Simulink - MathWorks. https://www.mathworks.com/discovery/feature-extraction.html.
(2) Feature Extraction Definition | DeepAI. https://deepai.org/machine-learning-glossary-and-terms/feature-extraction.
(3) Feature Extraction Techniques. An end to end guide on how to reduce a .... https://towardsdatascience.com/feature-extraction-techniques-d619b56e31be.
(4) 6.2. Feature extraction — scikit-learn 1.3.1 documentation. https://scikit-learn.org/stable/modules/feature_extraction.html.

```python
>>> measurements = [
...     {'city': 'Dubai', 'temperature': 33.},
...     {'city': 'London', 'temperature': 12.},
...     {'city': 'San Francisco', 'temperature': 18.},
... ]

>>> from sklearn.feature_extraction import DictVectorizer
>>> vec = DictVectorizer()

>>> vec.fit_transform(measurements).toarray()
array([[ 1.,  0.,  0., 33.],
       [ 0.,  1.,  0., 12.],
       [ 0.,  0.,  1., 18.]])

>>> vec.get_feature_names_out()
array(['city=Dubai', 'city=London', 'city=San Francisco', 'temperature'], ...)
```
