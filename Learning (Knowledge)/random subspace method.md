#machinelearning 
Random subspace method, juga dikenal sebagai attribute bagging atau feature bagging, adalah algoritma ensemble yang mencoba mengurangi korelasi antara estimator dalam sebuah ensemble dengan melatih mereka pada sampel acak fitur alih-alih set fitur lengkap

Dalam pembelajaran ensemble, kita mencoba menggabungkan model yang dihasilkan oleh beberapa pembelajar menjadi sebuah ensemble yang berkinerja lebih baik daripada pembelajar asli¹. Salah satu cara menggabungkan pembelajar adalah bootstrap aggregating atau bagging, yang menunjukkan setiap pembelajar sampel acak subset dari titik pelatihan sehingga pembelajar akan menghasilkan model yang berbeda yang dapat dirata-ratakan dengan masuk akal¹.

Metode subspace acak mirip dengan bagging kecuali bahwa fitur ("atribut", "prediktor", "variabel independen") secara acak diambil sampel, dengan penggantian, untuk setiap pembelajar¹. Secara informal, ini menyebabkan pembelajar individu untuk tidak terlalu fokus pada fitur yang tampak sangat prediktif/deskriptif dalam set pelatihan, tetapi gagal menjadi prediktif untuk titik di luar set tersebut¹.

Metode subspace acak telah digunakan untuk pohon keputusan; ketika dikombinasikan dengan "bagging" pohon keputusan "biasa", model yang dihasilkan disebut hutan acak¹. Metode ini juga telah diterapkan pada klasifikasi linier¹, mesin vektor pendukung¹, tetangga terdekat¹ dan jenis klasifikasi lainnya. Metode ini juga dapat diterapkan pada klasifikasi satu kelas¹.

