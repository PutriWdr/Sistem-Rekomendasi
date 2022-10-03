# Laporan Proyek Machine Learning: Sistem Rekomendasi Movie - Putri Wulandari
-- --
### Domain proyek  

> **Domain proyek yang dipilih pada proyek machine learning ini ialah terkait industri perfilman dengan judul proyek "Sistem Rekomendasi Movie"**.

* Latar Belakang

Gambar1. Informasi mengenai movie di indonesia melalui website pendukung.

![WhatsApp Image 2022-09-28 at 20 41 33](https://user-images.githubusercontent.com/111127023/193485195-b9849a5e-7717-48e4-8c21-e1f9418d92e1.jpeg)

Film adalah salah satu media hiburan yang populer di masyarakat. Banyaknya judul-judul yang telah rilis membuat masyarakat kesulitan untuk menemukan film mana yang mereka ingin tonton. Untuk mengatasi masalah tersebut, perlu adanya informasi mengenai film yang akan memudahkan masyarakat untuk menemukan film yang cocok dengan preferensi user. Oleh karena itu, user perlu sebuah sistem yang dapat memberikan rekomendasi film.
Dari sekian banyaknya film yang diproduksi membuat calon penonton kesulitan dalam menentukan film yang akan ditontonnya. Untuk mencari film tentunya akan memakan waktu, selain itu film yang sudah ditentukan untuk ditonton belum tentu sesuai dengan keinginan calon penonton setelah menontonnya, sehingga akan menghabiskan waktu lebih banyak lagi. Menonton film melalui bioskop, platform penyedia layanan streaming, maupun penyewaan dan pembelian kaset DVD juga diperlukan biaya, akan terbuang sia-sia apabila film yang ditonton tidak sesuai keinginan. 
Dalam mencari kemiripan dapat menggunakan metode cosine similarity yang digunakan dalam penelitian sistem temu kembali buku berbahasa Arab yang ditulis oleh (Fauzi, Arifin and Yuniarti, 2017).
Dengan mengolaborasikan frekuensi kata, inverse frekuensi dokumen, inverse frekuensi kelas, dan inverse frekuensi buku yang menjadi nilai hitung pembobotan term. Kemudian, hasil pembobotan akan dicari kemiripannya pada setiap dokumen menggunakan metode cosine similarity. Proyek yang dikerjakan saat ini ialah proyek membuat sistem rekomendasi judul film berdasarkan genre menggunakan data dari metadata movies yang didownload dari kaggle. Oleh sebab itu, dibuatlah sistem rekomendasi yang dapat menyelasaikan permasalahan pelanggan agar dapat dengan mudah mendapatkan rekomendasi film berdasarkan genre dari judul film yang dicari atau yang telah diinput sebelumnya. Metode untuk sistem rekomendasi judul film atau movie berdasarkan genre ini menggunakan teknik content-based filtering. 
___

# Business Understanding
---
### Problem Statements

Berdasarkan latar belakang di atas maka terdapat rumusan masalah yang dapat diselesaikan pada proyek ini sebagai berikut:

- Bagaimana caranya memberikan rekomendasi judul film berdasarkan genre pada setiap judul film yang pelanggan input sehingga dapat memberikan preferensi yang sesuai keinginan pelanggan?
- Bagaimana cara melakukan pra-pemrosesan pada data movie recomendation yang akan digunakan agar dapat membuat model yang baik menggunakan teknik content-base filtering?

### Goals

Berdasarkan rumusan masalah di atas maka mendapat penyelesaian sebagai berikut:

- Diharapkan membuat pelanggan lebih mudah menemukan judul film yang tepat dengan bantuan sistem rekomendasi judul film berdasarkan genre yang dibuat.
- Diharapkan melakukan pra-pemrosesan dengan baik agar dapat digunakan dalam pembuatan model.

### Solution statements
   
   Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini ialah sebagai berikut:
* Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, antara lain:
    * Mengecek masalah data yang kosong dengan melakukan pengecekan terlebih dahulu.
    * Menghitung besar atau panjang data pada dataset. Kemudian, mencoba untuk menguraikan jenis-jenis fitur pada kolom genre.
    * mengurutkan data movieId dan menghapus data yg sama
    * Membuang judul film yg duplikat dengan method ``` drop_duplicats()```.
* Metode yang digunakan pada projek ini adalah Content Based Filtering. Content Based Filtering adalah rekomendasi berbasis konten yang merekomendasikan item yang memiliki kemiripan dengan item yang disukai/diinput pengguna sebelumnya. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna [[6](http://103.23.20.161/index.php/semnasif/article/view/1148)]. Kelebihan dan Kekurangan dari Content-based Filtering ialah sebagai berikut:
    * Kekurangan
      * New User
        Sistem tidak dapat memberikan rekomendasi yang dapat diandalkan pada pengguna baru, karena membutuhkan penelusuran terlebih dahulu pada preferensi pengguna.
    * Kelebihan
      * User Independence
        Tidak bergantung kepada user lain dalam memberikan rekomendasi yang ada. New Item Mampu merekomendasikan item yang belum dinilai oleh setiap pengguna. 
     
# Data Understanding
---
Gambar2. Dataset bersumber kaggle

![WhatsApp Image 2022-09-28 at 20 26 34](https://user-images.githubusercontent.com/111127023/193491025-94791318-f78b-4719-b22d-754191617cbe.jpeg)

Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle. Dimana, fokus pada data tersebut menyajikan data-data daftar film dari yg terlama hingga ke yg terbaru serta memberikan korelasi dengan data rating yg disediakan pada dataset (tidak terlalu banyak digunakan pada studi kasus projek ini).
Informasi dataset dapat dilihat pada tabel dibawah ini:

Tabel1. Keterangan mengenai dataset

Jenis | Keterangan
--- | ---
Sumber | (https://www.kaggle.com/datasets/sayan0211/movie-recomendation-pjct)
Lisensi | Unknown
Kategori | Movies, TV Shows, Recomendations Movie Dataset
Jenis dan Ukuran Berkas | Zip (866 kB)

Berikut ini beberapa tahapan Data Understanding antara lain:
- Meload Dataset ke dalam sebuah Dataframe menggunakan pandas
- ``` df.info()``` digunakan untuk mengecek tipe kolom pada dataset
- ```df.isna().sum()``` digunakan untuk mengecek apakah ada kolom yg kosong, pada dataset ini nilai kosong tidak ditemukan
- ```df.describe()``` digunakan utk mendapatkan info mengenai dataset terhadap nilai rata-rata, median, banyaknya data, nilai Q1 hingga Q3 dan lain-lain.
- ``` len(nama_variable.unique()) ```menghitung panjang data unique dari variable tertentu
- Mengurutkan dataset dan menghapus data movieId yg sama

Gambar3. Mengurutkan dataset dan menghapus data movieId yg sama

![WhatsApp Image 2022-10-03 at 09 51 56](https://user-images.githubusercontent.com/111127023/193497353-f29fc4c7-0918-4455-b1c2-8058467b9763.jpeg)

Gambar4. Menampilkan rata-rata genre yg paling banyak muncul pada dataset

![WhatsApp Image 2022-10-03 at 09 58 43](https://user-images.githubusercontent.com/111127023/193497566-0b8e4f31-a1e1-4b9d-aaa4-c46aeb24edeb.jpeg)

Pada berkas yang diunduh yakni movies.csv berisi 9743 rows × 3 columns dan ratings.csv berisi 100k++ baris dan 4 columns. Kolom-kolom tersebut terdiri dari 2 buah kolom bertipe objek dan 1 buah kolom bertipe numerik (tipe data int64) pada file movies.csv dan pada files ratings.csv terdiri dari 4 buah kolom bertipe numerik (int64 dan float64). Untuk itu, penjelasan mengenai variabel-variable pada dataset movies recomendation ini dapat dilihat sebagai berikut:

- movieId merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap film.
- userId merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap pengguna.
- rating merupakan parameter berisi nilai rating film yg diberikan pengguna.
- genre merupakan parameter yg menyimpan tiap-tiap kategori film.
- title merupakan parameter yg menyimpan judul masing-masing film.

# Data Preparation
---
Berikut ini ialah ialah tahapan-tahapan dalam melakukan Persiapan data:

Gambar5. Menghitung jumlah data pada genre

![WhatsApp Image 2022-10-03 at 10 08 19](https://user-images.githubusercontent.com/111127023/193499666-32b5a983-5e63-4b7e-8f25-09fc65fa8234.jpeg)

Gambar6. Drop judul yg duplikat (membersihkan data)

![WhatsApp Image 2022-10-03 at 10 11 52](https://user-images.githubusercontent.com/111127023/193499779-c0b838ce-353d-4b26-b3d2-92f18029c325.jpeg)

Gambar7. Mereset ulang penomoran index data (tranformasi data)

![WhatsApp Image 2022-10-03 at 10 13 19](https://user-images.githubusercontent.com/111127023/193499978-7edd4b50-e4c9-4280-8fb7-a28c10a8aa39.jpeg)

Teknik yang digunakan pada tahapan Proses Data adalah vektorisasi fungsi CountVectorizer dari library scikit-learn. CountVectorizer digunakan untuk mengubah teks yang diberikan menjadi vektor berdasarkan frekuensi (jumlah) setiap kata yang muncul di seluruh teks. CountVectorizer membuat matriks di mana setiap kata unik diwakili oleh kolom matriks, dan setiap sampel teks dari dokumen adalah baris dalam matriks. Nilai setiap sel tidak lain adalah jumlah kata dalam sampel teks tertentu. Pada proses vektorisasi digunakan metode sebagai berikut:

Gambar8. fit metode berfungsi untuk melakukan perhitungan idf pada data

![WhatsApp Image 2022-10-03 at 10 15 10](https://user-images.githubusercontent.com/111127023/193500179-d89fca8a-6f5d-4ee1-82d1-7c5b992a97ad.jpeg)

get_feature_names_out() berfungsi untuk melakukan mapping array dari fitur index integer ke fitur nama

Gambar9. fit_transform() berfungsi untuk mempelajari kosa kata dan Inverse Document Frequency (IDF) dengan memberikan nilai return berupa document-term matrix

![WhatsApp Image 2022-10-03 at 10 16 33](https://user-images.githubusercontent.com/111127023/193500440-1795406b-bb79-4209-b037-6737fbe293cf.jpeg)

Gambar10. todense() berfungsi untuk mengubah vektor tf-idf dalam bentuk matriks

![WhatsApp Image 2022-10-03 at 10 17 38](https://user-images.githubusercontent.com/111127023/193500554-ab69817c-7844-4221-92a4-51d9841d3beb.jpeg)

# Modeling
---
Setelah dilakukan pra-pemrosesan pada dataset. Langkah selanjutnya ialah modeling terhadap data. Pada tahap ini Model machine learning yang digunakan pada sistem rekomendasi ialah model content-based filtering dengan simlarty measure yang digunakan adalah Cosine Similarity.. Model content-based filtering ini bekerja dengan mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna dengan menggunakan similarity tertentu.
**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**
