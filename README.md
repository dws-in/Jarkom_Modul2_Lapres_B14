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
1. Membuat domain `http://semerub14.pw` dengan DNS MALANG dan mengarah ke IP Server PROBOLINGGO sebagai berikut:
2. Membuat alias `http://www.semerub14.pw` dengan konfigurasi sebagai barikut:
3. Membuat subdomain `http://penanjakan.semerub14.pw` dengan konfigurasi sebagai berikut:
4. Membuat reverse domain untuk domain utama sebagai berikut:
5. Membuat DNS Server Slave pada MOJOKERTO sebagai berikut:
6. Membuat subdomain `http://gunung.semerub14.pw` pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO sebagai berikut:
7. Membuat subdomain `http://naik.gunung.semerub14.pw` pada MOJOKERTO dan mengarah ke IP Server PROBOLINGGO sebagai berikut:
8. Membuat `DocumentRoot` pada `/var/www/semerub14.pw` yang dapat diakses melalui `http://semerub14.pw/index.php/home` sebagai berikut:
9. Mengatifkan mode rewrite sehingga menjadi `http://semerub14.pw/home` sebagai berikut:
10. 

