Decision boundary adalah garis atau permukaan yang memisahkan dua atau lebih kelas data. Garis ini didefinisikan oleh model pembelajaran mesin, dan digunakan untuk memprediksi kelas data baru.

![[Pasted image 20230917124221.png|375]]

Dalam konteks data mining, decision boundary digunakan untuk mengklasifikasikan data. Misalnya, kita dapat menggunakan decision boundary untuk memisahkan data pelanggan menjadi dua kelas: pelanggan yang akan berlangganan layanan baru dan pelanggan yang tidak akan berlangganan.

Ada berbagai jenis model pembelajaran mesin yang dapat digunakan untuk menentukan decision boundary. Beberapa model yang umum digunakan adalah:

- **Logistic regression**
- **Support vector machines**
- **Decision trees**
- **Random forests**

**Logistic regression** menggunakan fungsi logistik untuk memprediksi probabilitas suatu data masuk ke dalam suatu kelas. Decision boundary untuk model logistic regression adalah garis yang memotong titik di mana probabilitas untuk dua kelas sama.

**Support vector machines** menggunakan konsep margin untuk menentukan decision boundary. Margin adalah jarak antara decision boundary dan titik terdekat dari setiap kelas. Model support vector machines akan memilih decision boundary yang memaksimalkan margin.

**Decision trees** menggunakan pohon keputusan untuk menentukan decision boundary. Pohon keputusan adalah struktur berhierarki yang membagi data menjadi dua atau lebih bagian. Decision boundary untuk model decision trees adalah garis yang membagi dua bagian dari pohon keputusan.

**Random forests** adalah ensemble dari decision trees. Decision boundary untuk model random forests adalah garis yang merupakan kombinasi dari decision boundary dari decision trees dalam ensemble.

**Formula untuk decision boundary**

Formula untuk decision boundary untuk model pembelajaran mesin yang umum digunakan adalah sebagai berikut:

- **Logistic regression:**

```
f(x) = 1 / (1 + exp(-(β0 + β1*x1 + β2*x2)))
```

di mana:

- f(x) adalah nilai output dari model
- β0, β1, β2 adalah parameter model
- x1 dan x2 adalah fitur data

- **Support vector machines:**

```
f(x) = sign(w1*x1 + w2*x2 + b)
```

di mana:

- f(x) adalah nilai output dari model
- w1, w2, b adalah parameter model
- x1 dan x2 adalah fitur data

- **Decision trees:**

```
f(x) = T(x)
```

di mana:

- f(x) adalah nilai output dari model
- T(x) adalah fungsi keputusan dari model