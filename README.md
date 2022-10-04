# Laporan Proyek Machine Learning: Sistem Rekomendasi Movie - Putri Wulandari
-- --
### Domain proyek  

> **Domain proyek yang dipilih pada proyek machine learning ini ialah terkait industri perfilman dengan judul proyek "Sistem Rekomendasi Movie"**.

## Latar Belakang

Gambar1. Informasi mengenai movie di indonesia melalui website pendukung.

![WhatsApp Image 2022-09-28 at 20 41 33](https://user-images.githubusercontent.com/111127023/193485195-b9849a5e-7717-48e4-8c21-e1f9418d92e1.jpeg)

Film adalah salah satu media hiburan yang populer di masyarakat. Banyaknya judul-judul yang telah rilis membuat masyarakat kesulitan untuk menemukan film mana yang mereka ingin tonton. Untuk mengatasi masalah tersebut, perlu adanya informasi mengenai film yang akan memudahkan masyarakat untuk menemukan film yang cocok dengan preferensi *user. Oleh karena itu, *user* perlu sebuah sistem yang dapat memberikan rekomendasi film[1].

Dari sekian banyaknya film yang diproduksi membuat calon penonton kesulitan dalam menentukan film yang akan ditontonnya. Untuk mencari film tentunya akan memakan waktu, selain itu film yang sudah ditentukan untuk ditonton belum tentu sesuai dengan keinginan calon penonton setelah menontonnya, sehingga akan menghabiskan waktu lebih banyak lagi. Menonton film melalui bioskop, platform penyedia layanan streaming, maupun penyewaan dan pembelian kaset DVD juga diperlukan biaya, akan terbuang sia-sia apabila film yang ditonton tidak sesuai keinginan.
Dalam mencari kemiripan dapat menggunakan metode cosine similarity yang digunakan dalam penelitian sistem temu kembali buku berbahasa Arab yang ditulis oleh (Fauzi, Arifin and Yuniarti, 2017)[2].

Dengan mengolaborasikan frekuensi kata, inverse frekuensi dokumen, inverse frekuensi kelas, dan inverse frekuensi buku yang menjadi nilai hitung pembobotan term. Kemudian, hasil pembobotan akan dicari kemiripannya pada setiap dokumen menggunakan metode cosine similarity[3]. Proyek yang dikerjakan saat ini ialah proyek membuat sistem rekomendasi judul film berdasarkan genre menggunakan data dari metadata movies yang didownload dari kaggle. Oleh sebab itu, dibuatlah sistem rekomendasi yang dapat menyelasaikan permasalahan pelanggan agar dapat dengan mudah mendapatkan rekomendasi film berdasarkan genre dari judul film yang dicari atau yang telah diinput sebelumnya. Metode untuk sistem rekomendasi judul film atau movie berdasarkan genre ini menggunakan teknik content-based filtering. 
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
* Metode yang digunakan pada projek ini adalah Content Based Filtering. Content Based Filtering adalah rekomendasi berbasis konten yang merekomendasikan item yang memiliki kemiripan dengan item yang disukai/diinput pengguna sebelumnya. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna. Content-based filtering mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna [[4](http://103.23.20.161/index.php/semnasif/article/view/1148)]. Kelebihan dan Kekurangan dari Content-based Filtering ialah sebagai berikut:
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

Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle. Dimana, fokus pada data tersebut menyajikan data-data daftar film dari yg terlama hingga ke yg terbaru serta memberikan korelasi dengan data rating yang disediakan pada dataset (tidak terlalu banyak digunakan pada studi kasus projek ini).
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

Menyiapkan path dataset pada penyimpanan content serta menampilkan overview dataset Movie menggunakan library pandas. Library pandas ialah alat yang sangat berguna sebagai library yang mengatur tata letak data sehingga mudah dicari secara intuitif. Pandas biasa digunakan untuk membuat tabel, mengubah dimensi data, mengecek data, dan lain sebagainya.

Kemudian, Memuat dataset ke dalam variable baru, memuat dataset ke dalam variable baru, mengurutkan data dan menghapus data yang sama dengan metode *sort* dan atribut *unique.*
Dimana, metode sort ialah suatu proses penyusunan kembali kumpulan objek menggunakan tata aturan tertentu. Atribut unique digunakan untuk menghasilkan nilai unik dari suatu kolom, hasilnya dalam bentuk numpy array. 

- Menampilkan jumlah kata paling banyak yang muncul dalam kolom genre menggunakan *counter.*

Pada berkas yang diunduh yakni movies.csv berisi 9743 rows × 3 columns dan ratings.csv berisi 100k++ baris dan 4 columns. Kolom-kolom tersebut terdiri dari 2 buah kolom bertipe objek dan 1 buah kolom bertipe numerik (tipe data int64) pada file movies.csv dan pada files ratings.csv terdiri dari 4 buah kolom bertipe numerik (int64 dan float64). Untuk itu, penjelasan mengenai variabel-variable pada dataset movies recomendation ini dapat dilihat sebagai berikut:

- movieId merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap film.
- userId merupakan parameter bernilai unique. Parameter ini digunakan utk mengindetifikasi daftar tiap-tiap pengguna.
- rating merupakan parameter berisi nilai rating film yg diberikan pengguna.
- genre merupakan parameter yg menyimpan tiap-tiap kategori film.
- title merupakan parameter yg menyimpan judul masing-masing film.

# Data Preparation
---
Berikut ini ialah ialah tahapan-tahapan dalam melakukan Persiapan data:

- Memilih kolom berdasarkan data yang dibutuhkan untuk melakukan content based learning berdasarkan genre yaitu judul dan genre.
- Menghitung jumlah data pada genre dari setiap *unique value* menggunakan atribut *unique* .
- Drop judul yang duplikat (membersihkan data) dengan menggunakan metode drop. Tujuannya menjatuhkan label tertentu dari baris dan kolom. Fungsi drop menghapus baris dan kolom.
- Mereset ulang penomoran index data (tranformasi data) agar penomoran dilakukan berurutan. Menggunakan metode *reset index*. Tujuannya untuk mengatur ulang indeks dari DataFrame. ... index baru, harus dilakukan langkah reset index terlebih dahulu.

Teknik yang digunakan pada tahapan Proses Data adalah vektorisasi fungsi CountVectorizer dari library scikit-learn. CountVectorizer digunakan untuk mengubah teks yang diberikan menjadi vektor berdasarkan frekuensi (jumlah) setiap kata yang muncul di seluruh teks. CountVectorizer membuat matriks di mana setiap kata unik diwakili oleh kolom matriks, dan setiap sampel teks dari dokumen adalah baris dalam matriks. Nilai setiap sel tidak lain adalah jumlah kata dalam sampel teks tertentu. Pada proses vektorisasi digunakan metode sebagai berikut:

- Fit metode berfungsi untuk melakukan perhitungan idf pada data. Melakukan Proses fit dan melihat jumlah ukuran matrix dengan melakukan fit lalu ditransformasikan ke bentuk matrix dan melihat ukuran matrix tfidf. get_feature_names_out() berfungsi untuk melakukan mapping array dari fitur index integer ke fitur nama.
- Fit_transform() berfungsi untuk mempelajari kosa kata dan Inverse Document Frequency (IDF) dengan memberikan nilai return berupa document-term matrix.
- Todense() berfungsi untuk mengubah vektor tf-idf dalam bentuk matriks.

![WhatsApp Image 2022-10-03 at 10 17 38](https://user-images.githubusercontent.com/111127023/193500554-ab69817c-7844-4221-92a4-51d9841d3beb.jpeg)

# Modeling
---
Setelah dilakukan pra-pemrosesan pada dataset. Langkah selanjutnya ialah modeling terhadap data. Pada tahap ini Model machine learning yang digunakan pada sistem rekomendasi ialah model content-based filtering dengan simlarty measure yang digunakan adalah Cosine Similarity.. Model content-based filtering ini bekerja dengan mempelajari profil minat pengguna baru berdasarkan data dari objek yang telah dinilai pengguna. Metode ini bekerja dengan menyarankan item serupa yang pernah disukai sebelumnya atau sedang dilihat sekarang kepada pengguna berdasrakan kategori tertentu dari item yang dinilai oleh pengguna dengan menggunakan similarity tertentu.

Sedangkan cosine similarity adalah salah satu teknik mengukur kesamaan yang bekerja dengan mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama dengan menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity. cara kerja dari fungsi cosine similiraty yaitu dengan melakukan perhitungan yang sering digunakan untuk menghitung kemiripan diantara item-item [5]. Secara umum, fungsi similarity adalah fungsi yang menerima dua buah obyek berupa bilangan riil (0 dan 1) dan mengembalikan nilai kemiripan (similarity) antara kedua obyek tersebut berupa bilangan riil. Cosine similarity merupakan salah satu metode pengukuran kemiripan yang populer. Metode ini digunakan untuk menghitung nilai kosinus sudut antara dua vektor dan biasanya digunakan untuk mengukur kemiripan antara dua teks/dokumen. Fungsi cosine similarity antara item A dan item B sebagai berikut:

 Rumus Cosine similarity

$sim(A,B)= n(A and B)/\sqrt{n(A)n(B)}$

Keterangan:

𝑠𝑖𝑚(𝐴, 𝐵) = nilai similaritas dari item A dan item B
𝑛(𝐴) = banyaknya fitur konten item A 
𝑛(𝐵) = banyaknya fitur konten item B 
𝑛(𝐴 ∩ 𝐵)  = banyaknya fitur konten yang terdapat pada item A dan juga terdapat pada item B

Jika kedua objek memiliki nilai similaritas 1, maka kedua objek dikatakan identik dan sebaliknya. Semakin besar hasil dari fungsi similarity, maka kedua objek yang dievaluasi dianggap semakin mirip dan sebaliknya.

- Berikut cara melatih model dengan menggunakan consine similarity.

Gambar12. Cara melatih model dengan menggunakan consine similarity

![WhatsApp Image 2022-10-03 at 10 26 48](https://user-images.githubusercontent.com/111127023/193513254-2b02efb8-abbc-4e19-98a9-66034d684d08.jpeg)

- Pada tahapan ini menampilkan matriks kesamaan setiap judul dengan menampilkan judul film dalam 10 sampel kolom (axis = 1) dan 10 sampel baris (axis=0).

Gambar13. Matriks kesamaan setiap judul dengan menampilkan judul film dalam 10 sampel kolom (axis = 1) dan 10 sampel baris (axis=0).

![WhatsApp Image 2022-10-03 at 10 28 36](https://user-images.githubusercontent.com/111127023/193513795-c5ab6e45-19a4-4180-b113-94622d403793.jpeg)

- Dalam pemanggilan rekomendasi judul film menggunakan function yang dibuat dengan code seperti di bawah ini:

Gambar14. Pemanggilan rekomendasi judul film menggunakan function

![WhatsApp Image 2022-10-03 at 10 32 10](https://user-images.githubusercontent.com/111127023/193514028-9b47256f-5b50-4005-8763-a92163ba521f.jpeg)

Tahapan yang dilakukan pada fungsi tersebut antara lain:

- Mengambil indeks dari judul film yang telah didefinisikan sebelumnnya.
- Mengambil skor kemiripan dengan semua film.
- Mengurutkan film berdasarkan skor kemiripan.
- Mengambil 19 judul berdasarkan kemiripan dari 1-20 karena urutan 0 memberikan indeks yang sama dengan judul film yang diinput.
- Mengambil judul film dari skor kemiripan.
- Mengembalikan 19 rekomendasi judul film dari kemiripan skor yang telah diurutkan dan menampilkan genre dari 19 rekomendasi film.

Berikut top-20 recommemdation berdasarkan genre dari judul film "Jhonny English Reborn (2011)"

judul | genre
---|---
Jhonny English Reborn (2011) | Adventure, Comedy, Thriller
![WhatsApp Image 2022-10-03 at 10 34 34](https://user-images.githubusercontent.com/111127023/193514547-4165d0cf-c157-42be-8b06-e6707495f5ac.jpeg)
Dengan hasil yang diberikan di atas berdasarkan judul film "Jhonny English Reborn (2011)" dengan genre Adventure, Comedy, Thriller maka didapatkan 19 rekomendasi judul film dengan genre yang serupa ataupun mirip.

# Evaluation
---
Pada proyek ini, Metric yang digunakan pada sistem rekomendasi judul film berdasarkan genre adalah accuracy precision. Precision adalah metrik yang membandingkan rasio prediksi benar atau positif dengan keseluruhan hasil yang diprediksi positif dengan rumus

$$\ Precission=TP/(TP+FP)$$
~~~
keterangan:
TP = True Positif (prediksi positif dan hal tersebut benar)
FP = False Positif (prediksi positif dan hal tersebut salah)
~~~
Alasan accuracy Precision dipilih adalah karena metrik ini dapat membandingkan rasio prediksi benar atau positif dengan keseluruhan hasil yang diprediksi positif. Dalam hal ini adalah rasio item yang direkomendasikan memiliki genre yang mirip atau serupa dibandingkan dengan genre dari judul film yang diinput.

Code yang digunakan untuk melihat jumlah genre yang mirip atau serupa adalah sebagai berikut.
~~~
# menghitung banyaknya data genre pada hasil rekomendasi yg dilakukan 
value = pd.DataFrame(recomendation['genre'].value_counts().reset_index().values, columns = ['genre', 'count'])
value.head()
~~~
Output:

 genre   	                        count
0	    Comedy|Thriller	                    7
1	    Adventure|Comedy	                6
2	    Action|Adventure|Comedy|Thriller	3
3	    Adventure|Comedy|Thriller	        2
4	    Adventure|Comedy|Crime|Thriller	    1


Dari output tersebut dihitung accuracy precision nya adalah
```
TP = 19 #jumlah prediksi benar untuk genre yang mirip atau serupa
FP = 0 #jumlah prediksi salah untuk genre yang mirip atau serupa

Precision = TP/(TP+FP)
print("{0:.0%}".format(Precision))
```
Dipilih nya nilai True Positif 19 karna ia merupakan nilai atau jumlah yg diduga memiliki kemiripan/identik dengan genre yg dipilih yaitu 19 (7+6+3+2+1). hasil rekomendasi yg dihasilkan model menunjukan kemiripan dengan genre film yg dinput yaitu Adventure|comedy|thriller
sedangkan untuk nilai False Positif tidak teridentifikasi pada hasil output dari genre yg diinput maka nilai nya 0 
Output:
```
100%
```
## Kesimpulan

Dari output yang dihasilkan bahwa prediksi rekomendasi yang diberikan 100% presisi sesuai genre yang mirip atau serupa dengan genre dari judul yang diinput.

Dari output tersebut dihitung accuracy precision nya adalah
```
TP = 19 #jumlah prediksi benar untuk genre yang mirip atau serupa
FP = 0 #jumlah prediksi salah untuk genre yang mirip atau serupa

Precision = TP/(TP+FP)
print("{0:.0%}".format(Precision))
```
Dipilih nya nilai True Positif 19 karna ia merupakan nilai atau jumlah yg diduga memiliki kemiripan/identik dengan genre yg dipilih yaitu 19 (7+6+3+2+1). hasil rekomendasi yg dihasilkan model menunjukan kemiripan dengan genre film yg dinput yaitu Adventure|comedy|thriller
sedangkan utk nilai False Positif tidak teridentifikasi pada hasil output dari genre yg diinput maka nilai nya 0 
Output:
```
100%
```
Kesimpulan dari output yang dihasilkan bahwa prediksi rekomendasi yang diberikan 100% presisi sesuai genre yang mirip atau serupa dengan genre dari judul yang diinput.

## Referensi
---
[1] Hadi, I., Santoso, L. W., & Tjondrowiguno, A. N. (2020). Sistem Rekomendasi Film menggunakan User-based Collaborative Filtering dan K-modes Clustering. Jurnal Infra, 8(1), 228-234. https://publication.petra.ac.id/index.php/teknik-informatika/article/view/9800/8798.

[2] Fajriansyah, Muhammad, Putra Pandu Adikara, & Agus Wahyu Widodo. " Sistem Rekomendasi Film Menggunakan Content Based Filtering." Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer [Online], 5.6 (2021): 2188-2199. Web. 9 Mei. 2022 https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/9163/4159/.

[3] Fauzi, M. A., Arifin, A. Z. and Yuniarti, A. (2017) ‘Arabic book retrieval using class and book index based term weighting’, International Journal of Electrical and Computer Engineering, 7(6), pp. 3705–3710. doi: 10.11591/ijece.v7i6.pp3705-3711. 

[4] Badriyah, T., Fernando, R., & Syarif, I. (2018). Sistem Rekomendasi Content Based Filtering Menggunakan Algoritma Apriori. Konferensi Nasional Sistem Informasi (KNSI) 2018. http://103.23.20.161/index.php/semnasif/article/view/1148.

[5] D. Jannach, M. Zanker, A. Felfernig, and G. Friedrich, Recommender systems: an introduction, vol. 40. 2011. 



**---Ini adalah bagian akhir laporan---**
