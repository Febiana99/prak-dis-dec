<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert04</h1>
<h3>Nama : Febiana Serao Da Cruz</h3>
<h3>NIM: 235410032</h3>

***Cloud Computing***

1. Membuat env Python 3.14.4
   <img width="710" height="378" alt="image" src="https://github.com/user-attachments/assets/a04c0a5d-6416-4dec-97d0-d6e7c49ed9ea" />

pembahasan :
Perintah ls -la digunakan untuk menampilkan seluruh file dan folder termasuk file tersembunyi seperti .venv. Dari hasil ini dapat dipastikan bahwa virtual environment berhasil dibuat karena folder .venv muncul di direktori project.
   
2. Install Paket yang Diperlukan
   <img width="828" height="320" alt="image" src="https://github.com/user-attachments/assets/b73e1bd1-00e2-4c7f-9bdf-42d850511494" />

pembahasan :
Perintah uv pip install -e . digunakan untuk menginstall seluruh dependency project berdasarkan file konfigurasi pyproject.toml. Opsi -e berarti editable mode sehingga project tetap terhubung dengan source code asli dan perubahan kode dapat langsung digunakan.

menjalankan aplikasi tersebut setelah inisialisasi database :
<img width="669" height="259" alt="image" src="https://github.com/user-attachments/assets/a31ce4f5-9bf0-4cb8-b6ea-843c27bd7c20" />

pembahasan :
Perintah flask --app flaskr init-db digunakan untuk membuat database awal aplikasi Flask berupa SQLite yang berfungsi menyimpan data pengguna, autentikasi, dan post blog. 
Sedangkan perintah flask --app flaskr run menjalankan aplikasi Flask secara lokal pada 127.0.0.1:5000 sehingga aplikasi dapat diuji melalui browser dengan fitur register dan login.

hasil saat aplikasi berjalan di browser :
<img width="808" height="249" alt="image" src="https://github.com/user-attachments/assets/3f5b43f2-934c-4b96-bcd9-fc584178254f" />


hasil saat mencoba aplikasinya :
- Register
  <img width="779" height="289" alt="image" src="https://github.com/user-attachments/assets/231b4fec-a4c8-428b-8645-0b6051e822af" />

  
- Login
  <img width="731" height="379" alt="image" src="https://github.com/user-attachments/assets/948512e3-1fb7-4119-87a1-046fcf7e7311" />

  
Tampilan setelah Login 
<img width="940" height="273" alt="image" src="https://github.com/user-attachments/assets/6f268abd-01a6-4339-b18d-90fa6887e6f0" />

3. Buat Aplikasi Menjadi CA - Docker
   file utk build docker: Dockerfile. File diletakkan di direktori root dari aplikasi. Isinya adalah sebagai berikut:
   <img width="823" height="243" alt="image" src="https://github.com/user-attachments/assets/c380a605-d18b-4fda-96a0-3732eff2461f" />

pembahasan :
Kode Dockerfile ini digunakan untuk mengubah aplikasi Flask menjadi container dengan Python 3.14 sebagai dasar, membuat direktori kerja /app, menyalin seluruh project ke dalam container, menginstall dependency, menginisialisasi database, membuka port 5000, dan menjalankan aplikasi Flask agar dapat diakses melalui browser secara konsisten di berbagai sistem.

Membuat Image :
<img width="940" height="680" alt="image" src="https://github.com/user-attachments/assets/7acc8d76-11e1-411e-9db6-5a99f6ebc50a" />
pembahasan :
Perintah ini digunakan untuk membangun Docker image berdasarkan Dockerfile. Nama image diberikan flaskr:1.0.0 sebagai identitas versi aplikasi container.

image telah berhasil dibuat :
<img width="891" height="201" alt="image" src="https://github.com/user-attachments/assets/edcb7ea9-53bb-4319-9cad-4e424dde857a" />

pembahasan :
Perintah docker images digunakan untuk menampilkan seluruh image yang tersedia pada sistem dan memastikan image flaskr:1.0.0 berhasil dibuat.

   
4. Menjalankan Image
   Jalankan dengan memetakan port 5000 pada aplikasi di container ke port 5001 di localhost:
   <img width="940" height="192" alt="image" src="https://github.com/user-attachments/assets/f79ab71d-cbd5-4524-b111-3f3343e06c3a" />

pembahasan :
Perintah ini menjalankan container dari image flaskr:1.0.0. Port 5001 pada localhost dipetakan ke port 5000 pada container sehingga aplikasi dapat diakses melalui browser pada localhost:5001.

   akses web browser :
   <img width="940" height="169" alt="image" src="https://github.com/user-attachments/assets/2422e5b9-9bf4-4883-a742-ab2937215f5d" />
Pada posisi ini, CA telah berhasil dijalankan.

   
5. Buat Aplikasi Menjadi CA - Podman
   <img width="940" height="950" alt="image" src="https://github.com/user-attachments/assets/e82c4ce9-039b-4ab1-9219-af1fb8b0e1f7" />
   <img width="940" height="315" alt="image" src="https://github.com/user-attachments/assets/8b05fd46-ad65-48c2-9578-a0a83ab212fd" />

pembahasan :
Perintah ini membangun image container menggunakan Podman dengan Dockerfile yang sama. Podman berfungsi sebagai alternatif Docker tanpa bergantung pada daemon Docker.

image telah berhasil dibuat :
<img width="909" height="126" alt="image" src="https://github.com/user-attachments/assets/eb21cf54-18f1-4a44-a4f3-494b6350d66a" />

pembahasan :
Perintah ini digunakan untuk melihat daftar image yang telah berhasil dibuat pada Podman dan memastikan image flaskr:1.0.0 tersedia.


Jalankan dengan memetakan port 5000 pada aplikasi di container ke port 5001 di localhost:
<img width="940" height="143" alt="image" src="https://github.com/user-attachments/assets/5d396830-d77f-47e6-b136-bcc9138883e6" />

Akses web browser:
<img width="940" height="160" alt="image" src="https://github.com/user-attachments/assets/37012cdf-e463-45f5-9efc-1eaa48d24cfd" />



   

   



