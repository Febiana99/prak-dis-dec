<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert09</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Data Terdistribusi</h3>

**1. Instalasi**<br>
**Ekstraksi**<br>
<p align="center">
   <img width="840" height="221" alt="image" src="https://github.com/user-attachments/assets/f7dcb66e-022b-40f2-8059-e6eb712926b5" />

**Buat symlink**<br>
  <p align="center">
<img width="840" height="590" alt="image" src="https://github.com/user-attachments/assets/f8ee6afa-b1b0-4ed2-a035-82f77b2b64d6" />


**Kerjakan post_install.sh**<br>
  <p align="center">
<img width="840" height="828" alt="image" src="https://github.com/user-attachments/assets/552222bc-8803-4016-a399-8a4f28a30257" />


**Buat file untuk env variables**<br>
<img width="840" height="71" alt="image" src="https://github.com/user-attachments/assets/f9ea3486-021f-49db-9f33-608098337217" />


**Source saat akan menggunakan pada shell tersebut**
  <p align="center">
<img width="840" height="495" alt="image" src="https://github.com/user-attachments/assets/8db8ef92-77b3-431e-8768-16ec6fec83a3" />



**2. Buat Kluster**<br>
**Node 1**
  <p align="center">
<img width="840" height="420" alt="image" src="https://github.com/user-attachments/assets/438ff68c-c895-4da9-b665-b3dc2194ac92" /><br>

Status :<br>
  <p align="center">
<img width="840" height="270" alt="image" src="https://github.com/user-attachments/assets/efc8e4d1-7ed6-4d72-a329-50366ed187d1" />

**Node 2**<br>
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/fc24beb1-6141-409e-83b9-db616de8bf30" />

Status :
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/4f693061-34e7-4335-9343-871098e9c00d" />


**Node 3**<br>
  <p align="center">
<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/11bcd42d-f041-4d01-a876-255090a3edb9" />

Status :<br>
  <p align="center">
<img width="840" height="250" alt="image" src="https://github.com/user-attachments/assets/03de09be-f93c-4957-bdb8-2aed2c716f42" />



**Atur data_placement dengan penempatan utama di node 1:**<br>
  <p align="center">
<img width="840" height="200" alt="image" src="https://github.com/user-attachments/assets/6aff0bc8-04ef-47ae-b01d-11430049eca8" />

Setelah mengaktifkan 3 nodes tersebut, UI berupa web tersedia di http://localhost:15433 sebagai berikut:<br>
  <p align="center">
<img width="840" height="400" alt="image" src="https://github.com/user-attachments/assets/f56acbec-b208-4e0c-b6ce-96a32c66dc74" />


**3. Sharding**<br>
**Range Sharding**<br>
Range sharding secara default akan membentuk hanya 1 tablet untuk 1 tabel:<br>
<p align="center">
<img width="940" height="433" alt="image" src="https://github.com/user-attachments/assets/3f7911db-6113-4c73-b663-29e1d9cf9d13" />

Jika ingin langsung membagi menjadi beberapa shards. gunakan SPLIT pada saat membuat table:<br>
<p align="center">
<img width="826" height="183" alt="image" src="https://github.com/user-attachments/assets/616a1c15-b862-450c-8aaf-76310e694ce5" /><br>

Berikut adalah perintah untuk melihat jumlah tablets:<br>
<p align="center">
<img width="940" height="834" alt="image" src="https://github.com/user-attachments/assets/e402e2db-336e-47d3-ad26-8fbc45ebbac6" /><br>

untuk setiap query berikut :<br>
<p align="center">
<img width="940" height="558" alt="image" src="https://github.com/user-attachments/assets/bd18a94e-d55d-4813-bf86-a4e8fd877dfc" /><br>

<p align="center">
<img width="940" height="535" alt="image" src="https://github.com/user-attachments/assets/0cdc617f-cc73-4219-a22d-0a6abf3a373c" /><br>

<p align="center">
<img width="940" height="468" alt="image" src="https://github.com/user-attachments/assets/66a08cf9-d9c5-4561-a80f-6c1a57d6109b" /><br

Untuk tabel yang di-split menjadi beberapa tablet, waktu eksekusi akan lebih cepat untuk query yang sudah diketahui berdasarkan kolom tertentu dan split dilakukan berdasarkan kolom tersebut:<br>
<p align="center">
<img width="940" height="544" alt="image" src="https://github.com/user-attachments/assets/3672af31-95d9-47f6-b6f9-79b07e6b9a88" /><br>


**Hash Sharding**<br>
Hash sharding tidak sesuai untuk hasil pembacaan berupa range.<br>
<p align="center">
<img width="940" height="370" alt="image" src="https://github.com/user-attachments/assets/2c624fa1-0e51-480c-b059-48bf644f0846" />

<p align="center">
<img width="940" height="553" alt="image" src="https://github.com/user-attachments/assets/d51d737c-50bf-49d8-9cc3-cd56d14197b0" /><br>

<p align="center">
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/3a75dc2f-d8d6-42e3-b4aa-463b8e544327" /><br>

<p align="center">
<img width="940" height="448" alt="image" src="https://github.com/user-attachments/assets/1b5785b0-af8c-4a85-924a-fa1b6cfdf6a9" /><br>

**4. Shutdown YugabyteDB**<br>
Untuk men-shutdown YugabyteDB, gunakan parameter lokasi base_dir:<br>
<img width="940" height="177" alt="image" src="https://github.com/user-attachments/assets/4fbe0d31-7b3a-44a0-bc97-f33726e52bba" />


