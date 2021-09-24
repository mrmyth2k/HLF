# Hyperledger Fabric Installation For UBUNTU OS

At first we need to update our pc.
```bash
sudo apt update && sudo apt upgrade -y
```
After updating your pc you need to install some essential tools
```bash
sudo apt install build-essentials git curl python3-pip -y
```
So, after getting essentials we go and install node js
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```
After this restart your terminal and then execute these commands.
```bash
nvm install v14.17.6
```
To check whether installation of node is complete or not run these command.
```bash
node -v
npm -v
```
So you will find the output like this.

After installation of node we install `go language`.
```bash
sudo apt install golang -y
```
To check the installation of go lang.
```bash
go version
```
After this set environment path of go lang. Make a directory for go.
```bash
mkdir go
cd go
mkdir src bin pkg
```
After creating directory, open your .bashrc file by these command.
```bash
nano ~/.bashrc
```
Add these lines at the end of yor `.bashrc` file.
```bash
export GOPATH=/home/$USER/go
export PATH=$PATH:$GOPATH/bin
```
Then press `ctrl + x` then press `y` then press `Enter`. After this you came out of `.bashrc` file and reload your terminal.
```bash
source ~/.bashrc
```
Now we will configure our git inorder to install HLF
```bash
git config --global core.autocrlf false
git config --global core.longpaths true
```
Now we will install docker. So docker provides us a script inorder to install it on [https://get.docker.com/](https://get.docker.com/).
So we install it simply by running these lines.
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```
To check docker installation was successful or not run these commands.
```bash
docker --version
```
After installation fo docker we need to install docker compose.
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
To check docker compose installation run this commands.
```bash
docker-compose --version
```
No now our all requirements are fullfilled. Now let's start installing HLF.
```bash
cd ~/go/src
mkdir HyperledgerFabric && cd HyperledgerFabric
```
Now here comes the options if you want to install HLF of specific verion then run.
```bash
curl -sSL http://bit.ly/2ysbOFE | bash -s <your version goes here
```
for example : `curl -sSL http://bit.ly/2ysbOFE | bash -s 1.4.4 1.4.4 0.4.18` This will install HLF 1.4
if you want to install latest version of HLF,rhn run this command.
```bash
curl -sSL http://bit.ly/2ysbOFE | bash -s
```
Congratulation your HLF installed succesfully.

Now go to the `first-network` folder placed uder `HyperledgerFabric` folder.
```bash
cd fabric-samples/first-network
```
Here you will find `byfn.sh` file which is a script for building your first network. So run it by 
```bash
./byfn.sh generate
```
Now it's time to up our blockchain network. If you want to write your chaincode in go then run directly by
```bash
./byfn.sh up
```
Apart from it HLF provides us two more language to write our chaincode. In `node` and `java`.
so for achieving this up your network with `-l` flag.
As `./byfn.sh up -l node` or `./byfn.sh up -l java`

You can also provide odering service at the time of uping your network by using `-o` flag.
As `./byfn.sh up -o etcdraft` for `Raft` as odering service.
and for `Kafka` odering service run like this `./byfn.sh up -o kafka`

Finally when you want to down your network then use 
```bash
./byfn.sh down
```
