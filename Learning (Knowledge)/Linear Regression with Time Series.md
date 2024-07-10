#machinelearning #supervisedlearning 
For the first part of this course, we'll use the linear regression algorithm to construct forecasting models. Linear regression is widely used in practice and adapts naturally to even complex forecasting tasks.

**Algoritma regresi linier** mempelajari cara menjumlahkan bobot dari fitur input-nya. For two features, we would have:

```
target = weight_1 * feature_1 + weight_2 * feature_2 + bias
```

During training, the regression algorithm learns values for the parameters `weight_1`, `weight_2`, and `bias` that best fit the `target`. (This algorithm is often called _ordinary least squares_ since it chooses values that minimize the squared error between the target and the predictions.) The weights are also called _regression coefficients_ and the `bias` is also called the [[Intercept]] karena memberi tahu Anda di mana grafik fungsi ini melintasi sumbu y.

### Time-step features[](https://www.kaggle.com/code/ryanholbrook/linear-regression-with-time-series#Time-step-features)

Contoh penerapan regresi linier dengan time series adalah untuk memprediksi penjualan produk di masa depan berdasarkan data penjualan di masa lalu. Fitur time-step yang dapat digunakan dalam model ini adalah bulan, tahun, atau bahkan hari. Selain itu, kita juga dapat menggunakan fitur lag, seperti penjualan bulan lalu atau penjualan dua bulan lalu.

Regresi linier dengan time series adalah metode peramalan yang sederhana dan efektif. Namun, penting untuk diperhatikan bahwa metode ini tidak dapat menangkap semua kompleksitas data time series. Jika data Anda sangat kompleks, Anda mungkin perlu menggunakan metode peramalan yang lebih *advance*.