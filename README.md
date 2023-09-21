# Laporan Resmi Praktikum Jaringan Komputer Modul 1
### Kelompok : B03
### Anggota :
| Nama    | NRP | Kelas |
| ------- | --- | --- |
| Syarifah Talitha Erfany | 5025211175  | Jaringan Komputer B |
| Wan Sabrina Mayzura    | 5025211023  | Jaringan Komputer B |

# Soal dan Solusi
## 1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
**a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?**
- Untuk mencari aktivitas yang berinteraksi dengan suatu file (salah satunya adalah mengunggah), cari packet yang memiliki perintah "STOR" yang digunakan untuk mengunggah file ke server. Lalu digunakan syntax `ftp.request.command == STOR` karena menggunakan protokol FTP dan request command digunakan untuk memfilter perintah yang dikirim oleh klien.

    ![1a](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/1a1.png)

- Setelah didapatkan bahwa aktivitas menunggah terjadi di packet `147`, periksa detail packet untuk menemukan sequence number (raw) sebagai berikut:

    ![1a](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/1a2.png)

**b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?**
- Acknowledge number pada packet juga didapatkan dari detail packet 147.

    ![1b](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/1b.png)

**c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?**

- Untuk mendapati response dari aktivitas packet 147, dilakukan filtering menggunakan `frame contains "c75-GrabThePhisher.zip"` untuk mencari packet yang juga berinteraksi dengan file yang diunggah. Lalu didapati packet `149` yang terdapat info bertulisan Response. Dan didapatkan sequence number (raw) sebagai berikut:

    ![1c](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/1c.png)

**d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?**
- Acknowledge number pada packet juga didapatkan dari detail packet 149.

    ![1d](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/1d.png)

- Sehingga didapatkan flag dari jawaban-jawaban di atas:

    ![terminal 1](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no1/terminal%201.png)

**Kendala:** Tidak ada kendala pada pengerjaan nomor 1.

## 2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
- Pada file PCAP, dilakukan filtering untuk mencari packet yang menggunakan protocol `HTTP` karena yang akan dicari adalah suatu website. Lalu dipilih packet yang memiliki tulisan `OK` dan `text/html`.

    ![2](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no2/2.1.png)

- Lalu karena ini merupakan soal stream, untuk mendapatkan nama web server yang digunakan, `follow http stream` seperti berikut:

    ![2](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no2/2.2.png)

- Lalu pada kode HTML, cari nama server tersebut dan didapatkan `gunicorn` sebagai nama server tersebut.

    ![2](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no2/2.3.png)

- Sehingga didapatkan flag dari jawaban tersebut:

    ![2](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no2/2.4.png)

**Kendala:** Tidak ada kendala pada pengerjaan nomor 2.

## 3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

**a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?**

- Untuk pencarian menggunakan IP source dan IP destination bisa menggunakan `(ip.src == 239.255.255.250 || ip.dst == 239.255.255.250)`

![3a.1](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no3/no3a.1.png)

- Setelah diketahui IP-nya, akan dicari port 3702. Karena setelah difilter berdasarkan IP, didapatkan 2 protokol yaitu SSDP dan UDP.

- Pada gambar dibawah SSDP tidak ada port pada pertanyaan yang diinginkan.

- Digunakan protokol UDP dan didapatkan jawaban sebanyak 21 paket yang tercapture.

**b. Protokol layer transport apa yang digunakan?**
UDP

**Kendala:** Tidak ada kendala pada pengerjaan nomor 3.

## 4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?

- Mnggunakan `frame.number == 130` untuk mencari nomor paket yang diinginkan.

- Untuk mencari checksum dapat digunakan `ip.checksum` dalam filter tambahannya, atau langsung dapat mengklik 2x di paket yang sudah terfilter menggunakan frame number.

- Lalu didapatkan checksum paketnya adalah

**Kendala:** Tidak ada kendala pada pengerjaan nomor 4.

## 5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
**a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?**

**b. Port berapakah pada server yang digunakan untuk service SMTP?**

**c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?**

**Kendala:** 

## 6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
- Berdasarkan soal, `server SOURCE ADDRESS 7812` menunjukkan bahwa packet yang akan ditelusuri adalah packet pada frame 7812. Sehingga dilakukan filtering dengan syntax `frame.number == 7812`, dan didapatkan detail sebagai berikut:

    ![6](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no6/6.1.png)

- Pada soal yang diberikan, terdapat clue dari pesan tersembunyi yang membentuk kata `"SUBTITUSI"`. 

    ![6](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no6/6.2.png)

- Lalu pada hasil pencarian hanya menampilkan `a1 e5 u21`, dan dapat ditafsirkan bahwa angka pada sebelah kanan masing-masing huruf adalah urutan huruf tersebut di dalam suatu abjad.

    | Huruf    | Urutan |
    | ------- | ---   |
    | a       | 1     |
    | b       | 2     |
    | c       | 3     |
    | d       | 4     |
    | e       | 5     |
    | f       | 6     |
    | g       | 7     |
    | h       | 8     |
    | i       | 9     |
    | j       | 10    |
    | k       | 11    |
    | l       | 12    |
    | m       | 13    |
    | n       | 14    |
    | o       | 15    |
    | p       | 16    |
    | q       | 17    |
    | r       | 18    |
    | s       | 19    |
    | t       | 20    |
    | u       | 21    |
    | v       | 22    |
    | w       | 23    |
    | x       | 24    |
    | y       | 25    |
    | z       | 26    |

- Lalu dari IP yang didapatkan pada packet 7812, lakukan substitusi IP tersebut dari angka menjadi huruf.
    ```
    104.18.14.101
    10 4 18 14 10 1

    10 = J
    4 = D
    18 = R
    14 = N
    10 = J
    1 = A

    JDRNJA
    ```

- Sehingga didapatkan flag dari jawaban tersebut:

    ![6](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no6/6.3.png)

**Kendala:** Soal nomor 6 tidak dapat diselesaikan pada masa praktikum, sehingga diselesaikan pada masa revisi. 

## 7. Berapa jumlah packet yang menuju IP 184.87.193.88?

- dengan menggunakan filter `ip.addr == 184.87.193.88` dapat diketahui jumlah paket yang menuju/destination IP 184.87.193.88 adalah sebanyak 6

**Kendala:** Tidak ada kendala pada pengerjaan nomor 7.

## 8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)
- Kueri filter yang digunakan untuk mengambil semua protokol paket yang menuju port 80 adalah `tcp.dstport == 80 || udp.dstport == 80`. Filter `tcp.dstport == 80` berarti kita mencari paket-paket yang menuju ke port 80 menggunakan protokol TCP. Filter `udp.dstport == 80` berarti kita mencari paket-paket yang menuju ke port 80 menggunakan protokol UDP.

- Sehingga didapatkan flag dari jawaban tersebut:

    ![8](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no8/8.png)

**Kendala:** Tidak ada kendala pada pengerjaan nomor 8.

## 9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

- Kueri yang digunakan adalah `ip.src == 10.51.40.1 && ip.dst != 10.51.40.1`

**Kendala:** Tidak ada kendala pada pengerjaan nomor 9. 

## 10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet.
- Pada file PCAP, dilakukan filtering untuk mencari packet yang menggunakan protokol `telnet` saja.

    ![10.1](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no10/10.1.png)

- Lalu pilih salah satu packet (yang paling bawah). Dan follow stream (TCP Stream).

    ![10.2](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no10/10.2.png)

- Lalu didapatkan username dari `Login: ddhhaaffiinn` dan password dari `Password: kesayangannyak0k0`.

    ![10.3](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no10/10.3.png)

- Sehingga didapatkan flag dari jawaban (untuk username ddhhaaffiinn tidak berhasil, sehingga digunakan dhafin saja sebagai username) tersebut:

    ![10.4](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/raw/main/no10/10.4.png)

**Kendala:** Tidak ada kendala pada pengerjaan nomor 10.


