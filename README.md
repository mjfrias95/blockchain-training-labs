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

after installing open vscode then go to view => extension => on search bar type hyperledger composer then install it. You 

Hyperledger Activity:

Mandatory:

    1. First, if you have existing blockchain-training-labs folder in your directory. You should rename it so you wont have any problems when you clone another blockchain-training-labs in git hub.
    
    2. Type in your terminal: git clone https://github.com/khrandm/blockchain-training-labs
    
    3. Then, open the your directory and copy supply and chaincode folder.

    4. Paste it to your fabric samples folder.
    
    5. Open supply folder. Then, right click open terminal and type npm install.
       Just ctrl+c if you get stuck.
       
    6. Paste this to your terminal: ./startFabric.sh

    7. then, node enrollUser.js
       
    8. followed by node registerUser.js

    9. Last, node app.js

    11. Now, we will push data using postman. Change the “GET” to “POST” and then type this in the url bar localhost:3000/invoice.
    
    12. Click on Body and select x-www-form-urlencoded then click Bulk Edit
    
    13. Then, paste this:
    
       invoicenumber:INVOICE6
       billedto:OEM
       invoicedate:02/08/19
       invoiceamount:10000
       itemdescription:KEYBOARD
       goodreceived:False
       ispaid:False
       paidamount:0
       repaid:False
       repaymentamount:0

       14. Then, click send and it will return success

       15. click on Key-Value edit then change “POST” to “PUT” and follow this:


        we will change the value of goodreceived to true if the good is received and then, click send.


        Now, we will paid the good. Uncheck goodreceived and check paidamount and change the value from 0 to 10000 then click send.


    Change “PUT” to “GET” and the url to localhost:3000 then click send to see the updated record.

Optional:

    1. Open terminal then “git clone https://github.com/khrandm/blockchain-training-labs”
    
    2. Open the folder that you cloned and paste it into your fabric-samples folder.
    
    3. Then download the required library for our chaincode. Type this into your terminal:
       go get github.com/golang/protobuf/proto
       go get github.com/hyperledger/fabric/common/attrmgr
       go get github.com/pkg/errors
       go get github.com/hyperledger/fabric/core/chaincode/lib/cid
       
    4. After downloading the library. Go to home/go/src/github.com/
    
    5. Copy the 3 folder then paste it into your fabric-sample/chaincode.
    
    6. Back to supply folder right click then open terminal and type this:
       ./startFabric.sh
       
    7. npm install
    
    8. Type node enrollAdmin.js
      
    9. node registerSupplier.sh
    
    10. node registerOem.sh
    
    11. node registerBank.sh
    
    12.  node app.js
       terminal should ouput this:
       Store path:/home/mark/fabric-samples/supply/hfc-key-store
       Example app listening on port 3000!
       
    13. we will check if its running. Open postman type in URL bar localhost:3000/invoice click header then add in content-type: user then value is supplier and change “GET” to “POST”
    
    14. Then click on body and click Bulk Edit then paste this:
       invoicenumber:INVOICE6
       billedto:OEM
       invoicedate:02/08/19
       invoiceamount:10000
       itemdescription:KEYBOARD
       goodreceived:False
       ispaid:False
       paidamount:0
       repaid:False
       repaymentamount:0
       
    15. click send and wait for the request to finish and it will return success
    
    16. Now we will set goodreceived to true. Click on headers change the value of user to oem
    
    17. Go to body and uncheck all keys except “invoicenumber” and “goodreceived” and change the value of goodreceived to true.
    
    18. now we will pay the supplier. Click on header and change the user value to “bank” and go to body and uncheck all except “invoicenumber” and “paidamount” then change the value of paidamount to “10000” and click send
    
    19. now we will check if the data is updated.
	Now in your terminal you can see the the isPaid key value is updated to “True” when we enter the paidamount.


NOTE:
If you get stuck here:
![selection_024](https://user-images.githubusercontent.com/44287989/52777794-95941300-307f-11e9-89f0-5d2d1d02f9a1.png)

and also this kind of error:
![selection_035](https://user-images.githubusercontent.com/44287989/52777691-5960b280-307f-11e9-9dac-fcff3a3c25b2.png)

you need to kill your docker by typing this into your terminal.
First right click on your fabric-samples/supply open terminal then type:
docker kill $(docker ps -q)
docker rm $(docker ps -aq)
docker rmi $(docker images dev-* -q)

then repeat from step 6 to 19.


REFERENCE:

https://hyperledger.github.io/composer/latest/installing/installing-prereqs.html
https://golang.org/
https://github.com/khrandm/blockchain-training-labs
