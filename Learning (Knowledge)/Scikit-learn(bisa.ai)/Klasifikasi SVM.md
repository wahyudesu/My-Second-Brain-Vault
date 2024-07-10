#supervisedlearning #machinelearning #scikit-learn 
Support Vector Machine (SVM) merupakan salah satu algoritma machine learning yang menerapkan supervised learning atau pembelajaran terarah. Algoritma ini dapat digunakan baik untuk regresi maupun klasifikasi. Namun, algoritma ini seringkali digunakan untuk klasifikasi. 

SVM adalah algoritma machine learning yang digunakan untuk memisahkan kelas dalam data. Ketika data tidak bisa dipisahkan dengan garis lurus (linier), [[kernel SVM]] memungkinkan untuk memisahkan data yang lebih advance.

Pada SVM, kita memplotkan setiap item data sebagai titik dalam ruang berdimensi-n (dimana n adalah banyak fitur / variabel yang kita miliki). Kemudian, kita melakukan klasifikasi dengan cara menemukan hyper-plane yang membedakan kedua kelas dengan sangat baik. Ilustrasinya dapat dilihat dibawah ini:
![[Pasted image 20231021075805.png]]
Support vector adalah koordinat dari data observasi kita. Pengklasifikasian SVM bekerja dalam pembatasan atau pembagian menjadi 2 kelas. Cara SVM bekerja:
- Mengidentifikasi hyper-plane terbaik (Scenario-I): Disini kita memiliki 3 hyper-plane (A,B,C).
![[Pasted image 20231021075839.png]]
- Perlu diingat kembali bahwa algoritma SVM akan menentukan hyper-plane terbaik untuk membagi kelas menjadi 2, pada skenario ini hyper-plane terbaik yaitu B. Mengidentifikasi hyper-plane terbaik (Scenario-2): Disini kita memiliki 3 hyper-plane (A,B,C) yang membagi kelas dengan baik
### Implementasi SVM pada Python:
```python
from sklearn.datasets import load_iris
from sklearn import svm

# import dataset

iris = iris_load()
X,y = iris.data[:,0:2], iris.target
```
![[Pasted image 20231021080249.png]]
```python
# define model
clf = svm.SVC()

# fitting model

clf.fit(X,y)
```
![[Pasted image 20231021080330.png]]
[[Exercise SVM=70]]

