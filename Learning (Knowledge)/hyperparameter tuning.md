#sklearn #machinelearning 
## proses menemukan kombinasi hyperparameter terbaik untuk suatu model machine learning
```python
from sklearn.model_selection import GridSearchCV
from sklearn.neighbors import KNeighborsClassifier

# Tentukan parameter yang akan di-tuning
param_grid = {
    'n_neighbors': [3, 5, 7, 9],
    'weights': ['uniform', 'distance'],
    'leaf_size': [15, 20]
}

# Buat objek GridSearchCV
knn = KNeighborsClassifier()
gs_knn = GridSearchCV(knn, param_grid, scoring='accuracy', cv=5)

# Fit model pada data training
gs_knn.fit(X_train, y_train)

# Dapatkan parameter terbaik
best_params = gs_knn.best_params_

# Print parameter terbaik
print(best_params)
```

- **KNeighborsClassifier**
    - `n_neighbors`: jumlah tetangga terdekat yang akan digunakan untuk membuat prediksi
    - `weights`: metode untuk menghitung bobot tetangga terdekat
    - `leaf_size`: ukuran daun dari pohon keputusan yang digunakan untuk mewakili data
- **LogisticRegression**
    - `C`: kekuatan regularisasi
    - `penalty`: jenis regularisasi yang akan digunakan
    - `solver`: algoritma yang akan digunakan untuk melatih model
- **RandomForestClassifier**
    - `n_estimators`: jumlah pohon keputusan yang akan dibangun
    - `max_depth`: kedalaman maksimum dari setiap pohon keputusan
    - `min_samples_split`: jumlah sampel minimum yang diperlukan untuk membagi node dalam pohon keputusan
- **SupportVectorMachine**
    - `C`: kekuatan regularisasi
    - `kernel`: jenis kernel yang akan digunakan
    - `gamma`: parameter kernel