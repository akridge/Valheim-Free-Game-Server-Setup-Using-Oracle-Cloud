# Oralce-Cloud-Valheim-Game-Server-Setup
![valheim_oracle](docs/valheim_oracle.png)

Step 1:
Sign up for Oracle Cloud Free Tier: https://www.oracle.com/cloud/free/

![valheim_oracle](docs/oracle_free_tier.png)
- Its a free trial and a free account too. 
- You won't be charged and can still use everal free services after the trail. 
- Plus they nicely label all the free stuff. 
- In this we will use 1 of the 2 free virtual machines. 


Step 2:
Create The Virtual Machine

Step 3:
Go ahead and setup the firewall stuff. Valheim using the following ports, but could be changed if you want during config. 

Install the following one at a time
```
sudo firewall-cmd --permanent --zone=public --add-port=2456/udp
```
```
sudo firewall-cmd --permanent --zone=public --add-port=2457/udp
```
```
sudo firewall-cmd --reload
```

Step 4: Install the linux game server manager
https://linuxgsm.com/lgsm/vhserver/

4a: Dependencies install
login
then  type the following to login as root
```
sudo su 
```
Then install the dependecies. Run the following one at a time
```
yum install epel-release
```
```
yum install curl wget tar bzip2 gzip unzip python3 binutils bc jq tmux glibc.i686 libstdc++ libstdc++.i686
```
4b. Install GameDig since its a recommended additional module that allows LinuxGSM to gather more info from the game
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
```
yum install nodejs
```
```
npm install gamedig -g
```
```
npm update -g
```
4c.
Then run this since it seems to be left out when installing linux game server manager
```
sudo yum install nmap-ncat
```
Step 5: Use LGSM to install Valheim
The next few steps are pretty easy. 
Create the user 
```
adduser vhserver
```
login as that user
```
su - vhserver
```
2. Download linuxgsm
```
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh vhserver
```
3. Run the installer following the on-screen instructions.
```
./vhserver install
```
And done. Now for config and useage. When logged into server as vhserver. 

See all commands:
```
./vhserver
```
Basic stuff
```
./vhserver start
./vhserver stop
./vhserver restart
./vhserver update
./vhserver details
./vhserver backup
./vhserver monitor
```
Once you start the server it will populate with a default config. 

Step 6: Optional - Migrate your world
```
sudo chmod -R ugo+rwx /home/vhserver/
```
