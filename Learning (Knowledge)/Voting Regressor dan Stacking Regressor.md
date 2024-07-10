#ensemble
VotingRegressor dan StackingRegressor adalah dua metode ensemble learning yang digunakan dalam machine learning untuk menggabungkan beberapa model regresi menjadi satu model yang lebih kuat. Perbedaan utama antara keduanya adalah:

- VotingRegressor mengambil rata-rata tertimbang dari prediksi setiap model regresi individu dan mengembalikan prediksi akhir. VotingRegressor dapat menangani perbedaan skala antara model regresi dan dapat meningkatkan akurasi dan stabilitas model. Contoh:

```python
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor
from sklearn.ensemble import VotingRegressor

# Membuat model regresi individu
lr = LinearRegression()
dt = DecisionTreeRegressor()

# Membuat model VotingRegressor dengan bobot 0.7 untuk lr dan 0.3 untuk dt
vr = VotingRegressor(estimators=[('lr', lr), ('dt', dt)], weights=[0.7, 0.3])

# Melatih model VotingRegressor dengan data X dan y
vr.fit(X, y)

# Memprediksi nilai y baru dengan model VotingRegressor
y_pred = vr.predict(X_new)
```

- StackingRegressor mengambil output dari setiap model regresi individu dan menggunakan model regresi final untuk menghitung prediksi akhir. StackingRegressor dapat mempelajari hubungan non-linear antara model regresi dan dapat meningkatkan performa dan generalisasi model. Contoh:

```python
from sklearn.linear_model import RidgeCV
from sklearn.svm import LinearSVR
from sklearn.ensemble import RandomForestRegressor
from sklearn.ensemble import StackingRegressor

# Membuat model regresi individu
svr = LinearSVR(random_state=42)
rf = RandomForestRegressor(n_estimators=10, random_state=42)

# Membuat model regresi final
ridge = RidgeCV()

# Membuat model StackingRegressor dengan model regresi individu sebagai estimators dan model regresi final sebagai final_estimator
sr = StackingRegressor(estimators=[('svr', svr), ('rf', rf)], final_estimator=ridge)

# Melatih model StackingRegressor dengan data X dan y
sr.fit(X, y)

# Memprediksi nilai y baru dengan model StackingRegressor
y_pred = sr.predict(X_new)
```

Untuk informasi lebih lanjut, Anda dapat membaca dokumentasi berikut: atau . Anda juga dapat melihat contoh perbandingan antara keduanya di .
