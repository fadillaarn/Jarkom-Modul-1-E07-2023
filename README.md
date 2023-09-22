# Jarkom-Modul-1-E07-2023
Laporan Resmi Praktikum Modul 1 Jaringan Komputer 2023

### Kelompok E07
| Nama | NRP |
|:----:|:---:|
| [Akmal Sulthon Fathulloh](https://github.com/afsulthon) | 5025211047 |
| [Fadilla Rizky Nurhidayah](https://github.com/fadillaarn) | 5025211110 |

### Daftar Soal
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 6](#soal-6)
- [Soal 7](#soal-7)
- [Soal 8](#soal-8)
- [Soal 9](#soal-9)
- [Soal 10](#soal-10)

## Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
1. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
2. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?
3. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
4. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
   
### Jawaban
Mencari pada protocol FTP yang memiliki perintah `STOR`, karena `STOR` merupakan perintah untuk melakukan upload file ke FTP server.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/46450e69-c3b1-4308-bed8-bcb853b28f96">

Melihat ke bagian detail Transmission Control Protocol, dan didapatkan sequence number (raw) dan acknowledge number (raw) untuk pertanyaan 1 dan 2.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/066c33d4-2239-4bcc-930d-98cc8c90a723">

Kemudian menerapkan display filter `ftp contains "c75-GrabThePhisher.zip"`.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/2120b999-73ce-443a-8a7b-7ad7a0519ea4">

Melihat ke bagian detail Transmission Control Protocol lagi, dan didapatkan sequence number (raw) dan acknowledge number (raw) untuk pertanyaan 3 dan 4.  
<img width="75%" alt="Screenshot 2023-09-22 at 08 24 46" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/d1c7bd0e-c1f3-4376-b08b-119eb169dbaf">

Screenshot flag pada netcat  
<img width="75%" alt="Screenshot 2023-09-22 at 08 27 36" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/69d7c7a8-1496-4490-9a55-16e80cd0defc">

## Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

### Jawaban
Untuk mengetahui web server yang digunakan pada portal tersebut, kita dapat melihat pada salah satu paket berprotokol HTTP. Oleh karena itu, untuk mempermudah dan memfokuskan pencarian paket, saya akan menerapkan display filter `http`.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/64c933c8-7ed2-4ad8-ac77-274a327467f4">

Setelah itu, Follow HTTP stream pada salah satu paket berprotokol HTTP yang ada.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/62eecba1-c5f0-4720-91c5-94419adf436d">

Didapatkan detail sebagai berikut dan ditemukan web server yang digunakan, yakni **gunicorn**.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/7f2fad58-99f2-4631-b48c-845c568efd43">

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/3f168013-f1ec-4954-954f-11548a1901eb">

## Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
1. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah `239.255.255.250` dengan port `3702`?
2. Protokol layer transport apa yang digunakan?

### Jawaban
Menerapkan display filter `(ip.src == 239.255.255.250 and udp.port == 3702) or (ip.dst == 239.255.255.250 and udp.port == 3702)`.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/1ea37527-e37a-463f-b27c-d4e866b0831d">

Sehingga didaptkan capture paket berikut, dimana jumlahnya yang tercapture ada **21** paket dengan protokol layer yang digunakan merupakan **User Datagram Protocol(UDP)**
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/d54a4738-445b-4e9a-90d4-c048a5e8cf02">

Screenshot flag pada netcat<br>
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/99733f16-8415-474d-979f-1d0b2e5e6e3d">

## Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

### Jawaban
Pada soal ini, kita diminta untuk mencari nilai checksum dari header paket nomor 130. Agar lebih cepat, kita dapat menggunakan tool "Go to spesified packet" di Wireshark.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/b49451fe-73d9-4833-8ee8-63d2052727e2">

Ternyata ditemukan paket yang diminta berprotokol QUIC (Quick UDP Internet Connections). Highlight paket tersebut dengan cara mengkliknya dan lihat detail pada kolom kiri bawah.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/b5db59b7-8588-485e-9aae-1c56768355b2">

Expand bagian User Datagram Protocol dan ditemukan checksum dari header paket ini, yaitu `0x18e5`.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/a03d51ec-6457-4149-a07b-d2e30248ce4b">

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/d2f72d57-38be-4ebe-bbf8-a5f665ad9726">

## Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
1. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
2. Port berapakah pada server yang digunakan untuk service SMTP?
3. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

### Jawaban
Menerapkan display filter `smtp`.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/ecf500a2-5574-4f97-96d3-cfae61dfbbaa">

Kemudian, Follow TCP Stream pada paket tersebut
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/121f5f28-d009-4fe3-8e67-13c8abf1329e">

Sehingga, didapatkan sebagai berikut.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/1e91b12f-8f12-4e1b-84a9-205e94c36117">

Berdasarkan penemuan tadi, kita diminta untuk men-decode password tersebut dengan Base64. Dalam hal ini, kita gunakan website https://www.rapidtables.com/web/tools/base64-decode.html dan didapatkan hasil decoding sebagai berikut.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/e699df4c-b102-4bdd-8fa2-0b5d0e23be2c">

Lalu gunakan password yang telah didapatkan tadi untuk mengekstrak zip.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/31787485-53c4-4a1e-bc8c-cdc8b7d33eb5">

Maka, akan didapatkan file berikut.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/8dead238-c516-4c2c-8e91-bce6becd7d8a">

Setelah connect ke instance yang tertera tadi, maka jawaban dari pertanyaan untuk poin 1 adalah **60 paket**.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/9881c58e-3881-40a1-8601-af56b3e50448">

Untuk pertanyaan poin 2, port yang digunakan untuk service SMTP adalah **25**.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/164f2020-57ee-40e5-8e53-b607e2942821">

Pertanyaan poin 3, dari semua alamat IP yang tercapture, IP yang merupakan IP publik adalah **74.53.140.153**.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/0d99b970-6f0f-49ec-b8d6-db2355b63f83">

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/7a7d86e3-25cd-4754-831f-a3a56136cf5e">

## Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan `server SOURCE ADDRESS 7812 is invalid`. ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Jawaban
Beberapa hint yang dapat dilihat dari soal adalah sebagai berikut. 
- `server SOURCE ADDRESS 7812 is invalid`
- a1 e5 u21
- Terdapat beberapa huruf kapital pada kalimat soal yang apabila digabung membentuk kata "SUBSTITUSI"

Setelah melakukan analisis lebih lanjut terhadap hint yang ada, kemungkinan kita diminta untuk mencari paket nomor 7812. Oleh karena itu, langsung saja kita menuju paket nomor 7812.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/c74c7b06-8420-4028-a559-d03580e15c22">

Ditemukan paket tersebut memiliki SOURCE ADDRESS `104.18.14.101`.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/41b6cb8f-8448-43b6-ba41-fa5d25a9d255">

Dari kata-kata hint **SUBSTITUSI** dan hasil pencarian aneh **a1 e5 u21**, kemungkinan **a1 e5 u21** merupakan pasangan huruf alfabet dan urutannya secara alfabetik. Jadi, **a** disubstitusikan menjadi **1** karena **a** merupakan alfabet pertama. Begitu pula dengan **e** urutan **5** dan **u** urutan **21**. Pola enkripsi ini dikenal dengan **A1Z26 cipher**. Dari situ, dapat disimpulkan bahwa kemungkinan SOURCE ADDRESS yang telah ditemukan tadi juga dienkripsi dengan pola serupa.

```
104.18.14.101
```
Karena enkripsi **A1Z26 cipher** terbatas pada rentang 1 - 26, maka kita pecah masing-masing digitnya yang melebihi batas (>26) dan menjadi seperti berikut.
```
10 4 18 14 10 1
```
Kita decode ciphertext di atas dan mendapatkan hasil akhir plain text sebagai berikut.
```
JDRNJA
```

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/359ee1ef-1dea-4324-a7f5-25eca82b96c7">


## Soal 7
Berapa jumlah packet yang menuju IP `184.87.193.88`?

### Jawaban
Menerapkan display filter `ip.src == 184.87.193.88`, sehingga didapatkan **6 paket**.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/8b685ef9-b830-4d39-8713-fb81aa2c184b">

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/6e05ad13-6720-4e3a-a756-67bd06b6cee5">

## Soal 8
Berikan kueri filter sehingga Wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

### Jawaban
Untuk mengambil semua protokol paket, baik TCP maupun UDP, yang menuju port 80, kita dapat menggunakan kueri filter sebagai berikut.
```
tcp.dstport == 80 || udp.dstport == 80
```
Berikut adalah hasil capture paket dari kueri filter yang telah digunakan.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/5dd97260-2c01-4a81-8592-4683d3b545c1">

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/8d5ba204-2215-4512-8e8c-f6e5784420ea">

## Soal 9
Berikan kueri filter sehingga Wireshark hanya mengambil paket yang berasal dari alamat `10.51.40.1` tetapi tidak menuju ke alamat `10.39.55.34`!

### Jawaban
Untuk mengambil paket yang berasal dari alamat `10.51.40.1` tetapi tidak menuju ke alamat `10.39.55.34`, kita dapat menggunakan kueri filter sebagai berikut.
```
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34
```

Screenshot flag pada netcat  
<img width="563" alt="Screenshot 2023-09-22 at 08 59 22" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/91003946/70ed84a4-8f1c-456f-975e-f03404e97210">

## Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet!

### Jawaban
Untuk mendapatkan paket yang berprotokol Telnet, kita terapkan display filter `telnet` pada Wireshark sebagai berikut.  
<img src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/2812ce7c-89c0-46cc-9151-8359451b5320">

Dari hasil capture di atas, dapat kita amati terdapat banyak paket yang berprotokol Telnet. Saya mencoba untuk melakukan Follow TCP Stream pada beberapa paket acak dan ditemukan kredensial user yang benar pada paket nomor 231.  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/f48cac6d-1646-4be8-a174-4b549790e93f">
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/0d4a1c36-48b6-4b7e-83f1-450ac50197c2">

Kredensial user tersebut adalah sebagai berikut.
```
Login: dhafin
Password: kesayangannyak0k0
```
Format yang diminta pada soal adalah `[username]:[password]`, sehingga jawaban akhir setelah diformat adalah sebagai berikut.
```
dhafin:kesayangannyak0k0
```

Screenshot flag pada netcat  
<img width="75%" src="https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/33626fef-3a74-4814-a85b-b4277833dcde">

## Kendala
Beberapa kendala yang kami hadapi saat melakukan **Praktikum Modul 1 Jaringan Komputer 2023** adalah sebagai berikut.
- Konektivitas jaringan yang lambat akibat penggunaan VPN menjadi hambatan saat ingin mengunduh berkas yang diperlukan dalam rangka menyelesaikan soal.
- Koneksi server yang terkadang down, karena mungkin meng-handle banyak request sekaligus, juga menjadi hambatan.
- Sempat terjadi kesalahan teknis pada soal sehingga saat men-submit jawaban yang benar dianggap salah.