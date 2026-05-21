<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert09</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Arsitektur Microservices untuk Sistem Terdistribusi: GraphQL dan gRPC</h3>

**0. Pengantar**<br>
   1. Database yang digunakan adalah database yang telah dibuat pada pertemuan 8 (departemen-sdm.db).<br>
   2. Software uv telah terinstall dan penggunaannya telah dipahami. Lihat ke https://github.com/NEO-X-School/notes/blob/main/uv/00.md untuk panduan praktis.<br>
   3. Instalasi Python menggunakan uv - Python 3.14.5:<br>
      <p align="center">
        <img width="940" height="681" alt="image" src="https://github.com/user-attachments/assets/5df6815d-1447-41df-aaee-6e2c65a83194" /><br>

      Urutan Direktori :<br>
      <p align="center">
         <img width="450" height="771" alt="image" src="https://github.com/user-attachments/assets/70615100-5d8f-4b93-badd-d9c7764af0d4" /><br>

   
**1. GraphQL**<br>
   **1.1 GraphQL Server**<br>
   Untuk membangun server GraphQL di Python, kita bisa menggunakan salah satu pustaka di Python,   yaitu Strawberry (https://strawberry.rocks/). Berikut adalah source code untuk server:<br>

 <p align="center">
   <img width="940" height="880" alt="image" src="https://github.com/user-attachments/assets/c28659f1-fe30-4cbd-a9ca-bd3677448a3c" /><br>

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

    Untuk keperluan praktikum ini, berikut adalah file service.proto:<br>
    <img width="670" height="968" alt="image" src="https://github.com/user-attachments/assets/67922794-3825-48ad-8eb9-d82597c28238" /><br>

    Kompilasi service.proto tersebut (perhatikan ada titik yang berarti current directory):
    <p align="center">
       <img width="940" height="28" alt="image" src="https://github.com/user-attachments/assets/e4183571-5bde-4ee2-bc28-eae63d2584af" />

     Hasilnya adalah 2 file sebagai berikut: 
     <img width="771" height="88" alt="image" src="https://github.com/user-attachments/assets/2451560a-ac98-4f19-b0a2-42b454c860c1" />



    


   
   
**2. gRPC**
   **2.1 gRPC Server**
   **2.2 gRPC Client**

**3. Tugas**
