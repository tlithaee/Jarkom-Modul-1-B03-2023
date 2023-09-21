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

gambar

- Setelah didapatkan bahwa aktivitas menunggah terjadi di packet `147`, periksa detail packet untuk menemukan sequence number (raw) sebagai berikut:

gambar

**b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?**
- Acknowledge number pada packet juga didapatkan dari detail packet 147.

gambar

**c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?**

- Untuk mendapati response dari aktivitas packet 147, dilakukan pemfilteran menggunakan `frame contains "c75-GrabThePhisher.zip"` untuk mencari packet yang juga berinteraksi dengan file yang diunggah. Lalu didapati packet `149` yang terdapat info bertulisan Response. Dan didapatkan sequence number (raw) sebagai berikut:

gambar

**d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?**
- Acknowledge number pada packet juga didapatkan dari detail packet 149.

gambar

- Sehingga didapatkan flag dari jawaban-jawaban di atas:
gambar

**Kendala:** Tidak ada kendala pada pengerjaan nomor 1.

## 2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
- Pada file PCAP, dilakukan pemfilteran untuk mencari packet yang menggunakan protocol `HTTP` karena yang akan dicari adalah suatu website. Lalu dipilih packet yang memiliki tulisan `OK` dan `text/html`.

gambar 2.1

- Lalu karena ini merupakan soal stream, untuk mendapatkan nama web server yang digunakan, `follow http stream` seperti berikut:

gambar 2.2

- Lalu pada kode HTML, cari nama server tersebut dan didapatkan `gunicorn` sebagai nama server tersebut.

gambar 2.3

- Sehingga didapatkan flag dari jawaban tersebut:
gambar 2.4

**Kendala:** Tidak ada kendala pada pengerjaan nomor 2.

## 3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

**a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?**

Untuk pencarian menggunakan IP source dan IP destination bisa menggunakan `(ip.src == 239.255.255.250 || ip.dst == 239.255.255.250)`

**Screenshot :**

![3a.1](https://github.com/tlithaee/Jarkom-Modul-1-B03-2023/blob/main/no3/no3a.1.png)

setelah diketahui IP-nya, akan dicari port 3702. Karena setelah difilter berdasarkan IP, didapatkan 2 protokol yaitu SSDP dan UDP

### b. Protokol layer transport apa yang digunakan?
UDP

**Kendala:** 

## 4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?
**Kendala:** 

## 5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
**a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?**

**b. Port berapakah pada server yang digunakan untuk service SMTP?**

**c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?**

**Kendala:** 

## 6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
**Kendala:** 

## 7. Berapa jumlah packet yang menuju IP 184.87.193.88?
**Kendala:** 

## 8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)
**Kendala:** 

## 9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!
**Kendala:** 

## 10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet
**Kendala:** 


