# dedbscan
Dynamic Epsilon DBSCAN for earthquake dataset

## Penjelasan Algoritma
### Algoritma Clustering DBSCAN
Proses pengelompokan dengan DBSCAN dapat digambarkan sebagai pohon. Dimulai dengan titik mana pun yang memiliki setidaknya titik MinPts terdekat dalam radius epsilon (ε). Kemudian lakukan pencarian pertama di sepanjang masing-masing titik terdekat ini. Untuk setiap titik terdekat, periksa berapa banyak titik yang ada dalam radius. Jika memiliki titik dalam radius ε kurang dari MinPts, titik ini menjadi titik perbatasan. Namun, jika memiliki setidaknya MinPts, maka titik itu menjadi cabang, dan semua tetangganya ditambahkan ke antrian FIFO (First In First Out) dari pencarian pertama ini. Komputasi dari DBSCAN adalah sebagai berikut:
1.	Inisialisasi parameter MinPts dan eps (ε)
2.	Tentukan titik awal atau p secara acak
3.	Hitung ε atau semua jarak titik yang density reachable terhadap p
4.	Jika titik yang memenuhi ε lebih dari MinPts maka titik p adalah core point dan cluster terbentuk
5.	Jika p adalah border point dan tidak ada titik yang density reachable terhadap p, maka proses dilanjutkan ke titik yang lain
6.	Ulangi langkah 3 – 5 hingga semua titik diproses

### Dynamic Epsilon DBSCAN
Kami memodifikasi parameter ε dengan nilai magnitude, sehingga nilainya untuk setiap titik akan berbeda berdasarkan pada magnitude. Karena itu, kami menyebutnya DBSCAN dengan nilai epsilon (ε) yang dinamis (Dynamic Epsilon DBSCAN / DE-DBSCAN). Nilai magnitude digunakan sebagai ε karena besarannya dapat mempengaruhi luas area yang terdampak akibat gempa. Untuk parameter MinPts, dapat digunakan nilai 4, untuk mengurangi kompleksitas komputasi kerena data hanya terdiri dari dua fitur.

## Implementasi Program
### Program Dynamic Epsilon DBSCAN
Implementasi algoritma Dynamic DBSCAN pada program ini dilakukan dengan memodifikasi program DBSCAN biasa yang dibuat oleh Chris McCormic. Implementasinya dilakukan menggunakan bahasa pemrograman Python. Program dan modifikasi DE-DBSCAN adalah seperti berikut dynamicDBSCAN.py

### Format Data Gempa
Fitur yang digunakan adalah koordinat spasial, yaitu lintang (latitude) dan bujur (longitude), serta besar kekuatan gempa (magnitude). Setiap baris (record) pada data menunjukkan titik terjadinya getaran gempa.

### Eksekusi Program Clustering Data Gempa
Karena program dibuat dalam bahasa pemrograman Python dan tanpa GUI, maka untuk eksekusi program dapat dilakukan dari command prompt/terminal pada sistem operasi, melalui Jupyter yang menggunakan browser, maupun dengan interface Python lainnya. Berikut adalah contoh tahapan eksekusi program dari aplikasi Jupyter di browser:
1.	Pertama-tama, import library-library yang dibutuhkan, termasuk program Dynamic Epsilon DBSCAN
2.	Kemudian berikan perintah untuk membaca data gempa dan melakukan proses clustering
3.	Lakukan evaluasi terhadap hasil clustering yang didapat dan tampilkan visualisasi hasil cluster
