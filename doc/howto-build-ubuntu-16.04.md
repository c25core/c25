
# Ubuntu 16.04 x64  build instructions.

To build you required: libssl, libboost, libevent.
Also you may need this: miniupnpc, libdb4.8, qt, protobuf, libqrencode, univalue, libzmq3. You can install it via apt-get.
1. Update your Ubuntu
	```bash
	sudo apt-get update 
	sudo apt-get upgrade
	sudo reboot	
	```
2. Install some required packages
	```bash
	sudo apt-get install build-essential autoconf libtool autotools-dev pkg-config libevent-dev
	```
3. Install required libevent packages
	```bash
	wget http://archive.ubuntu.com/ubuntu/pool/main/libe/libevent/libevent-2.1-6_2.1.8-stable-4build1_amd64.deb
	wget http://archive.ubuntu.com/ubuntu/pool/main/libe/libevent/libevent-core-2.1-6_2.1.8-stable-4build1_amd64.deb
	wget http://archive.ubuntu.com/ubuntu/pool/main/libe/libevent/libevent-pthreads-2.1-6_2.1.8-stable-4build1_amd64.deb
	sudo dpkg -i libevent-core-2.1-6_2.1.8-stable-4build1_amd64.deb
	sudo dpkg -i libevent-pthreads-2.1-6_2.1.8-stable-4build1_amd64.deb
	sudo dpkg -i libevent-2.1-6_2.1.8-stable-4build1_amd64.deb
	```
4. Add Bitcoin repository
	```bash
	sudo add-apt-repository ppa:bitcoin/bitcoin 
	```
	and install required libdb packages
	```bash
	sudo apt-get update 
	sudo apt-get upgrade 
	sudo apt-get install libstdc++6 libdb4.8-dev libdb4.8++-dev gcc g++
	```
5. Download and install Openssl	
	```bash
	wget https://www.openssl.org/source/old/1.1.0/openssl-1.1.0i.tar.gz
	tar xvf openssl-1.1.0i.tar.gz
	cd openssl-1.1.0i
	./config --prefix=/usr/local --openssldir=/usr/local/ssl -Wl,-rpath,/usr/local/lib 
	make
	sudo make install
	```
6. Download and install libboost
	```bash
	wget https://dl.bintray.com/boostorg/release/1.65.1/source/boost_1_65_1.tar.gz
	tar xvf boost_1_65_1.tar.gz
	cd boost_1_65_1
	./bootstrap.sh --prefix=/usr/local
	sudo ./b2 install
	```
7. Reboot Ubuntu
	```bash
	sudo reboot
	```
8. Download and build C25
	```bash
	cd ~
	git clone https://github.com/c25core/c25 c25
	chmod -R 775 ~/c25
	cd ~/c25
	./autogen.sh
	./configure
	make
	(Optional): make install
	```