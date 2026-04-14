**Praktikum Sistem Terdistribusi dan Terdesentralisasi Pert02**

Nama : Febiana Serao Da Cruz<br>
NIM: 235410032

**Sinkronisasi Waktu**<br>
<img width="790" height="564" alt="image" src="https://github.com/user-attachments/assets/509f47f9-8743-4ec9-8375-783d890259bd" />

penjelasan :
Proses sinkronisasi dilakukan saat aplikasi NetTime terhubung ke server NTP melalui internet untuk mengambil waktu standar yang akurat. Setelah menerima data waktu dari server, NetTime membandingkan waktu server dengan waktu pada komputer, lalu menghitung selisihnya dan menyesuaikan jam komputer secara otomatis. Pada hasil yang diperoleh, sinkronisasi berhasil karena status menunjukkan “Time is synchronized”, server dalam keadaan “Good”, dan tidak ada error pada proses sinkronisasi.


**Vector Clock**
1. program **vclocks.py** :
<img width="842" height="867" alt="image" src="https://github.com/user-attachments/assets/8adfe918-dff5-4cd3-aa32-3f869ee48fb5" />
<img width="737" height="762" alt="image" src="https://github.com/user-attachments/assets/e6bcb74e-6ffa-4e7b-ac47-8cc6d55a7460" />

outputnya :

<img width="495" height="446" alt="image" src="https://github.com/user-attachments/assets/2ec64ee2-ff86-4dbe-b737-d6900afcb088" />

penjelsanan :
Dari hasil program vector clock terlihat bahwa setiap proses memiliki pencatat waktu masing-masing yang berubah setiap kali terjadi event. Pada awalnya semua proses bernilai nol, kemudian ketika proses 0 melakukan event lokal nilainya bertambah. Saat proses 0 mengirim pesan ke proses 1, nilai vector clock ikut dikirim dan proses 1 menyesuaikan nilainya dengan mengambil nilai terbesar dari clock yang diterima lalu menambah 1 pada prosesnya sendiri. Jika dilakukan manual, langkahnya sama yaitu setiap kejadian dicatat satu per satu, lalu saat menerima pesan setiap indeks dibandingkan dan dipilih nilai maksimum. Dengan cara ini urutan kejadian antar proses dapat diketahui secara tepat.

2. - modul Python **vectorclock.py**
     <img width="735" height="463" alt="image" src="https://github.com/user-attachments/assets/258aa373-07b5-4357-b149-0e548aa9f6b2" />
     
   - **test_vectorclock.py**
     <img width="432" height="296" alt="image" src="https://github.com/user-attachments/assets/069f474f-3aee-4ff2-b9e0-9f2c3f62aeca" />

     outputnya :
     <img width="736" height="150" alt="image" src="https://github.com/user-attachments/assets/510dc31e-8159-498b-b7c2-d71628d6d9c3" />

penjelasan :
Class VectorClock dibuat menjadi modul Python dengan memisahkan class ke file tersendiri agar dapat dipakai ulang di program lain tanpa menulis ulang kode. Contoh penggunaannya adalah membuat file modul bernama vectorclock.py, lalu file lain seperti test_vectorclock.py memanggilnya dengan perintah import.


**Problem tanpa sinkronisasi**
program **multithreaded-example.py**
<img width="677" height="682" alt="image" src="https://github.com/user-attachments/assets/a71e1412-65fc-4321-84d5-acb0fdc8bbb3" />

outputnya :
<img width="803" height="582" alt="image" src="https://github.com/user-attachments/assets/94caea98-4a71-426e-a422-5c9860af5d9d" />

penjelasan :
Output program bisa berbeda karena semua thread berjalan secara bersamaan dalam waktu yang sama.
Setiap thread mendapat giliran eksekusi dari sistem operasi secara bergantian.Urutan thread yang selesai tidak selalu sama karena diatur oleh CPU scheduler.Walaupun semua task memiliki waktu tunggu 5 detik, proses selesai bisa berbeda urutan. Pada percobaan pertama task A selesai lebih dulu, sedangkan pada percobaan kedua task B lebih dulu. Hal ini menunjukkan bahwa multithreading tidak memiliki urutan hasil yang tetap setiap dijalankan. Jadi perbedaan output terjadi karena pembagian waktu eksekusi thread bersifat dinamis.

**Data Race/Race Conditions**
1. program **race-conditions-01.py**
   
   
   
2. program **race-conditions-02.py**

**Deadlock**
1. program **deadlock-01.py**
2. program **deadlock-02.py**

**Algoritma Raft**






