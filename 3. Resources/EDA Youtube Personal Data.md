![](https://miro.medium.com/v2/resize:fit:683/1*2We5BOe0sQTb1y7mo8ahkQ.png)

Pernahkah kalian berpikir apa saja yang kalian tonton di platform Youtube sampai bisa menghabiskan waktu berjam jam setiap harinya . Itulah yang penulis sering pikirkan ketika melihat waktu tonton rata-rata dalam seminggu di akun penulis yang mencapai 3 jam 23 menit, bahkan ada 1 hari yang bisa mencapai 6jam dalam 1 hari. Rasa penasaran kita bisa sedikit terjawab, karena Google sebagai induk perusahaan dari Youtube menyediakan Google Takeout, yaitu sebuah fitur dari Google untuk mengambil personal data dari akun pribadi kita. Google Takeout menyediakan banyak personal data pada akun kita seperti kalender, chrome, youtube, dan lain-lain. Akhirnya, penulis berinisiatif untuk melakukan Exploratory Data Analitics (EDA) pada personal data youtube dari akun penulis untuk mengetahui apa saja insight yang didapat dari data itu.

![](https://miro.medium.com/v2/resize:fit:875/0*npjsJ3eUN8FqzZ5E)

Untuk mendapatkan data tersebut kita hanya perlu masuk ke [GoogleTakeout](https://takeout.google.com/settings/takeout) kemudian kita perlu memilih data apa saja yang kita gunakan, untuk kali ini penulis hanya menggunakan data youtube saja. Kemudian kita hanya perlu menunggu data yang kita inginkan dikirim ke email kita.

![](https://miro.medium.com/v2/resize:fit:563/1*-KtJbYAUpiP2DPW28HgJxQ.png)

## Isi data personal Youtube

Jika dilihat dari data yang didapatkan terdapat banyak data yang tersedia, berikut ialah list beberapa data yang didapatkan:

**·** Lagu.csv

**·** Liked videos.csv

**·** Uplod from \*(nama akun).csv

**·** Watch later.csv

**·** Histori-penelurusan.json

**· Histori-tontonan.json**

**·** Dll.

Kali ini data yang akan dilakukan EDA adalah data **Histori-tontonan.json**. Untuk isi dari data tersebut adalah berupa data tontonan apa saja yang kita lihat dari akhir 2021 sampai sekarang. Data ini memiliki beberapa feature yaitu _header, title, titleUrl, subtitles, time, products, activityControls, description,_ dan _details._

## Exploring the Data

Pertama-tama hal yang perlu dilakukan adalah memanggil beberapa library yang diperlukan untuk tahap awal ini.

```
import jsonimport pandas as pdimport numpy as np
```

Setelah itu, kita perlu memuat data yang akan digunakan yaitu **Histori-tontonan.json** dengan menggunakan _json.load()_ seperti dibawah ini.

```
yt_data = json.load(open('/content/drive/MyDrive/Project01/Dataset/Yt/Takeout/YouTube dan YouTube Music/histori/histori-tontonan.json'))
```

![](https://miro.medium.com/v2/resize:fit:661/1*KUzfqI9YNeRBBivKsrw8xw.png)

Isi data pada file **Histori-tontonan.json**

Guna mempermudah analisis kita perl menampilkan data dengan lebih proporsional, yaitu dalam bentuk data tabular dengan menggunakan metode pd.json\_normalize() dan hasilnya seperti ini.

```
yt_data_df = pd.json_normalize(yt_data)
```

![](https://miro.medium.com/v2/resize:fit:780/1*C9dyUjlzVT7INKcxya1Vyg.png)

Isi data **Histori-tontonan.json** dalam **DataFrame**

## Data cleaning

Hal selanjutnya yang perlu dilakukan adalah data cleaning. Hal ini perlu dilakukan untuk membuang data yang tidak diperlukan agar mendapat hasil insight yang lebih akurat. Dibuatlah sebuah fungsi bernama _unique\_list()_ untuk menemukan unique value apa saja yang dimiliki oleh setiap _feature ._

```
def unique_list(a_list):    seen = set()    for x in a_list:        key = repr(x)        if key not in seen:            seen.add(key)            print(x)
```

Dari semua feature yang dilakukan penngecekan, ada 1 feature yang memiliki nilai yang menurut penulis harus dibuang, yaitu feature detail dengan value \[{‘name’: ‘From Google Ads’}\] dengan menggunakan teknik _list comprehension_ seperti di bawah ini

```
yt_data_df_clean = yt_data_df.loc[yt_data_df['details'].isin([np.NaN]) ]
```

Dihapusnya data tersebut karena ditontonnya video tersebut bukanlah keinginan dari penulis dan dinilai dapat menggangu akurasi insight yang didapatkan.

## Analisyst Result

Setelah dilakukan beberapa analisis pada data, penulis berkesimpulan terdapat beberapa insight yang dapat diambil dari data tersebut ialah sebagai berikut:

1.  Terdapat pada channel mana saja video yang paling banyak ditonton?(1 video bisa ditonton lebih dari 1 kali)
2.  Topik apa saja yang paling banyak di tonton berdasarkan keyword dari judul video?
3.  Pada jam berapa kita sering menonton video di youtube?

## Anlisyt Time !!!

## Channel Paling Sering Ditonton

Setelah menentukan insgight apa saja yang ingin kita cari dari data tesebut, sekarang waktunya kita mengeksekusinya. Pertama-tama yang perlu dilakukan adalah melihat contoh data pada kolom subtitles dan berikut hasilnya.

```
yt_data_df_clean.subtitles[0]
```

![](https://miro.medium.com/v2/resize:fit:526/1*QEdXGi_8pX-xBqSd5mhrcw.png)

Bentuk data pada kolom subtitles

Pada data diatas dapat dilihat pada data diatas bahwa isi dari kolom subtitles memiliki data bertipe list kemudian berisi dictionary dengan 2 key yaitu ‘name’ dan ‘url’. Dengan demikian, perlu dilakukan pengambilan data key ‘name’ dengan cara dan hasil berikut.

```
channel_name = []n = 0for i in yt_data_df_clean.subtitles:  if not pd.isnull(i):    channel_name.append(i[0]['name'])
```

![](https://miro.medium.com/v2/resize:fit:185/1*4kDLETEt9ZXS81w4A_NLAg.png)

Isi variabel channel\_name

Kemudian penulis juga ingin melihat berapa jumlah channel yang ada dalam list diatas menggunakan fungsi unique\_list() yang sebelumnya pernah dibuat dan didapatkan hasil berikut.

![](https://miro.medium.com/v2/resize:fit:503/1*RyqE-AEjS89ZE2Jsfgi9ww.png)

Unique value variabel channel\_name

Setelah dilakukan pengecekan, ternyata banyak channel yang ada di list berjumlah 9389, kemudian dilakukan data list tersebut dijadikan DataFrame, agar dapat dilakukan pengelompokan berdasarkan unique value menggunakan fungsi _value\_counts()_ yang tersedia pada library _pandas_ seperti berikut dan hasilnya.

```
top_Channel = pd.Index(channel_name).value_counts()topChannel_df = pd.DataFrame(top_Channel)topChannel_df.head(10)
```

![](https://miro.medium.com/v2/resize:fit:239/1*Eho0IppFZWm4p2zNjOxj8A.png)

5 channel paling banyak ditonton

Nahh, akhirnya kita bisa melihat channel apa saja yang videonya sering penulis lihat. Dari gambar diatas bisa dilihat kalau channel Tara Arts Game Indonesia menjadi yang tertinggi diantara channel-channel yang lain dengan jumlah video ditonton sebanyak 381 kali.

## Topik Pada Keyword Judul

Selanjutnya, penulis ingin mengetahui apa jenis video apa saja yang sering dilihat. Namun, penulis mendapatkan sebuah kendala disini, yaitu tidak adanya kolom yang menampilkan jenis video yang ditonton. Bahkan pemberian hastag (#) yang biasanya terdapat pada deskripsi video dan mewakilkan video tidak ada dalam data yang didapatkan.

Akan tetapi penulis tidak kehilangan akal, setelah beberapa saat penulis mepelajari data ini, penulis menemukan ada hal menarik pada kolom title.

![](https://miro.medium.com/v2/resize:fit:779/1*0xE1LY8JJ6rY73qg8Ey0IQ.png)

Contoh topik pada keyword judul

Dari contoh 2 data diatas kita dapat melihat bahwa di dalam judul video pembuat video biasanya mencantumkan jenis video yang dibuat. Dalam hal ini memang tidak semua judul video memiliki, akan tetapi hal ini akan menjadi sebuah insight yang menarik jika berhasil dilakukan. Hal pertama yang perlu dilakukan adalah melihat beberapa sample dari data pada kolom title.

![](https://miro.medium.com/v2/resize:fit:453/1*XMtIGEp9kDDug4TiQJ6wsw.png)

Data kolom title

Setelah melihat data dari kolom title, kita bisa melihat bahwa data memiliki berbagai macam hal yang dapat mengganggu hasil yaitu seperti angka, punctuation, dan lain-lain. Oleh karena itu, perlu dilakukan data cleaning kembali pada data kolom title dengan menghapus hal-hal tersebut.

```
import reimport stringdata_clean = []for d in yt_data_df_clean.title:        document_test = re.sub(r'[^\x00-\x7F]+', '', d)        document_test = re.sub(r'@\w+', '', document_test)        document_test = document_test.lower()        document_test = re.sub(r'[%s]' % re.escape(string.punctuation), '', document_test)        document_test = re.sub(r'[0-9]', '', document_test)        document_test = re.sub(r'\s{2,}', '', document_test)    document_test = re.sub(r'\n', ' ', document_test)    data_clean.append(document_test)
```

![](https://miro.medium.com/v2/resize:fit:605/1*vVACpNFMQjam8MImBAIAwA.png)

Data ‘title’ setelah dibersihkan

Data dari kolom tabel telah dilakukan data cleaning seperti diatas dan telah dimasukan kedalam variabel data\_clean. Setelah itu, karena tujuan dari project kali ini adalah mencari insight dari keyword judul, kita perlu melakukan split data menjadi per kata dengan cara sebagai berikut.

```
word_titles=[]for title in data_clean:  title_split = title.split(' ')   for word_title in title_split:    word_titles.append(word_title)
```

![](https://miro.medium.com/v2/resize:fit:130/1*ocbOBsjtVKlhDUfe1f2S_A.png)

Data setelah dipisah perkata

Setelah dilkukan pemisahan perkata, ternyata masih ada beberapa hal yang menurut penulis dapat mengganggu hasil dari insight yang di dapat yaitu adanya stoprods seperti the, of, dan, atau. Sehingga penulis harus kembali melakukan data cleaning pada data yaitu penghapusan stopwords.

Oleh karena Bahasa yang digunakan rata-rata Bahasa inggris dan Bahasa Indonesia, akan dilakukan penghapusan stopword pada kedua Bahasa tersebut. Penulis memanfaat kan 2 library yang tersedia yaitu Natural Language ToolKit (nltk) untuk penghapusan stopwords Bahasa inggris dan sastrawi untuk penghapusan stopword berbahasa Indonesia.

```
import nltkfrom nltk.corpus import stopwords nltk.download('stopwords')print(stopwords.words('english'))from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactoryindo_stopword = StopWordRemoverFactory().get_stop_words()
```

![](https://miro.medium.com/v2/resize:fit:730/1*gopk6kGMerf-r_TqO46W4w.png)

Contoh data stopword Indonesia dan English

Setelah mendapatkan data yang diperlukan dari kedua library tersebut, selanjutnya kita melakukan proses penghapusan data stopword pada variable word\_titles seperti berikut.

```
word_titles_clean=[]for v in word_titles:  if v not in eng_stopword and v not in indo_stopword:    word_titles_clean.append(v)
```

Setelah data sudah cukup bersih, kita kembali memanfaatkan fungsi _value\_counts()_ pada library pandas untuk melihat jumlah unique data.

```
top_wordTitle = pd.Index(word_titles_clean).value_counts()top_wordTitle_df = pd.DataFrame(top_wordTitle)top_wordTitle_df.head(10)
```

![](https://miro.medium.com/v2/resize:fit:125/1*L7db86y6Sa-wIcDDL-WPNQ.png)

10 keyword yang sering muncul pada judul video

Setelah semua langkah dilakukan, kita dapat melihat beberapa keyword pada kolom title paling banyak muncul, walaupun kita sudah melakukan beberapa tahap pembersihan data kita tetap tidak bisa membuat data benar-benar bersih seperti yang kita inginkan (setidaknya untuk penulis J). Mengesampingkan kekurangan tersebut, dari 10 keyword teratas kita mendapatkan beberapa kata yang bisa dimasukan kedalam jenis video. Dari kata-kata tersebut yang tertinggi adalah ‘shorts’, usaha youtube untuk menyaingi tiktok dan Instagram reels cukup mebuahkan hasil karena ketika sekali kita membuka yt short akan sangat sulit untuk berhenti scroll layar hahaha. Selain itu, terdapat beberapa kata yang masuk kedalam jenis video yaitu music, nba dan viral. Insight yang didapatkan kali ini cukup baik melihat dari data yang didapatkan diawal, ini sudah cukup mewakili jenis video yang dilihat setidaknya menurut penulis.

## Jam Paling Sering Menonton Video Youtube

Setelah mengetahui channel dan jenis video yang sering dilihat di kanal youtube, sekarang penulis ingin tahu pada jam berapa saja yang penulis sering habiskan untuk menonton video di youtube. Untuk mengetahui hal itu penulis menggunakan kolom time yang berisikan data waktu dimana kita menonton video yang dimaksud.

Pertama-tama seperti biasa perlu dilakukan pengecekan apakah ada data yang kosong pada channel tersebut.

```
yt_data_df_clean.loc[yt_data_df['time'].isin([np.NaN]) ]
```

![](https://miro.medium.com/v2/resize:fit:684/1*c2iunEUcbplrzsVLkTlphg.png)

Tidak ada data kosong

Setelah di lakukan cek, ternyata tidak ada data yang kosong jadi kita bisa lanjut ke tahap selanjutnya. Sekarang perlu kita lihat bagaimana penampakan dari data kolom time.

![](https://miro.medium.com/v2/resize:fit:234/1*epw2ZaDKP9agb_uEyvTr-w.png)

Data pada kolom time

Hal pertama yang terlihat jelas pada data tersebut adalah penyajian data waktu yang lengkap dan detail dari tahun hingga ke detik. Untuk melihat pada jam berapa saja kita menghabiskan waktu untuk menonton video, kita perlu membuat penggolongan dan untuk kali ini penulis menentukan waktu menonton per 1 jam. Setelah menentukan grub tersebut, data yang tersaji perlu dilakukan sedikit penyesuaian, yaitu data akan dilakukan pembulatan ke jam terdekat dengan fungsi _hour\_rounder()_.

```
def hour_rounder(t):        return (t.replace(second=0, microsecond=0, minute=0, hour=t.hour)               +timedelta(hours=t.minute//30))
```

Akan tetapi masalah kembali muncul, yaitu data yang tersaji pada kolom tersebut masih bertipe data String.

![](https://miro.medium.com/v2/resize:fit:384/1*xvC6RXgbJmqTdC69BOMxgw.png)

Akhirnya penulis membuat sebuah fungsi untuk menyesuaikan data seperti yang diperlukan yaitu mengubah data menjadi bertype _datetime_, kemudian membulatkan data ke jam terdekat, penambahan 7 jam untuk penyesuaian GMT+7 dan sekaligus menghapus tanggal sehingga hanya tesisa jam saja.

```
def time_hour_adjustment(times_data):  times = []  for i in times_data:    t = re.sub('[T,Z]',' ', i)    t = re.sub('[].].*',' ',t)    dt = datetime.strptime(t, '%Y-%m-%d %H:%M:%S ')    dt = hour_rounder(dt)    dt = dt + timedelta(hours=7)    time_str = str(dt)    hour = re.sub(r".*[' ']",'', time_str)    times.append(hour)  return times
```

![](https://miro.medium.com/v2/resize:fit:101/1*5MjhRWdPBKBcLJu3Wrul_w.png)

Data setelah diakukan penyesuaian

Setelah data sudah sesuai keperluan, kita kembali memanfaatkan fungsi value\_counts() pada library pandas untuk melihat jumlah unique data.

![](https://miro.medium.com/v2/resize:fit:276/1*GGIpWXP4ILxNzVNh9ZHE2A.png)

Jam paling sering menonton(kiri) dan paling sedikit(kanan)

Setelah semua hal diatas dilakukan, didapatkan data tersebut. Ternyata jam paling sering penulis gunakan untuk menonton video youtub adalah pada jam-jam istirahat yang seharusnya digunakan untuk tidur yaitu pada jam 9 sampai 11 malam dan beberapa di jam istirahat siang yaitu jam 11 dan 2 siang. Sedangkan untuk jam paling sedikit menonton sudah bisa ditebak yaitu dari jam 1 sampai 5 pagi. Setelah melihat insgiht pada bagian ini, tidak heran penulis merasa kurang tidur ternyata bukan karena banyak perkerjaan tapi digunakan untuk melihat video yotube. Hasil pada jam 1–5 pagi yang menunjukan hasil sedikit juga tidak membuat penulis lega, karena apa yang sebenarnya penulis lakukan sampai di jam-jam seperti itu masih menonton video hahaha.

## Kesimpulan

Akhirnya kita sampai pada akhir tulisan ini, walaupun hanya menganalisa satu data saja dari data pribadi youtube, sudah didapatkan insight yang cukup banyak. Dari data ini mungkin kekurangan menurut penulis ialah kurangnya detail jenis video dan isi deskripsi hanya membedakan video iklan dan tidak saja.

Untuk code lengkapnya bisa cek di [Github](https://github.com/mrafin/EDA_Youtube_Personal_Data)