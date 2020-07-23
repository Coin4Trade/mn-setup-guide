![Example-Logo](https://i.imgur.com/SgvydEE.png)
# Coin4Trade Masternode Setup Guide (Ubuntu 16.04)
This guide will assist you in setting up a Coin4Trade Masternode on a Linux Server running Ubuntu 16.04.

If you require further assistance contact the support team [Discord](https://discord.gg/6kfD7h4)
***
## Requirements
1) **1000 Coin4Trade coins (buy on [Crex24](https://crex24.com/ru/exchange/C4T-BTC))**
2) **VPS (Vultr) running Linux Ubuntu 16.04**
3) **Windows or MAC OS X local wallet**
4) **SSH client such as [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe)**
***
## Contents
* [Section A](#Section-A) - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061)
* [Section B](#Section-B) - Downloading and installing Bitvise
* [Section C](#Section-C) - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise
* [Section D](#Section-D) - Preparing the local wallet
* [Section E](#Section-E) - Editing the configs
* [Section F](#Section-F) - Starting the masternode
***

## <a name = "Section-A"></a> Section A - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061) 
***Step 1***
* Register at [Vultr](https://www.vultr.com/?ref=7485061)
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) and choose Server - Cloud Compute

![Example-Location](https://i.imgur.com/fyKmJuN.png)
***

***Step 3*** 
* Choose a server location (preferably somewhere close to you)

![Example-Location](https://i.imgur.com/UnxUKI5.png)
***

***Step 4***
* Choose a server type: 64 bit OS -> Ubuntu 16.04

![Example-OS](https://i.imgur.com/Z21waGc.png)
***

***Step 5***
* Choose a server size: $3.5/mo

![Example-OS](https://i.imgur.com/P2wiUpX.png)
***

***Step 6*** 
* Set a Server Hostname & Label (name it whatever you want)

![Example-hostname](https://i.imgur.com/neqnC36.png)
![Example-hostname](https://i.imgur.com/SIIZ20I.png)
***

***Step 7***
* Click "Deploy now"

![Example-Deploy](https://i.imgur.com/KsCg74D.png)
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-B"></a> Section B - Downloading and installing BitVise

***Step 1***
* Download Bitvise [here](https://dl.bitvise.com/BvSshClient-Inst.exe)
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-C"></a> Section C - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise

***Step 1***
* Click on your server
![Example-Vultr](https://i.imgur.com/TZKtynE.png)
***

***Step 2***
* Copy your VPS IP
![Example-Vultr](https://i.imgur.com/dD3N4Li.png)
***

***Step 3***
* Open the bitvise application and fill in the "Host" box with the IP

![Example-BitviseInstaller](https://i.imgur.com/hJYKYA5.png)
***

***Step 4***
* Copy the root password from the VULTR server page
![Example-RootPass](https://i.imgur.com/n7rK0ez.png)
***

***Step 5***
* type "root" as the username
* type "password" as the Initial method
* type password
* then press "Login"

![Example-RootPass](https://i.imgur.com/wm0UzzF.png)

* then press "Accept and Save"

![Example-RootPass](https://i.imgur.com/kChNPVQ.png)
***

***Step 6 (Updating)***
* Paste the code below into the Bitvise terminal then press enter

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/dgOMhX8.png)
***

***Step 7 (Install all required libraries)***

***Step 7.1*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install git automake build-essential libtool autotools-dev autoconf pkg-config libssl-dev libboost-all-dev software-properties-common
```

![Example-RootPassEnter](https://i.imgur.com/4cEHqIL.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/8YBQwSj.png)


***Step 7.2*** Paste the code below into the Bitvise terminal then press enter:

```
sudo add-apt-repository ppa:bitcoin/bitcoin
```

![Example-RootPassEnter](https://i.imgur.com/P2ESj6q.png)

Press enter to continue

![Example-RootPassEnter](https://i.imgur.com/IDUBqSV.png)


***Step 7.3*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/mJMpKdR.png)

***Step 7.4*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install libdb4.8-dev libdb4.8++-dev libminiupnpc-dev
```

![Example-RootPassEnter](https://i.imgur.com/ENJ0A5R.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/78aP97k.png)
***

***Step 8 (download daemon on VPS)***

***Step 8.1*** Paste the code below into the Bitvise terminal then press enter:

```
wget https://github.com/Coin4Trade/C4T/releases/download/C4T-v1.0/C4T-1.0-linux-x64.tar
```

![Example-RootPassEnter](https://i.imgur.com/CUvHuMj.png)

***Step 8.2*** Paste the code below into the Bitvise terminal then press enter:

```
tar -xvf C4T-1.0-linux-x64.tar
cd C4T-1.0-linux-x64
chmod -f 777 C4Td
chmod -f 777 C4T-cli
chmod -f 777 C4T-tx
./C4Td -daemon
```

![Example-RootPassEnter](https://i.imgur.com/Qi8Yz5a.png)

Once you’ve run the Daemon for the first time it has created the folder structure where the blockchain and all config files are going to be.

***Step 8.3*** Paste the code below into the Bitvise terminal then press enter:
```
./C4T-cli stop
```

![Example-RootPassEnter](https://i.imgur.com/AVkIkhK.png)

***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-D"></a> Section D - Preparing the local wallet

In your Wallet-App go to: Tools -> Debug console.  

![Example-Debugconsole](https://i.imgur.com/U8hEwIx.png)

follow these steps:


***Step 1*** Paste the code below into the Debug console then press enter:

```
getnewaddress MN1
```

answer: CXgJJsarKS6q7Bu7hyqUcbdaBVUfmNwbgU

![Example-getnewaddress](https://i.imgur.com/MNeqkqg.png)


***Step 2*** Paste the code below into the Debug console then press enter:

```
sendtoaddress CXgJJsarKS6q7Bu7hyqUcbdaBVUfmNwbgU 1000
```

answer: 94851732a3442be8c2e0aed397cae1c7bd8eba8d62bc80afd1ada94994daf057

![Example-sendtoaddress](https://i.imgur.com/ajKIrsG.png)


***Step 3*** Paste the code below into the Debug console then press enter:

```
masternode genkey
```

answer: 8ZL6YW4YdskEF4DKmxEc9v2FeJyB2vXde62BPUD2rpJSQxNabPT

![Example-genkey](https://i.imgur.com/1UkT3pW.png)


***Step 4*** Paste the code below into the Debug console then press enter:

```
masternode outputs
```

answer: 
  "txhash" : "94851732a3442be8c2e0aed397cae1c7bd8eba8d62bc80afd1ada94994daf057",
  "outputidx" : 0

![Example-outputs](https://i.imgur.com/kXgsTUV.png)


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-E"></a> Section E - Editing the configs


***Step 1*** Editing the configs via Bitvise terminal

Paste the code below into the Bitvise terminal then press enter:

```
apt-get install nano
```

![Example-nano](https://i.imgur.com/r2cgN4L.png)

Nano is a great console-based text-editor 

Let’s open the C4T.conf located in the .C4T folder 

This folder was created by the daemon on the first run! 

Paste the code below into the Bitvise terminal then press enter:

```
nano /root/.C4T/C4T.conf
```

![Example-conf](https://i.imgur.com/NKt7hU6.png)

This is configuration for masternode setup:

```
rpcuser={CHOOSE A RANDOM USER}
rpcpassword={CHOOSE A RANDOM PASSWORD}
rpcallowip=127.0.0.1
port=19333
rpcport=19666
listen=1
server=1
daemon=1
maxconnections=256
masternode=1
externalip={YOUR SERVER IP:19333}
masternodeprivkey={YOURPRIVKEY - WE WILL GET THAT LATER}
logtimestamps=1
masternodeaddr={YOUR SERVER IP}
```

which should result in something like that:

![Example-conf](https://i.imgur.com/14mLhfi.png)

Save the config (Ctrl+X --> Y --> Enter)

`Ctrl+x`

![Example-conf](https://i.imgur.com/PRnbhQC.png)

`Y`

![Example-conf](https://i.imgur.com/QSt7EK6.png)

`Enter`

![Example-conf](https://i.imgur.com/5t5xLuH.png)


***Step 2*** Editing the configs in your Wallet-App

Go to the tools tab within the wallet and click open "masternode configuration file"

![Example-configuration](https://i.imgur.com/xttmMuJ.png)

* Fill in the form  
* For `Alias` type something like "MN1" don't use spaces  
* The `Address` is the IP and port of your server (this will be in the putty terminal that you still have open)  
* The `PrivKey` is your masternode private key (This is also in the putty terminal that you have open)  
* The `TxHash` is the transaction ID/long key that you copied to the text file  
* The `Output Index` is the 0 or 1 that you copied to your text file  

![Example-configuration](https://i.imgur.com/vcInU4h.png)

Click "File Save"


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-F"></a> Section F - Starting the masternode


***Step 1*** Starting the daemon on the Ubuntu server:

```
cd C4T-1.0-linux-x64
./C4Td -daemon
```

The daemon should start minimized.   
You’ll only see a message like this:   

```
C4T server starting
```

![Example-starting](https://i.imgur.com/eursnBe.png)

wait for the full sync before continuing:

```
./C4T-cli mnsync status
```

You should see: "RequestedMasternodeAssets" : 999, (this means full sync)

![Example-mnsync](https://i.imgur.com/GSL2D6f.png)

***Step 2*** Move on your Wallet-App

Wait for the transaction to have at least 16 confirmations before continuing.

![Example-confirmations](https://i.imgur.com/CoCeZBP.png)

* Close out of the wallet and reopen Wallet  
* Go to the Masternodes
* select MN1
* click Start alias
* click Yes

![Example-startmasternode](https://i.imgur.com/wgifmyr.png)

* click ok

![Example-startmasternode](https://i.imgur.com/QixFwKU.png)

which should result in something like that:

![Example-startmasternode](https://i.imgur.com/JywjdKm.png)

***Step 3*** Check the status of your masternode within the VPS by using the command below:

```
./C4T-cli masternode status
```

You should see:

![Example-status](https://i.imgur.com/2KBS1nR.png)

If you do, congratulations! You have now setup a masternode.  
If you do not, please contact me or any other support

[:arrow_up: Contents :arrow_up:](#Contents)
