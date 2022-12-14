# Jarkom-Modul-1-C06-2022

## Anggota Kelompok

1. 5025202050 - Elshe Erviana Angely
2. 5025201051 - Muhammad Fath Mushaffa Azhar
3. 5025201076 - Raul Ilma Rajasa

## Soal 1

Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan. Tujuan pencarian tersebut adalah untuk menemukan web server yang digunakan pada "monta.if.its.ac.id"

Untuk itu, diterapkan filter yang dapat menampilkan semua paket dengan protokol HTTP dan host `monta.if.its.ac.id`, yaitu sebagai berikut:

```
http.request and http.host == "monta.if.its.ac.id"
```

dari filter tersebut didapatkan
![hasil-filter](https://cdn.discordapp.com/attachments/855800698602913792/1022144421560590416/unknown.png)
setelah itu dilakukan klik kanan dan `Follow TCP Stream`.
Didapatkan informasi berupa:
![informasi-1](https://cdn.discordapp.com/attachments/855800698602913792/1022144663928451154/unknown.png)

Dari hasil tersebut didapatkan informasi penting terkait web server yang digunakan, yaitu `nginx/1.10.3`.

## Soal 2

Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan. Diberikan clue berupa `ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id”`.

Untuk itu, diterapkan filter dengan protokol `http` yang teridentifikasi memiliki string "detail" dan "monta":

```
http contains "detail" and http contains "monta"
```

dari filter tersebut didapatkan
![hasil-filter](https://cdn.discordapp.com/attachments/855800698602913792/1022150353753481286/unknown.png)
setelah itu dilakukan klik kanan untuk `Follow TCP Stream`. Kemudian pada dropdown "Show data as" ubah dari ASCII menjadi Raw
Sehingga didapatkan informasi:
![informasi-1](https://cdn.discordapp.com/attachments/855800698602913792/1022150607517253703/unknown.png)
Dari hasil tersebut klik "Save as.." dan pada kolom `File name` set sebagai `soal2.zip`.
![informasi-2](https://cdn.discordapp.com/attachments/855800698602913792/1022151548668743680/unknown.png)

Kemudian ekstrak file `soal2.zip` tersebut sehingga akan muncul file `soal2` yang tidak memiliki ekstensi apapun.
![informasi-2](https://cdn.discordapp.com/attachments/855800698602913792/1022152175796883556/unknown.png)

Berikan ekstensi .html pada file `soal2` tersebut dengan merename-nya menjadi `soal2.html`:
![informasi-3](https://cdn.discordapp.com/attachments/855800698602913792/1022152504349302885/unknown.png)
Buka file `soal2.html` tersebut di browser seperti Google Chrome dan klik ID (4222):
![informasi-4](https://cdn.discordapp.com/attachments/855800698602913792/1022152949679521882/unknown.png)
Dari situ akan muncul popup yang menunjukkan detail dari proposal Tugas Akhir yang menunjukkan judul Tugas Akhirnya, yakni:
![informasi-4](https://cdn.discordapp.com/attachments/855800698602913792/1022153269662986351/unknown.png)
Sehingga ditemukan judul TA yang dibuka oleh Ishaq, yaitu: `Perancangan Sistem Pengendali Panas Otomatis pada Mesin Sangrai Kopi dengan Logika Fuzzy`

## Soal 3

Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan.
Untuk itu, diterapkan filter dengan protokol `tcp` dan `udp` karena pada soal tidak dispesifikasikan untuk jenis protokol apa. Lalu, filter dua protokol tersebut diperjelas dengan detail yang menampilkan paket yang menuju port 80 (dengan subdomain `dstport` - destined/tujuan port), sehingga filternya menjadi:

```
tcp.dstport == 80 or udp.dstport == 80
```

sehingga dari filter tersebut didapatkan paket-paket yang menuju port 80 (terdiri dari protokol TCP dan HTTP dari source yang sama):
![hasil-filter](https://cdn.discordapp.com/attachments/855800698602913792/1022154938375209000/unknown.png)

## Soal 4
Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan.
Untuk itu, diterapkan filter dengan protokol `tcp` dan `udp` karena pada soal tidak dispesifikasikan untuk jenis protokol apa. Lalu, filter dua protokol tersebut diperjelas dengan detail yang mengambil paket yang berasal dari port 21 (dengan subdomain `srcport`), sehingga filternya menjadi:
```
tcp.srcport == 21 or udp.srcport == 21
```

Sehingga hasil dari filter tersebut didapatkan paket yang berasal dari port 21
![hasil-filter-soal4](https://user-images.githubusercontent.com/87472508/191672636-6f511fab-c34f-4e61-88ff-c28be1d07f9f.png)

## Soal 5
Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan.
Untuk itu, diterapkan filter dengan protokol `tcp` dan `udp` karena pada soal tidak dispesifikasikan untuk jenis protokol apa. Lalu, filter dua protokol tersebut diperjelas dengan detail yang mengambil paket yang berasal dari port 443 (dengan subdomain `srcport`), sehingga filternya menjadi:
```
tcp.srcport == 443 or udp.srcport == 443
```

Sehingga hasil dari filter tersebut didapatkan paket yang berasal dari port 443
![hasil-filter-soal5](https://user-images.githubusercontent.com/87472508/191673089-ebac302b-43d5-40ef-8c31-d2f78b4985d5.png)

## Soal 6
Mahasiswa diminta untuk mencari informasi paket yang menuju ke lipi.go.id dari file `.pcap` yang diberikan.
Dikarenakan didalam soal yang diketahui hanya DNS-nya, maka sebelumnya harus mencari ip dari DNS tersebut, dengan cara membuka `cmd` atau `terminal`, lalu tuliskan:
```
ping lipi.go.id
```
nantinya akan mendapatkan ip dari DNS lipi.go.id
![hasil-ping](https://user-images.githubusercontent.com/87472508/191674395-2469572f-046d-41ef-b724-23c78916c896.png)

Setelah itu, mencari paket-paket yang menuju ke lipi.go.id dengan menggunakan `ip` dan subdomain `dst`, sehingga filternya menjadi:
```
ip.dst == 203.160.128.158
```
Sehingga hasil dari filter tersebut didapatkan paket yang menuju ip 203.160.128.158 atau menuju website lipi.go.id.
![hasil-filter-soal6](https://user-images.githubusercontent.com/87472508/191675242-4f013cd3-4cf8-4878-bffa-52274096965e.png)

## Soal 7
Mahasiswa diminta untuk mencari informasi paket yang berasal dari ip komputer sendiri.
Untuk mencari ip dari komputer sendiri, dapat dilakukan dengan cara membuka `cmd` atau `terminal`, lalu tulis command:
```
ipconfig
```
nantinya akan mendapatkan ip dari komputer.

![hasil-ipconfig](https://user-images.githubusercontent.com/87472508/191676604-5f74d498-6bc6-40bd-8515-9500229c3249.png)

Setelah itu, mencari paket-paket yang berasal dari ip komputer kita, sehingga filternya menjadi:
```
src host 192.168.2.22
```
Sehingga hasil dari filter tersebut didapatkan paket yang berasal dari ip 192.168.2.22
![hasil-filter-soal7](https://user-images.githubusercontent.com/87472508/191677040-c8f55ad9-be54-4763-8597-e47721f77c95.png)

## Soal 8

Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan. Diberikan clue berupa `percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut`. <br />

Untuk itu, diterapkan filter dengan protokol `tcp`, karena pada soal 10 disebutkan bahwa file dienkripsi dengan password, maka saya menggunakan filter pertama:

```
tcp contains "password"
```

dari filter tersebut didapatkan <br />
![hasil-filter](https://media.discordapp.net/attachments/964890423946543124/1022121998157099018/unknown.png) <br />
setelah itu dilakukan klik kanan dan `Follow TCP Stream`. <br />
Didapatkan informasi berupa: <br />
![informasi-1](https://media.discordapp.net/attachments/964890423946543124/1022124012261883944/unknown.png) <br />

Dari hasil tersebut didapatkan informasi penting terkait password, bentuk file yang dienkripsi yaitu `salt`, cara melakukan decrypt yaitu dengan `OpenSSL` dan `port 9002`. <br />
Untuk itu, dilakukan filter kedua dengan:

```
tcp.port == 9002
```

Dari situ didapatkan informasi penting lagi berupa detail passwordnya <br />
![password](https://media.discordapp.net/attachments/964890423946543124/1022123763820671008/unknown.png) <br />

## Soal 9

Dari informasi diatas, didapatkan informasi yaitu filenya merupakan salt, karena salt memiliki format `Salted__` maka saya coba filter:

```
tcp contains "Salted"
```

dari filter tersebut didapatkan <br />
![salted](https://media.discordapp.net/attachments/964890423946543124/1022124757988167701/unknown.png) <br />
karena setelah dilakukan `Follow TCP Stream` didapatkan <br />
![file-salted](https://media.discordapp.net/attachments/964890423946543124/1022125269311553636/unknown.png) <br >
maka dilakukan export raw file tersebut dalam bentuk `.bytes` dan disimpan dalam bentuk `.des3` <br />
![des3](https://media.discordapp.net/attachments/964890423946543124/1022126165382672424/unknown.png) <br /><br />

Kemudian file di decrypt dengan `OpenSSL` sesuai perintah pada percakapan yaitu dengan:

```sh
openssl des3 -d -salt -in c06.des3 -out flag.txt -k nakano
```

karena windows tidak bisa menjalankan command OpenSSL maka menggunakan WSL untuk melakukan decrypt, yaitu sebagai berikut: <br />
![decrypt](https://media.discordapp.net/attachments/964890423946543124/1022127452186759238/unknown.png) <br />
Akhirnya, didapatkan flag yaitu:

```
JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}
```

Informasi terkait password flag akan saya tulis pada nomor 10.

## Soal 10

Dari soal 9, saya sudah melakukan decrypt, dari informasi yang ada pada no 8, maka saya mencoba memasukkan password `gotoubunnohanayome` tapi masih salah. Informasi yang bisa saya ambil dari hasil stream no 8 adalah

1. nama karakter anime kembar lima, judulnya berarti `Gotoubun no Hanayome`
2. udah dicoba pake nama yang berbeda ternyata nggak ada yang bener
3. passwordnya sesimpel kesamaan
   Jadi dari percakapan diatas saya mendapat password yaitu:

```
nakano
```
