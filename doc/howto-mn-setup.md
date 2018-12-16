
					
# C25 HOWTO setup masternode
							
Here is some info about setup MN for those who could not do it yourself.
1. You must have a VPS with public IP address (You can run Ubuntu 16.04, 18.04 or another linux).
2. You must create a new address for masternode in your control wallet and send 2500 C25 to it. Wait for 6 confirmations.
3. Go to `Debug console` in menu and run `masternode genkey`. Save output data. It is your C25MNPrivateKey.
4. Go to `Debug console` in menu and run `masternode outputs`. Save output data. It is your C25MNtxid and C25MNcoi.
5. Minimal VPS config (~/.c25core/c25.conf):
	```
	rpcuser=C25MNUser
	rpcpassword=C25MNpassword
	rpcallowip=127.0.0.1
	daemon=1
	server=1
	listen=1
	masternode=1
	masternodeprivkey=C25MNPrivateKey
	```
	where     
	>C25MNUser is custom user for RPC access, <br/>
	>C25MNpassword is custom password for RPC access,<br/>
	>C25MNPrivateKey is output of command `masternode genkey` from your control wallet.<br/>
	
    Also you can add some additional parameters such as:
	```
	externalip=C25MNVpsExternalIp
	```
	and
	```
	bind=C25MNVpsExternalIp
	masternodeaddr=C25MNVpsExternalIp:12525
	```
	where
	>C25MNVpsExternalIp is your VPS public IP address.
		
6. Minimal config for control wallet (masternode.conf): 
	```
	mn01 C25MNVpsExternalIp:12525 C25MNPrivateKey C25MNtxid C25MNcoi
	```
	where
	>C25MNVpsExternalIp is your VPS public IP address,<br/>
	>C25MNPrivateKey is output of command `masternode genkey` from your control wallet,<br/>
	>C25MNtxid is transaction id of 2500 C25 transaction,<br/>
	>C25MNcoi is collateral output index of your 2500 C25 transaction.<br/>

7. Restart your control wallet and goto `Debug console`. 
	Run `masternode start-all`. 
	You will see something like that : `"overall": "Successfully started 1 masternodes, failed to start 0, total 1"`.
8. Congratulations. Your masternode successfully starts and will receive rewards shortly.
