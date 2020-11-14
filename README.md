# **Jarkom_Modul2_Lapres_B14**
### Anggota Kelompok:
- IQBAAL PRATAMA PUTRA  (05111840000021)
- DWI WAHYU SANTOSO     (05111840000121)

<img src="images/topologi.PNG" width="500">

## Topologi:
- SURABAYA    : Router
- MALANG      : DNS Server Master
- MOJOKERTO   : DNS Server Slave
- PROBOLINGGO : Web Server
- GRESIK      : Client
- SIDOARJO    : Client

## Langkah-langkah pengerjaan:
**1. Membuat domain `http://semerub14.pw` dengan DNS MALANG dan mengarah ke IP Server PROBOLINGGO.** <br>
- Edit file `etc/bind/named.conf.local` pada MALANG dengan setting berikut: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/1.1.png?raw=true) <br>
- Buat folder `/jarkom` di dalam folder`/etc/bind`. <br> 
- Salin file `db.local` pada `/etc/bind/jarkom` dan diubah namanya menjadi `semerub14.pw`. <br>
- Buka file `semerub14.pw` dan edit seperti gambar di bawah ini: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/1.2.png?raw=true) <br>
- Kemudian restart bind9 dengan cara `service bind9 restart`. <br>
- Untuk mengecek, `ping semerub14.pw` pada GRESIK. <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/1.3.png?raw=true) <br>
<br>
**2. Membuat alias `http://www.semerub14.pw`** <br>
- Edit file `etc/bind/jarkom/semerub14.pw` pada MALANG dengan setting berikut: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/2.1.png?raw=true) <br>
- Untuk mengecek, `ping www.semerub14.pw` pada GRESIK. <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/2.2.png?raw=true) <br>
<br>
3. Membuat subdomain `http://penanjakan.semerub14.pw`. <br>
- Edit file `etc/bind/jarkom/semerub14.pw` pada MALANG dengan setting berikut: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/3.1.png?raw=true) <br>
- Untuk mengecek, `ping penanjakan.semerub14.pw` pada GRESIK. <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/3.2.png?raw=true) <br>
<br>
4. Membuat reverse domain untuk domain utama. <br>
- Edit file `/etc/bind/named.conf.local` pada MALANG dengan setting berikut: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/4.1.png?raw=true) <br>
- Salin file `db.local` pada `/etc/bind/jarkom` dan diubah namanya menjadi `83.151.10.in-addr.arpa`. <br>
- Edit file `/etc/bind/jarkom/83.151.10.in-addr.arpa` seperti gambar di bawah ini: <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/4.2.png?raw=true) <br>
- Untuk mengecek, `host -t PTR 10.151.83.124` pada GRESIK. <br>
![alt text](https://github.com/dws-in/Jarkom_Modul2_Lapres_B14/blob/main/images/4.3.png?raw=true) <br>
<br>
5. Membuat DNS Server Slave pada MOJOKERTO sebagai berikut:
6. Membuat subdomain `http://gunung.semerub14.pw` pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO sebagai berikut:
7. Membuat subdomain `http://naik.gunung.semerub14.pw` pada MOJOKERTO dan mengarah ke IP Server PROBOLINGGO sebagai berikut:
8. Membuat `DocumentRoot` pada `/var/www/semerub14.pw` yang dapat diakses melalui `http://semerub14.pw/index.php/home` sebagai berikut:
9. Mengatifkan mode rewrite sehingga menjadi `http://semerub14.pw/home` sebagai berikut:
10. 

