<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert09</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Arsitektur Microservices untuk Sistem Terdistribusi: GraphQL dan gRPC</h3>

**0. Pengantar**<br>
   1. Database yang digunakan adalah database yang telah dibuat pada pertemuan 8 (departemen-sdm.db).<br>
   2. Software uv telah terinstall dan penggunaannya telah dipahami. Lihat ke https://github.com/NEO-X-School/notes/blob/main/uv/00.md untuk panduan praktis.<br>
   3. Instalasi Python menggunakan uv - Python 3.14.5:<br>
      <p align="center">
        <img width="740" height="681" alt="image" src="https://github.com/user-attachments/assets/5df6815d-1447-41df-aaee-6e2c65a83194" /><br>

      Urutan Direktori :<br>
      <p align="center">
         <img width="300" height="771" alt="image" src="https://github.com/user-attachments/assets/70615100-5d8f-4b93-badd-d9c7764af0d4" /><br>

   
**1. GraphQL**<br>
   **1.1 GraphQL Server**<br>
   Untuk membangun server GraphQL di Python, kita bisa menggunakan salah satu pustaka di Python,   yaitu Strawberry (https://strawberry.rocks/). Berikut adalah source code untuk server:<br>

 <p align="center">
   <img width="640" height="880" alt="image" src="https://github.com/user-attachments/assets/c28659f1-fe30-4cbd-a9ca-bd3677448a3c" /><br>

   untuk menjalankan :<br>
   <p align="center">
      <img width="576" height="59" alt="image" src="https://github.com/user-attachments/assets/20569606-d9c0-40d9-b102-a136350587a8" /><br>

   Untuk menguji, kita bisa mengakses GraphQL Explorer dengan menggunakan browser pada URL http://localhost:8000/graphql (lihat di atas):<br>
  <p align="center"> 
    <img width="858" height="514" alt="image" src="https://github.com/user-attachments/assets/1b5cd5f8-a724-412b-9b01-eecd2a299f1a" /><br>

    Pada sisi sebelah kiri, kita bisa menuliskan query GraphQL sesuai dengan resources yang telah kita definisikan. Tombol berikut:<br>
    <img width="52" height="42" alt="image" src="https://github.com/user-attachments/assets/e56b8e30-7b60-48c0-9f34-92c7a3ca3ff7" /><br>

    digunakan untuk menjalankan query GraphQL yang telah kita tulis di sisi sebelah kiri dan menampilkan hasilnya di sebelah kanan:<br>
    <p align="center">
      <img width="940" height="542" alt="image" src="https://github.com/user-attachments/assets/ffa54e82-7341-489b-bfe4-296164d1d58e" /><br>

   **1.2 GraphQL Client**
   Selain menggunakan GraphQL Explorer, developer juga bisa menggunakan script / source code untuk mengakses data yang ada pada server tersebut. Untuk keperluan tersebut, digunakan pustaka GraphQL client. Pustaka yang digunakan di sini adalah gql (https://github.com/graphql-python/gql). Install dengan menggunakan requirements.txt. Source code:<br>
   <p align="center">
     <img width="940" height="959" alt="image" src="https://github.com/user-attachments/assets/3b29d0ce-e124-47ba-85d6-ce12e932b73a" /><br>

    Jalankan dengan cara sebagai berikut:<br>
    <p align="center">
       <img width="940" height="120" alt="image" src="https://github.com/user-attachments/assets/bf51c776-1062-4ceb-b486-504ed221f3ca" /><br>
   
**2. gRPC**
  Untuk keperluan praktikum ini, berikut adalah file service.proto:<br>
    <img width="670" height="968" alt="image" src="https://github.com/user-attachments/assets/67922794-3825-48ad-8eb9-d82597c28238" /><br>

    Kompilasi service.proto tersebut (perhatikan ada titik yang berarti current directory):<br>
    <p align="center">
       <img width="940" height="28" alt="image" src="https://github.com/user-attachments/assets/e4183571-5bde-4ee2-bc28-eae63d2584af" /><br>

     Hasilnya adalah 2 file sebagai berikut: <br>
     <img width="771" height="88" alt="image" src="https://github.com/user-attachments/assets/2451560a-ac98-4f19-b0a2-42b454c860c1" /><br>

   **2.1 gRPC Server**
Source code untuk mengakses data di SQLite dan kemudian menserialisasikan hasilnya ke dalam protocol buffers untuk diakses oleh gRPC client adalah sebagai berikut:<br>
    <p align="center">
    <img width="921" height="1158" alt="image" src="https://github.com/user-attachments/assets/72cb1c8f-b490-4f6c-a70b-4b14cf3f2cf8" />
<img width="921" height="1158" alt="image" src="https://github.com/user-attachments/assets/a17cfd44-390b-4d9a-a388-7018180a6e4f" />

Jalankan dengan perintah berikut:
   <p align="center">
      <img width="545" height="83" alt="image" src="https://github.com/user-attachments/assets/fb047183-f0e7-4389-9017-b3dbbfda5113" />



   **2.2 gRPC Client**
   Source code untuk mengirimkan request untuk mengambil data SDM dengan id tertentu adalah sebagai berikut:
<p align="center">
   <img width="940" height="1054" alt="image" src="https://github.com/user-attachments/assets/83335620-b666-4451-af6a-7128a44fd862" />

   Pada source code tersebut, kita mengirimkan 2 requests: 1 untuk request dengan id yang benar-benar ada (1) dan 1 untuk request dengan id yang benar-benar tidak ada (10000). Jika dijalankan, hasilnya:
<p align="center">
   <img width="578" height="140" alt="image" src="https://github.com/user-attachments/assets/8018bbe1-c5a9-4b35-8938-5de35a9e51d2" />



**3. Tugas**
1. Dengan menggunakan file SQLite pada tugas kemarin (tabel yang mempunyai 1 primary key dan setidaknya berisi data dengan tipe INT, CHAR, VARCHAR, BOOLEAN, dan FLOAT), buat GraphQL endpoint untuk tabel tersebut dan berikan contoh akses client untuk mengambil semua data.<br>
langkah-langkahnya :<br>
-isi file tugas.py<br>
<p align="center">
  <img width="700" height="894" alt="image" src="https://github.com/user-attachments/assets/50709f62-541c-4508-99f2-c68a42cba580" /><br>

<p align="center">
   <img width="700" height="894" alt="image" src="https://github.com/user-attachments/assets/edea405d-a7ea-43f1-84ea-1fadf1718add" /><br>
   
File tugas.py digunakan untuk membuat GraphQL endpoint dan mengambil data produk dari database SQLite toko.db.<br>

- Hasil Menjalankan uvicorn<br>
<p align="center">
  <img width="600" height="206" alt="image" src="https://github.com/user-attachments/assets/d3805933-4f3a-4b5c-8f55-b3f58ac4929b" /><br>

Hasil tersebut menunjukkan bahwa GraphQL server berhasil dijalankan dan siap menerima query dari client.<br>

-Hasil Query pada Strawberry/GraphQL<br>
<p align="center">
   <img width="840" height="498" alt="image" src="https://github.com/user-attachments/assets/3398c1fb-5853-4e60-9c7f-1aa331e54d37" /><br>
   Hasil query menunjukkan bahwa GraphQL berhasil mengambil seluruh data produk dari tabel produk pada database SQLite.<br>


2. Dengan menggunakan file SQLite pada tugas kemarin (tabel yang mempunyai 1 primary key dan setidaknya berisi data dengan tipe INT, CHAR, VARCHAR, BOOLEAN, dan FLOAT), buat service.proto untuk semua data tersebut, kompilasi, buat gRPC servernya dan kemudian berikan contoh gRPC client untuk mengambil salah satu data.<br>
langkah-langkahnya :<br>
- Membuat Folder gRPC<br>
<p align="center">
  <img width="360" height="91" alt="image" src="https://github.com/user-attachments/assets/49a0d3e1-7b89-40b7-9e23-df6ffa3fb9dc" /><br>

Perintah ini digunakan untuk membuat folder server dan client. Folder server digunakan untuk menyimpan program gRPC server, sedangkan folder client digunakan untuk menyimpan program client yang akan meminta data ke server.<br>

- Masuk ke Folder Server<br>
<p align="center">
  <img width="300" height="45" alt="image" src="https://github.com/user-attachments/assets/d60d6543-3a47-4dfa-bf65-06e13230333f" /><br>

Masuk ke folder server agar semua file dan package gRPC server dibuat di lokasi tersebut.<br>

- Copy Database SQLite<br>
<p align="center">
  <img width="400" height="53" alt="image" src="https://github.com/user-attachments/assets/a6973d88-15f5-4cf6-a992-bcf8c1ee6262" /><br>
  
Database toko.db dari praktikum sebelumnya disalin ke folder server agar server gRPC dapat membaca data produk dari database tersebut.<br>

- isi file service proto<br>
<p align="center">
  <img width="556" height="472" alt="image" src="https://github.com/user-attachments/assets/44dad2ea-969d-49f0-9077-f37b9a5a66c2" /><br>

File service.proto digunakan untuk mendefinisikan service gRPC, request, dan response yang akan dipakai antara server dan client. Pada tugas ini dibuat method GetProduk untuk mengambil data produk berdasarkan ID.<br>

- kompilasi File Proto<br>
<p align="center">
  <img width="755" height="57" alt="image" src="https://github.com/user-attachments/assets/b029a769-89c8-421f-91a2-1894dc32f6f5" /><br>

Perintah ini digunakan untuk mengubah file service.proto menjadi file Python otomatis yang nantinya digunakan oleh server dan client gRPC.<br>

- Mengecek Hasil kompilasi<br>
<p align="center"> 
  <img width="682" height="88" alt="image" src="https://github.com/user-attachments/assets/517d3c92-bdfd-40db-a02b-30b658be5df0" /><br>

  File service_pb2.py dan service_pb2_grpc.py merupakan file hasil compile proto yang berfungsi untuk komunikasi data antara server dan client.<br>
  
- isi file server.py<br>
<p align="center">
  <img width="578" height="776" alt="image" src="https://github.com/user-attachments/assets/dcb0cd99-cb8c-49a7-afb7-dfb6d4ea64d1" /><br>

File server.py digunakan untuk membuat server gRPC. Server akan membaca data produk dari database toko.db berdasarkan ID yang diminta client, lalu mengirimkan hasilnya kembali ke client.<br>

- Menjalankan gRPC Server<br>
<p align="center">
   <img width="502" height="57" alt="image" src="https://github.com/user-attachments/assets/42274f00-7517-4cb7-9ee2-397fb58c1c20" /><br>

Perintah ini digunakan untuk menjalankan server gRPC pada port 50051 agar dapat menerima request dari client.<br>

- Masuk ke Folder Client<br>
<p align="center">
   <img width="407" height="58" alt="image" src="https://github.com/user-attachments/assets/959b06c4-ad0b-40fd-82d5-50e9e730e850" /><br>

Masuk ke folder client untuk membuat program client gRPC.<br>

-  Copy File Hasil Compile Proto<br>
<p align="center">
  <img width="457" height="70" alt="image" src="https://github.com/user-attachments/assets/65bad139-9039-483b-8149-7232ba0238e9" /><br>

File hasil compile dari server disalin ke client agar client dapat menggunakan struktur request dan response yang sama dengan server.<br>

-  isi file client.py<br>
<p align="center">
  <img width="587" height="287" alt="image" src="https://github.com/user-attachments/assets/abd74e47-6489-46af-b864-8f07b4b6c4ea" /><br>

File client.py digunakan untuk membuat client gRPC yang mengirim request ke server untuk mengambil data produk berdasarkan ID.<br>

- Menjalankan gRPC Client<br>
<p align="center">
  <img width="517" height="175" alt="image" src="https://github.com/user-attachments/assets/c5ea6794-919b-4a2b-9007-6e22a472348e" /><br>

Hasil tersebut menunjukkan bahwa client berhasil mengambil salah satu data produk dari database SQLite melalui gRPC server.<br>

