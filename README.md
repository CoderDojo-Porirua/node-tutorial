- Getting IP address for VirtualBox:
````
  VBoxManage list runningvms
	  "ubuntu nodejs installed" {e42c8b5a-3a0c-48fc-84cb-92f440df8d12}
````

````
  VBoxManage showvminfo "<vm name>" | grep mac -i
  	NIC 1:           MAC: 080027F7D29E, Attachment: Bridged Interface 'en0: Wi-Fi (AirPort)', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
````

````
  arp -a
	fritz.box (192.168.178.1) at 24:65:11:ed:9c:7d on en0 ifscope [ethernet]
	leighs-mbp.fritz.box (192.168.178.33) at 3c:15:c2:c1:9c:18 on en0 ifscope permanent [ethernet]
	ubuntu.fritz.box (192.168.178.39) at 8:0:27:f7:d2:9e on en0 ifscope [ethernet]
	vm-srv101.fritz.box (192.168.178.41) at 8:0:27:78:41:cc on en0 ifscope [ethernet]
	? (192.168.178.255) at ff:ff:ff:ff:ff:ff on en0 ifscope [ethernet]  
````

Inspired by http://cwbuecheler.com/web/tutorials/2013/node-express-mongo/

Part 1 - Install
================

````
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
````

````
sudo apt-get install git
````

````
nodejs --version
v0.10.25

npm --version
1.4.21
````

````
sudo npm install -g express
sudo npm install -g express-generator
````


# Get around node naming differences...
````
sudo ln -s /usr/bin/nodejs /usr/bin/node
````

Clone *this* tutorial
````
git clone https://github.com/CoderDojo-Porirua/node-tutorial
cd node-tutorial
````

Create test project
````
express nodetest1
cd nodetest1
sudo npm install
mkdir data
````

Browse to ````<ip address>````:3000
