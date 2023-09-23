# Entangle
How To Run an Entangle Validator
## Setup Your server
```
sudo apt update && apt upgrade -y
```
##  Installing git, make, jq, python, golangci-lint and solcjs.
```
sudo apt install curl git jq lz4 build-essential unzip fail2ban ufw -y
```
## Install Go
```
ver="1.19"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
go version
```
## Clone Entangle Repository and Open It
```
git clone https://github.com/Entangle-Protocol/entangle-blockchain
cd entangle-blockchain
```
## Installing the application
```
make install
```
## Generate Your Wallet
```
sh init_key.sh <key_name> <password>
```
Give any name youd like to give to `<key_name>` and in place of `<password>` set your desired password. After execution save the Mnemonic.
## Download The Previous Blocks
```
sh get_snapshot.sh
```
## Start Your Node
```
sh run_node.sh
```
## Exporting The Private Key To Metamask
```
entangled keys unsafe-export-eth-key <key_name>
```
replace `<key_name>` with your previously set keyname and import the private key into your metamask. 
## Acquire NGL Tokens From Entangle Discord Faucet
Copy your address in Metamask and Go to https://discord.com/channels/938906933732212846/1087639392753025084 to get NGL Tokens.
![image](https://github.com/blacknodes/Entangle/assets/85839823/64fdaadc-b0ae-46b8-a751-83b44a013be9)
Click on verify and check DM from Entangle Bot
![image](https://github.com/blacknodes/Entangle/assets/85839823/eceb38d4-f356-4335-80cf-554eece8e5e8)
Paste the Metamask address here
![metamask](https://github.com/blacknodes/Entangle/assets/85839823/6a69e5d4-c3a7-4bfd-9ed7-b03d3a5c8d1a)



## Start Your Validator
```
entangled tx staking create-validator \
--amount="5000000000000000000aNGL" \
--pubkey=$(entangled tendermint show-validator) \
--moniker="validator" \
--chain-id=entangle_33133-1 \
--commission-rate="0.10" \
--commission-max-rate="0.20" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1" \
--gas=500000 \
--gas-prices="10aNGL" \
--from=<key_name>
```
moniker is the name you want to give to your `validator`, for example moniker="BlackNodes" , You should set your own name or something
Replace `<keyname>` with your keyname 
## Search Your Validator
Go to https://explorer.nodexcapital.com/entangle/staking and checkout your validator
## Fill The Validator Form
https://forms.gle/sSCudse9ds55rCva6
paste the account address starting wit `eth*****` not the one with `0x*****`
![accountaddress](https://github.com/blacknodes/Entangle/assets/85839823/1e3d7bf2-959f-4940-bd58-9dce0b4cf0a2)

### Congratulations You Are All set

#### More information can be found here https://entangle-protocol.gitbook.io/entangle-protocol/validator-guidelines-technical
