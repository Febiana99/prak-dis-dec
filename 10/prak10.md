<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert10</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Data Terdistribusi </h3>

**1. Instalasi**<br>
**Ekstraksi**<br>
<p align="center">
  <img width="727" height="755" alt="image" src="https://github.com/user-attachments/assets/efcc13fc-fd3d-43da-9df1-e64658686e4c" /><br>
  
Pada tahap ini dilakukan ekstraksi file instalasi YugabyteDB menggunakan perintah tar -xvf yugabyte-2.25.1.0-b381-linux-x86_64.tar.gz. Sebelum ekstraksi, perintah ls -la digunakan untuk memastikan file instalasi tersedia pada direktori kerja. Hasil ekstraksi berupa folder Yugabyte yang akan digunakan pada tahap berikutnya.

**Buat symlink**<br>
  <p align="center">
<img width="840" height="590" alt="image" src="https://github.com/user-attachments/assets/f8ee6afa-b1b0-4ed2-a035-82f77b2b64d6" /><br>
    
Pada tahap ini dibuat symbolic link (symlink) untuk mempermudah akses ke direktori YugabyteDB. Hasil pembuatan symlink dapat diverifikasi menggunakan perintah ls -la.


**Kerjakan post_install.sh**<br>
  <p align="center">
<img width="840" height="828" alt="image" src="https://github.com/user-attachments/assets/552222bc-8803-4016-a399-8a4f28a30257" /><br>
    
post_install.sh dijalankan untuk melakukan konfigurasi tambahan yang diperlukan oleh YugabyteDB. Proses ini juga memeriksa beberapa komponen yang dibutuhkan sistem.

**Buat file untuk env variables**<br>
<img width="840" height="71" alt="image" src="https://github.com/user-attachments/assets/f9ea3486-021f-49db-9f33-608098337217" />

environment variable dibuat untuk menyimpan konfigurasi path YugabyteDB. Tujuannya agar sistem dapat mengenali lokasi instalasi YugabyteDB secara otomatis tanpa perlu menuliskan path lengkap setiap kali menjalankan perintah.

**Source saat akan menggunakan pada shell tersebut**
  <p align="center">
<img width="840" height="495" alt="image" src="https://github.com/user-attachments/assets/8db8ef92-77b3-431e-8768-16ec6fec83a3" />

Tahap ini dilakukan untuk memuat konfigurasi environment variable ke dalam shell yang sedang aktif. Setelah perintah source ~/.yb_env dijalankan, perintah YugabyteDB dapat digunakan secara langsung. Verifikasi dilakukan menggunakan perintah yugabyted --help untuk memastikan bahwa sistem telah berhasil mengenali instalasi YugabyteDB.

**2. Buat Kluster**<br>
**Node 1**
  <p align="center">
<img width="840" height="420" alt="image" src="https://github.com/user-attachments/assets/438ff68c-c895-4da9-b665-b3dc2194ac92" /><br>

Status :<br>
  <p align="center">
<img width="840" height="270" alt="image" src="https://github.com/user-attachments/assets/efc8e4d1-7ed6-4d72-a329-50366ed187d1" />
    
Perintah status digunakan untuk memeriksa kondisi node pertama setelah dijalankan. Informasi yang ditampilkan meliputi status layanan, lokasi data, status YSQL, dan informasi koneksi yang digunakan oleh YugabyteDB. Hasil status menunjukkan bahwa node pertama berhasil dijalankan.


**Node 2**<br>
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/fc24beb1-6141-409e-83b9-db616de8bf30" />

Status :
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/4f693061-34e7-4335-9343-871098e9c00d" />

Perintah status digunakan untuk memeriksa kondisi node kedua setelah dijalankan. Informasi yang ditampilkan meliputi status layanan, lokasi data, status YSQL, dan informasi koneksi yang digunakan oleh YugabyteDB. Hasil status menunjukkan bahwa node kedua berhasil dijalankan dan terhubung ke cluster

**Node 3**<br>
  <p align="center">
<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/11bcd42d-f041-4d01-a876-255090a3edb9" />

Status :<br>
  <p align="center">
<img width="840" height="250" alt="image" src="https://github.com/user-attachments/assets/03de09be-f93c-4957-bdb8-2aed2c716f42" />

Perintah status digunakan untuk memeriksa kondisi node ketiga setelah dijalankan. Informasi yang ditampilkan meliputi status layanan, lokasi data, status YSQL, dan informasi koneksi yang digunakan oleh YugabyteDB. Hasil status menunjukkan bahwa node ketiga berhasil dijalankan dan terhubung ke cluster


**Atur data_placement dengan penempatan utama di node 1:**<br>
  <p align="center">
<img width="840" height="200" alt="image" src="https://github.com/user-attachments/assets/6aff0bc8-04ef-47ae-b01d-11430049eca8" />

Pada tahap ini dilakukan konfigurasi data placement menggunakan parameter fault_tolerance=zone. Tujuan konfigurasi ini adalah mengatur penempatan data dan replika sehingga distribusi data dapat dilakukan secara lebih terstruktur berdasarkan zona yang telah ditentukan pada cluster.

Setelah mengaktifkan 3 nodes tersebut, UI berupa web tersedia di http://localhost:15433 sebagai berikut:<br>
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/f56acbec-b208-4e0c-b6ce-96a32c66dc74" /><br>

Setelah seluruh node aktif, YugabyteDB menyediakan antarmuka berbasis web yang dapat diakses melalui browser. Halaman UI ini digunakan untuk memantau kondisi cluster, melihat informasi node, status tablet, distribusi data, serta berbagai informasi operasional lainnya<br>


**3. Sharding**<br>
**Range Sharding**<br>
Membuat Tabel user_range
<p align="center">
<img width="940" height="433" alt="image" src="https://github.com/user-attachments/assets/3f7911db-6113-4c73-b663-29e1d9cf9d13" /><br>

Pada tahap ini dibuat tabel user_range yang menggunakan primary key biasa tanpa konfigurasi pembagian tablet tambahan. Tabel ini digunakan sebagai contoh tabel yang menyimpan data secara sederhana sehingga dapat dibandingkan dengan tabel yang menggunakan mekanisme sharding.<br>

Jika ingin langsung membagi menjadi beberapa shards. gunakan SPLIT pada saat membuat table:<br>
<p align="center">
<img width="826" height="183" alt="image" src="https://github.com/user-attachments/assets/616a1c15-b862-450c-8aaf-76310e694ce5" /><br>

Pada tahap ini dibuat tabel users menggunakan perintah SPLIT AT VALUES ((3), (6), (9)). Konfigurasi ini menyebabkan YugabyteDB membagi data ke dalam beberapa tablet berdasarkan rentang nilai primary key. Dengan demikian data dapat didistribusikan ke beberapa shard sehingga meningkatkan kemampuan pengelolaan data dalam lingkungan terdistribusi.<br>

Berikut adalah perintah untuk melihat jumlah tablets:<br>
<p align="center">
<img width="940" height="834" alt="image" src="https://github.com/user-attachments/assets/e402e2db-336e-47d3-ad26-8fbc45ebbac6" /><br>

Perintah yb_table_properties() digunakan untuk melihat jumlah tablet yang dimiliki oleh masing-masing tabel. Hasil menunjukkan bahwa tabel user_range hanya memiliki satu tablet, sedangkan tabel users memiliki empat tablet karena menggunakan konfigurasi SPLIT AT VALUES. Hal ini menunjukkan bahwa proses sharding berhasil dilakukan.<br>

untuk setiap query berikut :<br>
<p align="center">
<img width="940" height="558" alt="image" src="https://github.com/user-attachments/assets/bd18a94e-d55d-4813-bf86-a4e8fd877dfc" /><br>

Perintah ini digunakan untuk melihat cara YugabyteDB mengeksekusi query yang mengambil seluruh data pada tabel. Hasil EXPLAIN menunjukkan bahwa sistem membaca seluruh baris yang terdapat pada tabel<br>
Kesimpulannya : Data yang dibaca adalah seluruh baris yang terdapat pada tabel.<br>

<p align="center">
<img width="940" height="535" alt="image" src="https://github.com/user-attachments/assets/0cdc617f-cc73-4219-a22d-0a6abf3a373c" /><br>

Perintah ini digunakan untuk melihat proses pencarian data berdasarkan nilai primary key tertentu. Karena menggunakan primary key, YugabyteDB dapat langsung menemukan lokasi data yang dicari tanpa melakukan pembacaan seluruh isi tabel sehingga proses pencarian menjadi lebih cepat dan efisien<br>
kesimpulannya : Data yang dibaca hanya satu baris sesuai dengan kondisi query.<br>

<p align="center">
<img width="940" height="468" alt="image" src="https://github.com/user-attachments/assets/66a08cf9-d9c5-4561-a80f-6c1a57d6109b" /><br>
                                 
Pada query ini sistem melakukan pencarian berdasarkan rentang nilai primary key. YugabyteDB hanya membaca data yang sesuai dengan kondisi yang diberikan sehingga proses akses data menjadi lebih efisien dibandingkan membaca seluruh tabel.<br>
kesimpulannya : Data yang dibaca hanya baris yang memenuhi kondisi rentang nilai yang ditentukan.<br>

Untuk tabel yang di-split menjadi beberapa tablet, waktu eksekusi akan lebih cepat untuk query yang sudah diketahui berdasarkan kolom tertentu dan split dilakukan berdasarkan kolom tersebut:<br>
<p align="center">
<img width="940" height="544" alt="image" src="https://github.com/user-attachments/assets/3672af31-95d9-47f6-b6f9-79b07e6b9a88" /><br>

Perintah ini digunakan untuk melihat proses pencarian data berdasarkan nilai primary key tertentu. Karena menggunakan primary key, YugabyteDB dapat langsung menemukan lokasi data yang dicari tanpa melakukan pembacaan seluruh isi tabel sehingga proses pencarian menjadi lebih cepat dan efisien.<br>

**Hash Sharding**<br>
Hash sharding tidak sesuai untuk hasil pembacaan berupa range.<br>

Membuat Tabel user_hash<br>
<p align="center">
<img width="940" height="370" alt="image" src="https://github.com/user-attachments/assets/2c624fa1-0e51-480c-b059-48bf644f0846" /><br>

Pada tahap ini dibuat tabel user_hash yang menggunakan hash sharding pada primary key. Mekanisme hash sharding akan mendistribusikan data ke beberapa tablet berdasarkan hasil perhitungan hash sehingga distribusi data menjadi lebih merata.<br>

EXPLAIN Query Seluruh Data pada user_hash<br>
<p align="center">
<img width="940" height="553" alt="image" src="https://github.com/user-attachments/assets/d51d737c-50bf-49d8-9cc3-cd56d14197b0" /><br>

Perintah ini digunakan untuk melihat proses pengambilan seluruh data pada tabel yang menggunakan hash sharding. Karena data tersebar pada beberapa tablet, YugabyteDB akan melakukan pembacaan pada seluruh tablet yang terkait untuk memperoleh seluruh data yang tersedia.<br>
kesimpulannya : Data yang dibaca adalah seluruh baris yang terdapat pada tabel

EXPLAIN Query Satu Baris pada user_hash<br> 
<p align="center">
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/3a75dc2f-d8d6-42e3-b4aa-463b8e544327" /><br>

Perintah ini digunakan untuk melihat proses pencarian data berdasarkan nilai primary key tertentu. Karena menggunakan primary key, YugabyteDB dapat langsung menemukan lokasi data yang dicari tanpa melakukan pembacaan seluruh isi tabel sehingga proses pencarian menjadi lebih cepat dan efisien.<br>
kesimpulannya : Data yang dibaca hanya satu baris sesuai dengan kondisi query.<br>

EXPLAIN Query rentang data<br>
<p align="center">
<img width="940" height="448" alt="image" src="https://github.com/user-attachments/assets/1b5785b0-af8c-4a85-924a-fa1b6cfdf6a9" /><br>
  
Pada query ini sistem melakukan pencarian berdasarkan rentang nilai primary key. YugabyteDB hanya membaca data yang sesuai dengan kondisi yang diberikan sehingga proses akses data menjadi lebih efisien dibandingkan membaca seluruh tabel.<br>
kesimpulannya : Data yang dibaca hanya baris yang memenuhi kondisi rentang nilai yang ditentukan.<br>


**4. Shutdown YugabyteDB**<br>
Untuk men-shutdown YugabyteDB, gunakan parameter lokasi base_dir:<br>
<img width="940" height="177" alt="image" src="https://github.com/user-attachments/assets/4fbe0d31-7b3a-44a0-bc97-f33726e52bba" /><br>

Pada tahap akhir dilakukan penghentian layanan YugabyteDB menggunakan perintah yugabyted stop. Langkah ini memastikan seluruh node berhenti dengan aman setelah praktikum selesai.<br>

