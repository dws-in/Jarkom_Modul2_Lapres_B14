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
![alt text](/images/1.1.png) <br>
- Buat folder `/jarkom` di dalam folder`/etc/bind`. <br> 
- Salin file `db.local` ke `/etc/bind/jarkom` dan diubah namanya menjadi `semerub14.pw`. <br>
- Buka file `semerub14.pw` dan edit seperti gambar di bawah ini: <br>
![alt text](/images/1.2.png) <br>
- Kemudian restart bind9 dengan cara `service bind9 restart`. <br>
- Untuk mengecek, `ping semerub14.pw` pada GRESIK. <br>
![alt text](/images/1.3.png) <br>

**2. Membuat alias `http://www.semerub14.pw`.** <br>
- Edit file `etc/bind/jarkom/semerub14.pw` pada MALANG dengan setting berikut: <br>
![alt text](/images/2.1.png) <br>
- Untuk mengecek, `ping www.semerub14.pw` pada GRESIK. <br>
![alt text](/images/2.2.png) <br>

**3. Membuat subdomain `http://penanjakan.semerub14.pw`.** <br>
- Edit file `etc/bind/jarkom/semerub14.pw` pada MALANG dengan setting berikut: <br>
![alt text](/images/3.1.png) <br>
- Untuk mengecek, `ping penanjakan.semerub14.pw` pada GRESIK. <br>
![alt text](/images/3.2.png) <br>

**4. Membuat reverse domain untuk domain utama.** <br>
- Edit file `/etc/bind/named.conf.local` pada MALANG dengan setting berikut: <br>
![alt text](/images/4.1.png) <br>
- Salin file `db.local` pada `/etc/bind/jarkom` dan diubah namanya menjadi `83.151.10.in-addr.arpa`. <br>
- Edit file `/etc/bind/jarkom/83.151.10.in-addr.arpa` seperti gambar di bawah ini: <br>
![alt text](/images/4.2.png) <br>
- Untuk mengecek, `host -t PTR 10.151.83.124` pada GRESIK. <br>
![alt text](/images/4.3.png) <br>

**5. Membuat DNS Server Slave pada MOJOKERTO.** <br>
- Edit file `/etc/bind/named.conf.local` pada MALANG dengan setting berikut: <br>
![alt text](/images/5.1.png) <br>
- Edit file `/etc/bind/named.conf.local` pada MOJOKERTO dengan setting berikut: <br>
![alt text](/images/5.2.png) <br>
- Untuk mengecek, matikan dulu MALANG dengan `service bind9 stop`. <br>
![alt text](/images/5.3.png) <br>
- Kemudian `ping semerub14.pw` pada GRESIK. <br>
![alt text](/images/5.4.png) <br>
- Nyalakan kembali server MALANG `service bind9 restart`. <br>

**6. Membuat subdomain `http://gunung.semerub14.pw` pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.** <br>
- Edit file `etc/bind/jarkom/semerub14.pw` pada MALANG dengan setting berikut: <br>
![alt text](/images/6.1.png) <br>
- Edit file `etc/bind/jarkom/named.conf.options` pada MALANG dengan setting berikut: <br>
- Comment pada bagian `dnssec-validation auto` dan tambahkan baris berikut. <br>
![alt text](/images/6.2.png) <br>
- Edit file `etc/bind/jarkom/named.conf.options` pada MOJOKERTO dengan setting berikut: <br>
- Comment pada bagian `dnssec-validation auto` dan tambahkan baris berikut. <br>
![alt text](/images/6.3.png) <br>
- Buat folder `/delegasi` di dalam folder`/etc/bind`. <br> 
- Salin file `db.local` ke `/etc/bind/delegasi` dan diubah namanya menjadi `gunung.semerub14.pw`. <br>
- Buka file `/etc/bind/delegasi/gunung.semerub14.pw` dan edit seperti gambar di bawah ini: <br>
![alt text](/images/6.4.png) <br>
- Kemudian `ping gunung.semerub14.pw` pada GRESIK. <br>
![alt text](/images/6.5.png) <br>

**7. Membuat subdomain `http://naik.gunung.semerub14.pw` pada MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.** <br>
- Buka file `/etc/bind/delegasi/gunung.semerub14.pw` pada MOJOKERTO dan edit seperti gambar di bawah ini: <br>
![alt text](/images/7.1.png) <br>
- Kemudian `ping naik.gunung.semerub14.pw` pada GRESIK. <br>
![alt text](/images/7.2.png) <br>

**8. Membuat `DocumentRoot` pada `/var/www/semerub14.pw` yang dapat diakses melalui `http://semerub14.pw/index.php/home`.** <br>
- Buka file `var/www/semerub14.pw` pada PROBOLINGGO dan edit seperti gambar di bawah ini: <br>
- Tambahkan `ServerName` dan `DocumentRoot`. <br>
![alt text](/images/8.1.PNG) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `semerub14.pw`. <br>
![alt text](/images/8.2.jpeg) <br>

**9. Mengatifkan mode rewrite sehingga menjadi `http://semerub14.pw/home`.** <br>
- Aktifkan `a2enmod rewrite` pada PROBOLINGGO. <br>
![alt text](/images/9.1.png) <br>
- Buka file `var/www/semerub14.pw` dan edit seperti gambar di bawah ini: <br>
- Ganti `All` pada `AllowOverride`. <br>
![alt text](/images/9.2.png) <br>
- Edit file `.htaccess` seperti berikut: <br>
![alt text](/images/9.3.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `semerub14.pw/home`. <br>
![alt text](/images/9.4.jpeg) <br>

**10. Mengatur struktur folder pada `var/www/penanjakan.semerub14.pw`.** <br>
- Mengekstrak file ke folder penanjakan.semerub14.pw. <br>
![alt text](/images/10.1.png) <br>
- Tambahkan ServerName dan DocumentRoot dengan `penanjakan.semerub14.pw`. <br>
![alt text](/images/10.2.png) <br>
- Aktifkan `a2ensite penanjakan.semerub14.pw`. <br>
![alt text](/images/10.3.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `penanjakan.semerub14.pw`. <br>
![alt text](/images/10.4.png) <br>

**11. Enable directory listing hanya pada foolder `/public`.** <br>
- Tambahkan `Option +Indexes` untuk folder `penanjakan.semerub14.pw/public` dan `Option -Indexes` untuk folder `penanjakan.semerub14.pw/public/*`. <br>
![alt text](/images/11.1.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `penanjakan.semerub14.pw/public/`. <br>
![alt text](/images/11.2.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `penanjakan.semerub14.pw/public/css/`. <br>
![alt text](/images/11.3.png) <br>

**12. Mengganti error default 404.** <br>
- Tambahkan `ErrorDocument 404/errors/404html` pada `penanjakan.semerub14.pw`. <br>
![alt text](/images/12.1.png) <br>
- Lakukan `service apache2 restart`. <br>
![alt text](/images/12.2.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke link yang sebenarnya tidak ada. <br>
![alt text](/images/12.3.jpeg) <br>

**13. Mengubah alias `penanjakan.semerub14.pw/public/javascript` menjadi `penanjakan.semerub14.pw/js`.** <br>
- Menambahkan `Alias "/js"` seperti gambar di bawah ini. <br>
![alt text](/images/13.1.png) <br>
- Lakukan `service apache2 restart`. <br>
![alt text](/images/13.2.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `penanjakan.semerub14.pw/js`. Hasilnya tidak lagi not found, karena folder javascript memang tidak bisa di akses. <br>
![alt text](/images/13.3.png) <br>

**14. Membuat `naik.gunung.semerub14.pw` di port 8888.** <br>
- Setting `VirtualHost *:8888`, tambahkan ServerName dan DocumentRoot untuk `naik.gunung.semerub14.pw`. <br>
![alt text](/images/14.1.png) <br>
- Lalu pada file `/etc/apache2/ports.conf` tambahkan Listen untuk port 8888. <br>
![alt text](/images/14.2.png) <br>
- Lakukan `a2ensite naik.gunung.semerub14.pw` dan restart apache. <br>
![alt text](/images/14.3.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `naik.gunung.semerub14.pw:8888`. <br>
![alt text](/images/14.4.png) <br>

**15. Membuat auth username dan password pada `naik.gunung.semerub14.pw`.** <br>
- Jalankan `htpasswd -c /etc/apache2/.htpasswd semerub14.pw` untuk membuat username semerub14.pw. Kemudian masukkan password. <br>
![alt text](/images/15.1.png) <br>
- Lalu tambahkan Auth untuk directory `naik.gunung.semerub14.pw`. <br>
![alt text](/images/15.2.png) <br>
- Lakukan `service apache2 restart`. <br>
![alt text](/images/15.3.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `naik.gunung.semerub14.pw:8888`. <br>
![alt text](/images/15.4.png) <br>
- Setelah berhasil masuk maka muncul tampilan seperti di bawah ini. <br>
![alt text](/images/15.5.png) <br>

**16. Mengarahkan IP 10.151.83.124 ke `semerub14.pw`.** <br>
- Rubah .htaccess default pada PROBOLINGGO untuk meredirect ip PROBOLINGGO ke `semerub02.pw`. <br>
![alt text](/images/16.2.png) <br>
- Ganti `AllowOverride None` jadi `All` untuk directory `/var/www/`. <br>
![alt text](/images/16.3.png) <br>
- Lakukan `service apache2 restart`. <br>
![alt text](/images/16.4.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `10.151.83.124`. <br>
![alt text](/images/16.5.jpeg) <br>

**17. Mengarahkan req gambar yang mengandung substring "semeru" ke `semeru.jpg`.** <br>
- Edit file .htaccess seperti berikut. <br>
![alt text](/images/17.1.png) <br>
- Pada `/sites-available/penanjakan.semerub14.pw` tambahkan `AllowOverride All` untuk directory `/var/www/penanjakan.semerub02.pw`. <br>
![alt text](/images/17.2.png) <br>
- Untuk melihat hasilnya dapat diakses dengan browser ke `penanjakan.semerub14.pw/public/images/semeru.jpg`. <br>
![alt text](/images/17.3.jpeg) <br>


