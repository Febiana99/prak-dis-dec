<h1>Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert03</h1>
<h3>Nama : Febiana Serao Da Cruz</h3>
<h3>NIM: 235410032</h3>


**Sinkronisasi Waktu**<br>
<p align="center">
  <img width="500" height="564" alt="image" src="https://github.com/user-attachments/assets/509f47f9-8743-4ec9-8375-783d890259bd" />

penjelasan :<br>
Proses sinkronisasi dilakukan saat aplikasi NetTime terhubung ke server NTP melalui internet untuk mengambil waktu standar yang akurat. Setelah menerima data waktu dari server, NetTime membandingkan waktu server dengan waktu pada komputer, lalu menghitung selisihnya dan menyesuaikan jam komputer secara otomatis. Pada hasil yang diperoleh, sinkronisasi berhasil karena status menunjukkan “Time is synchronized”, server dalam keadaan “Good”, dan tidak ada error pada proses sinkronisasi.


**Vector Clock**
1. program **vclocks.py** :<br>
<p align="center">
  <img width="700" height="867" alt="image" src="https://github.com/user-attachments/assets/8adfe918-dff5-4cd3-aa32-3f869ee48fb5" />
<p align="center">
  <img width="710" height="762" alt="image" src="https://github.com/user-attachments/assets/e6bcb74e-6ffa-4e7b-ac47-8cc6d55a7460" />

outputnya :<br>
<p align="center">
  <img width="495" height="446" alt="image" src="https://github.com/user-attachments/assets/2ec64ee2-ff86-4dbe-b737-d6900afcb088" />

penjelsanan :<br>
Dari hasil program vector clock terlihat bahwa setiap proses memiliki pencatat waktu masing-masing yang berubah setiap kali terjadi event. Pada awalnya semua proses bernilai nol, kemudian ketika proses 0 melakukan event lokal nilainya bertambah. Saat proses 0 mengirim pesan ke proses 1, nilai vector clock ikut dikirim dan proses 1 menyesuaikan nilainya dengan mengambil nilai terbesar dari clock yang diterima lalu menambah 1 pada prosesnya sendiri. Jika dilakukan manual, langkahnya sama yaitu setiap kejadian dicatat satu per satu, lalu saat menerima pesan setiap indeks dibandingkan dan dipilih nilai maksimum. 

2. - modul Python **vectorclock.py**<br>
     <img width="450" height="463" alt="image" src="https://github.com/user-attachments/assets/258aa373-07b5-4357-b149-0e548aa9f6b2" />
     
   - **test_vectorclock.py**<br>
     <img width="400" height="296" alt="image" src="https://github.com/user-attachments/assets/069f474f-3aee-4ff2-b9e0-9f2c3f62aeca" />

     outputnya :<br>
     <img width="450" height="150" alt="image" src="https://github.com/user-attachments/assets/510dc31e-8159-498b-b7c2-d71628d6d9c3" />

penjelasan :<br>
Class VectorClock dibuat menjadi modul Python dengan memisahkan class ke file tersendiri agar dapat dipakai ulang di program lain tanpa menulis ulang kode. Contoh penggunaannya adalah membuat file modul bernama vectorclock.py, lalu file lain seperti test_vectorclock.py memanggilnya dengan perintah import.


**Problem tanpa sinkronisasi**<br>
program **multithreaded-example.py**<br>
<p align="center">
  <img width="500" height="682" alt="image" src="https://github.com/user-attachments/assets/a71e1412-65fc-4321-84d5-acb0fdc8bbb3" />

outputnya :<br>
<p align="center">
  <img width="500" height="582" alt="image" src="https://github.com/user-attachments/assets/94caea98-4a71-426e-a422-5c9860af5d9d" />

penjelasan :<br>
Output program bisa berbeda karena semua thread berjalan secara bersamaan dalam waktu yang sama.
Setiap thread mendapat giliran eksekusi dari sistem operasi secara bergantian.Urutan thread yang selesai tidak selalu sama karena diatur oleh CPU scheduler.Walaupun semua task memiliki waktu tunggu 5 detik, proses selesai bisa berbeda urutan. Pada percobaan pertama task A selesai lebih dulu, sedangkan pada percobaan kedua task B lebih dulu. Hal ini menunjukkan bahwa multithreading tidak memiliki urutan hasil yang tetap setiap dijalankan. Jadi perbedaan output terjadi karena pembagian waktu eksekusi thread bersifat dinamis.

**Data Race/Race Conditions**<br>
1. program **race-conditions-01.py**<br>
   <p align="center">
     <img width="500" height="415" alt="image" src="https://github.com/user-attachments/assets/072dd11c-6f3f-4520-a85e-bdf392ca53f6" />

    penjelasan :<br>
    <p align="center">
    <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/74682296-2899-4d92-bf62-073969f6c112" /><br>
    Dua thread membaca saldo bersamaan sebelum saldo diperbarui, sehingga keduanya sama-sama menganggap uang cukup.
    
   
3. program **race-conditions-02.py**<br>
   <p align="center">
     <img width="500" height="477" alt="image" src="https://github.com/user-attachments/assets/7db09a62-6493-4d99-ac0a-2b00c2d8c14f" />

   outputnya : <br>
    <p align="center">
      <img width="500" height="82" alt="image" src="https://github.com/user-attachments/assets/ba30e369-592a-4583-9c95-09d7ea6027ac" />

   penjelasan :<br>
Race condition tidak terjadi karena program sudah menggunakan lock untuk mengatur akses ke saldo. Dengan adanya lock, hanya satu thread yang bisa masuk lebih dulu, sedangkan thread lain harus menunggu.
   



**Deadlock**<br>
1. program **deadlock-01.py**<br>
   <p align="center">
     <img width="500" height="727" alt="image" src="https://github.com/user-attachments/assets/a436dc59-a70b-472b-96ba-b09267b99737" /><br>
     
  penjelasan :<br>
     <p align="center">
       <img width="400" height="634" alt="image" src="https://github.com/user-attachments/assets/1cfacf6c-8d6a-4cd2-a235-d73186d19961" />


2. program **deadlock-02.py**<br>
   <p align="center">
     <img width="500" height="880" alt="image" src="https://github.com/user-attachments/assets/3b6bc86b-af3b-4464-a057-979487e283b8" />

   outpurnya :<br>
   <p align="center">
     <img width="500" height="187" alt="image" src="https://github.com/user-attachments/assets/9bb0f06a-7e95-4db9-92a0-38acd0ab7162" />
   
   penjelasan :<br>
Deadlock tidak terjadi karena kedua thread masih bisa mendapatkan lock yang dibutuhkan dan melanjutkan prosesnya. Meskipun sempat saling menunggu, sistem tetap memberi jalan agar salah satu thread selesai lebih dulu. Setelah itu thread lainnya ikut berjalan sampai program selesai.


**Algoritma Raft**<br>
1. program **raft.py**:<br>
   <p align="center">
     <img width="540" height="763" alt="image" src="https://github.com/user-attachments/assets/8fc49a67-cbd4-4fd5-b504-c8a0eb0fe5d7" /><br>
    <p align="center">
      <img width="540" height="812" alt="image" src="https://github.com/user-attachments/assets/891d5d1c-de7d-4863-9cad-26a1555320a6" /><br>
    <p align="center">
      <img width="540" height="597" alt="image" src="https://github.com/user-attachments/assets/9ecedce0-6d7d-4301-a2a2-81f06b57d24b" /><br>
  
  penjelasan : <br>
   <p align="center">
       <img width="400" height="943" alt="image" src="https://github.com/user-attachments/assets/13161231-fb9c-46da-bde0-e2da71f66431" /><br>

  
2. - modul Python **raft_modul**<br>
     <p align="center">
       <img width="559" height="693" alt="image" src="https://github.com/user-attachments/assets/bcc56b64-8699-44ba-b511-cb6b420a60f1" />

   - **test_raft**<br>
     <p align="center">
       <img width="450" height="252" alt="image" src="https://github.com/user-attachments/assets/582da36c-45fc-47ff-b49b-33c241ef61b5" />

       







