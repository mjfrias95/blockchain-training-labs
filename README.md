# blockchain-training-labs
Laptop Specification
Manufacturer: Acer
Unit: Aspire 3 - A315-41-R287
OS: Ubuntu 18.04.1 LTS
OS Type: 64 bit
CPU: AMD Ryzen 3 2200U
Ram: 8 Gb
Kernel: Linux 4.15.0-43-generic (x86_64)

Installation:

First we need to install all of the dependencies for hyperledger. 
Open terminal then paste this:
curl -o https://hyperledger.github.io/composer/latest/prereqs-ubuntu.sh
chmod u+x prereqs-ubuntu.sh
./prereqs-ubuntu.sh

wait for it to finish installation. Then type this:

docker –version
npm –version
git –version
python –version 
node –version 

so you can check the version of your development environment.

after that, install Go language by pasting this to your terminal:

wget https://storage.googleapis.com/golang/go1.9.2.linux-amd64.tar.gz && \
sudo tar -C /usr/local -xzf go1.9.2.linux-amd64.tar.gz && \
rm go1.9.2.linux-amd64.tar.gz && \
echo 'export PATH=$PATH:/usr/local/go/bin' | sudo tee -a /etc/profile && \
echo 'export GOPATH=$HOME/go' | tee -a $HOME/.bashrc && \
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' | tee -a $HOME/.bashrc && \
mkdir -p $HOME/go/{src,pkg,bin}

wait for it to finish then type go –version.

Then install vscode. Just paste this to your terminal:
sudo snap install vscode --classic

after installing open vscode then go to view => extension => on search bar type hyperledger

Hyperledger Activity:

Mandatory:

First, if you have existing blockchain-training-labs folder in your directory. You should rename it so you wont have any problems when you clone another blockchain-training-labs in git hub.
Type in your terminal: git clone https://github.com/khrandm/blockchain-training-labs
Then, open the your directory and copy supply and chaincode folder.
Paste it to your fabric samples folder.
Open supply folder. Then, right click open terminal and type npm install.
    
    
