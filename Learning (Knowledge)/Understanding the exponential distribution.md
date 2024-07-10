#statistika 
## Lambda
Lambda (λ) adalah parameter distribusi eksponensial. Parameter lambda adalah parameter penting dari distribusi eksponensial yang menentukan tingkat rata-rata kejadian. Lambda adalah parameter laju, yang menunjukkan seberapa sering suatu peristiwa terjadi dalam interval waktu tertentu.
  
Lambda (λ) adalah parameter distribusi eksponensial yang tidak memiliki batasan atas. Artinya, λ dapat berupa bilangan positif apa pun.

Secara umum, semakin besar nilai λ, semakin sering suatu peristiwa terjadi. Misalnya, jika λ = 1/2, maka mean dan variansi distribusi eksponensial adalah 2 dan 4. Hal ini berarti bahwa, pada rata-rata, suatu peristiwa akan terjadi setiap 2 unit waktu.

Jika parameter lambda didefinisikan sebagai 2 maka:
- **Rata-rata waktu antara dua kejadian adalah 2.**
- **Probabilitas kejadian terjadi dalam waktu 2 adalah 0,5.**
- **Probabilitas kejadian terjadi dalam waktu 4 adalah 0,25.**
- **Probabilitas kejadian terjadi dalam waktu 6 adalah 0,125.**
Kok tau, hal ini dapat dihitung dengan menggunakan fungsi kepadatan peluang (pdf) dari distribusi eksponensial
## Contoh lambda 
Berikut adalah beberapa contoh nilai λ yang dapat digunakan untuk model peristiwa yang terjadi secara acak dan independen:
- **Waktu yang dibutuhkan untuk suatu komponen elektronik rusak:** λ = 1/1000
- **Waktu yang dibutuhkan untuk pelanggan tiba di antrian:** λ = 1/20
- **Waktu yang dibutuhkan untuk suatu panggilan telepon diterima:** λ = 1/10
- **Waktu yang dibutuhkan untuk suatu proyek selesai:** λ = 1/100
- **Waktu yang dibutuhkan untuk suatu penyakit berkembang:** λ = 1/10000
## Rumus lambda
Mean dan variansi distribusi eksponensial adalah sebagai berikut:

```
mean μ = E(x) = 1/λ 
σ² = Var(x) = 1/λ²
Source: wikipedia
```
Persamaan tersebut menyatakan bahwa rata-rata (μ) dari variabel acak yang terdistribusi secara eksponensial (x) sama dengan kebalikan dari parameter laju (λ). 
Dengan kata lain, semakin besar parameter laju, semakin pendek waktu yang diharapkan di antara kejadian-kejadian, dan semakin kecil mean dari distribusi.
## Kode R
R memiliki empat fungsi untuk menangani distribusi eksponensial, yaitu:

- `dexp()`: mengembalikan nilai fungsi kepadatan probabilitas (PDF) distribusi eksponensial.
- `pexp()`: mengembalikan nilai fungsi kumulatif probabilitas (CDF) distribusi eksponensial.
- `qexp()`: mengembalikan nilai kuantil distribusi eksponensial.
- `rexp()`: menghasilkan bilangan acak dari distribusi eksponensial.

```
# Mendefinisikan parameter lambda, contoh 2
lambda <- 2
# Mendefinisikan jumlah sampel acak yang akan dihasilkan, contoh 1000 kali percobaan
n <- 1000
# Mendefinisikan probabilitas terjadinya peristiwa sukses, contoh 90% 
p <- 0.9
# Mendefinisikan nilai yang akan diperiksa peluangnya, contoh x dari 0 hingga 8
x <- 0:8
# Menghitung (kepadatan peluang)pdf
dexp(x, lambda)
# Menghitung (fungsi kumulatif peluang)cdf
pexp(x, lambda)
# Menghitung kuantil
qexp(p, lambda)
```
## Distribusi eksponensial
Distribusi eksponensial adalah distribusi probabilitas kontinu yang menggambarkan waktu antara dua kejadian sukses Parameter lambda (λ) dari distribusi eksponensial menunjukkan rata-rata waktu antara dua kejadian.

Contoh distribusi eksponensial:
- **Waktu antar kedatangan pelanggan di bank**. Dalam hal ini, variabel acak X adalah waktu yang dibutuhkan untuk pelanggan berikutnya tiba di bank. Distribusi eksponensial dapat digunakan untuk memprediksi berapa lama waktu yang dibutuhkan untuk pelanggan berikutnya tiba di bank, berdasarkan data waktu kedatangan pelanggan sebelumnya.
- **Waktu antar kegagalan komponen**. Dalam hal ini, variabel acak X adalah waktu yang dibutuhkan untuk komponen gagal. Distribusi eksponensial dapat digunakan untuk memprediksi berapa lama waktu yang dibutuhkan untuk komponen gagal, berdasarkan data waktu kegagalan komponen sebelumnya.
- **Waktu antar panggilan telepon**. Dalam hal ini, variabel acak X adalah waktu yang dibutuhkan untuk panggilan telepon berikutnya masuk ke sistem telepon. Distribusi eksponensial dapat digunakan untuk memprediksi berapa lama waktu yang dibutuhkan untuk panggilan telepon berikutnya masuk ke sistem telepon, berdasarkan data waktu panggilan telepon sebelumnya.
## Metode Invers Transform
```r
eks <- function (n,lambda) {
	U <- runif(n)
	X <- -log(1-U)/lambda)
	return (X) #calculates the exponential random variables `X`
}
```
## Fungsi R
```r
rexp(n, lambda)
```
Fungsi `rexp()` mengembalikan vektor yang berisi sampel dari distribusi eksponensial.