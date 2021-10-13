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
<sub><sup>1. Eslamian, S., et al. "Drought Management: Current Challenges and Future Outlook, Ch. 34 in Handbook of Drought and Water Scarcity, Vol. 3: Management of Drought and Water Scarcity, Ed. by Eslamian S. and Eslamian F., Francis and Taylor." (2017).</sup></sub><br>
<sub><sup>2. NOAA. DROUGHT: Monitoring Economic, Environmental, and Social Impacts. (2021)</sup></sub><br>
<sub><sup>3. National Integrated Drought Information System (NIDIS). U.S. Drought Monitor. Data tanggal 13 Oktober 2021. (2021)</sup></sub><br>
<sub><sup>4. Peter Folger. Drought in the United States: Causes and Current Understanding. Congressional Research Service. (2017)</sup></sub>

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
 
- Pada pembuatan model digunakan algoritma **Logistic Regression** sebagai baseline untuk kemudian dibandingkan dengan beberapa algoritma yaitu **Multi Layer Perceptron**, **Support Vector Machine**, dan **LightGBM**

  * **Logistic Regression**: Merupakan model ***linear*** dalam kasus klasifikasi yang memprediksi response variable menggunakan fungsi persamaan ***sigmoid*** (***logit***) seperti pada gambar berikut. [<sup>5</sup>](https://medium.datadriveninvestor.com/logistic-regression-1532070cf349) Algoritma ini biasanya sering dijadikan sebagai `baseline model` karena kesederhanaannya.
 
    <img width="650" height="450" src="https://miro.medium.com/max/800/0*0daHL1k1qzunwQmc.png">
    
    Kelebihan   | Kekurangan
    -- | --
    Simpel, Cepat, Mudah | Kurang bagus pada data
    Tidak butuh asumsi distribusi pada fitur | Membangun berdasarkan model linear
    Dapat digunakan juga pada kasus multinomial | Limitasi utama yang mengasumsikan hubungan linear antara predictor dengan response variabel
    Tidak hanya menunjukkan seberapa perlunya koefisien, namun juga arah asosiasinya | Sering disalah artikan untuk kasus regresi
    Menghasilkan model cukup baik terutama jika terdapat hubungan linear cukup jelas | Memiliki asumsi bahwa antara fitur tidak berkorelasi sangat kuat
    
  * **Multi Layer Perceptron**: Merupakan model ***neural network*** sederhana yang biasanya hanya memiliki sebuah ***hidden layer*** seperti pada gambar di bawah berikut. Bekerja dengan meneruskan data dari ***input layer*** hingga ke ***hidden layer*** dan ***output layer*** atau biasa disebut dengan proses [***feedforward***](https://towardsdatascience.com/deep-learning-feedforward-neural-network-26a6705dbdc7). Kemudian diiterasikan kembali ke belakang atau disebut proses [***backward propagation***](https://towardsdatascience.com/how-does-back-propagation-in-artificial-neural-networks-work-c7cad873ea7) untuk memperkecil nilai `error` sehingga menghasilkan model yang baik. [<sup>6</sup>](https://www.educative.io/edpresso/what-is-a-multi-layered-perceptron) 
  
    <img width="460" height="400" src="https://scikit-learn.org/stable/_images/multilayerperceptron_network.png">
  
  Sedangkan berikut [kelebihan dan kekurangannya](https://scikit-learn.org/stable/modules/neural_networks_supervised.html).
  
   Kelebihan | Kekurangan
  -- | --
  Kemampuan dalam mempelajari data non-linear | Sensitive terhadap ***feature scaling***
  Kemampuan mempelajari model secara real time | Membutuhkan tuning hyperparameter yang cukup rumit
  Kemampuan menyelesaikan masalah `kompleks atau data sangat besar` dengan sangat baik (salah satu alasan pemilihan) | Perbedaan inisialisasi weight dapat menyebabkan nilai metrik pada validasi berbeda

  * **Support Vector Machine (SVM)**: Algoritma yang bekerja dengan cara menemukan garis pemisah (***hyperplane***) antar data dengan membuat kelas berbeda yang mampu menyelesaikan masalah baik *linear* maupun *non-linear* terutama pada kasus klasifikasi. *Hyperplane* tersebut sangat terpengaruh dengan adanya data point di dekatnya, sehingga dapat menyebabkan suatu margin yang berusaha dimaksimalkan untuk mendapatkan hasil terbaik sebagaimana pada gambar di bawah berikut. [<sup>7</sup>](https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47) 
  
    ![svm](https://miro.medium.com/max/600/0*9jEWNXTAao7phK-5.png) ![svm_optimal](https://miro.medium.com/max/600/0*0o8xIA4k3gXUDCFU.png)
   
    Penerapan pada proyek ini sendiri dengan mengaplikasikan teknik optimasi **Stochastic Gradient Descent (SGD)**. Dengan [penjelasan detail](https://leon.bottou.org/projects/sgd) yaitu:
     1. *Learning Rate* dituliskan dalam bentuk persamaan η0 / (1 + λ η0 t) dengan λ adalah nilai konstan untuk regularisasi,
     2. Nilai konstan η0 ditentukan terlebih dahulu pada *subsample data*,
     3. *Learning Rate* pada bias dikalikan dengan 0.001 karena biasanya dapat meningkatkan kondisinya,
     4. *Weight* direpresentasikan sebagai produk suatu skalar dan vektor dalam rangka memudahkan proses [*weight decay*](https://medium.com/analytics-vidhya/deep-learning-basics-weight-decay-3c68eb4344e9#:~:text=Weight%20decay%20is%20a%20regularization,weights%20and%20not%20the%20bias.).

    Berikut merupakan kelebihan serta kekurangan [SVM](https://scikit-learn.org/stable/modules/svm.html) menggunakan [SGD](https://scikit-learn.org/stable/modules/sgd.html#sgd) ini:
    Kelebihan | Kekurangan
    -- | --
    Efektif pada data berdimensi tinggi bahkan jika jumlah sampel cenderung sedikit | Jika jumlah sampel sedikit rentan overfitting
    Penggunaan memori yang efisien (alasan pemilihan model) | Penghitungan nilai probabilitas yang butuh *high computation*
    Algoritma serbaguna (dalam arti dapat memilih fungsi *decision* berbeda) | SGD membutuhkan parameter regularisasi dan jumlah iterasi
    Efisiensi yang sangat baik terutama pada data `berskala besar` (alasan pemilihan model) | Sensitif terhadap *feature scaling*
    Kemudahan proses implementasi dan interpretasi |
    
  * **LightGBM (LGBM)**: Algoritma berbasis [*gradient boosting*](https://machinelearningmastery.com/gentle-introduction-gradient-boosting-algorithm-machine-learning/) yang berbasis *tree*. Dibandingkan algoritma pada golongan sama yang menumbuhkan *tree* secara horizontal (*level-wise*). LGBM menumbuhkan *tree*nya secara vertikal (*leaf-wise*) yang memimilih *leaf* dengan nilai *loss* tersbesar untuk ditumbuhkan sebagaimana pada gambar di bawah. [<sup>8</sup>](https://www.analyticssteps.com/blogs/what-light-gbm-algorithm-how-use-it)

    <img width="560" height="400" src="https://miro.medium.com/max/724/0*4nrDSJJcTHNjMjmb.png">
    
    Keunikan yang dimiliki oleh LGBM adalah pada metode *boosting*nya yang bernama **GOSS (Gradient Based One Side Sampling)**. GOSS merupakan metode pengambilan sampel baru yaitu downsample menggunakan gradien. Dimana GOSS mengambil seluruh gradien instance yang bernilai besar, sedangkan untuk gradien bernilai kecil LGBM hanya diambil secara acak berupa sampel. Selain, itu terdapat juga **EFB (Exclusive Feature Building)** yang dapat mengurangi kompleksitas data dengan cara menmbundle beberapa fitur menjadi satu. [<sup>9</sup>](https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e) Berikut [kelebihan dan kekurangan](https://www.kaggle.com/questions-and-answers/103834) LGBM:
    
    Kelebihan | Kekurangan
    -- | --
    Cepat dan Efisien (alasan pemilihan model) | Kurangnya support maupun komunitas
    Penggunaan memori yang sedikit (alasan pemilihan model) | Model yang cenderung seperti *blackbox*
    Memiliki hasil lebih baik dibanding algoritma sejenis |
    Sanagt baik pada data berukuran sangat besar (alasan pemilihan model) |
    Kemampuan menggunakan komputasi GPU |
    Kemampuan dalam paralelization | 
    
- Kemudian hasil perbandingan tersebut dipilih model dengan nilai metrik terbaik untuk selanjutnya dapat dikembangkan lebih lanjut dengan menerapkan ***hyperparameter tuning*** secara otomatis menggunakan algoritma [**Bayesian Optimization**](https://github.com/fmfn/BayesianOptimization). Algoritma ini menerapkan prinsip **Bayes Theorem** didalam proses pencarian *hyperparamater* terbaik bagi model secara efisien dan efektif. Bayesian bekerja dengan cara membangun model probabilistik terhadap suatu objektif untuk kemudian dijadikan landasan menentukan di area mana selanjutnya *hyperparameter* untuk dievaluasi dengan tetap mengacu kepada hasil evaluasi dari area sebelumnya sebagaimana ditunjukkan pada gambar di bawah. [<sup>10</sup>](https://proceedings.neurips.cc/paper/2012/file/05311655a15b75fab86956663e1819cd-Paper.pdf)

  <img width="560" height="400" src="https://research.fb.com/wp-content/uploads/2018/09/bo_1d_opt.gif">

  Kelebihan | Kekurangan
  -- | --
  Meringankan beban dari objektif yang dijalankan | Bekerja kurang baik pada data dengan fitur categorical
  Bekerja seperti *high level* api  | Berjalan lambat jika jumlah *hyperparameter* semakin banyak
  Robust terhadap fungsi evaluasi yang kurang baik | Bergantung kepada suatu *optimizer*
  Optimal dalam mendapatkan hasil terbaik dengan waktu yang tidak panjang (alasan pemilihan) | Algoritma tidak mudah untuk dipahami
  
---
<sub><sup>5. Shubang Agrawal. Medium: Logistic Regression. (2021).</sup></sub><br>
<sub><sup>6. Edpresso Team. What is a multi-layered perceptron?</sup></sub><br>
<sub><sup>7. Rohith Gandhi. towardsdatascience: SVM, Introduction to Machin Learning Algorithms. (2018).</sup></sub><br>
<sub><sup>8. Rohit Dwivedi. analyticssteps: What is LightGBM Algorithm, How to use it? (2020)</sup></sub><br>
<sub><sup>9. Abhishek Sharma. towardsdatascience: What makes LightGBM lightning fast? (2018)</sup></sub><br>
<sub><sup>10. Acerbi, Luigi, and Wei Ji Ma. "Practical Bayesian optimization for model fitting with Bayesian adaptive direct search." Proceedings of the 31st International Conference on Neural Information Processing Systems. 2017.</sup></sub>

## Data Understanding
Berikut merupakan informasi datasets yang digunakan:
Detail | Keterangan
-- | --
Source | [Kaggle: Predict Droughts using Weather & Soil Data](https://www.kaggle.com/cdminix/us-drought-meteorological-data)
License | [Public (CC0 1.0)](https://creativecommons.org/publicdomain/zero/1.0/)
Format | zip (&pm;172 MB)
Domain | Weather, Climate, Earth Science, Environment
Timeframe | 2017/01/01 s.d. 2020/12/31
Data Pendukung | [us_county.csv](https://www.kaggle.com/headsortails/covid19-us-county-jhu-data-demographics?select=us_county.csv) <br><br> [us_climate_region.csv](https://www.kaggle.com/zeeniye/us-climate-regions?select=us_climate_regions.csv)

Data *meterorological* terdapat pada file utama. Untuk proyek ini menggunakan file `test_timeseries.csv` dan `validation_timeseries.csv` yang masing-masing berisi sebanyak 2.3 juta baris dan 21 fitur menunjukkan informasi berkaitan dengan cuaca dan iklim yang tercatat setiap hari (lebih detailnya adalah dalam sekian menit) serta telah terdapat level dari *drought* tercatat hanya setiap pekan (sehingga banyak informasi tidak ada). Kemudian data pada file `soil_data.csv` yang menunjukkan informasi berkaitan dengan tanah (tipe, ketinggian, dll) dengan 3109 baris dan 32 fitur. Serta terdapat dua data pendukung berisi informasi wilayah, selengkapnya penjelasan fitur pada datasets:

### Fitur-fitur pada data ***meteorological*** adalah sebagai berikut:
No | Fitur | Rincian
-- | -- | --
1.| `fips` | Menunjukkan kode dari setiap [*county*](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/national/home/?cid=nrcs143_013697) pada Amerika Serikat.
2.| `date` | Tanggal observasi (format yyyy-mm-dd).
3.| `PRECTOT` | Curah hujan (mm) dalam satu hari.
4.| `PS` | Tekanan Permukaan (kPa).
5.| `QV2M` | Kelembaban Spesifik pada ketinggian 2 Meter (g/kg)
6.| `T2M` | Suhu pada ketinggian 2 Meter (C).
7.| `T2MDEW` | Titik Embun/Beku pada ketinggian 2 Meter (C).
8.| `T2MWET` | Suhu Bola Basah pada ketinggian 2 Meter (C).
9.| `T2M_MAX` | Suhu maksimal pada ketinggian 2 Meter (C).
10.| `T2M_MIN` | Suhu minimal pada ketinggian 2 Meter (C).
11.| `T2M_RANGE` | T2M_MAX - T2M_MIN.
12.| `TS` | Suhu permukaan bumi (C).
13.| `WS10M` | Kecepatan angin pada ketinggian 10 Meter (m/s).
14.| `WS10M_MAX` | Kecepatan maksimum angin pada ketinggian 10 Meter (m/s).
15.| `WS10M_MIN` | Kecepatan minimum angin pada ketinggian 10 Meter (m/s).
16.| `WS10M_RANGE` | WS10M_MAX - WS10M_MIN.
17.| `WS50M` | Kecepatan angin pada ketinggian 50 Meter (m/s).
18.| `WS50M_MAX` | Kecepatan maksimum angin pada ketinggian 50 Meter (m/s).
19.| `WS50M_MIN` | Kecepatan minimum angin pada ketinggian 50 Meter (m/s).
20.| `WS50M_RANGE` | WS50M_MAX - WS50M_MIN.
21.| `score` | Ukuran tingkatan ***drought*** mulai dari D0 (tidak ada *drought*), D1-D4 (*drought* berskala). Tercatat hanya dalam kurun waktu setiap sepekan sekali.

### Fitur-fitur pada data pendukung adalah sebagai berikut:
No | Fitur | Rincian
-- | -- | --
1.| `fips` | Menunjukkan kode dari setiap *county* pada Amerika Serikat.
2.| `county` | Nama daerah *county*.
3.| `state` | Nama negara bagian.
4.| `state_code` | Kode dari negara bagian.
5.| `climate_regions` | [Nama wilayah berdasar pembagian iklim](https://www.ncdc.noaa.gov/monitoring-references/maps/us-climate-regions.php).

### Fitur-fitur pada data ***soil*** adalah sebagai berikut:
No | Fitur | Rincian
-- | -- | --
1.| `fips` | Menunjukkan kode dari setiap *county* pada Amerika Serikat.
2.| `lat` | Informasi *latitude* (garis lintang).
3.| `lot` |Informasi *longitude* (garis bujur).
4.| `elevation` | Median dari tingkat elevasi (meter).
5.| `slope1` | 0 % ≤ Tingkat kemiringan ≤ 0.5 %.
6.| `slope2` | 0.5 % ≤ Tingkat kemiringan ≤ 2 %.
7.| `slope3` | 2 % ≤ Tingkat kemiringan ≤ 5 %.
8.| `slope4` | 5 % ≤ Tingkat kemiringan ≤ 10 %.
9.| `slope5` | 10 % ≤ Tingkat kemiringan ≤ 15 %.
10.| `slope6` | 15 % ≤ Tingkat kemiringan ≤ 30 %.
11.| `slope7` | 30 % ≤ Tingkat kemiringan ≤ 45 %.
12.| `slope8` | 45 % ≤ Tingkat kemiringan.
13.| `aspectN` | Utara: 0˚< aspek kemiringan ≤45˚ or 315˚< aspek kemiringan ≤360˚.
14.| `aspectE` | Timur: 45˚< aspek kemiringan ≤135˚.
15.| `aspectS` | Selatan: 135˚< aspek kemiringan ≤225˚.
16.| `aspectW` | Utara: 225˚< aspek kemiringan ≤315˚.
17| `aspectUnknown` | Aspek kemiringan tidak terdifinisi atau jika nilai kemiringan ≤ 2%.
18.| `WAT_LAND` | Area perairan.
19.| `NVG_LAND` | Lahan tandus/sangat jarang vegetasi.
20.| `URB_LAND` | Perumahan dan Infrakstruktur (area pembangunan).
21.| `GRS_LAND` | Rumput / semak / hutan.
22.| `FOR_LAND` | Lahan hutan, dikalibrasi dengan statistik lahan FRA2000.
23.| `CULTRF_LAND` | Lahan pertanian tadah hujan.
24.| `CULTIR_LAND` | Lahan pertanian beririgasi, menurut GMIA 4.0.
25.| `CULT_LAND` | Total lahan yang ditanami.
26.| `SQ1` | Ketersediaan nutrisi.
27.| `SQ2` | Kapasitas retensi nutrisi.
28.| `SQ3` | Kondisi perakaran.
29.| `SQ4` | Ketersediaan oksigen untuk akar.
30.| `SQ5` | Kadar kelebihan garam.
31.| `SQ6` | Toksisitas.
32.| `SQ7` | Workability (tanpa adanya penghambat).

#### Visualisasi data untuk beberapa kolom dengan fitur *continuous*
![image](https://user-images.githubusercontent.com/59215827/137143625-2ce15a80-acee-467b-832b-9325ae881cc6.png)
![image](https://user-images.githubusercontent.com/59215827/137144234-31d02388-e58d-4b35-8e8d-b63a5e7e667e.png)
![image](https://user-images.githubusercontent.com/59215827/137144311-0405abb7-2b46-4dcf-b390-5a84c7e3d1ab.png)
![image](https://user-images.githubusercontent.com/59215827/137144931-d5a1b9f8-ffcf-4dc4-9535-f616f3433ce4.png)
![image](https://user-images.githubusercontent.com/59215827/137143960-66a37bb8-8a7f-46a3-9e9f-266668850513.png)
![image](https://user-images.githubusercontent.com/59215827/137144581-bad63791-4fde-4d5e-a2d2-715240f70c10.png)
![image](https://user-images.githubusercontent.com/59215827/137144659-ef134e16-2121-49aa-80f1-08618359a0aa.png)

#### Visualisasi data pada beberapa kolom dengan fitur *categorical*
![climate_region](https://user-images.githubusercontent.com/59215827/137142558-b4252712-72eb-4b76-862b-63eb2e18f8fa.png)
![month](https://user-images.githubusercontent.com/59215827/137142599-8c6d0ce6-ddc1-4a23-8a47-ec79a586fe79.png)
![sq1](https://user-images.githubusercontent.com/59215827/137142675-f86d67a1-0366-4557-b9e8-fd1837b774f2.png)
![sq4](https://user-images.githubusercontent.com/59215827/137145312-8091ac70-5ebc-4a31-94b0-f66c78501fb7.png)

- Kategori *default*
![score_5](https://user-images.githubusercontent.com/59215827/137143052-76f81c81-7fe3-4ebe-90ae-590e9ec7648f.png)
- Kategori menjadi *binary*
![score_2](https://user-images.githubusercontent.com/59215827/137143096-04042124-13f2-402c-9bff-322d0a3db528.png)

## Data Preparation
Sebagaimana telah disampaikan, bagian ini terbagi menjadi dua yaitu `*data preprocessing*` dan `*data wrangling*`: 
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
