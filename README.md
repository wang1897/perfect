What is QbaoChain?
--------------------------

QbaoChain is a kind of Consortium Blockchain. Every node involved in the Blockchain system is licensed. Unlicensed nodes cannot be connected to the system. The affiliate chain is a Blockchain that requires registration, also known as the Permissioned Blockchain.
QbaoChain not only perfectly realizes the characteristics of the blockchain that can not be tampered, forged, denied, distributed, no trust, point-to-point, collective maintenance, etc. QbaoChain is designed from the overall architecture to node coding development. From consensus algorithms to object storage; From encryption algorithms to broadcast strategies; From performance tuning to QbaoChain, there are huge innovations and breakthroughs. Therefore, QbaoChain has more obvious advantages over the original public chain.


**Powerful Functionality**  
Adopting the UTXO account model of BTC, which supports the simultaneous processing of multiple UTXO, is therefore highly scalable, enabling parallel transactions and encouraging scalability innovations. Also, if a user USES a new address for each transaction, UTXO can provide powerful anonymity to prevent it from being tracked. In addition to this, QbaoChain also supports a strong contract layer, a smart contract is a set of conventions defined in digital form, including those on which the contract participants can enforce them. Because of the immutable and distributed nature of blockchain, smart contracts, once created, can never be changed and can therefore solve trust issues.
regularly to indicate new official, stable release versions of Qtum.


**Lightning Speed**  
BTC trade at the rate of 3 per second, ETH speed is 6.7 per second, IBM's books theoretical peak is 200 transactions per second, by redesigning our consensus mechanism, separation of consensus steps, to discuss first, greatly improve the performance of the block chain network, in QbaoChain QbaoChain trading speed can reach 5000 transactions per second, as the future network bandwidth upgrade, further improve speed.


**Higher Safety**  
The information on the coalition chain is not accessible to all, and only the nodes on the alliance chain can be accessed, thus providing high-level security. It not only has the privacy of the private chain, but also has the decentralization thinking of the public chain, which ensures the high privacy of data on the chain and avoids the occurrence of attacks on nodes.


**Ultralight Storage**  
BTC blockchain requires huge storage space of tens of gigabytes, some even larger, which requires nodes to provide proprietary large-capacity storage devices, and in QbaoChain, the space required for QbaoChain will shrink by about 100 times, or even less. Because it only needs to store the data after blockchain hash and key checkpoints, the storage space is reduced directly to a dozen M or even several M.


**A Truly Private Wallet**     
BTC/ETH kind of wallet must with the help of a centralized server, often stolen events, QbaoChain provide real private decentralized purse, wallet to store in the center of the third party no longer on the server, but rather direct access to the block chain nodes, and better protect the private key, my wallet is no longer as third-party credit problems, safety problems lead to lost wallet, has realized the real can't steal block chain private purses.

*


What is Qtc Core?
------------------------------------

Qtc Core is our primary mainnet wallet. It implements a full node and is capable of storing, validating, and distributing all history of the Qbao network. Qtc Core is considered the reference implementation for the Qtum network. 

Qtc Core currently implements the following:

* Sending/Receiving Qtc
* Sending/Receiving QRC20 tokens on the Qbao network
* Staking and creating blocks for the Qbao network
* Creating and interacting with smart contracts
* Running a full node for distributing the blockchain to other users
* "Prune" mode, which minimizes disk usage
* Regtest mode, which enables developers to very quickly build their own private Qbao network for Dapp testing
* Compatibility with the Bitcoin Core set of RPC commands and APIs

*

Alternative Wallets
--------------------------------------

Qtc Core uses a full node model, and thus requires downloading the entire blockchain. If you do not need the entire blockchain, and do not intend on developing smart contracts, it may be more ideal to use an alternative wallet such as one of our light wallets that can be synchronized in a matter of seconds. 


These wallets run on mobile devices and synchronize quickly.   
Android Download:   
https://play.google.com/store/apps/details?id=org.qtc.wallet

iOS Download:   
https://github.com/qtcproject/qtc-ios (open source, we are still working with Apple to get approval for their app store)

*


Building Qtc Core
---------------------------------------

### (1)Build on Ubuntu
This is a quick start script for compiling Qtc on  Ubuntu.
  
####1.Install protobuf(The version of apt-get is too low)

	wget https://github.com/google/protobuf/archive/v3.5.1.tar.gz
	tar -xzvf v3.5.1.tar.gz
	cd protobuf-3.5.1/ 
	./autogen.sh 
	./configure
	make -j8 && make install 
	
	1. 创建文件 /etc/ld.so.conf.d/libprotobuf.conf 包含内容：
	/usr/local/lib
	输入命令 
	sudo ldconfig
	这时，再运行protoc –version 就可以正常看到版本号了

#####2.Installing Dependencies for Qtc

    apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils git cmake libboost-all-dev
    apt-get install software-properties-common
    add-apt-repository ppa:bitcoin/bitcoin
    apt-get update
    apt-get install libdb4.8-dev libdb4.8++-dev

###### If you want to build the Qt GUI:
	apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler qrencode

###### Compile Qtc
	git clone --recursive http://43.254.148.146:83/QbaoChain/perfect.git
	cd qtc
	./autogen.sh
	./configure 
    

### (2)Build on CentOS

Here is a brief description for compiling Qtc on CentOS

##### Compiling boost manually
    sudo yum install python-devel bzip2-devel
    git clone https://github.com/boostorg/boost.git
    cd boost
    git checkout boost-1.66.0
    git submodule update --init --recursive
    ./bootstrap.sh --prefix=/usr --libdir=/usr/lib64
    ./b2 headers
    sudo ./b2 -j4 install
    
##### Installing Dependencies for Qtc
    sudo yum install epel-release
    sudo yum install libtool libdb4-cxx-devel openssl-devel libevent-devel
    
    # If you want to build the Qt GUI:
    sudo yum install qt5-qttools-devel protobuf-devel qrencode-devel
    
    # Building Qtc
    git clone --recursive http://43.254.148.146:83/QbaoChain/perfect.git
    cd qtc
    ./autogen.sh
    ./configure
    make -j4

### (3)Build on OSX

The commands in this guide should be executed in a Terminal application.
The built-in one is located in `/Applications/Utilities/Terminal.app`.

##### 1) Preparation

Install the OS X command line tools:

`xcode-select --install`

When the popup appears, click `Install`.

Then install [Homebrew](https://brew.sh).

##### 2) Dependencies

    brew install cmake automake berkeley-db4 libtool boost --c++11 --without-single --without-static miniupnpc openssl pkg-config qt5 libevent imagemagick --with-librsvg qrencode

protobuf install(The version of brew is too high):
	
	wget https://github.com/google/protobuf/archive/	v3.5.1.tar.gz
	tar -xzvf v3.5.1.tar.gz
	cd protobuf-3.5.1/ 
	./autogen.sh 
	./configure
	make 
	make check
	make install
	protoc --version

NOTE: Building with Qt4 is still supported, however, could result in a broken UI. Building with Qt5 is recommended.



NOTE: the support boost version must be 1.66 or less 1.60

##### 3) Build Qtc Core

######1. Clone the qtc source code and cd into `qtc`

        git clone --recursive http://43.254.148.146:83/QbaoChain/perfect.git
        cd perfect

######2.  Build qtc-core:

    Configure and build the headless qtc binaries as well as the GUI (if Qt is found).

    You can disable the GUI build by passing `--without-gui` to configure.

        ./autogen.sh
        ./configure
        make

######3.  It is recommended to build and run the unit tests:

        make check
        
#### 4) Initialization Parameter Configuration
######1. mkdir qtc folder and touch qtc.conf
		
		mkdir /Users/$UserName/Library/Application\ Support/Qtc
		cd /Users/$UseName/Library/Application\ Support/Qtc
		touch qtc.conf
	
Note: replace $UserName to your computer name

######2. echo cofiguration parmeter to qtc.conf, The list of configuration parameters is as follows:
	
	addressindex=1
	timestampindex=1
	spentindex=1
	rpcuser=admin
	rpcpassword=admin
	rpcallowip=0.0.0.0/0
	addrindex=1
	txindex=1
	#zmqpubhashtx=tcp://0.0.0.0:4000
	zmqpubhashblock=tcp://0.0.0.0:4000
	#daemon=1
	logevents=1
	chain=cup
	server=1
	addnode=47.100.27.65
	#debug=zmq
	maxmempool=100000


######3. mkdir chain_cup and add configuration file
		
		mkdir chain_cup
		cd chain_cup
		touch qtc.conf
		
######4. echo cofiguration parmeter to qtc.conf, The list of configuration parameters is as follows:

	poa=1
	token-name=CUP
	genesis-input=world cup
	msgstart=1234aabb
	poa-miner-list=QWXrSap9kvsoPmq9YrXp87NQQn4utwVqTk,QgZLtFbLAdRLcmEHtf6jscv9ZVCuHHtDEF,QS7AgqJNkiVhiEyNw9CTLE1dTWwdkAown2
	poa-interval=5
	poa-timeout=3
	default-port=8444
	subsidy-init=666
	subsidy-halving-interval=1500000
	subsidy-halving-time=8


*
Run
---------------------------------------
####(1) command-line
Then you can enter the project path, for example,cd ~/qtc.
	
	# enter your project path
	cd ~/qtc/src
	# 
	./qtcd -daemon   
And then, you can do something by your input commands, as:

	#get block chain height
	./qtc-cli getblockcount
	#get the blockHash of the first block  
	./qtc-cli getblockhash 1
	#get the chain params
	./qtc-cli getinfo



####(2) GUI 
If you want run Qt GUI, you need use OSX, not ubuntu, also input command:
	
	cd ~/qtc/src/qt
	./qtc-qt

And then you can using the GUI program Efficiently.


