# elixir_mainnet
A guide to how you can run a verifier on ELIXIR Mainnet
# elixir_mainnet A guide to how you can run a verifier on ELIXIR Mainnet

#1- you need Evm wallet 

#2- need sepolia faucet #need MOCK Elixir Tokens On Sepolia 

#https://testnet-3.elixir.xyz/ 

#4- Stake Your MOCK Tokens 

sudo apt update && sudo apt upgrade -y sudo apt install jq -y 

#install docker & curl(optional)

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 

sudo apt-get update sudo apt-get install docker-ce docker-ce-cli containerd.io docker version 


VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4) curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose chmod +x /usr/local/bin/docker-compose docker-compose --version 

#then docker pull elixirprotocol/validator:v3


git clone [https://github.com/0xbetax/elixir_mainnet]

#then


cd elixir-metadata

nano validator.env

#edit .env file with your wallet and etc. 

#then ctrl+x+y+Enter


#mainnet-part

#you need a new screen:

screen -s elixirtestnet


#then

sed -i '/^ENV=/ s/=.*/=/' validator.env
docker pull elixirprotocol/validator:testnet-3 --platform linux/amd64

sudo docker run --name elixir-testnet --env-file validator.env --env ENV=testnet-3 --platform linux/amd64 -p 17690:17690 --restart always elixirprotocol/validator:testnet-3

#then:

cd

screen -S elixirmainnet

cd elixir-metadata

docker pull elixirprotocol/validator --platform linux/amd64


sudo docker run --name elixir-mainnet --env-file validator.env --env ENV=prod --platform linux/amd64 -p 17691:17690 --restart always elixirprotocol/validator


#DONE!
