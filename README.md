# Coin2Play Masternode Setup Guide [ Ubuntu 16.04 ]

THIS GUIDE IS FOR ROOT USERS -

YOU MUST BE A MEMBER OF THE FOLLOWING GROUP
```
User=root
Group=root
```

## Private Key

**This script can generate a private key for you, or you can generate your own private key on the Desktop software.**

Steps generate your own private key. 
1.  Download and install Coin2Play windows wallet from Releases
2.  Go to **Tools -> Click "Debug Console"** 
3.  Type the following command: **masternode genkey**  
4. You now have your generated **Private Key**  (MasternodePrivKey)


## VPS installation
First you will need a VPS to continue on with this guide. If you do not have one get one from here [Vultr.](https://www.vultr.com/?ref=7424168)

Next step is to download the script on the vps with command below.
```
cd &&  bash -c "$(wget -O - https://github.com/Coin2Play/c2pcore/releases/download/1.0.0/c2p-install.sh)"
```

