# Laporan Proyek Machine Learning: Sistem Rekomendasi Movie - Putri Wulandari
-- --
### Domain proyek  

> **Domain proyek yang dipilih pada proyek machine learning ini ialah terkait industri perfilman dengan judul proyek "Sistem Rekomendasi Movie"**.

* Latar Belakang

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
-  Diharapkan melakukan pra-pemrosesan dengan baik agar dapat digunakan dalam pembuatan model.

### Solution statements
   
   Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini ialah sebagai berikut:
* Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, diantaranya :
    * Mengecek masalah data yang kosong dengan melakukan pengecekan terlebih dahulu.
    * Menghitung besar/panjang data pada dataset terlebih dahulu kemudian mencoba untuk menguraikan jenis-jenis fitur pada kolom genre
    * mengurutkan data movieId dan menghapus data yg sama
    * Membuang judul film yg duplikat dengan method ``` drop_duplicats()``` 
## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**
