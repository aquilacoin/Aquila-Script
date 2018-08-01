![](https://cdn.discordapp.com/attachments/460803845614862337/462105794498789376/Nibex.png)

# Aquila v1.1.0.5 Masternode Setup Guide [ Ubuntu 16.04 ]

THIS GUIDE IS FOR ROOT USERS -

YOU MUST BE A MEMBER OF THE FOLLOWING GROUP
```
User=root
Group=root
```

Shell script to install a [Aquila Masternode](https://aquila.online/) on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Private Key

**This script can generate a private key for you, or you can generate your own private key on the Desktop software.**

Steps generate your own private key. 
1.  Download and install Aquila v1.1.0.5 for Windows -   Download Link  - https://github.com/aquilacoin/AquilaX/releases/
2.  Go to **Tools -> Click "Debug Console"** 
3.  Type the following command: **masternode genkey**  
4. You now have your generated **Private Key**  (MasternodePrivKey)


## VPS installation
```
wget -q https://github.com/CryptoNeverSleeps/Aquila-Script/raw/master/aquila-install.sh
bash aquila-install.sh
```
Once the VPS installation is finished.

Check the block height

We want the blocks to match whats on the Aquila block explorer (http://exploreraqx.aquila.online/)

Once they match you can proceed with the rest of the guide.

Check the block height with the following command
```
watch Aquila-cli getinfo
```
Make sure the version number matches.
```
"version" : 2030000,     ------------------This is the latest version (Aquila v1.1.0.5)
```

Once the block height matches the block explorer issue the following command.
```
CTRL and C  at the same time  (CTRL KEY and C KEY)
```
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the Aquila Desktop Wallet.  
2. Go to RECEIVE and create a New Address: **MN1**  
3. Send **5000** AQX to **MN1**. You need to send 5000 coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Tools -> Click "Debug Console"** 
6. Type the following command: **masternode outputs**  
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
## SAMPLE OF HOW YOUR MASTERNODE.CONF SHOULD LOOK LIKE.  (This should all be on one line)  

```
MN1 127.0.0.2:45454 93HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 0
```


* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. 
If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. 
12. Select your MN and right click on the masternode **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:

```
startmasternode alias 0 MN1 
``` 

14. Login to your VPS and check your masternode status by running the following command:.

```
Aquila-cli masternode status
```

You want to see **"Masternode started successfully and Status 4"**

***

## Usage:

```
Aquila-cli masternode status  
Aquila-cli getinfo
```

Also, if you want to check/start/stop **Aquila**, run one of the following commands as **root**:

```
systemctl status Aquila.service          #To check if Aquila service is running  
systemctl start Aquila.service           #To start Aquila service  
systemctl stop Aquila.service           #To stop Aquila service  
systemctl is-enabled Aquila.service      #To check if Aquila service is enabled on boot  
```  

***

## Donations

Any donation is highly appreciated

**AQX**: XUC1s4PriFDjsS76pVeZC6otaVZ4SkWGk6  
**BTC**: 32PN27dDZhUYAmyJTWuzDvNscbVpkL9855  
**ETH**: 0x02680cdF57EEDC20C8A12036CA03e8D5F813b33b  
**LTC**: MKYX9Pm58z6xSWT4Rc3CynjR58nj8hKo4F  
