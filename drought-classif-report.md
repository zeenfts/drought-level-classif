# Laporan Proyek Machine Learning - Muhammad Difagama Ivanka

## Domain Proyek
Proyek ***Machine Learning*** ini akan menyelesaikan permasalahan dalam domain **lingkungan** dengan judul "Prediksi Kekeringan parah berdasarkan Data *Meteorological* dan Data Informasi *Soil*".

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;[<sub><sup>image source</sup></sub>](https://unsplash.com/photos/8wuOLdN77A4)

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/137079905-72dcbb55-bd12-47c1-9f1a-ea89dffea504.jpg" alt="Source: https://unsplash.com/photos/8wuOLdN77A4">
</p>

### Latar Belakang
Kekeringan yang terjadi dengan tidak normal atau biasa disebut *drought* merupakan salah satu fenomena alam dengan dampak signifikan terhadap beberapa aspek seperti lingkungan, pertanian, masyarakat, hingga ekonomi. Ciri utama dari fenomena ini adalah kekurangan sumber air yang sangat parah pada suatu area tertentu ditandai dengan sangat kecilnya tingkat presipitasi dalam jangka waktu lumayan panjang. Dengan keadaan seperti itu fenomena ekstrem ini tetap dapat terjadi pada wilayah dengan tingkat presipitasi atau curah hujan sangat tinggi serta tanpa batasan keadaan iklim sama sekali. Sehingga dampak fenomena ini dapat lebih terasa jika dibandingkan dengan fenomena alam lainnya. [<sup>1</sup>](https://www.researchgate.net/publication/319328223_Drought_Management_Current_Challenges_and_Future_Outlook)

Menurut **National Oceanic dan Atmospheric Administration (NOAA)**, [<sup>2</sup>](https://www.ncdc.noaa.gov/news/drought-monitoring-economic-environmental-and-social-impacts) fenomena ini tidak tampak secara nyata dan mengerikan sebagaimana pada fenomena tornado. Namun faktanya kerugian yang dirasakan rata-rata mencapai kurang lebih 9 Miliar USD setiap tahunnya. Dampak tersebut dapat berpengaruh terhadap ekonomi seperti harga kebutuhan pokok maupun secara langsung terhadap produk olahan pertanian semisal keju, padi, dan sebagainya. Dampak lain yang dapat ditimbulkan berupa defisit air minum, penyakit sengatan panas, meningkatkan risiko kebakaran hutan, serta lainnya terutama apabila terjadi terus menerus dalam jangka waktu panjang.

> Statistik menunjukkan hampir setengah wilayah atau mencapai sekitar 47% keseluruhan Amerika Serikat mengalami fenomena ini berdasarkan skala tingkatan sejumlah 5 level mulai dari D0 hingga D4, dengan fenomena *drought* mulai ditunjukkan pada level D1. [<sup>3</sup>](https://www.drought.gov/) 
 
Untuk itu diperlukan suatu metode didalam membantu mengatasi fenomena ini dimana teknologi serta pemahaman peneliti semata masih terbatas untuk dapat memperkirakan akan terjadinya fenomena ini setidaknya beberapa bulan ke depan. [<sup>4</sup>](https://sgp.fas.org/crs/misc/R43407.pdf) Maka proyek ini mencoba menyelesaikan permasalahan yang ada dengan menerapkan kemampuan dari *machine learning* sehingga dapat membantu memprediksi fenomena *drought* tersebut berdasarkan data historis ***meteorological*** berupa informasi cuaca serta iklim dan juga data ***soil*** yang mengandung informasi keadaan tanah pada suatu wilayah dalam proyek ini mengambil contoh Amerika Serikat. Diharapkan *machine learning* dapat memudahkan para ahli maupun masyarakat untuk melakukan tindakan persiapan sebelum fenomena terjadi dengan proses implementasi yang secara *web* hingga *mobile* dapat diterapkan.

---
<sub><sup>1. Eslamian, S. et al. (2017). Drought Management: Current Challenges and Future Outlook. (pp.727-761, Chapter: 34).</sup></sub><br>
<sub><sup>2. NOAA. (2021). DROUGHT: Monitoring Economic, Environmental, and Social Impacts.</sup></sub><br>
<sub><sup>3. National Integrated Drought Information System (NIDIS). (2021). U.S. Drought Monitor. Data tanggal 13 Oktober 2021.</sup></sub><br>
<sub><sup>4. Peter Folger. (2017). Drought in the United States: Causes and Current Understanding. Congressional Research Service.</sup></sub>

## Business Understanding
Bagian ini menjelaskan proses klarifikasi masalah dengan mengajukan beberapa solusi dalam menyelesaikannya.

### Problem Statements
Berangkat dari latar belakang tersebut, maka rincian masalah yang dapat diselesaikan diantaranya:
1. Bagaimana proses ***data preparation*** yang baik, sehingga dataset ***meteorological*** dan dataset ***soil*** dapat digunakan untuk membuat model yang baik?
2. Bagaimana model ***machine learning*** terbaik yang dapat mengklasifikasikan fenomena ***drought***?

### Goals
Berikut merupakan tujuan dibuatnya proyek ini:
1. Melakukan proses ***data preparation*** sehingga data siap untuk digunakan dalam pembuatan model.
2. Membuat model ***machine learning*** terbaik untuk mengklasifikasikan fenomena ***drought*** dengan batas metrik `minimal 70%`.

### Solution statements
Solusi yang dapat diterapkan untuk mencapai tujuan tersebut diantaranya:
- Pada bagian ***data preparation*** yang dibagi ke dalam proses ***data preprocessing*** dan ***data wrangling*** terdiri atas:
  * Memilih data mulai dari tahun 2017 hingga 2020 (hanya data `test_timeseries dan validation_timeseries` dari sumber [original](https://www.kaggle.com/cdminix/us-drought-meteorological-data)).
  * Mengambil data yang menunjukkan tingkat *drought* secara bulat (bukan peralihan).
  * Mengekstrak fitur bulan berdasarkan fitur tanggal.
  * Menambahkan informasi wilayah berdasarkan *climate* dari data pendukung.
  * Menggabungkan dataset *meteorological* dengan dataset *soil*.
  * Merubah kelas kategori *drought* menjadi hanya dua.
  * Membagi dataset ke dalam data ***validation*** (2 bulan terakhir/ 3% dari total data) dan data ***train*** (sisanya atau 97%).
  * Mengubah fitur ke dalam tipe angka.
  * Menghilangkan data ***outliers*** pada data ***train***.
  * Mengatasi data tidak seimbang dengan proses ***oversampling*** serta ***undersampling***.
  * Melakukan ***data standardization*** pada semua fitur.
 
- Pada pembuatan model digunakan algoritma ***Logistic Regression*** sebagai baseline untuk kemudian dibandingkan dengan beberapa algoritma yaitu ***Multi Layer Perceptron***, ***Support Vector Machine***, dan ***LightGBM***

  * ***Logistic Regression***: Merupakan model ***linear*** dalam kasus klasifikasi yang memprediksi response variable menggunakan fungsi persamaan ***logit*** (***sigmoid***) seperti pada gambar berikut. [<sup>5</sup>](https://medium.datadriveninvestor.com/logistic-regression-1532070cf349) Algoritma ini biasanya sering dijadikan sebagai `baseline model` karena kesederhanaannya.
 
    ![sigmoid](https://miro.medium.com/max/800/0*0daHL1k1qzunwQmc.png) 
    Kelebihan   | Kekurangan
    -- | --
    Simpel, Cepat, Mudah | Kurang bagus pada data
    Tidak butuh asumsi distribusi pada fitur | Membangun berdasarkan model linear
    Dapat digunakan juga pada kasus multinomial | Limitasi utama yang mengasumsikan hubungan linear antara predictor dengan response variabel
    Tidak hanya menunjukkan seberapa perlunya koefisien, namun juga arah asosiasinya | Sering disalah artikan untuk kasus regresi
    Menghasilkan model cukup baik terutama jika terdapat hubungan linear cukup jelas | Memiliki asumsi bahwa antara fitur tidak berkorelasi sangat kuat
    
  * ***Multi Layer Perceptron***: Merupakan model ***neural network*** sederhana yang biasanya hanya memiliki sebuah ***hidden layer***. Bekerja dengan meneruskan data dari ***input layer*** hingga ke ***hidden layer*** dan ***output layer*** atau biasa disebut dengan proses [***feedforward***](https://towardsdatascience.com/deep-learning-feedforward-neural-network-26a6705dbdc7). Kemudian diiterasikan kembali ke belakang atau disebut proses [***backward propagation***](https://towardsdatascience.com/how-does-back-propagation-in-artificial-neural-networks-work-c7cad873ea7) untuk memperkecil nilai `error` sehingga menghasilkan model yang baik. [<sup>6</sup>](https://www.educative.io/edpresso/what-is-a-multi-layered-perceptron) Sedangkan berikut [kelebihan dan kekurangannya](https://scikit-learn.org/stable/modules/neural_networks_supervised.html).
  
   Kelebihan | Kekurangan
  -- | --
  Kemampuan dalam mempelajari data non-linear | Sensitive terhadap ***feature scaling***
  Kemampuan mempelajari model secara real time | Membutuhkan tuning hyperparameter yang cukup rumit
  Kemampuan menyelesaikan masalah `kompleks atau data sangat besar` dengan sangat baik (salah satu alasan pemilihan) | Perbedaan inisialisasi weight dapat menyebabkan nilai metrik pada validasi berbeda

  * ***Support Vector Machine***:
  * ***LightGBM***:

---
<sub><sup>5. Shubang Agrawal. (2021). Medium: Logistic Regression.</sup></sub><br>
<sub><sup>6. Edpresso Team. (2021). What is a multi-layered perceptron?</sup></sub>

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

## Data Preparation
Pada bagian ini Anda menjelaskan teknik yang digunakan pada tahapan Data Preparation. 
- Terapkan minimal satu teknik data preparation dan jelaskan proses yang dilakukan.
- Jelaskan alasan mengapa Anda perlu menerapkan teknik tersebut pada tahap Data Preparation. 

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. 

Jelaskan bagaimana Anda melakukan proses modeling dalam proyek. Misalnya, Anda menggunakan satu algoritma kemudian melakukan improvement dari baseline model atau Anda menggunakan dua atau lebih algoritma kemudian membandingkan performanya.

Sajikan model terbaik Anda sebagai solusi.
Jelaskan pula hasil dari model Anda (misal, hasil prediksi).

## Evaluation
Bagian ini menjelaskan mengenai metrik evaluasi yang digunakan untuk mengukur kinerja model. Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan dan bagaimana formulanya
- Kelebihan dan kekurangan metrik
- Bagaimana cara menerapkannya ke dalam kode.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
_Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
