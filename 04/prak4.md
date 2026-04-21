<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert04</h1>
<h3>Nama : Febiana Serao Da Cruz</h3>
<h3>NIM: 235410032</h3>

**4.1 treaming Replication Menggunakan PostgreSQL**<br>
**Menjalankan docker-compose**<br>
<p align="center">
  <img width="600" height="175" alt="image" src="https://github.com/user-attachments/assets/275a8abe-998c-473e-8ebc-64ef450d3635" />
Pada bagian ini dilakukan proses menjalankan container menggunakan Docker. Container ini berisi database PostgreSQL yang akan digunakan sebagai primary dan replica. Tahapan ini penting karena menjadi dasar untuk melakukan replikasi data.<br>


**Pemeriksaan container**<br>
<p align="center">
  <img width="600" height="89" alt="image" src="https://github.com/user-attachments/assets/631c2e87-6ae2-4793-a51f-b0fb170f9ad1" /><br>

Setelah container dijalankan, dilakukan pengecekan menggunakan perintah docker ps untuk memastikan semua container sudah berjalan dengan status healthy. Ini menandakan bahwa sistem sudah siap digunakan untuk tahap berikutnya.<br>

**Pengujian**<br>
<img width="600" height="269" alt="image" src="https://github.com/user-attachments/assets/2edcea86-a64f-4716-9e02-076a770e07d8" />
Pada bagian ini dilakukan koneksi ke database menggunakan psql. Kemudian digunakan perintah \x untuk mengubah tampilan hasil query menjadi lebih rapi, sehingga data lebih mudah dibaca saat ditampilkan.

<img width="600" height="173" alt="image" src="https://github.com/user-attachments/assets/3ba37e25-83f6-436a-9dc4-c52c4c40cd4a" />
Hasil t menunjukkan bahwa server tersebut berada dalam kondisi replica<br>

**sebelum pembuatan tabel**<br>
<img width="600" height="118" alt="image" src="https://github.com/user-attachments/assets/cd11a78e-8f67-4c4d-9930-61a84f7c5da6" />


**Manipulasi data pada primary**<br>
pada bagian ini dilakukan pembuatan tabel mahasiswa di server primary. Tabel ini digunakan untuk pengujian replikasi data antar server.
<img width="750" height="475" alt="image" src="https://github.com/user-attachments/assets/c600046c-bd0f-484f-8a47-6cd99ead5c4b" /><br>
Data yang sudah dimasukkan kemudian dicek menggunakan SELECT * FROM mahasiswa; dan hasilnya berhasil tampil sesuai input.<br>


Secara otomatis, manipulasi data tersebut akan direplikasi ke server replica:<br>
<img width="600" height="223" alt="image" src="https://github.com/user-attachments/assets/57b42315-0871-4337-bbbf-bc5c2a881bef" />


**High-Availability**<br>

Setelah diketahui bahwa primary server dalam kondisi down, maka kita bisa mempromosikan salah satu replica server untuk menjadi primary - dari kondisi hanya bisa menyediakan akses read menjadi primary server yang bisa menyediakan akses read-write. Berikut adalah perintah pg_promote() untuk mempromosikan replica menjadi primary:<br>

<img width="550" height="575" alt="image" src="https://github.com/user-attachments/assets/7fb543ab-bb8b-48f5-983e-da49ef99ea0c" />

mematikan semua primary dan replika :<br>
<img width="600" height="244" alt="image" src="https://github.com/user-attachments/assets/25bac90f-8a43-4974-bc05-55bc90b6d6a1" />


**4.2 Replikasi Master-Master Menggunakan Apache Ignite**<br>
**menjalankan docker compose**<br>
<img width="600" height="190" alt="image" src="https://github.com/user-attachments/assets/a5220eff-8e03-47e6-a469-d2ea55dd97f7" />

**setelah Setelah proses pull selesai dan docker-compose telah up, maka akan muncul sebagai berikut:**<br>
<img width="600" height="109" alt="image" src="https://github.com/user-attachments/assets/c1b89074-399a-419d-9d8b-f2549e00bb39" />

**Inisialisasi cluster**<br>
<img width="600" height="394" alt="image" src="https://github.com/user-attachments/assets/26f97f96-0780-42a5-a1d3-cb56f07fa6e5" />
Pada bagian ini mulai menjalankan container Apache Ignite sebagai database terdistribusi.

**eksekusi perintah-perintah sql**<br>
<img width="600" height="625" alt="image" src="https://github.com/user-attachments/assets/62363f15-b6ab-4255-8aa7-015dc2fc5096" /><br>

<img width="600" height="976" alt="image" src="https://github.com/user-attachments/assets/ea94615c-8a3b-4cc2-855b-70ef63b204ce" />



Masuk ke mode SQL dan berikan perintah SQL:<br>
<img width="600" height="474" alt="image" src="https://github.com/user-attachments/assets/17751bee-1d15-4a92-b609-1224905206f8" />


Untuk memeriksa apakah perubahan pada http://localhost:10300 tersebut telah dipropagasi ke node-node lainnya, kita bisa memeriksa dengan melakukan koneksi ke node-node lainnya. Berikut adalah node di http://localhost:10301:<br>
<img width="600" height="478" alt="image" src="https://github.com/user-attachments/assets/aa10be7a-0281-4bbe-9ab1-8ac09759f48a" /><br>

Dari posisi tersebut, kita bisa melihat bahwa 10301 juga telah berisi data seperti tadi yang telah diisikan pada 10300.<br>
 

query untuk analytics:<br>
<img width="600" height="868" alt="image" src="https://github.com/user-attachments/assets/cb23782e-bf01-474f-9769-528c1dd09dbd" />

pemeriksaan http://localhost:10302:<br>
<img width="600" height="616" alt="image" src="https://github.com/user-attachments/assets/fbafe658-4a68-4c9e-a6b4-8926bd7d6469" /><br>

Node ini ternyata juga telah berisi data. Dengan demikian kita bisa melihat bahwa telah terjadi replikasi Master-Master pada cluster Apache Ignite 3.1.0.<br>











