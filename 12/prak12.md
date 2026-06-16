<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert12</h1>
Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

<h3>Teknologi P2P (Peer-to-Peer)</h3>

**1. koneksi antar nodes**<br>

simple_chat.py:<br>
<p align="center">
<img width="840" height="1000" alt="image" src="https://github.com/user-attachments/assets/2be4fe65-4a82-4b10-b097-0c9b99cdb1b3" />

<p align="center">
<img width="840" height="407" alt="image" src="https://github.com/user-attachments/assets/06ae1b33-ae7f-454a-a0f5-320120b6d610" /><br>

Tugas :<br>
1. Program berhasil dijalankan pada dua node yang menggunakan port berbeda, yaitu port 5001 dan port 5002. Setelah koneksi berhasil dibuat, node pertama berhasil mengirim pesan "hello" kepada node kedua. Pesan tersebut diterima dan ditampilkan pada node kedua, sehingga membuktikan bahwa komunikasi antar node menggunakan Peer-to-Peer (P2P) telah berjalan.<br>
Node 1 :<br>
<p align="center">
<img width="940" height="232" alt="image" src="https://github.com/user-attachments/assets/d49ea9f1-50f5-4d37-b571-5df8d10a987b" /><br>

Node 2 :<br>
<p align="center">
  <img width="940" height="229" alt="image" src="https://github.com/user-attachments/assets/b934b249-c4df-4199-937e-c11401310558" /><br>

2. a. Membuka port yang akan menerima dan mengirim pesan<br>
bagian program yang digunakan :<br>
<img width="615" height="97" alt="image" src="https://github.com/user-attachments/assets/a7ec6a78-c9e3-4736-847f-e05124274276" /><br>

Kode tersebut digunakan untuk membuat socket server dan membuka port yang akan digunakan dalam komunikasi antar node. Fungsi socket.socket() digunakan untuk membuat socket TCP/IP, fungsi bind() digunakan untuk menghubungkan socket dengan alamat IP dan port yang dipilih, sedangkan fungsi listen() digunakan untuk membuat server menunggu koneksi dari node lain.<br>

b. Menerima pesan<br>
bagian program yang diguanakan :<br>
<img width="577" height="142" alt="image" src="https://github.com/user-attachments/assets/08ead068-7a7f-4f35-b6e2-6816b5d3354e" /><br>
pembahasan :<br>
Kode tersebut digunakan untuk menerima pesan dari node lain. Fungsi accept() digunakan untuk menerima koneksi yang masuk dari peer, sedangkan fungsi recv(1024) digunakan untuk menerima data atau pesan yang dikirimkan oleh node lain dengan ukuran maksimal 1024 byte.<br>

c. Mengirim pesan<br>
bagian program yang diguanakan :<br>
<img width="676" height="182" alt="image" src="https://github.com/user-attachments/assets/2e46c0eb-eb1c-44bd-a4d5-84e297b87397" /><br>
pembahasan :<br>
Kode tersebut digunakan untuk mengirim pesan ke node tujuan. Fungsi connect() digunakan untuk membuat koneksi ke alamat IP dan port tujuan. Pesan yang diketik pengguna dibaca menggunakan input(), kemudian diubah menjadi format byte menggunakan encode('utf-8') dan dikirim melalui socket menggunakan fungsi sendall().<br>

**2. DHT (Distributed Hash Table)<br>**

dht.py:<br>
<p align="center">
<img width="1000" height="827" alt="image" src="https://github.com/user-attachments/assets/79d9f505-c58f-4dbf-8c86-6a39dbaf8c70" />

<p align="center">
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/f942f930-f276-4e01-81d7-bd7de3edbfa7" /><br>

Tugas :<br>
1. hasil saat menjalankan program tersebut :<br>
<img width="755" height="512" alt="image" src="https://github.com/user-attachments/assets/8df9a4ac-37b9-44e3-8887-d461dfea862b" /><br>
pembahasan :<br>
Program DHT berhasil dijalankan dan menghasilkan output berupa pembuatan node, pembentukan ring DHT, penyimpanan data pada node yang sesuai berdasarkan hasil hashing, serta proses pencarian data yang berhasil maupun yang tidak ditemukan dalam jaringan.<br>

2. Program ini digunakan untuk mensimulasikan cara kerja Distributed Hash Table (DHT) pada jaringan P2P. Program membuat beberapa node, menyimpan data ke node tertentu berdasarkan hasil hash, dan melakukan pencarian data pada node yang sesuai.<br>

3. Pada DHT, setiap file diubah menjadi key menggunakan fungsi hash. Key tersebut digunakan untuk menentukan node yang bertanggung jawab menyimpan data. Saat data dicari, sistem akan menghitung kembali key file tersebut lalu mengarahkan pencarian ke node yang sesuai. Jika data ada pada node tersebut maka data akan ditemukan, sedangkan jika tidak ada maka sistem akan menampilkan pesan bahwa data tidak ditemukan.<br>
Algoritmanya : Mulai → Input nama file → Hitung hash file menjadi key → Cari node yang bertanggung jawab terhadap key → Arahkan permintaan ke node tersebut → Periksa keberadaan data → Jika data ditemukan tampilkan isi data → Jika tidak ditemukan tampilkan pesan gagal → Selesai.<br>


**3. Torrent**<br>

File .torrent merupakan file yang berisi data tentang file yang ada di platform P2P BitTorrent. Berikut adalah contoh program Python untuk membaca data yang ada pada suatu file .torrent:<br>
<p align="center">
<img width="590" height="760" alt="image" src="https://github.com/user-attachments/assets/76db7976-fa24-4526-8bd4-460f61589e09" />

Tugas :
1. hasil saat menjalankan program tersebut :<br>
<img width="742" height="166" alt="image" src="https://github.com/user-attachments/assets/b739f4d5-c2bf-4d6b-9cb9-60d94d30b0af" /><br>

2. Program menghasilkan output tersebut karena membaca metadata yang tersimpan di dalam file .torrent menggunakan library bcoding. Data yang berhasil dibaca kemudian ditampilkan berupa URL tracker, nama file, ukuran file, ukuran piece, nilai info hash yang dihitung, serta jumlah piece yang digunakan untuk membagi file.

3. - sourcode yang di ubah :<br>
  <img width="515" height="177" alt="image" src="https://github.com/user-attachments/assets/b6ddc705-61f7-446a-af36-9c8ea7799392" /><br>

hasil saat menjalankan python read_torrent.py FreeBSD-15.0-RELEASE-amd64-bootonly.iso.torrent.torrent<br>
<img width="755" height="176" alt="image" src="https://github.com/user-attachments/assets/020d7893-5c37-4b41-aa77-086032c34871" /><br>

Program dimodifikasi dengan menambahkan modul sys agar nama file .torrent dapat diberikan melalui parameter saat program dijalankan. Dengan cara ini, pengguna tidak perlu mengubah source code setiap kali ingin membaca metadata file torrent yang berbeda. Program akan mengambil nama file dari argumen yang diberikan pada command line dan meneruskannya ke fungsi baca_metadata_torrent() untuk diproses.




