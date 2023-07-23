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
* Membantu para trader dalam melakukan transaksi pada pasar forex khususnya dalam pasangan mata uang BTC/USD.

### Solution Statement
Solusi yang dapat dilakukan agar tujuan dapat tercapai adalah sebagai berikut:

* Melakukan analisa, eksplorasi, pemrosesan pada data dengan memvisualisasikan data agar mendapat gambaran bagaimana data tersebut.
* Membuat model regresi untuk memprediksi bilangan kontinu untuk memprediksi harga yang akan datang. Berikut beberapa algoritma yang digunakan pada proyek ini:
  * *Random Forest*
  * *K-Nearest Neighbors*
  * *Boosting Algorithm*
  
## Data Understanding
Dataset yang digunakan pada proyek ini adalah dataset riwayat dari forex market BTC/USD yang diambil dari website  https://finance.yahoo.com/quote/BTC-USD/history?p=BTC-USD

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
Menghapus fitur Date, Volume, dan Close. 

### Splitting Dataset
Membagi dataset menjadi 2 kategori yaitu sebagai data latih dan data uji. Proposi yang digunakan adalah 80% untuk data latih dan 20% untuk dat uji.

### Data Normalization
Proses normalisasi menggunakan library MinMaxScaler. Fungsi normalisasi diterapkan agar model lebih cepat dalam mempelajari data karena data telah diubah pada rentang tertentu seperti antara 0 dan 1

### Multivariate
### Unvariate
### Mengatasi Outlier
### Corelation Matrix

## Modeling
Model yang akan digunakan proyek kali ini yaitu *Random Forest, K-Nearest Neighbors,* dan *Boosting Algorithm*.

* *Random Forest*:
*Random Forest* adalah sebuah algoritma *ensemble learning* yang menggabungkan beberapa pohon keputusan *(decision trees)* untuk membuat prediksi yang lebih akurat dan stabil. Setiap pohon keputusan dihasilkan dengan memilih sebagian sampel data secara acak dan sebagian fitur dari dataset. Kemudian, hasil prediksi dari setiap pohon digunakan untuk mengambil mayoritas suara atau rata-rata, tergantung pada studi kasus yang dimiliki apakah masalah klasifikasi atau regresi.

* *K-Nearest Neighbors* (KNN):
*K-Nearest Neighbors* adalah algoritma *machine learning* yang digunakan baik untuk masalah klasifikasi maupun regresi. Algoritma ini berfungsi dengan mencari sejumlah K tetangga terdekat dari titik data yang akan diprediksi. Prediksi kemudian dibuat berdasarkan mayoritas kelas (untuk klasifikasi) atau rerata nilai (untuk regresi) dari tetangga-tetangga tersebut.

* *Boosting Algorithm*:
*Boosting* adalah metode ensemble learning lainnya yang juga menggabungkan beberapa model, namun dengan pendekatan berbeda. *Boosting* bekerja dengan mengurutkan model secara berurutan, di mana setiap model berfokus untuk memperbaiki kesalahan prediksi dari model sebelumnya. Model-model yang lemah dikombinasikan untuk membentuk model yang lebih kuat. Algoritma Boosting yang umum digunakan adalah AdaBoost dan Gradient Boosting.

## Evaluation
Proses evaluasi pada model *machine learning* ini, metrik yang digunakan adalah *mean squared error* (MSE). Metriks ini mengukur seberapa dekat hasil prediksi dari model dengan nilai sesungguhnya (titik data aktual) pada data pengujian. MSE menghitung selisih kuadrat antara nilai prediksi (Yi_hat) dan nilai sesungguhnya (Yi) dari setiap titik data, kemudian mengambil rata-rata dari selisih kuadrat tersebut untuk mendapatkan MSE.

Dengan menggunakan MSE sebagai metrik evaluasi, dapat menilai seberapa baik performa model dalam melakukan prediksi harga forex. Semakin kecil nilai MSE, semakin dekat garis regresi model dengan titik data aktual, dan semakin akurat prediksi model.

Hasil evaluasi menunjukkan bahwa model *Random Forest* memiliki MSE yang lebih rendah dibandingkan dengan model-model lainnya, sehingga dianggap memiliki performa optimal dalam memprediksi harga forex. Dengan demikian, model *Random Forest* dapat menjadi pilihan yang baik untuk membantu para trader dalam membuat keputusan transaksi di pasar forex.

Dengan performa yang optimal, model *Random Forest* memiliki potensi untuk membantu para trader dalam membuat keputusan pembelian dan penjualan pada pasar forex. Prediksi harga yang akurat dari model ini dapat memberikan informasi yang lebih handal dalam mengambil keputusan perdagangan di masa depan. Oleh karena itu, model *Random Forest* dapat menjadi alat yang berharga bagi para trader untuk meningkatkan potensi keberhasilan dan mengurangi risiko dalam aktivitas perdagangan di pasar forex.
