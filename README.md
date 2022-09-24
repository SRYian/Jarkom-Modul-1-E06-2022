# Jarkom-Modul-1-E06-2022
Repositori Jarkom Modul 1 kelompok E06

<details><summary>Anggota kelompok(click to show)</summary>
<p>

### Kelompok E06 :
1. Billy Brianto            5025201080  (nomor 1, 8-10)
2. Atha Dzaky Hidayanto    5025201269 (nomor )
3. Naily Khairiya            5025201244 (nomor )
</p>
</details>



## 1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"!

Untuk mendapatkan server yang dipakai oleh web tersebut, dapat dilakukan filtering string dengan wireshark untuk mencari alamat web tersebut dalam request http.
Filter: 
```http.host contains "monta.if.its.ac.id"```
![1.1](https://cdn.discordapp.com/attachments/818669323631591434/1022489131986735104/1.1.jpg)
Setelah itu dapat dilakukan follow tcp packet dan akan tergenerate popup window beserta command
```tcp.stream eq 4``` yang menarget tcp stream keempat
![1.2](https://cdn.discordapp.com/attachments/818669323631591434/1022489132326465576/1.2.jpg)
Dari popup window inilah, terlihat bahwa web server yang digunakan adalah nginx 1.10.3(Ubuntu)


## 2. Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?

Untuk mendapatkan topik ta yang dinginkan, dapat menggunakan display filter:
```http contains "detailTopik"```
![1.1](https://cdn.discordapp.com/attachments/1022895770426417274/1023110362096205895/unknown.png)


## 3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! 
Untuk mendapatkan paket yang menuju ke port 80, lakukan filtering: ```tcp.dstport ==80```
![1.1](https://cdn.discordapp.com/attachments/1022895770426417274/1023110984103100456/unknown.png)

## 4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!
Untuk mendapatkan paket yang menuju ke port 80, lakukan filtering: ```tcp.srcport ==21```
![1.1](https://cdn.discordapp.com/attachments/1022895770426417274/1023111253008330842/unknown.png)

## 5. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!
Pertama - tama, buka file pcapng lalu lakukan filtering dengan ```tcp.srcport == 443```.
Hasilnya sebagai berikut.
![soal 5](https://user-images.githubusercontent.com/72675854/192028680-4e352f6b-1905-4406-a91a-425b1596d6c2.jpg)

## 6. Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id !
Pertama - tama, buka file pcapng lalu lakukan filtering dengan ```http.host == lipi.go.id```.
Hasilnya sebagai berikut.
<img width="960" alt="image" src="https://user-images.githubusercontent.com/72675854/192029886-bdc0da4d-e86b-498f-af70-0f9266f846ea.png">


## 7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Pada bagian capture filter masukkan `src host [isi dengan IP kalian]` sebagai contoh `src host  192.168.1.4` . IP dapat dicari dengan `ipconfig.` <br>
<img width="463" alt="image" src="https://user-images.githubusercontent.com/72675854/192029338-c6ba83d7-f500-47b0-9fa6-5fe5e210d5b3.png">


Kemudian pilih wifi untuk mengambil wifi paket yang berasal dari ip sendiri. 
<img width="612" alt="image" src="https://user-images.githubusercontent.com/72675854/192029099-18a1aa92-02d4-4172-bf78-7c80d0626580.png">


Berikut merupakan hasilnya.


<img width="613" alt="image" src="https://user-images.githubusercontent.com/72675854/192029490-d50bc151-f8c3-4a65-8331-911e09755ea0.png">


## 8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
Soal menyatakan: 
> “Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut”

Sesuai soal, diminta untuk menerapkan filter terhadap suatu protokol. Karena protokol TCP adalah yang paling umum digunakan maka akan dicek terlebih dahulu menggunakan display filter 
```tcp.stream```
![8.1](https://cdn.discordapp.com/attachments/818669323631591434/1022489476448137276/8.1.jpg)

Selanjutnya, akan dilakukan filter ulang sebab yang menggunakan protokol tcp sangatlah banyak. Filter ulang tersebut dilakukan dengan filter
```tcp and frame contains "jawaban"```
![8.2](https://cdn.discordapp.com/attachments/818669323631591434/1022489476783673404/8.2.jpg)

Filter ini memfilter cukup banyak paket sehingga sisa beberapa yang dapat dicek secara manual dengan follow tcp stream. Akhirnya, ditemukan conversation antar 2 mahasiswa.
![8.3](https://cdn.discordapp.com/attachments/818669323631591434/1022489477047918642/8.3.jpg)


## 9. Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

Untuk nomor 9, diketahui nomor 9002 yang merupakan port. Dengan menerapkan display filter
```tcp.srcport == 9002```
Maka file langsung dapat ditemukan dengan follow tcp stream pada frame pertama.
![9.1](https://cdn.discordapp.com/attachments/818669323631591434/1022489477442179163/9.1.jpg)
Konten file tersebut adalah:
```Salted__.:....B(......$E...K)..<<......f ......B.G4..+..```
![9.2](https://cdn.discordapp.com/attachments/818669323631591434/1022489477815484456/9.2.jpg)
Setelah itu, dapat dilakukan save as untuk menyimpan dokumen dengan nama E06.des3

## 10. Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!
### Decoding
Didapat dari percakapan mahasiswa pada nomor 8, decoding pada file harus menggunakan openssl, toolkit pada linux untuk kriptografi. Akan tetapi, komputer praktikan menjalankan windows dan tidak memiliki motivasi untuk membuka VM. Untuk itu, digunakan web 
> https://www.cryptool.org/en/cto/openssl
untuk menjalankan openssl di web.
![10.1](https://cdn.discordapp.com/attachments/818669323631591434/1022489478125867058/10.1.jpg)
Langkah selanjutnya adalah mengecek string file yang sudah didapatkan. Setelah dilakukan pengecekan, string tersebut tidak kompatibel dengan input pada openssl pada web. untuk menangani hal tersebut, dilakukan konversi display file dari ASCII menjadi YAML. Setelah konversi, didapatkan string berupa

```U2FsdGVkX1+/Ot+vpIhCKM4FG9H2wSRFpBboSynB1jw8CBuLufz1ZiCVh5YTF+FC/0c05Nory88=```

yang kompatibel dengan openssl web.

### Password
![10.2](https://cdn.discordapp.com/attachments/818669323631591434/1022489478507536555/10.2.jpg)

Dari percakapan yang ditemukan pada nomor 8 terdapat 
password(karakter anime): yotsuba, miku, itsuki, nino, ichika
![10.3](https://cdn.discordapp.com/attachments/818669323631591434/1022489478834704414/10.3.jpg)

akan tetapi, terdapat beberapa conversatione extra yang ditemukan dengan display filter
```tcp and frame contains "jawaban"``` (nomor 8) yang menyatakan bahwa nama yang berbeda sudah dipakai untuk password tetapi masih salah. 
Dari conversation yang sama, didapatkan juga pernyataan

> "Ya kan nggak selamanya jawabannya dari hal yang berbeda, bisa aja jawabannya itu sesimpel hal yang jadi kesamaan di antara kita"

Kalimat itu menunjukan untuk mencoba mencari kesamaan diantara 5 karakter yang menjadi password untuk file yang akan didecode. Jika mencari lebih lanjut, didapatkan bahwa kelima kembar tersebut memiliki kesamaan dalam nama mereka, yaitu semuanya memiliki nama keluarga **nakano**

### Final result
![10.4](https://cdn.discordapp.com/attachments/818669323631591434/1022489479841329172/10.5.jpg)

Dengan menjalankan openssl dengan command
```echo U2FsdGVkX1+/Ot+vpIhCKM4FG9H2wSRFpBboSynB1jw8CBuLufz1ZiCVh5YTF+FC/0c05Nory88= | openssl enc -des3 -d -k nakano -a``` (generated dari web cryptool) didapatkan flag berupa teks
`JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}`
