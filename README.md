# Hyperledger Fabric Installation
---
In this blog you will find how to install and setup hyperledger fabric on you ubuntu machine.
---
At fist we need to update our pc.
> `sudo apt update && sudo apt upgrade -y`
After updating your pc you need to install some essential tools
> `sudo apt install build-essentials git curl python3-pip`
So, after getting essentials we go and install node js
> `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`
After this restart your terminal and then execute these commands.
> `nvm install v14.17.6`
To check whether installation of node is complete or not run these command.
> `node -v`
> `npm -v`
So you will find the output like this.

After installation of node we install `go language`.
> `sudo apt install golang`
To check the installation of go lang.
> `go version`
After this set environment path of go lang. Make a directory for go.
> `mkdir go`
> `cd go`
> `mkdir src bin pkg`
After creating directory, open your .bashrc file by these command.
> `nano ~/.bashrc`
Add these lines at the end of yor `.bashrc` file.
> `export GOPATH=/home/$USER/go`
> `export PATH=$PATH:$GOPATH/bin`
Then press `ctrl + x` then press `y` then press `Enter`. After this you came out of `.bashrc` file and reload your terminal.
> source ~/.bashrc`
Now we will configure our git inorder to install [HLF](# Hyperledger Fabric Installation).
> `git config --global core.autocrlf false`
> `git config --global core.longpaths true`
Now we will install docker. So docker provides us a script inorder to install it on [https://get.docker.com/](https://get.docker.com/).
So we install it simply by running these lines.
> `curl -fsSL https://get.docker.com -o get-docker.sh`
> `sh get-docker.sh`
To check docker installation was successful or not run these commands.
 > `docker --version`
After installation fo docker we need to install docker compose.
> `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
> `sudo chmod +x /usr/local/bin/docker-compose` 
To check docker compose installation run this commands.
> `docker-compose --version`
No now our all requirements are fullfilled. Now let's start installing HLF.
> `cd ~/go/src`
> `mkdir HyperledgerFabric && cd HyperledgerFabric`
Now here comes the options if you want to install HLF of specific verion then run.
> `curl -sSL http://bit.ly/2ysbOFE | bash -s <your version goes here`
for example : `curl -sSL http://bit.ly/2ysbOFE | bash -s 1.4.4 1.4.4 0.4.18`
if you want to install latest version of HLF,rhn run this command.
> `curl -sSL http://bit.ly/2ysbOFE | bash -s`
Congratulation your HLF installed succesfully.

Now go to the `first-network` folder placed uder `HyperledgerFabric` folder.
> `cd fabric-samples/first-network`
Here you will find `byfn.sh` file which is a script for building your first network. So run it by 
> `./byfn.sh generate`
Now it's time to up our blockchain network. If you want to write your chaincode in go then run directly by
> `./byfn.sh up`
Apart from it HLF provides us two more language to write our chaincode. In `node` and `java`.
so for achieving this up your network with `-l` flag.
As `./byfn.sh up -l node` or `./byfn.sh up -l java`

You can also provide odering service at the time of uping your network by using `-o` flag.
As `./byfn.sh up -o etcdraft` for `Raft` as odering service.
and for `Kafka` odering service run like this `./byfn.sh up -o kafka`

Finally when you want to down your network then use 
> `./byfn.sh down`
