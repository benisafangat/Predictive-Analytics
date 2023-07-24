# Laporan Proyek Machine Learning:

## Latar Belakang
Forex atau perdagangan mata uang asing adalah salah satu jenis investasi yang melibatkan perdagangan mata uang suatu negara terhadap mata uang negara lainnya (pasangan mata uang/pair) di pasar-pasar uang utama di seluruh dunia selama 24 jam non-stop. Pelaku usaha forex, yang dikenal sebagai trader, melakukan jual-beli mata uang dalam jangka pendek secara berkesinambungan atau dalam jangka panjang sebagai bentuk investasi.

Pergerakan nilai forex yang signifikan dan potensi keuntungan yang besar menarik banyak masyarakat untuk terlibat dalam pasar forex. Forex juga berfungsi untuk membantu kelancaran lalu lintas pembayaran internasional. Di pasar forex, terdapat tujuh mata uang dunia yang umum diperdagangkan, yaitu Dollar Amerika (USD), Poundsterling Inggris (GBP), Euro Dollar (EUR), Swiss Franc (CHF), Japanese Yen (JPY), Australian Dollar (AUD), dan Canadian Dollar (CAD).

Menurut data dari BIS (*Bank International for Settlement*) pada April 2019, nilai transaksi pasar forex mencapai lebih dari USD$ 6,6 triliun per hari. Forex termasuk dalam kategori investasi berisiko tinggi, yang berarti berisiko tinggi karena kesalahan dalam transaksi dapat dengan cepat mengurangi modal di akun trading. Oleh karena itu, para trader harus mengetahui kapan waktu yang tepat untuk masuk pasar, berapa lama menunggu, dan berapa kali melakukan pembelian atau penjualan. Salah satu cara yang dapat digunakan adalah dengan menggunakan teknik *forecasting*.

Teknik *forecasting* dalam konteks pasar forex membantu para trader untuk membuat keputusan yang lebih informasional dan mendukung dalam aktivitas perdagangan mereka dengan cara meramalkan pergerakan nilai mata uang di masa depan berdasarkan analisis data historis. Dalam hal ini, *time series forecasting* digunakan untuk mengidentifikasi pola dan tren dari data harga mata uang di masa lalu, kemudian membangun model matematika atau statistik yang dapat digunakan untuk memprediksi pergerakan harga di masa mendatang.

Berikut adalah beberapa cara teknik *forecasting* membantu para trader dalam perdagangan forex:

* Identifikasi Tren dan Pola
* Mengetahui Titik Support dan Resistance
* Memprediksi Peristiwa Ekonomi
* Mengatur Rencana dan Strategi
* Mengurangi Risiko

## Business Understanding
### Problem Statement
Berdasarkan pada penjelasan latar belakang, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

* Bagaimana cara menganalisis data harga pasangan mata uang BTC/USD di pasar forex?
* Bagaimana cara mengolah data agar bisa di latih oleh model dengan baik untuk *forecasting*?
* Bagaimana cara membangun model yang dapat melakukan prediksi time series *forecasting* dengan baik?

### Tujuan
Tujuan proyek ini dibuat adalah sebagai berikut :

* Memprediksi harga pasangan mata uang BTC/USD di pasar forex dengan akurat menggunakan model *machine learning*.
* Melakukan analisis dan pengolahan data yang optimal agar dapat diterima dengan baik oleh model *machine learning*.
* Membantu para trader dalam melakukan transaksi pada pasar forex khususnya dalam pasangan mata uang BTC/USD dengan bantuan *machine learning*.

### Solution Statement
Solusi yang dapat dilakukan agar tujuan dapat tercapai adalah sebagai berikut:

* Melakukan analisa, eksplorasi, pemrosesan pada data dengan memvisualisasikan data agar mendapat gambaran bagaimana data tersebut.
* Membuat model regresi untuk memprediksi bilangan kontinu untuk memprediksi harga yang akan datang. Berikut beberapa algoritma yang digunakan pada proyek ini:
  * *Random Forest*
  * *K-Nearest Neighbors*
  * *Boosting Algorithm*
  
## Data Understanding
Dataset yang digunakan pada proyek ini adalah dataset riwayat dari forex market BTC/USD yang diambil dari website  https://finance.yahoo.com/quote/BTC-USD/history?p=BTC-USD


![btc](https://github.com/benisafangat/predictive-analytics/assets/70525105/8fa77e42-009c-4fbf-a097-92c4f35f10f1)

Ini adalah grafik tren harga pasangan mata uang BTC/USD dari range 5 tahun terakhir.

Dataset ini memiliki format .csv yang mempunyai total 1827 data dengan 7 kolom (Date, Open, High, Low, Close, Adj Close, Volume) dengan informasi sebagai berikut:

* Date : Tanggal data tersebut direkam
* Open : Harga pembukaan pada hari tersebut
* High : Harga tertinggi pada hari tersebut
* Low : Harga terendah pada hari tersebut
* Close : Harga penutupan pada hari tersebut
* Adj Close (Adjusted Close) : Harga penutupan pada hari tersebut setelah disesuaikan dengan aksi korporasi seperti right issue, stock split atau stock reverse
* Volume : Banyaknya transaksi pada hari tersebut

## Data Preparation
### Menghapus fitur yang tidak diperlukan
Menghapus fitur Date, Volume, dan Close. Fitur Date dan Volumen dihapus dikarenakan fitur tersebut tidak merepresentasikan fitur yang akan digunakan dalam modeling. Fitur Close dihapus karena fitur pada Adj Close lebih akurat untuk merepresentasikan penutupan harga dari pada fitur Close.

### Splitting Dataset
Membagi dataset menjadi 2 kategori yaitu sebagai data latih dan data uji. Proposi yang digunakan adalah 80% untuk data latih dan 20% untuk data uji, pembagian ini sangatlah umum dalam machine learning. Pendekatan ini memungkinkan kita untuk melatih model menggunakan sebagian besar data yang tersedia (data latih) dan kemudian menguji kinerjanya menggunakan data yang tidak pernah dilihat oleh model sebelumnya (data uji). Hal ini membantu kita memastikan bahwa model yang dihasilkan dapat melakukan generalisasi dengan baik pada data baru yang belum pernah dilihat sebelumnya.

### Data Normalization
Proses normalisasi menggunakan library MinMaxScaler. Fungsi normalisasi diterapkan agar model lebih cepat dalam mempelajari data karena data telah diubah pada rentang tertentu seperti antara 0 dan 1

### Mengatasi Outlier
Terdapat 1 *outlier* pada fitur Volume. Untuk menangani outlier pada fitur tersebut, metode IQR (*Interquartile Range*) digunakan untuk menangani *outlier* dengan menghapus data yang berada di luar rentang IQR. Data yang berada di bawah Q1 (kuartil pertama) dan di atas Q3 (kuartil ketiga) akan dianggap sebagai *outlier* dan dihapus dari dataset.

### Unvariate
Univariate Analysis dilakukan untuk fokus memeriksa dan menganalisis fitur yang akan diprediksi, yaitu fitur "Adj Close". Dalam analisis ini, perhatian hanya difokuskan pada fitur tunggal ini untuk memahami karakteristik dan distribusi datanya. Hal ini membantu dalam memahami peran dan signifikansi fitur "Adj Close" terhadap target atau hasil prediksi yang diinginkan. Dengan Univariate Analysis, dapat melakukan identifikasi pola, outlier, dan statistik deskriptif lainnya yang berkaitan dengan fitur "Adj Close" secara khusus.

### Multivariate
Pada tahap ini dilakukan analisis korelasi fitur Adj Close terhadap fitur lain seperti Open, High, Low, Close dan Volume. Didapatkan bahwa Adj Close memiliki korelasi positif yang kuat terhadap fitur Open, High, Low dan Close, sedangkan untuk fitur Volume memiliki korelasi lemah terhadap fitur Adj Close.

### Corelation Matrix
Koefisien korelasi digunakan untuk mengukur kekuatan hubungan antara dua variabel serta arahnya (positif atau negatif). Korelasi memiliki rentang nilai antara -1 hingga 1. semakin dekat nilainya ke 1 atau -1, korelasinya semakin kuat. Sedangkan, semakin dekat nilainya ke 0, korelasinya semakin lemah. Pada studi kasus ini fitur Adj Close memiliki korelasi positif yang kuat terhadap fitur Open, High, Low dan Close,

## Modeling
Model yang akan digunakan proyek kali ini yaitu *Random Forest, K-Nearest Neighbors,* dan *Boosting Algorithm*.

* *Random Forest*:
*Random Forest* adalah sebuah algoritma *ensemble learning* yang menggabungkan beberapa pohon keputusan *(decision trees)* untuk membuat prediksi yang lebih akurat dan stabil. Setiap pohon keputusan dihasilkan dengan memilih sebagian sampel data secara acak dan sebagian fitur dari dataset. Kemudian, hasil prediksi dari setiap pohon digunakan untuk mengambil mayoritas suara atau rata-rata, tergantung pada studi kasus yang dimiliki apakah masalah klasifikasi atau regresi.

#### Kelebihan:
* *Random Forest* merupakan algoritma ensemble yang kombinasi dari beberapa pohon keputusan *(decision tree)*. Hal ini membuatnya dapat mengatasi masalah *overfitting* dan meningkatkan akurasi prediksi.
* Kemampuan dalam menangani data yang memiliki banyak fitur dan dapat melakukan prediksi pada data yang memiliki fitur yang hilang *(missing values)*.
* Kinerja yang baik dalam mengatasi masalah klasifikasi dan regresi pada dataset yang kompleks.

#### Kekurangan:
* Random Forest cenderung lebih kompleks dan memerlukan lebih banyak waktu untuk pelatihan dan prediksi jika dibandingkan dengan algoritma sederhana seperti KNN.
* Interpretasi hasil dari model Random Forest mungkin lebih sulit dibandingkan dengan model yang lebih sederhana karena keterlibatan banyak pohon keputusan.

* *K-Nearest Neighbors* (KNN):
*K-Nearest Neighbors* adalah algoritma *machine learning* yang digunakan baik untuk masalah klasifikasi maupun regresi. Algoritma ini berfungsi dengan mencari sejumlah K tetangga terdekat dari titik data yang akan diprediksi. Prediksi kemudian dibuat berdasarkan mayoritas kelas (untuk klasifikasi) atau rerata nilai (untuk regresi) dari tetangga-tetangga tersebut.

#### Kelebihan:
* Sederhana untuk dipahami dan diimplementasikan, cocok untuk pemula dalam machine learning.
* Tidak memerlukan pelatihan model karena algoritma KNN bersifat instance-based, sehingga proses pembelajaran terjadi saat prediksi.
* Cocok untuk masalah klasifikasi dan regresi, dan dapat bekerja dengan baik pada data yang tidak terstruktur atau data yang memiliki pola non-linear.

#### Kekurangan:
* KNN memiliki komputasi yang tinggi saat melakukan prediksi, terutama pada dataset yang besar.
* Rentan terhadap data *(outlier)* karena mengandalkan jarak antara data, sehingga mempengaruhi hasil prediksi secara signifikan jika data *outlier* ada dalam tetangga terdekat *(nearest neighbors)*.
* Perlunya menentukan parameter K (jumlah tetangga terdekat) yang optimal, yang dapat mempengaruhi kinerja model.

* *Boosting Algorithm*:
*Boosting* adalah metode ensemble learning lainnya yang juga menggabungkan beberapa model, namun dengan pendekatan berbeda. *Boosting* bekerja dengan mengurutkan model secara berurutan, di mana setiap model berfokus untuk memperbaiki kesalahan prediksi dari model sebelumnya. Model-model yang lemah dikombinasikan untuk membentuk model yang lebih kuat. Algoritma Boosting yang umum digunakan adalah AdaBoost dan Gradient Boosting.

#### Kelebihan:
* Kemampuan untuk meningkatkan kinerja model dalam hal akurasi prediksi dengan menggabungkan beberapa model yang lemah menjadi satu model yang kuat.
* Mampu menangani data yang kompleks, noise, dan data yang tidak linear.
* Mengurangi risiko *overfitting* karena memberi bobot lebih pada data yang salah diklasifikasikan oleh model sebelumnya.

#### Kekurangan:
* Proses pelatihan Boosting Algorithm cenderung lebih lambat daripada algoritma sederhana seperti KNN karena melibatkan iterasi berulang untuk memperbaiki model.
* Lebih sensitif terhadap data pencilan (outlier) dibandingkan dengan algoritma Random Forest.
* Menentukan parameter yang optimal untuk Boosting Algorithm (seperti jumlah iterasi atau learning rate) bisa menjadi tugas yang rumit dan memerlukan penyetelan (tuning) yang hati-hati.

## Evaluation
Proses evaluasi pada model *machine learning* ini, metrik yang digunakan adalah *mean squared error* (MSE). Metriks ini mengukur seberapa dekat hasil prediksi dari model dengan nilai sesungguhnya (titik data aktual) pada data pengujian. MSE menghitung selisih kuadrat antara nilai prediksi (Yi_pred) dan nilai sesungguhnya (Yi) dari setiap titik data, kemudian mengambil rata-rata dari selisih kuadrat tersebut untuk mendapatkan MSE. Berikut ada;ah rumusnya:


![Group 16](https://github.com/benisafangat/predictive-analytics/assets/70525105/d32cfd4e-97cb-4f36-8b89-1e8beaf985c0)

Keterangan:

* N = jumlah dataset
* Yi = nilai sebenarnya
* Yi_pred = nilai prediksi

Dengan menggunakan MSE sebagai metrik evaluasi, dapat menilai seberapa baik performa model dalam melakukan prediksi harga forex. Semakin kecil nilai MSE, semakin dekat garis regresi model dengan titik data aktual, dan semakin akurat prediksi model.

Hasil evaluasi menunjukkan bahwa model *Random Forest* memiliki MSE yang lebih rendah dibandingkan dengan model-model lainnya, sehingga dianggap memiliki performa optimal dalam memprediksi harga forex BTC/USD. Dengan demikian, model *Random Forest* dapat menjadi pilihan yang baik untuk membantu para trader dalam membuat keputusan transaksi di pasar forex BTSC/USD.

## Kesimpulan

Didapatkan bahwa pada studi kasus ini, performa model yang optimal adalah *Random Forest*. Model tersebut memiliki potensi untuk membantu para trader dalam membuat keputusan pembelian dan penjualan pada pasar forex. Prediksi harga yang akurat dari model ini dapat memberikan informasi yang lebih handal dalam mengambil keputusan perdagangan di masa depan. Oleh karena itu, model *Random Forest* dapat menjadi alat yang berharga bagi para trader untuk meningkatkan potensi keberhasilan dan mengurangi risiko dalam aktivitas perdagangan di pasar forex.

## Referensi

* Pavlyshenko, Bohdan M. "Bitcoin Price Predictive Modeling Using Expert Correction." 2019 XIth International Scientific and Practical Conference on Electronics and Information Technologies (ELIT). IEEE, 2019.
* Kumar, Vaibhav, and M. L. Garg. "Predictive analytics: a review of trends and techniques." International Journal of Computer Applications 182.1 (2018): 31-37.
* Hindrayani, Kartika Maulida, et al. "Studi Literatur Mengenai Prediksi Harga Saham Menggunakan Machine Learning." Prosiding Seminar Nasional Informatika Bela Negara. Vol. 1. 2020.
