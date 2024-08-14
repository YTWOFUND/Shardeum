# Shardeum

We suggest you use the [official documentation](https://docs.shardeum.org/node/run/validator). </br>
Below are the minimum system requirements for the project.</br>
CPU: 4 Core </br>
RAM: 16Gb </br>
SSD: 250Gb </br>
OS: Ubuntu 20.04 </br>

### Actually version:
Network:Shardeum Atomium

Version:1.29.2


### Server preparation + install docker+docker-compose.
```
sudo apt update
sudo apt install htop mc curl tar wget jq bsdmainutils git make ncdu gcc jq chrony net-tools iotop nload clang libpq-dev libssl-dev build-essential pkg-config openssl ocl-icd-opencl-dev libopencl-clang-dev libgomp1 -y
sudo apt install wget jq ca-certificates gnupg -y
source /etc/*-release
rm -f /usr/share/keyrings/docker-archive-keyring.gpg
wget -qO- "https://download.docker.com/linux/${DISTRIB_ID,,}/gpg" | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io apparmor -y
docker_compose_version=`wget -qO- https://api.github.com/repos/docker/compose/releases/latest | jq -r ".tag_name"`
sudo wget -O /usr/bin/docker-compose "https://github.com/docker/compose/releases/download/${docker_compose_version}/docker-compose-`uname -s`-`uname -m`"
sudo chmod +x /usr/bin/docker-compose
docker-compose -v
```

### Install node.
```
curl -O https://raw.githubusercontent.com/shardeum/validator-dashboard/main/installer.sh && chmod +x installer.sh && ./installer.sh
```

### Install screen + script autorestart node.
```
apt install screen
screen -S monitor
wget -q -O node_control.sh https://raw.githubusercontent.com/mesahin001/shardeum/main/node_control.sh && chmod +x node_control.sh && sudo /bin/bash node_control.sh
```

### Useful commands

### Start validator.
```
cd .shardeum
./shell.sh
operator-cli gui start
operator-cli start
```

### Stake tokens validator. [Faucet](https://discord.gg/shardeum)
```
operator-cli stake 10
operator-cli stake_info your adress evm 0xxxx
```

### Unstake tokens validator.
```
operator-cli unstake
operator-cli stake_info your adress evm 0xxxx
```

### Remove nove.
```
sudo docker stop $(sudo docker ps -a -q)
sudo docker rm $(sudo docker ps -a -q)
sudo docker rmi $(sudo docker images -q)
Rm -rf .Shardeum
```
