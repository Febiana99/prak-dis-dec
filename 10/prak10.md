<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert09</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Data Terdistribusi</h3>

**1. Instalasi**<br>
**Ekstraksi**<br>

<img width="940" height="241" alt="image" src="https://github.com/user-attachments/assets/f7dcb66e-022b-40f2-8059-e6eb712926b5" />

**Buat symlink**<br>
<img width="940" height="622" alt="image" src="https://github.com/user-attachments/assets/f8ee6afa-b1b0-4ed2-a035-82f77b2b64d6" />


**Kerjakan post_install.sh**<br>
<img width="940" height="928" alt="image" src="https://github.com/user-attachments/assets/552222bc-8803-4016-a399-8a4f28a30257" />


**Buat file untuk env variables**<br>
<img width="940" height="71" alt="image" src="https://github.com/user-attachments/assets/f9ea3486-021f-49db-9f33-608098337217" />


**Source saat akan menggunakan pada shell tersebut**
<img width="940" height="495" alt="image" src="https://github.com/user-attachments/assets/8db8ef92-77b3-431e-8768-16ec6fec83a3" />



**2. Buat Kluster**<br>
**Node 1**
<img width="940" height="429" alt="image" src="https://github.com/user-attachments/assets/438ff68c-c895-4da9-b665-b3dc2194ac92" /><br>

Status :<br>
<img width="940" height="270" alt="image" src="https://github.com/user-attachments/assets/efc8e4d1-7ed6-4d72-a329-50366ed187d1" />

**Node 2**<br>
<img width="940" height="444" alt="image" src="https://github.com/user-attachments/assets/fc24beb1-6141-409e-83b9-db616de8bf30" />

Status :
<img width="940" height="444" alt="image" src="https://github.com/user-attachments/assets/4f693061-34e7-4335-9343-871098e9c00d" />


**Node 3**<br>
<img width="940" height="444" alt="image" src="https://github.com/user-attachments/assets/11bcd42d-f041-4d01-a876-255090a3edb9" />

Status :<br>
<img width="940" height="271" alt="image" src="https://github.com/user-attachments/assets/03de09be-f93c-4957-bdb8-2aed2c716f42" />



**Atur data_placement dengan penempatan utama di node 1:**<br>
<img width="940" height="200" alt="image" src="https://github.com/user-attachments/assets/6aff0bc8-04ef-47ae-b01d-11430049eca8" />

Setelah mengaktifkan 3 nodes tersebut, UI berupa web tersedia di http://localhost:15433 sebagai berikut:<br>
<img width="940" height="479" alt="image" src="https://github.com/user-attachments/assets/f56acbec-b208-4e0c-b6ce-96a32c66dc74" />


**3. Sharding**<br>
**Range Sharding**
**Hash Sharding**

**4. Shutdown YugabyteDB**<br>
Untuk men-shutdown YugabyteDB, gunakan parameter lokasi base_dir:<br>
<img width="940" height="177" alt="image" src="https://github.com/user-attachments/assets/4fbe0d31-7b3a-44a0-bc97-f33726e52bba" />


