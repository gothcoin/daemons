## Install a node with Ubuntu 18.04.
`adduser USERNAME`  
`adduser USERNAME sudo` 

`sudo apt-get update && sudo apt-get upgrade -y`

`sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common redis-server npm git nano cmake screen -y`

Install the repository ppa:bitcoin/bitcoin:

`sudo add-apt-repository ppa:bitcoin/bitcoin`

Confirm the installation of the repository by pressing the enter key.

Install Berkeley DB:

`sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y`

Download the Linux daemon for your wallet with the following command:

`wget "https://github.com/gothcoin/daemons/raw/main/Linux/gothcoind" -O gothcoind`  
`wget "https://github.com/gothcoin/wallet/raw/main/Linux/gothcoin-cli" -O gothcoin-cli`    
`wget "https://github.com/gothcoin/wallet/raw/main/Linux/gothcoin-tx" -O gothcoin-tx`  

Install the daemon and tools for your wallet:

`chmod 755 gothcoin* ;sudo mv gothcoind gothcoin-cli gothcoin-tx /usr/bin/`

Create the data directory for your coin with the following command:

`mkdir $HOME/.gothcoin; cd $HOME/.gothcoin`

Copy `gothcoin.conf` into the directory and start the chain:  
`gothcoind`  
  
Your node is now ready to serve! Make sure you check the daemon from time to time and start at reboot:  
`crontab -e` and add  
```
@hourly /usr/bin/gothcoind
@reboot /usr/bin/gothcoind
```
