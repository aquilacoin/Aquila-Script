![logo](https://aquila.online/images/logo2x.png)

# Aquila v1.2.0.2 Masternode Setup Guide [ Ubuntu 16.04 ]

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
1.  Download and install Aquila v1.2.0.2 for Windows -   Download Link  - https://github.com/aquilacoin/AquilaX/releases/
2.  Go to **Tools -> Click "Debug Console"** 
3.  Type the following command: **masternode genkey**  
4. You now have your generated **Private Key**  (MasternodePrivKey)


## VPS installation
First you will need a VPS to continue on with this guide. If you do not have one get one from here [Vultr.](https://www.vultr.com/?ref=7424168)

Next step is to download the script on the vps with command below.
```
cd &&  bash -c "$(wget -O - https://raw.githubusercontent.com/aquilacoin/Aquila-Script/master/aquila-install.sh)"
```

You will have 6 options one you run the command above.
1. This option Will install a fresh MNN VPS instance
2. This option will update your MN wallet on the vps if a network or wallet update is needed.
3. This option will Start Aquila Masternode
4. This option will Stop Aquila Masternode
5. This option will show Aquila Server Status
6. This option will Rebuild Aquila Masternode Index


If you need to go back and either start or stop Aquila just use this command.
```
cd &&  bash -c "$(wget -O - https://raw.githubusercontent.com/aquilacoin/Aquila-Script/master/aquila-install.sh)"
```
That command above will be your shortcut to control your masternode. 
More commands will come in time.

Once the VPS installation is finished.

Check the block height

```
watch ./Aquila-cli getinfo
```

We want the blocks to match whats on the Aquila block explorer (http://exploreraqx.aquila.online/)

Once they match you can proceed with the rest of the guide.



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
./Aquila-cli masternode status
```

You want to see **"Masternode started successfully and Status 4"**

***

## Usage:

```
./Aquila-cli getinfo
./Aquila-cli mnsync status
./Aquila-cli masternode status
```
  
