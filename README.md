# Jarkom-Modul-2-D02-2021
**Laporan Resmi Praktikum JarKom** \
**Nama Anggota Kelompok D02**
- Sabrina Lydia Simanjuntak (05111940000107)
- Zulfayanti Sofia Solichin (05111940000189)
- Nadia Tiara Febriana (05111940000217)<br><br>
Luffy adalah seorang yang akan jadi Raja Bajak Laut. Demi membuat Luffy menjadi Raja Bajak Laut, Nami ingin membuat sebuah peta, bantu Nami untuk membuat peta berikut :

<img width="642" alt="Screen Shot 2021-10-28 at 22 49 43" src="https://user-images.githubusercontent.com/72669398/139291194-1e71e271-4ae7-4ed9-9549-54fad2e22d1a.png">

EniesLobby akan dijadikan sebagai DNS Master, Water7 akan dijadikan DNS Slave, dan Skypie akan digunakan sebagai Web Server. Terdapat 2 Client yaitu Loguetown, dan Alabasta. Semua node terhubung pada router Foosha, sehingga dapat mengakses internet. 

# Soal & Jawaban
# Soal No 1
EniesLobby akan dijadikan sebagai DNS Master, Water7 akan dijadikan DNS Slave, dan Skypie akan digunakan sebagai Web Server. Terdapat 2 Client yaitu Loguetown, dan Alabasta. Semua node terhubung pada router Foosha, sehingga dapat mengakses internet.

Pertama yang dilakukan terlebih dahulu adalah membuat topologi seperti berikut:

![no1](https://user-images.githubusercontent.com/72669398/139531800-575957e2-0747-4627-9871-f3029f3dcfb5.jpg)

Kemudian, konfigurasi dilakukan pada setiap node yang ada seperti berikut:
- Foosha
dengan menjalankan command ``iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.22.0.0/16`` pada router foosha gunanya agar dapat terkoneksi dengan internet.

![no1-a](https://user-images.githubusercontent.com/72669398/139532067-211ff5bb-139a-4df1-9da0-ec3ddf1eb084.jpg)

- Loguetown

![no1-b](https://user-images.githubusercontent.com/72669398/139532023-bfb397e9-8eda-4e94-98fb-ebbc02792053.jpg)

- Alabasta

![no1-c](https://user-images.githubusercontent.com/72669398/139532030-d27cb209-4c2a-4a23-bbdb-9839961f6ccc.jpg)

- EniesLobby

![no1-d](https://user-images.githubusercontent.com/72669398/139532033-d6ade27c-f08e-4336-9b85-076087762f5e.jpg)

- Water7

![no1-f](https://user-images.githubusercontent.com/72669398/139532611-e8c121ba-c061-4d6c-86c1-64a800db6f4e.jpg)

- Skypie

![no1-e](https://user-images.githubusercontent.com/72669398/139532034-b59be5ae-9cb5-40c0-b196-778cbd7cb360.jpg)

Diatas merupakan hasil dari setiap node yang sudah terkoneksi dengan internet.

# Soal No 2
Luffy ingin menghubungi Franky yang berada di EniesLobby dengan denden mushi. Kalian diminta Luffy untuk membuat website utama dengan mengakses ``franky.yyy.com`` dengan alias ``www.franky.yyy.com`` pada folder kaizoku

Kami melakukan konfigurasi terhadap file ``/etc/bind/named.conf.local`` dengan menambahkan seperti berikut pada server EniesLobby, :

![no2-a](https://user-images.githubusercontent.com/72669398/139532616-911786c6-c4e6-486d-bdb8-a23c80e39d4d.jpg)

Kemudian, dibuat direktori baru ``/etc/bind/kaizoku`` Selanjutnya, menambahkan konfigurasi pada ``/etc/bind/kaizoku/franky.d02.com`` 

![no2-b](https://user-images.githubusercontent.com/72669398/139532619-37f9750b-a33e-4555-b963-55d4f9a24bdf.jpg)

Kemudian, dilakukan testing ``ping franky.d02.com``dan ``ping www.franky.d02.com``menghasilkan seperti berikut:

![no2-c](https://user-images.githubusercontent.com/72669398/139532621-c51c4602-0b86-4452-bae4-07a761cfaff3.jpg)

# Soal No 3
Setelah itu buat subdomain ``super.franky.yyy.com``dengan alias ``www.super.franky.yyy.com`` yang diatur DNS nya di EniesLobby dan mengarah ke Skypie

Pada server EniesLobby, pada file ``/etc/bind/kaizoku/franky.d02.com`` diedit menjadi seperti berikut:

![no3-a](https://user-images.githubusercontent.com/72669398/139533158-6a633d40-aba1-4e11-8c18-f37cf2607e6a.jpg)

Kemudian edit file``/etc/bind/named.conf.options`` menjadi sebagi berikut:

![no3-b](https://user-images.githubusercontent.com/72669398/139533162-aba4cff1-b332-4506-a409-949b890d3ffe.jpg)

Kemudian edit file``/etc/bind/named.conf.local`` menjadi sebagi berikut:

![no3-c](https://user-images.githubusercontent.com/72669398/139533163-a10b9333-5093-4b92-8d1e-2fdc0d7cb72b.jpg)

Kemudian pada node ``Skypie`` buka file ``/etc/bind/named.conf.options`` dan edit filenya menjadi sebagai berikut:

![no3-d](https://user-images.githubusercontent.com/72669398/139533165-76629c50-65c6-4350-8532-603eae4d5e18.jpg)

Kemudian, buat direktori dengan nama delegasi, lalu Copy db.local ke direktori pucang dan edit namanya menjadi super.franky.d02.com. Lalu edit file tersebut menjadi sebagai berikut:

![no3-e](https://user-images.githubusercontent.com/72669398/139533252-6eb25c20-d923-4984-8570-32101ae42e30.jpg)

Kemudian, dilakukan testing ``ping super.franky.d02.com``dan ``ping www.super.franky.d02.com`` pada client Loguetown menghasilkan seperti berikut:

![no3-f](https://user-images.githubusercontent.com/72669398/139533253-41dfa946-c784-4157-9766-2dbb3ac4dd17.jpg)

# Soal No 4
Buat juga reverse domain untuk domain utama 

Pada Server EnniesLobby file ``/etc/bind/named.conf.local`` diedit menjadi sebagai berikut:

![no4-a](https://user-images.githubusercontent.com/72669398/139533600-02ecff88-37a5-4436-a43a-3f5f30abd8c1.jpg)


Kemudian, Copykan file db.local pada path /etc/bind ke dalam folder jarkom yang baru saja dibuat dan ubah namanya menjadi ``2.22.10.in-addr.arpa`` lalu ubah konfigurasi pada file ``/etc/bind/kaizoku/2.22.10.in-addr.arpa`` dilakukan seperti berikut ini:

![no4-b](https://user-images.githubusercontent.com/72669398/139533608-2afd91cd-7a63-465c-9ffc-da3e9fc668d7.jpg)

Kemudian dilakukan testing seperti berikut:

![no4-c](https://user-images.githubusercontent.com/72669398/139533610-fbd3faa9-30fe-4d04-9821-71d896c19290.jpg)

# Soal No 5
Supaya tetap bisa menghubungi Franky jika server EniesLobby rusak, maka buat Water7 sebagai DNS Slave untuk domain utama

Lakukan konfigurasi pada file ``/etc/bind/named.conf.local``

![no5-a](https://user-images.githubusercontent.com/72669398/139533611-47a5c5a8-afae-4ef8-b644-a9f0443107d0.jpg)

![no5-b](https://user-images.githubusercontent.com/72669398/139533612-55a22668-7898-45be-bf82-9642cc58353c.jpg)

Kemudian untuk testing, matikan servi bind9 pada server ``EniesLobby`` testing seperti berikut dengan melakukan ping dengan server Longuetown:

![no5-c](https://user-images.githubusercontent.com/72669398/139533614-acf02a5b-a4c8-4789-8c52-3be327012eb9.jpg)


# Soal No 6
Setelah itu terdapat subdomain ``mecha.franky.yyy.com`` dengan alias ``www.mecha.franky.yyy.com`` yang didelegasikan dari EniesLobby ke Water7 dengan IP menuju ke Skypie dalam folder sunnygo

# Soal No 7
Untuk memperlancar komunikasi Luffy dan rekannya, dibuatkan subdomain melalui Water7 dengan nama ``general.mecha.franky.yyy.com`` dengan alias`` www.general.mecha.franky.yyy.com`` yang mengarah ke Skypie

# Soal No 8
Setelah melakukan konfigurasi server, maka dilakukan konfigurasi Webserver. Pertama dengan webserver ``www.franky.yyy.com``. Pertama, luffy membutuhkan webserver dengan DocumentRoot pada ``/var/www/franky.yyy.com``. 

# Soal No 9
Setelah itu, Luffy juga membutuhkan agar url ``www.franky.yyy.com/index.php/home`` dapat menjadi menjadi ``www.franky.yyy.com/home``. 

# Soal No 10
Setelah itu, pada subdomain ``www.super.franky.yyy.com``, Luffy membutuhkan penyimpanan aset yang memiliki DocumentRoot pada ``/var/www/super.franky.yyy.com`` .ini!

# Soal No 11
Akan tetapi, pada folder ``/public``, Luffy ingin hanya dapat melakukan directory listing saja.

# Soal No 12
Tidak hanya itu, Luffy juga menyiapkan error file ``404.html`` pada folder ``/error`` untuk mengganti error kode pada apache . 

# Soal No 13
Luffy juga meminta Nami untuk dibuatkan konfigurasi virtual host. Virtual host ini bertujuan untuk dapat mengakses file asset ``www.super.franky.yyy.com/public/js`` menjadi ``www.super.franky.yyy.com/js``. 

# Soal No 14
Dan Luffy meminta untuk web ``www.general.mecha.franky.yyy.com`` hanya bisa diakses dengan ``port 15000`` dan ``port 15500`` 

# Soal No 15
dengan autentikasi ``username luffy`` dan ``password onepiece`` dan file di ``/var/www/general.mecha.franky.yyy`` 

# Soal No 16
Dan setiap kali mengakses IP Skypie akan dialihkan secara otomatis ``ke www.franky.yyy.com``

# Soal No 17
Dikarenakan Franky juga ingin mengajak temannya untuk dapat menghubunginya melalui website ``www.super.franky.yyy.com``, dan dikarenakan pengunjung web server pasti akan bingung dengan randomnya images yang ada, maka Franky juga meminta untuk mengganti request gambar yang memiliki substring ``“franky”`` akan diarahkan menuju ``franky.png``. Maka bantulah Luffy untuk membuat konfigurasi dns dan web server ini!

# Kendala
