## Hardware: 
```
Ubuntu 20.04 + 64 bit
AWS- 2CPU + 4Gb + 50Gig
t3a.medium

Security Group/Ports: 
1. Custom TCP : 8081 - Anywhere - Pokt RPC 
2. Custom TCP : 26656 - Anywhere -Tendermint P2P
3. Custom TCP : 80 - SSL
```
## Running the pocket node
### Step 1: ssh into the server
```
ssh -i "your_private.pem" ubuntu@ec2-1-2-3-4.compute-1.amazonaws.com
```
### Step 2: create user
```
git clone https://github.com/satycool16/pokt-validator-configurator.git && cd pokt-validator-configurator && chmod 755 ./*.sh && sudo ./makeuser.sh
```
>Session starts with the username just created, we need to clone the repo again.
### Step 3: Install Dependencies
```
git clone https://github.com/satycool16/pokt-validator-configurator.git && cd pokt-validator-configurator && chmod 755 ./*.sh && ./dependencyinstaller.sh
```
> [sudo] password for nodeuser:
>
>Do you want to continue? [y/N] y
>
> Do you want to install the latest go version? [y/N] y
> 
> STARTING NEW SHELL TO LOAD G-INSTALL...

### Step 4: SSL

>https://my.freenom.com/ - Register DNS with public ip address
>
```
sudo apt-get install python3-certbot-nginx
```
```
sudo certbot --nginx
```
### Step 5: install pocket-cli 
```
cp ~/pokt-validator-configurator/install.sh ~ && ~/install.sh
```
> Enter domain name for node:
> 
> Use seeds for Mainnet or Testnet (m/T): m
> 
> Use RC-0.6.1? n=use 0.5.2.9 (Y/n): Y
> 
> [sudo] password for nodeuser:
> 
> NGINX IS RESTARTED! CONFIGURATION COMPLETE

### Step 6: Create Pocket Account and Sync the Node
```
pocket accounts create
```

>Close the session and login again as the nodeuser

```
pocket start
```
