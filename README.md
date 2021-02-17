# Oralce-Cloud-Valheim-Game-Server-Setup-for-Free
![valheim_oracle](docs/valheim_oracle.png)

A more enhanced how-to guide coming soon after I do some testing of different compute configurations. 

## Step 1: Sign up for Oracle Cloud Free Tier
Link: https://www.oracle.com/cloud/free/

![valheim_oracle](docs/oracle_free_tier.png)
- Its a free trial and a free account too. 
- You won't be charged and can still use everal free services after the trail. 
- Plus they nicely label all the free stuff. 
- In this we will use 1 of the 2 free virtual machines. 



## Step 2: Create The Virtual Machine. 

Choose the following and make sure to download the SSH keys to login in the next step.
![valheim_oracle](docs/s1.jpg)
![valheim_oracle](docs/s2.jpg)
![valheim_oracle](docs/s3.jpg)
![valheim_oracle](docs/s4.jpg)

## Step 3: Login to the Virtual Machine

This will be different for every operating system so check out the offical oracle doc:
https://docs.oracle.com/en-us/iaas/Content/Compute/Tasks/accessinginstance.htm


## Step 4: Go ahead and setup the firewall stuff. 

Valheim uses the following ports, but could be changed if you want during config. 

Run the following one at a time
```
sudo firewall-cmd --permanent --zone=public --add-port=2456/udp
```
```
sudo firewall-cmd --permanent --zone=public --add-port=2457/udp
```
```
sudo firewall-cmd --reload
```

You will also need to add 

## Step 5: Install the linux game server manager
https://linuxgsm.com/lgsm/vhserver/


### 5a: Dependencies install
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
###5b. Install GameDig since 
Its a recommended additional module that allows LinuxGSM to gather more info from the game
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
###5c.Run this since it seems to be left out when installing linux game server manager
```
sudo yum install nmap-ncat
```
## Step 6: Use LGSM to install Valheim

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
___
# And done. Now for config and daily use cases. 

### When logged into server as vhserver. See all commands:
```
./vhserver
```
### Valheim Basic Server Command stuff
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

## Step 7: Setup your config file
...to be added

## Step 8: Optional - Migrate your world
...to be added
```
sudo chmod -R ugo+rw /home/vhserver/
```
