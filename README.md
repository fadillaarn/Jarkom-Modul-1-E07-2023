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

## Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

### Jawaban
Untuk mengetahui web server yang digunakan pada portal tersebut, kita dapat melihat pada salah satu paket berprotokol HTTP. Oleh karena itu, untuk mempermudah dan memfokuskan pencarian paket, saya akan menerapkan display filter `http`.
![2-1](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/64c933c8-7ed2-4ad8-ac77-274a327467f4)
Setelah itu, Follow HTTP stream pada salah satu paket berprotokol HTTP yang ada.
![2-2](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/62eecba1-c5f0-4720-91c5-94419adf436d)
Didapatkan detail sebagai berikut dan ditemukan web server yang digunakan, yakni **gunicorn**.
![2-3](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/7f2fad58-99f2-4631-b48c-845c568efd43)

## Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
1. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah `239.255.255.250` dengan port `3702`?
2. Protokol layer transport apa yang digunakan?

### Jawaban

## Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

### Jawaban
Pada soal ini, kita diminta untuk mencari nilai checksum dari header paket nomor 130. Agar lebih cepat, kita dapat menggunakan tool "Go to spesified packet" di Wireshark.
![4-1](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/b49451fe-73d9-4833-8ee8-63d2052727e2)
Ternyata ditemukan paket yang diminta berprotokol QUIC (Quick UDP Internet Connections). Highlight paket tersebut dengan cara mengkliknya dan lihat detail pada kolom kiri bawah.
![4-2](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/b5db59b7-8588-485e-9aae-1c56768355b2)
Expand bagian User Datagram Protocol dan ditemukan checksum dari header paket ini, yaitu `0x18e5`.
![4-3](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/a03d51ec-6457-4149-a07b-d2e30248ce4b)

## Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
1. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
2. Port berapakah pada server yang digunakan untuk service SMTP?
3. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

### Jawaban

## Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan `server SOURCE ADDRESS 7812 is invalid`. ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Jawaban
Beberapa hint yang dapat dilihat dari soal adalah sebagai berikut. 
- `server SOURCE ADDRESS 7812 is invalid`
- a1 e5 u21
- Terdapat beberapa huruf kapital pada kalimat soal yang apabila digabung membentuk kata "SUBSTITUSI"

Setelah melakukan analisis lebih lanjut terhadap hint yang ada, kemungkinan kita diminta untuk mencari paket nomor 7812. Oleh karena itu, langsung saja kita menuju paket nomor 7812.
![6-1](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/c74c7b06-8420-4028-a559-d03580e15c22)
Ditemukan paket tersebut memiliki SOURCE ADDRESS `104.18.14.101`
![6-2](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/41b6cb8f-8448-43b6-ba41-fa5d25a9d255)
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

## Soal 7
Berapa jumlah packet yang menuju IP `184.87.193.88`?

### Jawaban

## Soal 8
Berikan kueri filter sehingga Wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

### Jawaban
Untuk mengambil semua protokol paket, baik TCP maupun UDP, yang menuju port 80, kita dapat menggunakan kueri filter sebagai berikut.
```
tcp.dstport == 80 || udp.dstport == 80
```
Berikut adalah hasil capture paket dari kueri filter yang telah digunakan.
![8](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/5dd97260-2c01-4a81-8592-4683d3b545c1)

## Soal 9
Berikan kueri filter sehingga Wireshark hanya mengambil paket yang berasal dari alamat `10.51.40.1` tetapi tidak menuju ke alamat `10.39.55.34`!

### Jawaban

## Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet!

### Jawaban
Untuk mendapatkan paket yang berprotokol Telnet, kita terapkan display filter `telnet` pada Wireshark sebagai berikut.
![image](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/2812ce7c-89c0-46cc-9151-8359451b5320)
Dari hasil capture di atas, dapat kita amati terdapat banyak paket yang berprotokol Telnet. Saya mencoba untuk melakukan Follow TCP Stream pada beberapa paket acak dan ditemukan kredensial user yang benar pada paket nomor 231.
![image](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/f48cac6d-1646-4be8-a174-4b549790e93f)
![image](https://github.com/fadillaarn/Jarkom-Modul-1-E07-2023/assets/107914177/0d4a1c36-48b6-4b7e-83f1-450ac50197c2)
Kredensial user tersebut adalah sebagai berikut.
```
Login: dhafin
Password: kesayangannyak0k0
```
Format yang diminta pada soal adalah `[username]:[password]`, sehingga jawaban akhir setelah diformat adalah sebagai berikut.
```
dhafin:kesayangannyak0k0
```