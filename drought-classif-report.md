# Laporan Proyek Machine Learning - Muhammad Difagama Ivanka
---
## Domain Proyek
Proyek *machine learning* ini akan menyelesaikan permasalahan dalam domain **lingkungan** dengan judul "Prediksi Kekeringan parah berdasarkan Data *Meteorological* dan Data informasi *Soil*".

### Latar Belakang
Kekeringan yang terjadi dengan tidak normal atau biasa disebut *drought* merupakan salah satu fenomena alam dengan dampak signifikan terhadap beberapa aspek seperti lingkungan, pertanian, masyarakat, hingga ekonomi. Ciri utama dari fenomena ini adalah kekurangan sumber air yang sangat parah pada suatu area tertentu ditandai dengan sangat kecilnya tingkat presipitasi dalam jangka waktu lumayan panjang. Dengan keadaan seperti itu fenomena ekstrem ini tetap dapat terjadi pada wilayah dengan tingkat presipitasi atau curah hujan sangat tinggi serta tanpa batasan keadaan iklim sama sekali. Sehingga dampak fenomena ini dapat lebih terasa jika dibandingkan dengan fenomena alam lainnya. [<sup>1</sup>](https://www.researchgate.net/publication/319328223_Drought_Management_Current_Challenges_and_Future_Outlook)

Menurut National Oceanic dan Atmospheric Administration (NOAA), [<sup>2</sup>](https://www.ncdc.noaa.gov/news/drought-monitoring-economic-environmental-and-social-impacts) fenomena ini tidak tampak secara nyata dan mengerikan sebagaimana pada fenomena tornado. Namun faktanya kerugian yang dirasakan rata-rata mencapai kurang lebih 9 Miliar USD setiap tahunnya. Dampak tersebut dapat berpengaruh terhadap ekonomi seperti harga kebutuhan pokok maupun secara langsung terhadap produk olahan pertanian semisal keju, padi, dan sebagainya. Dampak lain yang dapat ditimbulkan berupa defisit air minum, penyakit sengatan panas, meningkatkan risiko kebakaran hutan, serta lainnya terutama apabila terjadi terus menerus dalam jangka waktu panjang.

> Statistik menunjukkan hampir setengah wilayah atau mencapai sekitar 47% keseluruhan Amerika Serikat mengalami fenomena ini berdasarkan skala tingkatan sejumlah 5 level mulai dari D0 hingga D4, dengan fenomena *drought* mulai ditunjukkan pada level D1. [<sup>3</sup>](https://www.drought.gov/) 
 
Untuk itu diperlukan suatu metode didalam membantu mengatasi fenomena ini dimana teknologi serta pemahaman peneliti semata masih terbatas untuk dapat memperkirakan akan terjadinya fenomena ini setidaknya beberapa bulan ke depan. [<sup>4</sup>](https://sgp.fas.org/crs/misc/R43407.pdf) Maka proyek ini mencoba menyelesaikan permasalahan yang ada dengan menerapkan kemampuan dari *machine learning* sehingga dapat membantu memprediksi fenomena *drought* tersebut berdasarkan data historis *meteorological* berupa informasi cuaca serta iklim dan juga data *soil* yang mengandung informasi keadaan tanah pada suatu wilayah dalam proyek ini mengambil contoh Amerika Serikat. Diharapkan *machine learning* dapat memudahkan para ahli maupun masyarakat untuk melakukan tindakan persiapan sebelum fenomena terjadi dengan proses implementasi yang secara *web* hingga *mobile* dapat diterapkan.

---
<sub><sup>1. Eslamian, S. et al. (2017). Drought Management: Current Challenges and Future Outlook. (pp.727-761, Chapter: 34).</sup></sub><br>
<sub><sup>2. NOAA. (2021). DROUGHT: Monitoring Economic, Environmental, and Social Impacts.</sup></sub><br>
<sub><sup>3. National Integrated Drought Information System (NIDIS). (2021). U.S. Drought Monitor.</sup></sub><br>
<sub><sup>4. Peter Folger. (2017). Drought in the United States: Causes and Current Understanding. Congressional Research Service.</sup></sub>

## Business Understanding
Bagian ini menjelaskan proses klarifikasi masalah dan mengajukan minimal satu solusi untuk menyelesaikan permasalahan. Bagian laporan ini mencakup:

### Problem Statements
Tuliskan problem statement Anda di sini. Anda dapat menggunakan kalimat tanya untuk mendefinisikan bagian ini.

### Goals
Tuliskan dan jelaskan goal proyek yang ingin Anda capai di bagiani ini. Anda dapat menggunakan bullet point jika memiliki lebih dari satu goals proyek.

### Solution statements
Sampaikan solusi yang Anda ajukan untuk menyelesaikan permasalahan di sini. Misalnya, Anda mengajukan dua algoritma machine learning sebagai solusi permasalahan, yaitu Random Forest dan Boosting Algorithm. Jelaskan secara singkat mengenai kedua algoritma ini. 
Sebagai contoh:
- **Random Forest**. Kalimat selanjutnya menjelaskan informasi atau cara kerja algoritma ini. Selain itu, dapat juga Anda tambahkan kelebihan dan kekurangan algoritma ini.
- **Boosting Algorithm**. Sama dengan di atas. 

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
