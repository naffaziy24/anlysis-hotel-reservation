# anlysis-hotel-reservation
## Project Overview 
Project ini berfokus pada analisis proses reservasi hotel berdasarkan dataset reservasi hotel yang terdiri dari 119.390 data observasi dari City Hotel dan Resort Hotel. Data mencakup reservasi yang berhasil maupun reservasi yang dibatalkan dalam periode 1 Juli 2015 hingga 31 Agustus 2017.
## Business Problem
Dalam industri perhotelan, proses reservasi menjadi salah satu aspek penting yang memengaruhi pengalaman dan kepuasan pelanggan. Sistem reservasi yang mudah, cepat, dan efisien dapat meningkatkan loyalitas pelanggan serta memperbesar kemungkinan pelanggan untuk kembali melakukan pemesanan di masa mendatang.
Namun, berdasarkan data observasi yang tersedia, ditemukan beberapa permasalahan utama pada proses reservasi hotel, di antaranya:
1. Tingginya tingkat pembatalan reservasi oleh pelanggan.
2. Variasi lead time yang tidak menentu sehingga menyulitkan pengelolaan kamar dan sumber daya hotel.
3. Permintaan khusus pelanggan (special request) yang sering tidak terpenuhi.
4. Proses pembayaran yang kurang efisien dan berpotensi menyebabkan kegagalan transaksi.
5. Kurangnya komunikasi yang efektif selama proses Check-In dan Check-Out.
## Tujuan
Adapun tujuan dari project ini adalah:
1. Menganalisis faktor-faktor yang memengaruhi tingginya cancellation rate.
2. Mengidentifikasi pengaruh lead time terhadap proses reservasi hotel.
3. Menganalisis dampak special request terhadap kepuasan pelanggan.
4. Mengevaluasi proses pembayaran dalam reservasi hotel.
5. Mengidentifikasi permasalahan komunikasi dalam layanan pelanggan hotel.
6. Memberikan rekomendasi strategi bisnis berdasarkan hasil analisis data.
## Data Preparation
Data preparation atau data processing merupakan proses pembersihan dan transformasi data mentah menjadi format yang siap digunakan untuk analisis data. Pada project ini digunakan dataset `midterm_hotel_data.csv` yang berisi 119.390 data reservasi City Hotel dan Resort Hotel pada periode Juli 2015 hingga Agustus 2017, termasuk reservasi yang berhasil maupun yang dibatalkan.
Tahapan data preparation yang dilakukan meliputi:

### 1. Import Library dan Dataset
Mengimpor beberapa library Python seperti:
- Pandas
- NumPy
- Seaborn

Dataset kemudian diimpor dari file CSV ke Google Colab untuk dilakukan proses analisis dan cleaning data.

### 2. Pengecekan Tipe Data
Dilakukan pengecekan tipe data pada setiap kolom untuk memastikan kesesuaian tipe data dengan isi informasi pada kolom tersebut. Contohnya, kolom `country` menggunakan tipe data object/string karena berisi kode negara pelanggan.

### 3. Pengecekan Data Duplikat
Dilakukan pengecekan data duplikat pada seluruh kolom dataset dan tidak ditemukan data duplikat.

### 4. Pengecekan Missing Value
Ditemukan beberapa kolom yang memiliki missing value, di antaranya:
- `lead_time`
- `stays_in_weekend_nights`
- `adults`
- `country`
- `children`
- `adr`
- `total_of_special_requests`
- `company`
- `agent`

### 5. Analisis Statistik Deskriptif
Dilakukan perhitungan statistik deskriptif seperti:
- Mean
- Median
- Standard Deviation
- Minimum
- Maximum
- Mode

Statistik ini digunakan sebagai pertimbangan dalam proses penanganan missing value.

### 6. Penanganan Missing Value
Penanganan missing value dilakukan berdasarkan tipe data dan konteks bisnis:

- Kolom numerik seperti `lead_time`, `stays_in_weekend_nights`, `adults`, `children`, `adr`, dan `total_of_special_requests` diisi menggunakan nilai median karena terdapat perbedaan yang cukup signifikan antara mean dan median.
- Kolom `country` diisi menggunakan modus karena merupakan data kategorikal.
- Kolom `agent` dan `company` diisi dengan nilai `0` untuk merepresentasikan pelanggan yang melakukan reservasi secara mandiri tanpa agen atau company.

### 7. Pengecekan Outlier
Pengecekan outlier dilakukan menggunakan metode IQR (Interquartile Range) pada kolom numerik.

Beberapa kolom memiliki outlier seperti:
- `lead_time`
- `stays_in_weekend_nights`
- `adults`
- `adr`
- `total_of_special_requests`

Namun, outlier tidak dihapus karena dianggap masih merepresentasikan kondisi nyata pada bisnis perhotelan, seperti:
- Reservasi jauh hari sebelum tanggal check-in
- Reservasi grup dalam jumlah besar
- Perubahan harga hotel berdasarkan musim dan permintaan
- Variasi permintaan khusus pelanggan

### 8. Menghapus Kolom yang Tidak Diperlukan
Kolom tanpa nama (`Unnamed`) yang hanya berisi indeks dihapus agar dataset lebih bersih dan mudah dianalisis.

### 9. Menyimpan Dataset Hasil Cleaning
Dataset yang telah dibersihkan kemudian disimpan kembali ke dalam file CSV baru dengan nama:
processed_hotel_data.csv

## Data Extraction

Proses data extraction dilakukan menggunakan DBeaver dan SQL Query pada dataset `processed_hotel_data` untuk memperoleh insight terkait reservasi hotel.

Beberapa analisis yang dilakukan meliputi:

- Menghitung cancellation rate berdasarkan jenis hotel dan tahun reservasi
- Menganalisis hubungan lead time dengan special request pelanggan
- Mengidentifikasi tanggal dengan average daily rate (ADR) tertinggi
- Menganalisis hubungan antara lead time dan rata-rata ADR hotel

SQL digunakan untuk:
- Data filtering
- Aggregation
- Grouping
- Common Table Expression (CTE)
- Business insight analysis

Tools yang digunakan:
- DBeaver
- PostgreSQL / SQL
