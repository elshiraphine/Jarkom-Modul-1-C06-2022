# Jarkom-Modul-1-C06-2022

## Anggota Kelompok
1. 5025202050 - Elshe Erviana Angely
2. 5025201051 - Muhammad Fath Mushaffa Azhar
3. 5025201076 - Raul Ilma Rajasa

## Soal 8
Mahasiswa diminta untuk mencari informasi dari file `.pcap` yang diberikan. Diberikan clue berupa `percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut`. <br />

Untuk itu, diterapkan filter dengan protokol `tcp`, karena pada soal 10 disebutkan bahwa file dienkripsi dengan password, maka saya menggunakan filter pertama:
```
tcp contains "password"
```

dari filter tersebut didapatkan <br />
![hasil-filter](https://media.discordapp.net/attachments/964890423946543124/1022121998157099018/unknown.png)
setelah itu dilakukan klik kanan dan `Follow TCP Stream`. <br />
Didapatkan informasi berupa: <br />
![informasi-1](https://media.discordapp.net/attachments/964890423946543124/1022124012261883944/unknown.png)

Dari hasil tersebut didapatkan informasi penting terkait password, bentuk file yang dienkripsi yaitu `salt`, cara melakukan decrypt yaitu dengan `OpenSSL` dan `port 9002`. <br />
Untuk itu, dilakukan filter kedua dengan:
```
tcp.port == 9002
```
Dari situ didapatkan informasi penting lagi berupa detail passwordnya <br />
![password](https://media.discordapp.net/attachments/964890423946543124/1022123763820671008/unknown.png)

## Soal 9
Dari informasi diatas, didapatkan informasi yaitu filenya merupakan salt, karena salt memiliki format `Salted__` maka saya coba filter:
```
tcp contains "Salted"
```
dari filter tersebut didapatkan <br />
![salted](https://media.discordapp.net/attachments/964890423946543124/1022124757988167701/unknown.png)
karena setelah dilakukan `Follow TCP Stream` didapatkan <br />
![file-salted](https://media.discordapp.net/attachments/964890423946543124/1022125269311553636/unknown.png)
maka dilakukan export raw file tersebut dalam bentuk `.bytes` dan disimpan dalam bentuk `.des3` <br />
![des3](https://media.discordapp.net/attachments/964890423946543124/1022126165382672424/unknown.png) <br /><br />

Kemudian file di decrypt dengan `OpenSSL` sesuai perintah pada percakapan yaitu dengan:
```sh
openssl des3 -d -salt -in c06.des3 -out flag.txt -k nakano
```
karena windows tidak bisa menjalankan command OpenSSL maka menggunakan WSL untuk melakukan decrypt, yaitu sebagai berikut: <br />
![decrypt](https://media.discordapp.net/attachments/964890423946543124/1022127452186759238/unknown.png)
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