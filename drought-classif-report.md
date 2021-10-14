# Laporan Proyek Machine Learning - Muhammad Difagama Ivanka

## Domain Proyek
Proyek ***Machine Learning*** ini akan menyelesaikan permasalahan dalam domain **lingkungan** dengan judul "Prediksi Kekeringan parah berdasarkan Data *Meteorological* dan Data Informasi *Soil*".

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/137079905-72dcbb55-bd12-47c1-9f1a-ea89dffea504.jpg"><br>
  <sup><sub><a href="https://unsplash.com/photos/8wuOLdN77A4">image source</a></sub></sup>
</p>

### Latar Belakang
Kekeringan yang terjadi dengan tidak normal atau biasa disebut *drought* merupakan salah satu fenomena alam dengan dampak signifikan terhadap beberapa aspek seperti lingkungan, pertanian, masyarakat, hingga ekonomi. Ciri utama dari fenomena ini adalah kekurangan sumber air yang sangat parah pada suatu area tertentu ditandai dengan sangat kecilnya tingkat presipitasi dalam jangka waktu lumayan panjang. Dengan keadaan seperti itu fenomena ekstrem ini tetap dapat terjadi pada wilayah dengan tingkat presipitasi atau curah hujan sangat tinggi serta tanpa batasan keadaan iklim sama sekali. Sehingga dampak fenomena ini dapat lebih terasa jika dibandingkan dengan fenomena alam lainnya. [<sup>1</sup>](https://www.researchgate.net/publication/319328223_Drought_Management_Current_Challenges_and_Future_Outlook)

Menurut **National Oceanic dan Atmospheric Administration (NOAA)**, [<sup>2</sup>](https://www.ncdc.noaa.gov/news/drought-monitoring-economic-environmental-and-social-impacts) fenomena ini tidak tampak secara nyata dan mengerikan sebagaimana pada fenomena tornado. Namun faktanya kerugian yang dirasakan rata-rata mencapai kurang lebih 9 Miliar USD setiap tahunnya. Dampak tersebut dapat berpengaruh terhadap ekonomi seperti harga kebutuhan pokok maupun secara langsung terhadap produk olahan pertanian semisal keju, padi, dan sebagainya. Dampak lain yang dapat ditimbulkan berupa defisit air minum, penyakit sengatan panas, meningkatkan risiko kebakaran hutan, serta lainnya terutama apabila terjadi terus menerus dalam jangka waktu panjang.

> Statistik menunjukkan hampir setengah wilayah atau mencapai sekitar 47% keseluruhan Amerika Serikat mengalami fenomena ini berdasarkan skala tingkatan sejumlah 5 level mulai dari D0 hingga D4, dengan fenomena *drought* mulai ditunjukkan pada level D1. [<sup>3</sup>](https://www.drought.gov/) 
 
Untuk itu diperlukan suatu metode didalam membantu mengatasi fenomena ini dimana teknologi serta pemahaman peneliti semata masih terbatas untuk dapat memperkirakan akan terjadinya fenomena ini setidaknya beberapa bulan ke depan. [<sup>4</sup>](https://sgp.fas.org/crs/misc/R43407.pdf) Maka proyek ini mencoba menyelesaikan permasalahan yang ada dengan menerapkan kemampuan dari *machine learning* sehingga dapat membantu memprediksi fenomena *drought* tersebut berdasarkan data historis ***meteorological*** berupa informasi cuaca serta iklim dan juga data ***soil*** yang mengandung informasi keadaan tanah pada suatu wilayah dalam proyek ini mengambil contoh Amerika Serikat. Diharapkan *machine learning* dapat memudahkan para ahli maupun masyarakat untuk melakukan tindakan persiapan sebelum fenomena terjadi dengan proses implementasi yang secara *web* hingga *mobile* dapat diterapkan.

---
<sub><sup>1. Eslamian, S., et al. (2017). "Drought Management: Current Challenges and Future Outlook, Ch. 34 in Handbook of Drought and Water Scarcity, Vol. 3: Management of Drought and Water Scarcity, Ed. by Eslamian S. and Eslamian F., Francis and Taylor."</sup></sub><br>
<sub><sup>2. NOAA. (2021). DROUGHT: Monitoring Economic, Environmental, and Social Impacts.</sup></sub><br>
<sub><sup>3. National Integrated Drought Information System (NIDIS). U.S. Drought Monitor. Data tanggal 13 Oktober 2021.</sup></sub><br>
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
 
- Pada pembuatan model digunakan algoritma **Logistic Regression** sebagai baseline untuk kemudian dibandingkan dengan beberapa algoritma yaitu **Multi Layer Perceptron**, **Support Vector Machine**, dan **LightGBM**

  * **Logistic Regression**: Merupakan model ***linear*** dalam kasus klasifikasi yang memprediksi response variable menggunakan fungsi persamaan ***sigmoid*** (***logit***) seperti pada gambar berikut. [<sup>5</sup>](https://medium.datadriveninvestor.com/logistic-regression-1532070cf349) Algoritma ini biasanya sering dijadikan sebagai `baseline model` karena kesederhanaannya.
 
    <img width="650" height="450" src="https://miro.medium.com/max/800/0*0daHL1k1qzunwQmc.png"><br>
    <sup><sub><a href="https://medium.datadriveninvestor.com/logistic-regression-1532070cf349">image source</a></sub></sup>
    
    Kelebihan   | Kekurangan
    -- | --
    Simpel, Cepat, Mudah | Kurang bagus pada data
    Tidak butuh asumsi distribusi pada fitur | Membangun berdasarkan model linear
    Dapat digunakan juga pada kasus multinomial | Limitasi utama yang mengasumsikan hubungan linear antara predictor dengan response variabel
    Tidak hanya menunjukkan seberapa perlunya koefisien, namun juga arah asosiasinya | Sering disalah artikan untuk kasus regresi
    Menghasilkan model cukup baik terutama jika terdapat hubungan linear cukup jelas | Memiliki asumsi bahwa antara fitur tidak berkorelasi sangat kuat
    
  * **Multi Layer Perceptron (MLP)**: Merupakan model ***neural network*** sederhana yang biasanya hanya memiliki sebuah ***hidden layer*** seperti pada gambar di bawah berikut. Bekerja dengan meneruskan data dari ***input layer*** hingga ke ***hidden layer*** dan ***output layer*** atau biasa disebut dengan proses [***feedforward***](https://towardsdatascience.com/deep-learning-feedforward-neural-network-26a6705dbdc7). Kemudian diiterasikan kembali ke belakang atau disebut proses [***backward propagation***](https://towardsdatascience.com/how-does-back-propagation-in-artificial-neural-networks-work-c7cad873ea7) untuk memperkecil nilai `error` sehingga menghasilkan model yang baik. [<sup>6</sup>](https://www.educative.io/edpresso/what-is-a-multi-layered-perceptron) 
  
    <img width="460" height="400" src="https://scikit-learn.org/stable/_images/multilayerperceptron_network.png"><br>
    <sup><sub><a href="https://scikit-learn.org/stable/modules/neural_networks_supervised.html">image source</a></sub></sup>
  
  Sedangkan berikut [kelebihan dan kekurangannya](https://scikit-learn.org/stable/modules/neural_networks_supervised.html).
  
   Kelebihan | Kekurangan
  -- | --
  Kemampuan dalam mempelajari data non-linear | Sensitive terhadap ***feature scaling***
  Kemampuan mempelajari model secara real time | Membutuhkan tuning hyperparameter yang cukup rumit
  Kemampuan menyelesaikan masalah `kompleks atau data sangat besar` dengan sangat baik (salah satu alasan pemilihan) | Perbedaan inisialisasi weight dapat menyebabkan nilai metrik pada validasi berbeda

  * **Support Vector Machine (SVM)**: Algoritma yang bekerja dengan cara menemukan garis pemisah (***hyperplane***) antar data dengan membuat kelas berbeda yang mampu menyelesaikan masalah baik *linear* maupun *non-linear* terutama pada kasus klasifikasi. *Hyperplane* tersebut sangat terpengaruh dengan adanya data point di dekatnya, sehingga dapat menyebabkan suatu margin yang berusaha dimaksimalkan untuk mendapatkan hasil terbaik sebagaimana pada gambar di bawah berikut. [<sup>7</sup>](https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47) 
  
    ![svm](https://miro.medium.com/max/600/0*9jEWNXTAao7phK-5.png) ![svm_optimal](https://miro.medium.com/max/600/0*0o8xIA4k3gXUDCFU.png)<br>
    <sup><sub><a href="https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47">image source</a></sub></sup>
   
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

    <img width="560" height="400" src="https://miro.medium.com/max/724/0*4nrDSJJcTHNjMjmb.png"><br>
    <sup><sub><a href="https://www.analyticsvidhya.com/blog/2017/06/which-algorithm-takes-the-crown-light-gbm-vs-xgboost/">image source</a></sub></sup>
    
    Keunikan yang dimiliki oleh LGBM adalah pada metode *boosting*nya yang bernama **GOSS (Gradient Based One Side Sampling)**. GOSS merupakan metode pengambilan sampel baru yaitu downsample menggunakan gradien. Dimana GOSS mengambil seluruh gradien instance yang bernilai besar, sedangkan untuk gradien bernilai kecil LGBM hanya diambil secara acak berupa sampel. Selain, itu terdapat juga **EFB (Exclusive Feature Building)** yang dapat mengurangi kompleksitas data dengan cara menmbundle beberapa fitur menjadi satu. [<sup>9</sup>](https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e) Berikut [kelebihan dan kekurangan](https://www.kaggle.com/questions-and-answers/103834) LGBM:
    
    Kelebihan | Kekurangan
    -- | --
    Cepat dan Efisien (alasan pemilihan model) | Kurangnya support maupun komunitas
    Penggunaan memori yang sedikit (alasan pemilihan model) | Model yang cenderung seperti *blackbox*
    Memiliki hasil lebih baik dibanding algoritma sejenis |
    Sangat baik pada data berukuran sangat besar (alasan pemilihan model) |
    Kemampuan menggunakan komputasi GPU |
    Kemampuan dalam paralelization | 
    
- Kemudian hasil perbandingan tersebut dipilih model dengan nilai metrik terbaik untuk selanjutnya dapat dikembangkan lebih lanjut dengan menerapkan ***hyperparameter tuning*** secara otomatis menggunakan algoritma [**Bayesian Optimization**](https://github.com/fmfn/BayesianOptimization). Algoritma ini menerapkan prinsip **Bayes Theorem** didalam proses pencarian *hyperparamater* terbaik bagi model secara efisien dan efektif. Bayesian bekerja dengan cara membangun model probabilistik terhadap suatu objektif untuk kemudian dijadikan landasan menentukan di area mana selanjutnya *hyperparameter* untuk dievaluasi dengan tetap mengacu kepada hasil evaluasi dari area sebelumnya sebagaimana ditunjukkan pada gambar di bawah. [<sup>10</sup>](https://proceedings.neurips.cc/paper/2012/file/05311655a15b75fab86956663e1819cd-Paper.pdf)

  <img width="560" height="400" src="https://research.fb.com/wp-content/uploads/2018/09/bo_1d_opt.gif"><br>
  <sup><sub><a href="https://research.fb.com/blog/2018/09/efficient-tuning-of-online-systems-using-bayesian-optimization/">image source</a></sub></sup>

  Kelebihan | Kekurangan
  -- | --
  Meringankan beban dari objektif yang dijalankan | Bekerja kurang baik pada data dengan fitur categorical
  Bekerja seperti *high level* api  | Berjalan lambat jika jumlah *hyperparameter* semakin banyak
  Robust terhadap fungsi evaluasi yang kurang baik | Bergantung kepada suatu *optimizer*
  Optimal dalam mendapatkan hasil terbaik dengan waktu yang tidak panjang (alasan pemilihan) | Algoritma tidak mudah untuk dipahami
  
---
<sub><sup>5. Shubang Agrawal. (2021). Medium: Logistic Regression.</sup></sub><br>
<sub><sup>6. Edpresso Team. What is a multi-layered perceptron?</sup></sub><br>
<sub><sup>7. Rohith Gandhi. (2018). towardsdatascience: SVM, Introduction to Machin Learning Algorithms.</sup></sub><br>
<sub><sup>8. Rohit Dwivedi. (2020). analyticssteps: What is LightGBM Algorithm, How to use it?</sup></sub><br>
<sub><sup>9. Abhishek Sharma. (2018). towardsdatascience: What makes LightGBM lightning fast?</sup></sub><br>
<sub><sup>10. Acerbi, Luigi, and Wei Ji Ma. (2017). "Practical Bayesian optimization for model fitting with Bayesian adaptive direct search." Proceedings of the 31st International Conference on Neural Information Processing Systems.</sup></sub>

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
26.| `SQ1` | Ketersediaan nutrisi (Tekstur tanah, karbon organik tanah, pH tanah, total basa yang dapat ditukar)
27.| `SQ2` | Kapasitas retensi nutrisi (Karbon organik tanah, tekstur tanah, kejenuhan basa, kapasitas tukar kation tanah dan fraksi liat)
28.| `SQ3` | Kondisi perakaran (Tekstur tanah, bulk density, fragmen kasar, sifat tanah vertikal dan fase tanah yang mempengaruhi penetrasi akar dan kedalaman tanah dan volume tanah)
29.| `SQ4` | Ketersediaan oksigen untuk akar (Drainase tanah dan fase tanah yang mempengaruhi drainase tanah)
30.| `SQ5` | Kadar kelebihan garam (Salinitas tanah, sodisitas tanah dan fase tanah yang mempengaruhi kondisi garam)
31.| `SQ6` | Toksisitas (Kadar calcium carbonate dan gypsum)
32.| `SQ7` | Workability (tanpa adanya penghambat) (Tekstur tanah, kedalaman/volume efektif tanah, dan fase tanah yang membatasi pengelolaan tanah (kedalaman tanah, singkapan batuan, kekasaran, kerikil/konkresi, dan hardpans)).

* Informasi tambahan fitur `SQ`:<br>
  1: Tidak ada atau sedikit batasan.<br>
  2: Batasan sedang.<br>
  3: Batasan parah<br>
  4: Batasan yang sangat parah<br>
  5: Terutama non-tanah<br>
  6: daerah permafrost<br>
  7: Badan air.
  
#### Visualisasi lokasi dari dataset
![image](https://user-images.githubusercontent.com/59215827/137269797-5b14adb4-1799-4c92-9015-6392f7793da0.png)


#### Visualisasi data pada beberapa fitur *categorical*
![climate_region](https://user-images.githubusercontent.com/59215827/137142558-b4252712-72eb-4b76-862b-63eb2e18f8fa.png)
![month](https://user-images.githubusercontent.com/59215827/137142599-8c6d0ce6-ddc1-4a23-8a47-ec79a586fe79.png)
![sq1](https://user-images.githubusercontent.com/59215827/137142675-f86d67a1-0366-4557-b9e8-fd1837b774f2.png)
![sq4](https://user-images.githubusercontent.com/59215827/137145312-8091ac70-5ebc-4a31-94b0-f66c78501fb7.png)

- Kategori *default*

![score_5](https://user-images.githubusercontent.com/59215827/137143052-76f81c81-7fe3-4ebe-90ae-590e9ec7648f.png)

- Kategori menjadi *binary*
 
![score_2](https://user-images.githubusercontent.com/59215827/137143096-04042124-13f2-402c-9bff-322d0a3db528.png)

#### Visualisasi data untuk beberapa fitur *continuous*
![image](https://user-images.githubusercontent.com/59215827/137143625-2ce15a80-acee-467b-832b-9325ae881cc6.png)
![image](https://user-images.githubusercontent.com/59215827/137144234-31d02388-e58d-4b35-8e8d-b63a5e7e667e.png)
![image](https://user-images.githubusercontent.com/59215827/137144311-0405abb7-2b46-4dcf-b390-5a84c7e3d1ab.png)
![image](https://user-images.githubusercontent.com/59215827/137144931-d5a1b9f8-ffcf-4dc4-9535-f616f3433ce4.png)
![image](https://user-images.githubusercontent.com/59215827/137143960-66a37bb8-8a7f-46a3-9e9f-266668850513.png)
![image](https://user-images.githubusercontent.com/59215827/137144581-bad63791-4fde-4d5e-a2d2-715240f70c10.png)
![image](https://user-images.githubusercontent.com/59215827/137144659-ef134e16-2121-49aa-80f1-08618359a0aa.png)

## Data Preparation
Sebagaimana telah disampaikan, bagian ini terbagi menjadi dua yaitu *`data preprocessing`* dan *`data wrangling`*: 
### ***Data Preprocessing***
Proses *preparation* yang dilakukan langsung setelah data mentah diambil sebelum dilakukan proses *exploratory*.

* Memilih data mulai dari tahun 2017 hingga 2020 (hanya data `test_timeseries dan validation_timeseries` dari sumber [original](https://www.kaggle.com/cdminix/us-drought-meteorological-data))

  Hal ini dilakukan mengingat data observasi keseluruhan dimulai sejak tahun 2000 dengan total ukuran datasets sebesar ±2.7 GB, total baris sebanyak ±23.8 juta, dan sebanyak 21 fitur, jika langsung diterapkan menggunakan keselurahan datasets, maka membutuhkan komputasi baik memori serta waktu yang luar biasa besar. Sehingga dilakukan iterasi mengambil sampel beberapa datasets hingga diambil keputusan berdasarkan kemampuan menghasilkan model yang baik dengan tetap mempertahankan jumlah data serta tidak membutuhkan komputasi yang sangat besar, bahwa hanya data observasi pada rentang waktu tersebut saja untuk digunakan.
    
* Mengambil data yang menunjukkan tingkat *drought* secara bulat (bukan peralihan)
    
  Kelas pada data yang menunjukkan fenomena *drought* memiliki 5 kelas, akan tetapi tidak semuanya ditunjukkan secara [diskret (bulat)](https://www.open.edu/openlearn/ocw/mod/oucontent/view.php?id=85587&section=1#:~:text=Discrete%20data%20is%20information%20that%20can%20only%20take%20certain%20values.&text=This%20type%20of%20data%20is,all%20examples%20of%20continuous%20data.), beberapa diantaranya tidak sedikit berada pada bilangan desimal (dapat menunjukkan kelas tersebut sedang masa peralihan atau terjadi kesalahan saat pengumpulan dataset). Sehingga perlu dilakukan proses filtering dengan hanya mengambil kelas yang menunjukkan level *drought* tersebut. Selain itu dikarenakan hasil observasi *drought* hanya terjadi setiap pekannya, maka terdapat banyak data harian *meteorological* memiliki NAN Values. Pada kasus *supervised learning* seperti ini tidak terdapatnya kelas akan menjadi masalah, oleh karena itu dilakukan pendekatan filter tersebut (sudah sekaligus menghilangkan NAN values) sehingga menyisakan dataset yang memiliki nilai pada kelasnya dan jumlah baris pada dataset menjadi ±460 ribu baris.
    
* Mengekstrak fitur bulan berdasarkan fitur tanggal
  
  Cuaca dan iklim salah satu yang berhubungan dengannya adalah informasi berkaitan dengan musim. Maka diputuskan musim diambil dari fitur tanggal dengan mengekstrak fitur bulan. Fitur tersebut diekstrak dengan memperluas pembagian musim menjadi adanya *early*, *mid*, dan *late* dari 4 musim yang ada agar lebih mendetailkan ciri khas dari setiap musim tersebut. [<sup>11</sup>](https://www.ukgardening.co.uk/planting-seasons.php)
    
* Menambahkan informasi wilayah berdasarkan *climate* dari data pendukung

  Menurut penelitian yang dilakukan salah satunya menunjukkan, [<sup>12</sup>](https://repository.library.noaa.gov/view/noaa/10238) informasi berdasarkan iklim ini dijelaskan yaitu daerah atau suau wilayah tertentu dapat memiliki suatu ciri khas (pola) yang menunjukkan kecenderungan keadaaan iklim pada wilayah tersebut. Sehingga diputuskan untuk menambahkan fitur ini yang dapat memperbanyak informasi terhadap dataset untuk dilakukan pemodelan. 
   
* Menggabungkan dataset *meteorological* dengan dataset *soil*
    
  Kemudian langkah *preprocessing* terakhir adalah dengan menggabungkan seluruh datasets menjadi satu buah dataset agar memudahkan dalam pembuatan model. Proses penggabungan ini diterapkan dengan melakukan [*left join*](https://learnsql.com/blog/what-is-left-join-sql/#:~:text=LEFT%20JOIN%20%2C%20also%20called%20LEFT,columns%20of%20the%20right%20table.) data *soil* ke data *meteorological* berdasarkan informasi *key* sama pada fitur *fips* yang menunjukkan kode *county* pada Amerika Serikat. Setelah dilakukannya proses tersebut maka perlu dihapus informasi dari *state* Alaska, Hawaii, dan Puerto Rico karena tidak terdapat pada dataset awal.
  
### ***Data Wrangling***
Proses *preparation* yang dilakukan setelah dataset dilakukan proses *exploratory* untuk menyesuaikan agar mendapatkan model *machine learning* yang baik.

* Merubah kelas kategori *drought* menjadi hanya dua

  Kategori pada data yang menunjukkan fenomena *drought* memiliki 5 level tingkatan dengan dimulai dari D0 hingga D4, akan tetapi mengacu kepada tujuan untuk memprediksi fenomena *drought* bukan mengklasifikasikannya dari tingkat keparahan. Maka tingkatan level yang menunjukkan *drought* dimulai dari D1 hingga D4 digabungkan menjadi satu kelas. Sehingga kelas D0 akan menjadi kelas *NO Drought* (dilambangkan angka '0') dan D1 hingga D4 menjadi kelas *Drought* (dilambangkan angka '1').
  
* Membagi dataset ke dalam data ***validation*** (2 bulan terakhir/ 3% dari total data) dan data ***train*** (sisanya atau 97%)

  Melakukan suatu proses evaluasi sebelum menerapkannya pada data sebenarya diperlukan pembagian dataset setidaknya ke dalam dua bagian yaitu data *train* dan data *validation*. Hal ini perlu dilakukan agar dapat menguji performa model berdasarkan metrik yang telah ditetapkan. Pembagian sendiri dilakukan dengan perbandingan 97:3 yang dilakukan secara manual dengan mengambil data 2 bulan terakhir sebagai data *validation*. Proses latih model sendiri akan dilakukan pada data *train* untuk kemudian akan diuji secara terpisah pada data *validation* dengan harapan hasil pengujian mendapatkan performa sebaik pada data *train*. Proses ini dilakukan cukup awal demi menghindari terjadinya [*data leakage*](https://www.kaggle.com/alexisbcook/data-leakage) pada kedua data tersebut. 
  
* Mengubah fitur ke dalam tipe angka

    Model *machine learning* memerlukan fitur pada dataset dalam format angka untuk dilatih. Sehingga diperlukan proses pengubahan terutama dalam fitur region iklim perlu dilakukan. Proses pengimplementasian dilakukan dengan bantuan [LabelEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html) yang bekerja dengan mengganti label asli fitur ke dalam angka diskret dimulai dari '0' hingga 'total kategori-1' dan dilakukan pada fitur *categorical*.
    
* Menghilangkan data ***outliers*** pada data ***train***

  *Outliers* merupakan suatu nilai tidak wajar pada dataset yang dapat mengakibatkan analisis statistik menjadi kacau serta merubah asumsi yang telah ada sebelumnya. [<sup>13</sup>](https://statisticsbyjim.com/basics/remove-outliers/) Pada model sendiri adanya nilai tidak wajar ini dapat mengakibatkan interpretasi yang dihasilkan kurang begitu bagus dan berdampak terhadap performa model itu sendiri. Salah satu tindakan dalam menangani nilai tidak wajar adalah dengan membuangnya dan hal ini yang akan diterapkan dengan pendekatan [nearest neighbors](https://scikit-learn.org/0.24/modules/generated/sklearn.neighbors.LocalOutlierFactor.html#sklearn.neighbors.LocalOutlierFactor.kneighbors). Cara kerjanya dengan melakukan voting terhadap beberapa *neighbors* terdekat yang dihitung berdasarkan jarak [manhattan](https://machinelearningmastery.com/distance-measures-for-machine-learning/). Kemudian hasil voting tersebut dapat menunjukkan apakah nilai yang terdapat pada dataset termasuk ke dalam *outliers* atau bukan. Proses ini dipilih karena menerapkan asumsi dari populasi memiliki batas wajar dalam hal observasi data *meteorological*.

* Mengatasi data tidak seimbang dengan proses ***oversampling*** serta ***undersampling***

  Jumlah data yang tidak seimbang dapat menyebabkan model memiliki performa yang tidak sesuai harapan. Pada kasus nyata hal ini sangat dihindari karena model diharapkan memiliki kemampuan lebih utama dalam mendeteksi kelas positif (yang biasanya dilambangkan dengan selain angka '0'). Sehingga diperlukan penanganan terhadap distribusi kelas pada datasets yang dilakukan dengan menerapkan *oversampling* sekaligus *undersampling*. Teknik *oversampling* atau memperbanyak data dilakukan pada kelas *minority* yaitu *Drought* dengan mengimplementasikan SMOTENC (Syntethic Minority Oversampling Method for Nominal and Continous) yang bekerja dengan membuat suatu data sintetis baru baik untuk data kuantitatif serta data kualitatif yang didasarkan pada *nearest neighbors* berdasarkan jarak [*euclidian*](https://scikit-learn.org/stable/modules/neighbors.html). Kemudian pada kelas *majority* diterapkan *undersampling* menggunakan TomekLinks yang bekerja dengan menerapkan prinsip *nearest neighbors* jika mendapatkan kelas tersebut lebih dekat kepada *neighbors* kelas *minority* maka akan dihilangkan dari dataset. Penerapan kedua metode sekaligus adalah agar menghilangkan bias yang timbul setelah diperbanyaknya kelas *minority* dengan mengurangi kelas *majority*. [<sup>14</sup>](https://www.inf.ufrgs.br/maslab/pergamus/pubs/balancing-training-data-for.pdf)
  
* Melakukan ***data standardization*** pada semua fitur

  Tahapan terakhir dengan melakukan proses *standardization* pada semua fitur datasets kecuali *response variable*. Proses ini dilakukan dengan mneghilangkan nilai *mean* dan mengubah ke dalam satuan unit *variance* sama. Pentingnya tahap ini adalah karena beberapa algoritma membutuhkan asumsi data yang berada pada distrbusi sama atau format rentang sama (`sensitif terhadap feature scaling`). Selain itu proses ini dapat mempersingkat jarak yang dibutuhkan terutama pada penghitungan nilai *error* atau *loss* pada performa model. [<sup>15</sup>](https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/) Fungsi persamaan dalam melakukan *standardization* terlihat pada gambar berikut.

  <img width="350" height="170" src="https://www.thoughtco.com/thmb/IuWRp3Yt6U06_Ditky8XbUKllnY=/768x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/zscore-56a8fa785f9b58b7d0f6e87b.GIF"><br>
  <sup><sub><a href="https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/">image source</a></sub></sup>
  
---
<sub><sup>11. ukgardening. (2021). Planting seasons.</sup></sub><br>
<sub><sup>12. Thomas R. Karl & Walter James Koss, 1984: "Regional and National Monthly, Seasonal, and Annual Temperature Weighted by Area, 1895-1983." Historical Climatology Series 4-3, National Climatic Data Center, Asheville, NC, 38 pp.</sup></sub><br>
<sub><sup>13. Jim Frost. (2021). Guidelines for Removing and Handling Outliers in Data.</sup></sub><br>
<sub><sup>14. Zeng, M., Zou, B., Wei, F., Liu, X., and Wang, L. (2016). Effective prediction of three common diseases by combining SMOTE with Tomek links technique for imbalanced medical data. 2016 IEEE International Conference of Online Analysis and Computing Science (ICOACS), pp. 225–228..</sup></sub><br>
<sub><sup>15. Aniruddha Bhandari. (2020). Analytics Vidhya: Feature Scaling for Machine Learning: Understanding the Difference Between Normalization vs. Standardization.</sup></sub><br>

## Modeling
Data yang telah dilakukan *preparation* dengan baik kemudian digunakan pada proses ***modelling*** dengan menerapkan satu algoritma *baseline*, selanjutnya dilakukan perbandingan terhadap beberapa algoritma lain, dan terakhir hasil perbandingan tersebut akan diambil satu model terbaik untuk dikembangkan lebih lanjut dengan harapan mengalami peningkatan performa.

* Model ***baseline***
  
  Pada tahap ini model *baseline* yang digunakan adalah **Logistic Regression** tanpa menerapkan parameter khusus. Kemudian melakukan pengujian dengan memprediksi data *validation* yang selanjutnya performa model diukur.
  
* Model **perbandingan**

  Setelah melihat performa pada model *baseline*, maka dilakukan penambahan model baru sejumlah tiga yaitu **SVM**, **MLP**, dan **LGBM**. Kemudian ketiga model baru dilakukan proses pengujian dengan memprediksi data *validation* yang selanjutnya performa model terukur dibandingkan dengan model *baseline*.
  
* Model **pengembangan**

  Terakhir berdasarkan perbandingan dari keempat model, selanjutnya dilakukan proses optimasi mengimplementasikan *hyperparameter tuning* dengan harapan performa model terbaik dari hasil perbandingan tersebut mengalami peningkatan dan semakin baik serta handal dalam menangani permasalahan ini.
  
Berikut adalah hasil model terbaik yang didapatkan:

![image](https://user-images.githubusercontent.com/59215827/137250566-b75e3afa-4ed1-4a3c-92e3-7b6cdfac2368.png)

Beserta contoh prediksi dari model terbaik tersebut:

![image](https://user-images.githubusercontent.com/59215827/137254572-9003f1a9-9325-40bf-93e1-1282740391b0.png)
![image](https://user-images.githubusercontent.com/59215827/137254602-cdd95e6c-0225-4002-83ca-9340525c0984.png)
![image](https://user-images.githubusercontent.com/59215827/137254658-0008e554-f72e-499c-813c-5ad9c9706d3a.png)
![image](https://user-images.githubusercontent.com/59215827/137254690-e089c120-0597-48bc-9da8-2daaa4979d8c.png)

Hasil prediksi fenomena:

![image](https://user-images.githubusercontent.com/59215827/137255008-f7646fdf-6ebd-4c12-b25c-c5f148f34db1.png)

## Evaluation [<sup>16</sup>](https://towardsdatascience.com/confusion-matrix-for-your-multi-class-machine-learning-model-ff9aa3bf7826)
Metrik yang digunakan pada proyek permasalahan ini adalah *accuracy*, *precision*, *recall*, *f1 score*, dan *ROC-AUC*. Hasil performa dari semua model yang telah dibangun terlihat pada tabel dan gambar di bawah serta di bawahnya lagi terdapat penjelasan lebih detail mengenai kelima metrik tersebut.

<p align="center">
  <img src="https://user-images.githubusercontent.com/59215827/137258052-ec837c8a-24d3-4854-b269-75106aa10cd9.png"><br>
  <img src="https://user-images.githubusercontent.com/59215827/137258087-7f1bd2e9-bfff-4b84-b1eb-7630c49c43bc.png">
</p>

### Confusion Matriks
Merupakan metrik yang akan menjadi dasar dari perhitungan metrik yang digunakan.

<img width="550" height="370" src="https://miro.medium.com/max/1000/1*fxiTNIgOyvAombPJx5KGeA.png"><br>
<sup><sub><a href="https://towardsdatascience.com/confusion-matrix-for-your-multi-class-machine-learning-model-ff9aa3bf7826">image source</a></sub></sup>

* True Positive (TP): Jumlah prediksi dari kelas positif yang diprediksi secara benar oleh model sebagai kelas positif.
* True Negative (TN): Jumlah prediksi dari kelas negatif yang diprediksi secara benar oleh model sebagai kelas negatif.
* False Positive (FP): Jumlah prediksi dari kelas negatif yang diprediksi secara salah oleh model sebagai kelas positif. Biasa juga disebut sebagai *type 1 error*.
* False Negative (FN): Jumlah prediksi dari kelas positif yang diprediksi secara salah oleh model sebagai kelas negatif. Biasa juga disebut sebagai *type 2 error*.

### Accuracy
Metrik yang menunjukkan keseluruhan performa dari model atau dengan kata lain menunjukkan berapa banyak kelas yang diprediksi dengan benar oleh model. Merupakan model paling sering dipakai namun pada kasus data tidak seimbang memiliki kerentanan terhadap salahnya interpretasi performa (*bias*). Persamaan dari metrik ini sendiri adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/137261017-2f50a126-5d06-4828-abfb-9d5d835e392c.png)

### Precision
Metrik yang menunjukkan seberapa baik model melakukan prediksi kelas positif dengan benar sebagai kelas positif (aktual). Namun metrik ini tidak dapat menggambarkan secara jelas kelas positif (aktual) memiliki berapa banyak hasil prediksi benar. Persamaan dari metrik ini sendiri adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/137260975-447aa482-bc47-4e96-a959-4f909828773f.png)

### Recall (True Positive Rate (TPR))
Metrik yang menunjukkan seberapa baik kelas positif (aktual) diprediksi dengan benar sebagai kelas positif. Namun metrik ini tidak dapat menggambarkan seberapa baik model melakukan prediksi kelas positif sebagai kelas positif (aktual). Persamaan dari metrik ini sendiri adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/137261556-7fca427f-8c2e-4638-a93f-a8512e0e5e8c.png)

### F1 Score
Metrik yang menutupi kekurangan pada *precision* dan *recall* didalam penilaian performa terhadap kelas positif dengan cara menghitung [rata-rata *harmonic*](https://www.mathsisfun.com/numbers/harmonic-mean.html) dari keduanya. Namun dikarenakan kedua metrik sebelumnya hanya berfokus pada kelas positif menyebabkan *f1 score* juga tidak dapat menggambarkan secara spesifik penilaian performa terhadap kelas negatif. Akan tetapi semua hal tersebut diatasi dengan menerapkan versi *weighted* yang memperhitungkan keseluruhan kelas yang ada beserta distribusinya. Persamaan dari metrik ini sendiri adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/137265008-efe87699-0ccb-422f-8935-d513f3cfbf17.png)

### ROC AUC Score [<sup>17</sup>](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc?hl=id)
Metrik yang dapat menunjukkan relasi antara TPR dengan FPR (False Positive Rate) atau dengan kata lain menunjukkan performa dari model dalam semua ambang batas pada proses prediksi yang dilakukan. Namun metrik ini kurang begitu bagus jika digunakan pada kasus yang lebih cenderung hanya mempertimbangkan kelas positifnya seperti pada kasus real. Persamaan dari metrik ini sendiri adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/137264020-fc1a7d05-7cdd-410f-abf8-ed7e2c414bb4.png)<br>
![image](https://user-images.githubusercontent.com/59215827/137263988-bcf1e626-8fc1-4784-9a72-360e6efd45d5.png)

---
<sub><sup>16. Joydwip Mohajon. (2020). towardsdatascience: Confusion Matrix for Your Multi-Class Machine Learning Model.</sup></sub><br>
<sub><sup>17. Google. (2021). Machine Learning Crash Course: "Classification: ROC Curve and AUC".</sup></sub><br>

## Kesimpulan dan Saran
Terdapat 11 tahapan pada *data preparation* yang dilakukan sehingga dataset dapat digunakan dalam proses latih model. Kemudian model dengan performa metrik terbaik serta `>70%` diraih oleh model LightGBM tanpa adanya proses *hyperparameter tuning*. Namun, hasil tersebut menunjukkan bahwa adanya kemungkinan proses *data preparation* dapat lebih ditingkatkan lagi serta dalam pengolahan data tidak seimbang dapat memperbanyak jumlah dataset (seperti menggunakan rentang tahun lebih lama (dataset original train)) agar mendapatkan hasil lebih baik dan aman dari masalah data tidak seimbang. Serta, dapat melihat dan mencoba dengan model lain lagi atau menggunakan pendekatan hyperparameter tuning berbeda.

---
**---Ini adalah bagian akhir laporan---**
