<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert07</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Cloud Computing</h3>

**1. Membuat env Python 3.14.4**<br>
 <p align="center">
   <img width="710" height="378" alt="image" src="https://github.com/user-attachments/assets/a04c0a5d-6416-4dec-97d0-d6e7c49ed9ea" /><br>

pembahasan :<br>
Perintah ls -la digunakan untuk menampilkan seluruh file dan folder termasuk file tersembunyi seperti .venv. Dari hasil ini dapat dipastikan bahwa virtual environment berhasil dibuat karena folder .venv muncul di direktori project.<br>
   
**2. Install Paket yang Diperlukan**<br>
 <p align="center">
   <img width="828" height="320" alt="image" src="https://github.com/user-attachments/assets/b73e1bd1-00e2-4c7f-9bdf-42d850511494" /><br>

pembahasan :<br>
Perintah uv pip install -e . digunakan untuk menginstall seluruh dependency project berdasarkan file konfigurasi. Opsi -e berarti editable mode sehingga project tetap terhubung dengan source code asli dan perubahan kode dapat langsung digunakan.<br>

menjalankan aplikasi tersebut setelah inisialisasi database :<br>
<p align="center">
    <img width="669" height="259" alt="image" src="https://github.com/user-attachments/assets/a31ce4f5-9bf0-4cb8-b6ea-843c27bd7c20" /><br>

pembahasan :<br>
Perintah flask --app flaskr init-db digunakan untuk membuat database awal aplikasi Flask yang berfungsi menyimpan data pengguna, autentikasi, dan post blog. 
Sedangkan perintah flask --app flaskr run menjalankan aplikasi Flask secara lokal pada 127.0.0.1:5000 sehingga aplikasi dapat diuji melalui browser dengan fitur register dan login.<br>

hasil saat aplikasi berjalan di browser :<br>
<p align="center">
    <img width="808" height="249" alt="image" src="https://github.com/user-attachments/assets/3f5b43f2-934c-4b96-bcd9-fc584178254f" /><br>


hasil saat mencoba aplikasinya :<br>
- Register
<p align="center">
  <img width="779" height="289" alt="image" src="https://github.com/user-attachments/assets/231b4fec-a4c8-428b-8645-0b6051e822af" /><br>

  
- Login<br>
<p align="center">
  <img width="731" height="379" alt="image" src="https://github.com/user-attachments/assets/948512e3-1fb7-4119-87a1-046fcf7e7311" /><br>

  
Tampilan setelah Login<br>
<p align="center">
    <img width="940" height="273" alt="image" src="https://github.com/user-attachments/assets/6f268abd-01a6-4339-b18d-90fa6887e6f0" /><br>

3. Buat Aplikasi Menjadi CA - Docker<br>
   file utk build docker: Dockerfile. File diletakkan di direktori root dari aplikasi. Isinya adalah sebagai berikut:<br>
 <p align="center">  
   <img width="823" height="243" alt="image" src="https://github.com/user-attachments/assets/c380a605-d18b-4fda-96a0-3732eff2461f" /><br>

pembahasan :<br>
Kode Dockerfile ini digunakan untuk mengubah aplikasi Flask menjadi container dengan Python 3.14 sebagai dasar, membuat direktori kerja /app, menyalin seluruh project ke dalam container, menginstall dependency, menginisialisasi database, membuka port 5000, dan menjalankan aplikasi Flask agar dapat diakses melalui browser.<br>

Membuat Image :<br>
<p align="center">
    <img width="940" height="680" alt="image" src="https://github.com/user-attachments/assets/7acc8d76-11e1-411e-9db6-5a99f6ebc50a" /><br>
 
pembahasan :<br>
Perintah ini digunakan untuk membangun Docker image berdasarkan Dockerfile. Nama image diberikan flaskr:1.0.0 sebagai identitas versi aplikasi container.<br>

image telah berhasil dibuat :<br>
<p align="center">
  <img width="891" height="201" alt="image" src="https://github.com/user-attachments/assets/edcb7ea9-53bb-4319-9cad-4e424dde857a" /><br>

pembahasan :<br>
Perintah docker images digunakan untuk menampilkan seluruh image yang tersedia pada sistem dan memastikan image flaskr:1.0.0 berhasil dibuat.<br>

   
4. Menjalankan Image<br>
   Jalankan dengan memetakan port 5000 pada aplikasi di container ke port 5001 di localhost:<br>
<p align="center">
   <img width="940" height="192" alt="image" src="https://github.com/user-attachments/assets/f79ab71d-cbd5-4524-b111-3f3343e06c3a" /><br>

pembahasan :<br>
Perintah docker run -p 5001:5000 flaskr:1.0.0 menjalankan container dari image flaskr:1.0.0. Port 5001 pada localhost dipetakan ke port 5000 pada container sehingga aplikasi dapat diakses melalui browser pada localhost:5001.<br>

   akses web browser :<br>
<p align="center">   
   <img width="940" height="169" alt="image" src="https://github.com/user-attachments/assets/2422e5b9-9bf4-4883-a742-ab2937215f5d" /><br>
 
Pada posisi ini, CA telah berhasil dijalankan.<br>
 
**5. Membuat Aplikasi Menjadi CA - Podman**<br>
<p align="center">
   <img width="940" height="950" alt="image" src="https://github.com/user-attachments/assets/e82c4ce9-039b-4ab1-9219-af1fb8b0e1f7" />
<p align="center">
   <img width="940" height="315" alt="image" src="https://github.com/user-attachments/assets/8b05fd46-ad65-48c2-9578-a0a83ab212fd" /><br>

pembahasan :<br>
Perintah  podman build -f Dockerfile -t flaskr:1.0.0 . membangun image container menggunakan Podman dengan Dockerfile yang sama.<br>

image telah berhasil dibuat :<br>
<p align="center">
   <img width="909" height="126" alt="image" src="https://github.com/user-attachments/assets/eb21cf54-18f1-4a44-a4f3-494b6350d66a" /><br>

pembahasan :<br>
Perintah podman image ls digunakan untuk melihat daftar image yang telah berhasil dibuat pada Podman dan memastikan image flaskr:1.0.0 tersedia.<br>


Jalankan dengan memetakan port 5000 pada aplikasi di container ke port 5001 di localhost:<br>
<p align="center">
   <img width="940" height="143" alt="image" src="https://github.com/user-attachments/assets/5d396830-d77f-47e6-b136-bcc9138883e6" /><br>

Akses web browser:<br>
<p align="center">
    <img width="940" height="160" alt="image" src="https://github.com/user-attachments/assets/37012cdf-e463-45f5-9efc-1eaa48d24cfd" />



   

   



