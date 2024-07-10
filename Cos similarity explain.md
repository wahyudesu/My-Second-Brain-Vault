Cosine similarity adalah metrik yang digunakan dalam sistem rekomendasi untuk mengukur sejauh mana dua item mirip satu sama lain. [Ini adalah metode yang populer dalam sistem rekomendasi karena efektif dalam mengidentifikasi kesamaan antara dua item berdasarkan atribut mereka, bahkan jika ukuran (magnitudo) vektor yang mewakili item tersebut berbeda](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems).

Misalkan kita memiliki dua jet ski yang bergerak di danau. Kedua jet ski tersebut bergerak ke arah timur laut, yang berarti ada dua fitur di sini (ruang dua dimensi): Utara dan Timur. [Posisi jet ski dapat diwakili oleh nilai numerik dalam arah utara dan timur dan posisi jet ski dapat diwakili sebagai vektor dari titik asal](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems).

Untuk mendapatkan cosine similarity antara jet ski dalam dimensi timur laut, kita perlu menemukan kosinus sudut antara kedua vektor ini. Cosine similarity didefinisikan sebagai:

![[Pasted image 20240110212357.png]]

Sehingga, untuk kasus (a) dalam gambar, cosine similarity adalah:

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><semantics><mrow><mtext>Cosine&nbsp;similarity</mtext><mo>=</mo><mi>cos</mi><mo>⁡</mo><mo stretchy="false">(</mo><mtext>blue&nbsp;jet&nbsp;ski,&nbsp;orange&nbsp;jet&nbsp;ski</mtext><mo stretchy="false">)</mo><mo>=</mo><mi>cos</mi><mo>⁡</mo><mo stretchy="false">(</mo><mn>30</mn><mi mathvariant="normal">°</mi><mo stretchy="false">)</mo><mo>=</mo><mn>0.866</mn></mrow><annotation encoding="application/x-tex">\text{Cosine similarity} = \cos(\text{blue jet ski, orange jet ski}) = \cos(30°) = 0.866
</annotation></semantics></math>

Sekarang, untuk menentukan apakah Kasus (b) dan Kasus © mirip dengan Kasus (a), kita dapat menerapkan cosine similarity ke dua kasus lainnya:

- Kasus (b):\cos(0°) = 1[Mirip]
- Kasus ©:\cos(90°) = 0[Tidak mirip]

Cosine similarity berkisar dari -1 hingga 1. [Nilai 1 menunjukkan bahwa item tersebut sama, sedangkan -1 menunjukkan bahwa item yang dibandingkan berbeda](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems).

Perlu dicatat bahwa cosine similarity dalam kasus (b) adalah 1 (mirip) meskipun ukuran vektor jet ski biru lebih besar dari yang oranye. Ini menunjukkan bahwa cosine similarity tidak bergantung pada magnitudo atau ukuran vektor. Ini hanya bergantung pada arah vektor. [Ketika sudut antara vektor kecil, kesamaannya lebih tinggi](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems).

[Dalam aplikasi praktis di mana menemukan sudut antara vektor adalah non-trivial, kita dapat menggunakan formulasi cosine di bawah ini yang diperoleh dari produk dalam antara dua vektor dalam aljabar linear](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems):

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><semantics><mrow><mtext>Cosine&nbsp;Similarity</mtext><mo stretchy="false">(</mo><mi>A</mi><mo separator="true">,</mo><mi>B</mi><mo stretchy="false">)</mo><mo>=</mo><mfrac><mrow><mi>A</mi><mo>⋅</mo><mi>B</mi></mrow><mrow><mi mathvariant="normal">∣</mi><mi mathvariant="normal">∣</mi><mi>A</mi><mi mathvariant="normal">∣</mi><mi mathvariant="normal">∣</mi><mi mathvariant="normal">∣</mi><mi mathvariant="normal">∣</mi><mi>B</mi><mi mathvariant="normal">∣</mi><mi mathvariant="normal">∣</mi></mrow></mfrac><mo>=</mo><mfrac><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi>A</mi><mi>i</mi></msub><msub><mi>B</mi><mi>i</mi></msub></mrow><mrow><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>A</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt><msqrt><mrow><munderover><mo>∑</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msubsup><mi>B</mi><mi>i</mi><mn>2</mn></msubsup></mrow></msqrt></mrow></mfrac></mrow><annotation encoding="application/x-tex">\text{Cosine Similarity} (A, B) = \frac{A \cdot B}{||A|| ||B||} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^{n} A_i^2} \sqrt{\sum_{i=1}^{n} B_i^2}}
</annotation></semantics></math>

Di mana:
- A dan B adalah dua vektor yang ingin kita hitung kesamaannya.
- A dan B adalah elemen ke-i dari vektorAdanB.
- n adalah jumlah elemen dalam vektor.

Dalam konteks sistem rekomendasi, cosine similarity digunakan untuk mengukur kesamaan antara preferensi pengguna dan item yang tersedia. [Item dengan nilai cosine similarity yang tinggi terhadap preferensi pengguna akan direkomendasikan](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[1](https://indiaai.gov.in/article/cosine-similarity-the-metric-behind-recommendation-systems)[2](https://analyticsindiamag.com/cosine-similarity-in-machine-learning/).