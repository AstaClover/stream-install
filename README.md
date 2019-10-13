# StreamitCoin
Script Shell untuk menginstal [StreamitCoin Masternode] (http://www.streamitcoin.com/) di server Linux yang menjalankan Ubuntu 14.04, 16.04 atau 18.04. Gunakan dengan risiko Anda sendiri.


***
## Dompet instalasi (versi terbaru):

```
git clone https://github.com/StreamitCoin/stream-install/
cd stream-install
bash stream-install.sh
```
***
## Perbarui dompet ke versi terbaru:

```
cd ~/stream-install/
git pull
bash stream-update.sh
```
***
## Desktop wallet setup

Setelah MN aktif dan berjalan, Anda harus mengkonfigurasi dompet desktop yang sesuai. Inilah langkah-langkah untuk Windows Wallet
1. Buka Dompet Desktop StreamitCoin Coin.
2. Pergi ke RECEIVE dan buat Alamat Baru: ** MN1 **
3. Kirim ** 20000 ** ** StreamitCoin ** ke ** MN1 **.
4. Tunggu 15 konfirmasi.
5. Buka ** Alat -> "Konsol debug - Konsol" **
6. Ketikkan perintah berikut: ** output masternode **
7. Pergi ke ** Tools -> "Buka File Konfigurasi Masternode"
8. Tambahkan entri berikut:
```
Alias Address Privkey TxHash Output_index
```
* Alias: ** MN1 **
* Alamat: ** VPS_IP: PORT **
* Privkey: ** masternode privkey **
* TxHash: ** Nilai pertama dari Langkah 6 **
* Indeks Output: ** Nilai kedua dari Langkah 6 **
9. Simpan dan tutup file.
10. Pergi ke ** Masternode Tab **. Jika tab Anda tidak ditampilkan, harap aktifkan dari: ** Pengaturan - Opsi - Dompet - Tampilkan Tab Masternodes **
11. Klik ** Perbarui status ** untuk melihat simpul Anda. Jika tidak ditampilkan, tutup dompet dan mulai lagi. Pastikan dompet tidak terkunci.
12. Buka ** Konsol Debug ** di dompet dan ketik lokal:
```
startmasternode "alias" "0" "MN1"
```
13. Buka konsol VPS Linux dan ketik:

```
streamitcoin-cli startmasternode local false
```
Jika berhasil, Anda akan dijawab:
Masternode successfully started
***

## Penggunaan:
```
streamitcoin-cli getinfo
streamitcoin-cli mnsync status
streamitcoin-cli masternode status
```
Juga, jika Anda ingin memeriksa / memulai / menghentikan ** StreamitCoin **, jalankan salah satu dari perintah berikut sebagai ** root **:

**Ubuntu 16.04 or 18.04**:
```
systemctl status StreamitCoin #To check the service is running.
systemctl start StreamitCoin #To start StreamitCoin service.
systemctl stop StreamitCoin #To stop StreamitCoin service.
systemctl is-enabled StreamitCoin #To check whetether StreamitCoin service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/StreamitCoin start #To start StreamitCoin service
/etc/init.d/StreamitCoin stop #To stop StreamitCoin service
/etc/init.d/StreamitCoin restart #To restart StreamitCoin service
```
***
