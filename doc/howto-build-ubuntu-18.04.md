
# Ubuntu 18.04 x64 build instructions.

To build you required: libssl, libboost, libevent.
Also you may need this: miniupnpc, libdb4.8, qt, protobuf, libqrencode, univalue, libzmq3. You can install it via apt-get.
1. Add universe repository and update your Ubuntu
	```bash
	sudo add-apt-repository universe
	sudo apt-get update 
	sudo apt-get upgrade
	```
2. Install some required packages
	```bash
	sudo apt-get install libssl-dev libevent-dev build-essential libtool autotools-dev automake pkg-config bsdmainutils
	```
3. Install some libboost packages
	```bash
	sudo apt-get install liboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev libboost-test-dev libboost-chrono-dev  
	```
4. Add Bitcoin repository
	```bash
	sudo add-apt-repository ppa:bitcoin/bitcoin 
	```
	and install required libdb packages
	```bash
	sudo apt-get update 
	sudo apt-get upgrade 
	sudo apt-get install libdb4.8-dev libdb4.8++-dev
	```
5. Clone from GitHub and build C25
	```bash
	git clone https://github.com/c25core/c25 c25
	chmod -R 775 ~/c25
	cd ~/c25
	./autogen.sh
	./configure
	make
	(Optional): make install
	```