# StreamitCoin
Shell script to install a [StreamitCoin Masternode](http://www.streamitcoin.com/) on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation:
```
git clone https://github.com/StreamitCoin/stream-install/
cd stream-install
bash stream-install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the StreamitCoin Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **20000** **StreamitCoin** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** in local wallet and type:
```
startmasternode "alias" "0" "MN1"
```
13. Open the Linux VPS console and type:
```
streamitcoin-cli startmasternode local false
```
If successful, you will be answered:
Masternode successfully started
***

## Usage:
```
streamitcoin-cli getinfo
streamitcoin-cli mnsync status
streamitcoin-cli masternode status
```
Also, if you want to check/start/stop **StreamitCoin** , run one of the following commands as **root**:

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
