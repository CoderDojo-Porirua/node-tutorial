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

````
npm start
````
Browse to ````<ip address>````:3000 - verify we get Express welcome page

- Change package.json, adding mongodb and monk

````
npm install
````

- Add routes and view for helloworld

````
npm start
````
Browse to ````<ip address>````:3000/helloworld

Add MongoDB database
````
sudo apt-get install mongodb
````
(If on windows, ````mongod --dbpath <path>/node-tutorial/exercises/nodetest1/data/````

````
coderdojo@ubuntu:~$ mongo
MongoDB shell version: 2.6.3
connecting to: test


> show dbs
admin  (empty)
local  0.078GB


> use nodetest1
switched to db nodetest1


> db.usercollection.insert({ "username" : "ninja", "email" : "ninja@coderdojo.org.nz" })
WriteResult({ "nInserted" : 1 })


> db.usercollection.find().pretty()
{
	"_id" : ObjectId("5466bb2df53ee4cfd1954edc"),
	"username" : "ninja",
	"email" : "ninja@coderdojo.org.nz"
}


> show dbs
admin      (empty)
local      0.078GB
nodetest1  0.078GB


> newstuff = [{ "username" : "ninja2", "email" : "ninja2@coderdojo.org.nz" }, { "username" : "ninja3", "email" : "ninja3@coderdojo.org.nz" }]
[
	{
		"username" : "ninja2",
		"email" : "ninja2@coderdojo.org.nz"
	},
	{
		"username" : "ninja3",
		"email" : "ninja3@coderdojo.org.nz"
	}
]


> db.usercollection.insert(newstuff);
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 2,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})


> db.usercollection.find().pretty()
{
	"_id" : ObjectId("5466bb2df53ee4cfd1954edc"),
	"username" : "ninja",
	"email" : "ninja@coderdojo.org.nz"
}
{
	"_id" : ObjectId("5466bbd6f53ee4cfd1954edd"),
	"username" : "ninja2",
	"email" : "ninja2@coderdojo.org.nz"
}
{
	"_id" : ObjectId("5466bbd6f53ee4cfd1954ede"),
	"username" : "ninja3",
	"email" : "ninja3@coderdojo.org.nz"
}



````

Our data will look like:

````
{
    "_id" : 1234,
    "username" : "ninja",
    "email" : "ninja@coderdojo.org.nz"
}
````