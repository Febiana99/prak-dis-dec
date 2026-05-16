<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert08</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Arsitektur Microservices untuk Sistem Terdistribusi</h3>

**1. Prasyarat**<br>
Untuk mengerjakan materi pada pertemuan ini, berikut adalah beberapa prasyarat:<br>
1. Software uv telah terinstall dan penggunaannya telah dipahami. Lihat ke https://github.com/NEO-X-School/notes/blob/main/uv/00.md untuk panduan praktis.<br>
2. Instalasi Python menggunakan uv - Python 3.14.4<br>
<p align="center">
   <img width="550" height="400" alt="image" src="https://github.com/user-attachments/assets/7c556c1c-4702-4640-a77d-93b9858a8019" /><br>
   
3. Install paket FastAPI dan SQLModel:<br>
<p align="center">
   <img width="400" height="650" alt="image" src="https://github.com/user-attachments/assets/168a1d4e-037b-418b-95b8-33e63bcc2cb7" /><br>
   
Installasi package dilakukan menggunakan perintah uv pip install fastapi[standard] sqlmodel. Package tersebut digunakan untuk membuat RESTful API dan menghubungkan Python dengan database SQLite.

4. Install SQLite jika belum ada di OS yang digunakan:<br>
<p align="center">
  <img width="600" height="408" alt="image" src="https://github.com/user-attachments/assets/9c59cd80-2cde-4f5d-8808-3bc1cd731ee3" /><br>
   
<p align="center">
   <img width="910" height="52" alt="image" src="https://github.com/user-attachments/assets/2dbc8bad-5e30-4d7c-8a0b-4ef7c35d7588" /><br>
   
Pada gambar dilakukan pengecekan SQLite menggunakan perintah sqlite3 --version. Dari hasil yang tampil, SQLite sudah dikenali oleh sistem sehingga dapat digunakan untuk membuat database.<br>

5. Buat database:<br>
<p align="center">
   <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/d519a32e-c53b-4cdd-9420-51d0b35bc7a0" /><br>
   
Membuat database departemen-sdm.db menggunakan SQLite. Setelah itu dibuat tabel sdm yang digunakan untuk menyimpan data karyawan.
   
**2. Source Code**<br>
<p align="center">
   <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/8c22fdc0-7fab-4d07-899e-be9f305f52e5" /><br>
   
Source code dibuat pada file main.py yang berisi koneksi database departemen-sdm.db, model tabel sdm, serta endpoint FastAPI untuk menampilkan data karyawan. Source code tersebut digunakan agar data pada database SQLite dapat ditampilkan dalam bentuk RESTful API.<br>
   
**3. Menjalankan Source Code**<br>
<p align="center">
   <img width="600" height="120" alt="image" src="https://github.com/user-attachments/assets/9b0769cf-176e-4361-995c-7546026429a4" /><br>
   
Source code dijalankan menggunakan perintah uvicorn main:app --reload agar server FastAPI dapat berjalan dan endpoint dapat diakses melalui browser menggunakan localhost.

Untuk memeriksa, akses dari browser atau dari headless tool (curl atau wget):<br>
<p align="center">
   <img width="600" height="90" alt="image" src="https://github.com/user-attachments/assets/584fcc5e-173e-4965-9401-72ec1deff889" />

<p align="center">
   <img width="600" height="80" alt="image" src="https://github.com/user-attachments/assets/c28e0146-f184-4175-91f8-29c410aacfb8" /><br>

**4. Tugas**<br>
1. Buat satu tabel baru menggunakan SQLite, tabel berbeda dari yang ada pada contoh. Tabel tersebut mempunyai 1 primary key dan setidaknya berisi data dengan tipe INT, CHAR, VARCHAR, BOOLEAN, dan FLOAT.<br>
<p align="center">
  <img width="650" height="150" alt="image" src="https://github.com/user-attachments/assets/3f3887fb-f018-425b-804e-0effcdb008c4" /><br>
   
Database toko.db dibuat menggunakan SQLite kemudian dibuat tabel produk yang berisi tipe data INTEGER, CHAR, VARCHAR, BOOLEAN, dan FLOAT
   
2. Isikan 5 data menggunakan script Python<br>
<p align="center">
  <img width="500" height="650" alt="image" src="https://github.com/user-attachments/assets/581b2858-a36d-498f-bc0b-9597ec11f661" /><br>

<p align="center">
   <img width="500" height="550" alt="image" src="https://github.com/user-attachments/assets/b707d17b-cee5-4f82-897e-e1d81d5b5c98" /><br>

<p align="center">
  <img width="500" height="113" alt="image" src="https://github.com/user-attachments/assets/27bfe87b-38e0-4c2e-9c04-be12bc848a8d" /><br>
   
Data produk dimasukkan menggunakan script Python melalui fungsi session.add() pada file tugas.py sehingga data dapat tersimpan otomatis ke dalam database toko.db.

3. Buat RESTful API endpoint untuk menampilkan semua data yang telah diisikan.<br>
<p align="center">
  <img width="700" height="107" alt="image" src="https://github.com/user-attachments/assets/0246c928-3ac6-4c29-9b4a-731a44f3db96" /><br>

<p align="center">
   <img width="700" height="160" alt="image" src="https://github.com/user-attachments/assets/ea74e9bf-20c1-4bde-ba69-22dfb728a567" /><br>
   
RESTful endpoint dijalankan menggunakan perintah uvicorn tugas:app --reload kemudian endpoint /produk/ diakses melalui browser untuk menampilkan seluruh data produk dari database toko.db dalam format JSON.
   
4. Tampilkan hasil RESTful API endpoint tersebut menggunakan curl.<br>
<p align="center">
   <img width="850" height="86" alt="image" src="https://github.com/user-attachments/assets/d8274ec4-beaf-4254-9631-049ea63e1444" /><br>
   
Pengujian endpoint dilakukan menggunakan perintah curl http://127.0.0.1:8000/produk/ untuk menampilkan data produk melalui terminal.

