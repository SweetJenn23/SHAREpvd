# Errata for SHARE Academy Blockchain labs
## Lab 1
### p. 13 

* Step 11 - This step instructs you to log out and then log back in again.  In order to log out, enter either ```exit``` or ```logout``` from the command line. Then to log in you may need to start a PuTTY new session again and then log in with ```bcuser@192.168.22.*xxx*```

### p. 14

* Step 16 - leave off the `==1.12` from the command.  I.e., enter ```pip install docker-compose```
* Step 17 - the output from the `docker-compose --version` command will show **1.15.0**
* Step 19 - the output from the `docker-compose --version` command will show **1.15.0**

### p. 15
* Step 25 - the tilde in the ```cd ~``` command is not highlighted in yellow in the workbook by mistake.  Make sure to enter it.
### p. 17
* Step 1 - if the command listed in this step fails, run the command ```sudo apt-get update``` and then retry the command that failed
### p. 18
* Step 7 - issue this command instead of the one printed in the workbook: ```git checkout v1.0.0```  
### p. 19
* Step 13 - this command spans lines in the PDF document and copy/paste will fail due to a linefeed being added by the PDF.  You can copy/paste the entire command from here instead:
```./network_setup.sh up mychannel 10 couchdb```
### p. 21
* Step 5 - issue this command instead of the one printed in the workbook: ```git checkout v1.0.0```  
### p. 23
* Step 8 - this command spans lines in the PDF document and copy/paste will fail due to a linefeed being added by the PDF.  You can copy/paste the entire command from here instead: ```git clone https://gerrit.hyperledger.org/r/fabric-sdk-node```
### p. 24
* Step 11 - issue this command instead of the one printed in the workbook: ```git checkout v1.0.0``` 
* Step 14 - there is a period that is accidentally highlighted in yellow but this part of the output and not part of the command to enter.  The command to enter is simply ```npm list```
## Lab 2
### p. 47
* Step 3 - the single quotes in this command got converted by PDF into a character that will not work if copy/paste is used from the PDF.  You can copy/paste the command from here instead:  ```find . -name '*' -mmin -15```
### p. 50
* Step 1.  The second highlighted line is not part of the command to be entered.  The command to be entered is from the first line only, i.e.: ```docker exec -it cli bash```
### p. 52
* Step 5 - Copy and paste the command from here instead of using what is printed in the PDF. The contents of the command have changed due to changes in Hyperledger Fabric code since the workbook was created: ```export FABRIC_TLS="--tls --cafile /opt/gopath/src/github.com/hyperledger/fabric/peer/crypto/ordererOrganizations/blockchain.com/orderers/orderer.blockchain.com/msp/tlscacerts/tlsca.blockchain.com-cert.pem"```
### p. 54
* Step 4 - __It is critical to repeat these steps for the other three peers__. To do this, repeat steps 1-4 three times, but use a different combination of __*n n*__ in Step 1 each time, i.e.  **source scripts/setpeer 0 1**, **source scripts/setpeer 1 0**, **source scripts/setpeer 1 1**.  You can use the up arrow key to recall commands, which you may find helpful.
### p. 55
* Section 6 - The first **peer channel create** command spans a line in the PDF which breaks copy/paste due to an unwanted line feed in the PDF.  You may copy and paste the command from here.
```peer channel create -o orderer.blockchain.com:7050 -f channel-artifacts/Org0MSPanchors.tx $FABRIC_TLS -c mychannel```
### p. 55
* Step 2 - The command spans a line in the PDF which breaks copy/paste.  You may copy and paste the command from here: ```peer chaincode install -n marbles -v 1.0 -p github.com/hyperledger/fabric/examples/chaincode/go/marbles```
* Step 4 - The command spans a line in the PDF which breaks copy/paste.  You may copy and paste the command from here: ```peer chaincode install -n marbles -v 1.0 -p github.com/hyperledger/fabric/examples/chaincode/go/marbles```
### p. 56
* Step 4 - The command in the PDF is broken for copy/paste due to spanning a line, and single- and double-quote conversion issues.  You may copy/paste the command from here: ```peer chaincode instantiate -o orderer.blockchain.com:7050 -n marbles -v 1.0 -c '{"Args":["init","1"]}' -P "OR ('Org0MSP.member','Org1MSP.member')" $FABRIC_TLS -C mychannel```
* Step 5 - the command shown in this step was already issued in Step 4, and you do not need to re-enter it here in Step 5.
### p. 57
* Step 7 - Copy and paste the command from here to avoid PDF copy/paste issues: ```peer chaincode instantiate -o orderer.blockchain.com:7050 -n marbles -v 1.0 -c '{"Args":["init","1"]}' -P "OR ('Org0MSP.member','Org1MSP.member')" $FABRIC_TLS -C mychannel```
### p. 58
* Step 2 - Copy and paste the command from here to avoid PDF copy/paste issues: ```peer chaincode invoke -n marbles -c '{"Args":["init_owner", "o0000000000001","John","Marbles Inc"]}' $FABRIC_TLS -C mychannel```
### p. 60
* Step 5 - Copy and paste the command from here to avoid PDF copy/paste issues: ```peer chaincode invoke -n marbles -c '{"Args":["init_marble","m0000000000001","blue","35","o0000000000001","Marbles Inc"]}' $FABRIC_TLS -C mychannel```
### p. 61
* Step 7 - Copy and paste the command from here to avoid PDF copy/paste issues: ```peer chaincode invoke -n marbles -c '{"Args":["init_owner","o0000000000002","Barry","United Marbles"]}' $FABRIC_TLS -C mychannel```
### p. 62
* Step 9 - This is the same command from Step 7. You may use the up arrow to retrive the command or copy and paste it again from here: ```peer chaincode invoke -n marbles -c '{"Args":["init_owner","o0000000000002","Barry","United Marbles"]}' $FABRIC_TLS -C mychannel```
* Step 11 - all of these commands will have copy/paste issues from the PDF due to single- and double-quote conversion issues.  They are all listed here, and should work correctly if you copy and paste them from here:
```
peer chaincode invoke -n marbles -c '{"Args":["init_marble","m0000000000002","yellow","16","o0000000000002","United Marbles"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -n marbles -c '{"Args":["read_everything"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -n marbles -c '{"Args":["set_owner","m0000000000002","o0000000000001","United Marbles"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -n marbles -c '{"Args":["getHistory","m0000000000002"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -o orderer.blockchain.com:7050 -n marbles -c '{"Args":["delete_marble","m0000000000002","Marbles Inc"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -n marbles -c '{"Args":["getHistory","m0000000000002"]}' $FABRIC_TLS -C mychannel
```
```
peer chaincode invoke -n marbles -c '{"Args":["read_everything"]}' $FABRIC_TLS -C mychannel
```
## Lab 3
### p. 70
* Step 9 - This step is optional-  you only have to change the names if you want to. But if you do, the example shown in the PDF will not copy/paste well due to the issue with double-quotes conversion.  You can copy and paste the command from here: ```sed -i "s/alice/vincent/" marbles1.json```
### p. 73
* The commands at the top of this page are only needed if you did not use the default channel name of *mychannel* in Lab 2.  But if you do, the second command, besides having the double-quote conversion issue with PDF, also had the *s* in *sed* truncated from the workbook.  The correct command will look like this: ```sed -i "s/mychannel/tim/" blockchain_creds1.json```
### p. 81
* Step 4 - The second and third commands in this step are not highlighted in yellow or bolded in the workbook, but they should be entered: ```docker rm $(docker ps -aq)``` and ```docker ps -a```
### p. 82
* Step 5 - The second and third commands in this step are not highlighted in yellow or bolded in the workbook, but they should be entered: ```docker rmi $(docker images -q dev-*)``` and ```docker images dev-*```
## Lab 4
### p. 90
* Step 1 - leave the *0.8.1* off of the *npm install* command, that is, enter this instead of what is printed in the workbook:  ```npm install -g composer-cli```
* Step 4 - you do not need to enter this command.  Cordova is now installed as part of the npm install from a later step.
### p. 91
* Step 8 - the **npm install** command is accidentally not bolded or highlighted in the PDF but be sure to enter it
### p. 92
* Step 13 - the second command in this step spans lines so a copy/paste from PDF will fail. You can copy and paste it from here: ```grep x86_64 docker-compose.yml```
* Step 13 - the third command in this step spans a page so a copy/paste from PDF will fail. You can copy and paste it from here:  ```sed -i s/x86_64/s390x/ docker-compose.yml```
### p. 93
* Step 13 - the fourth command in this step spans a line so a copy/paste from PDF will fail. You can copy and paste it from here:  ```grep x86_64 docker-compose.yml```
* Step 13 - the fifth command in this step spans a line so a copy/paste from PDF will fail. You can copy and paste it from here: ```grep s390x docker-compose.yml```
* Step 13 - the final four commands in this step all span lines in the PDF so that copy/paste will fail.  You can copy and paste them from here:<br />
```grep x86_64 downloadFabric.sh```<br />
```sed -i s/x86_64/s390x/g downloadFabric.sh```<br />
```grep x86_64 downloadFabric.sh```<br />
```grep s390x downloadFabric.sh```
### p. 94
* Step 20 - type ```2k``` instead of *3k* as listed in the instructions and this will put you on the line right under the comment that reads *Join peer0.org1.example.com to the channel*
* Step 23 - type ```23dw``` instead of *28dw* as listed in the workbook and this will delete the next 23 words
* Step 26 - type ```sh -c “CORE_PEER_MSPCONFIGPATH=/etc/hyperledger/msp/users/Admin@org1.example.com/msp``` and add a
space, which will insert all this between peer0.org1.example.com and peer channel join. Make sure that you type in the double quotes near the beginning, after sh -c, but leave a space before the double quotes, and also type a space
at the end of ...Admin@org1.example.com/msp so that there is a space between ...Admin@org1.example.com/msp and peer
channel join...
* Step 28 - the last sentence should read *Your cursor will be on the k at the end of composerchannel.block*
### p. 95
* Step 30 - the line you modified should look like this:```docker exec peer0.org1.example.com sh -c "CORE_PEER_MSPCONFIGPATH=/etc/hyperledger/msp/users/Admin@org1.example.com/msp peer channel join -b composerchannel.block"```
* **Skip** steps 32 through 43
### p. 96
* Step 46 - the output from the command in this step should look like this:
>docker exec peer0.org1.example.com peer channel create -o orderer.example.com:7050 -c composerchannel -f /etc/hyperledger/configtx/composer-channel.tx
>
>  \# Join peer0.org1.example.com to the channel.
>docker exec peer0.org1.example.com sh -c "CORE_PEER_MSPCONFIGPATH=/etc/hyperledger/msp/users/Admin@org1.example.com/msp peer channel join -b composerchannel.block"
>
>cd ../..
### p. 99
* Step 50 - This command spans two lines in the PDF-  copy and paste it from here: ```cd ~/composer-sample-applications/packages/digitalproperty-app/```
### p. 100
* Step 53 - the command is accidentally not bolded and highlighted in the workbook, but make sure to run it:  ```npm run listAssets```
### p. 102
* Step 1 - leave the *@0.8.1* off of the *npm install* command.  That is, enter this: ```npm install -g composer-playground```
### p. 103
* Step 5 - The command shown here is an example and will not work on the SHARE Academy workstations. Follow instructor-provided instructions for how to perform the scp file transfer on your workstation.
### p. 109
* Step 6 - the instructions say to leave *forSale* as *false* but this value no longer shows up on your screen unless you click the *Optional Properties* underneath where you are entering the text.  You don't need to do that as the default value is *false*.
### p. 113
* Step 15 - the double quotes in the line to copy will break because of the PDF double-quote conversion issue.  You can copy that line from here instead: ```propertyForSale.title.information += " . He really needs the money. ";```
### p. 116
* Step 25 - Due to a [bug in Hyperledger Composer](https://github.com/hyperledger/composer/issues/1654) which I have reported but has not been fixed yet, you will not see the GoldNuggets listed on the left until you deploy the model a second time.   Go back to Define and click Model File and click the Deploy button again.  If the button is not active, you can add a single space in the file to activate the button.
### p. 117
* Step 28 - The command shown here is an example and will not work on the SHARE Academy workstation. Follow instructor-provided instructions for how to perform the scp file transfer on your workstation.
* Step 30 - The command spans lines in the PDF so copy and paste it from here: ```composer network list -n digitalproperty-network -p hlfv1 -i admin -s adminpw```
### p. 119
* Step 32 - The command spans lines in the PDF so copy and paste it from here: ```composer network update -a ~/modified-digitalproperty-network.bna -p hlfv1 -i admin -s adminpw```
<br/>**Note**: Due to the same [bug in Hyperledger Composer](https://github.com/hyperledger/composer/issues/1654) previously mentioned, you will need to **repeat** this command a second time.
* Step 33 - This command spans lines in the PDF so copy and paste it from here: ```composer network list -n digitalproperty-network -p hlfv1 -i admin -s adminpw```
### p. 120
* Step 3 - Leave the *0.8.1* off of the *npm install* command. That is, enter this: ```npm install -g composer-rest-server```
### p. 121
* Step 5 - there are additional questions added since the workbook was created.   For the question, *Specify if you want to enable event publication over WebSockets: (Y/n)*, enter **n**. For the question, *Specify if you want to enable TLS security for the REST API: (y/N)* hit enter to accept the default of *No*. 
* Step 5 - ignore the *UnhandledPromiseRejectionWarning* message once the REST server starts up
### p. 128
* Step 3 - Leave the *0.8.1* off of the *npm install* command. That is, enter this: ```npm install -g generator-hyperledger-composer```
### p. 129
* Step 7 - the first command has single quotes which will be a problem if copied and pasted from the PDF.  You may copy and paste it from here: ```grep 'ng serve' package.json```
* Step 7 - the second command has double quotes which will be a problem if copied and pasted from the PDF.  But you are going to have to change the command anyway to put in your IP address in place of 192.168.22.225 so go ahead and type the command in manually.
* Step 7 - the third command is a repeat of the first command.  Use the up arrow key to recall it and enter it, since copying it from the PDF will fail because of the quote problem.
### p. 133
* Step 7 - The drawing shows the Channel name as *mychannel*.  On your system, the channel will be set to *composerchannel*.  Leave it set to *composerchannel*.
* Step 7 - The instructions ask you to change the *Key Value Store Directory* value to */home/bcuser/.hfc-key-store.  You need to change it to **/home/bcuser/.composer-credentials**  (Don't forget the period, or dot, at the front of *.composer-credentials*)
### p. 140
* Step 21 - You will need to do a second Deploy (add a blank space if necessary to activate the Deploy button for the second Deploy) due to the same [bug in Hyperledger Composer](https://github.com/hyperledger/composer/issues/1654) previously mentioned.
