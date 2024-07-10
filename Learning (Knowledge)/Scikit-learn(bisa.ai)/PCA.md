#scikit-learn #machinelearning 
## Reduksi Dimensi dengan PCA
Principal Component Analysis (PCA) adalah teknik yang memunculkan pola yang kuat dalam suatu kumpulan data dengan melihat variansinya. Hal ini dapat membantu untuk membersihkan kumpulan data agar mudah diexplore dan dianalisis. Definisi lain dari PCA adalah suatu metode untuk
mereduksi dimensi dengan mengubah kumpulan variabel besar menjadi variabel yang lebih kecil namun masih berisi sebagian besar informasi dari
data besar tersebut. Jadi, kesimpulan dari penggunaan PCA adalah menyederhakan banyak variabel dari suatu kumpulan data besar namun
mempertahankan informasi sebanyak mungkin.
## AdidasProses PCarkan pada:
- Varians dan Covarians
- Eigen Vector dan Eigen Values
## Langkah — langkah algoritma PCA:
### Standarisasi
Tujuan dalam langkah ini ialah untuk menstandarkan range variabel awal sehingga masing — masing variabel akan memberikan distribusi yang sama. Langkah ini sangatlah penting untuk proses sebelum PCA adalah karena PCA sangatlah sensitif terhadap varians dari sebuah variabel. Artinya jika ada perbedaan besar antara range variabel, variabel dengan range lebih besar akan mendominasi variabel dengan range kecil (misalnya jika ada variabel yang memiliki range 0 — 100 akan mendominasi variabel yang memiliki range 0 — 1) yang akan menyebabkan hasil bias. Jadi, dengan menstandarkan range tiap variabel ke Skala yang sebanding akan mencegah masalah ini.
### Formula standarisasi adalah sebagai berikut:
![[Pasted image 20231021075448.png]]
Tujuan dari langkah ini adalah untuk memahami bagaimana
variabel dari kumpulan data input bervariasi dari rata - rata
terhadap satu sama lainnya, dengan kata lain untuk melihat
apakah ada hubungan di antara mereka. Karena terkadang
variabel sangat berkorelasi sedemikian rupa sehingga mengandung informasi yang berlebihan. Jadi, untuk mengidentifikasi korelasi ini perlulah menghitung Covariance Matrix.
Matriks kovarians selalu berbentuk persegi (pxp) dimana p adalah
banyak dimensi (banyak variabel). Sebagai contoh jiika terdapat 3
variabel (x,y,z) maka matriks kovariansnya adalah:
![[Pasted image 20231021075623.png]]
### Hitung Eigen Vector dan Eigen Values
Eigenvector dan eigenvalues merupakan konsep dari aljabar linier
yang dihitung dari matriks kovarians sebelumnya untuk digunakan
dalam proses pencarian principal component dari sebuah data.
Principal Component adalah variabel baru yang dibuat sebagai
kombinasi linier dari variabel awal. Kombinasi ini dilakukan
sedemikian rupa sehingga variabel baru (principal component)
tidak berkorelasi dan sebagian besar informasi dalam variabel
awal diperas atau dikompresi ke dalam first component. Jadi jika
kita memiliki 10 dimensi akan memberikan 10 principal
component, tetapi PCA mencoba untuk memasukkan informasi
maksimum yang mungkin di first component, lalu informasi sisa
maksimum di second component dan seterusnya. Hingga
membentuk seperti gambar dibawah ini:
![[Pasted image 20231021075705.png]]
