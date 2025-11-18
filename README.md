# gensyn-rl-swarm
How to run gensyn rl swarm with vps just 4 cpu 8gb ram(Its my experiment better use more than this) 
### "ATTENTION" USE FOR SWARM ONLY IF YOU TRY TO USE 4 CPU TOO

i already suggest you to use specs more than this, you can rent it on contabo for the lowest one if you want to try

# This guide is going through the easiet default way to participate on testnet, you can checkout Official Repo for more details.

cause we are using 8gb ram we need to make a swapfile first

make the swapfile 
```bash
sudo fallocate -l 32G /swapfile
sudo dd if=/dev/zero of=/swapfile bs=1G count=32 status=progress
```
```bash
sudo chmod 600 /swapfile
```
```bash
sudo mkswap /swapfile
```
```bash
sudo swapon /swapfile`
```
```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```
cek
```bash
free
```
reboot
```bash
sudo reboot
```
### 1. instal depedencies 

1. lets update first
```bash
sudo apt update && sudo apt upgrade -y
```
# Note: if there is any choices just press enter

2. Install General Utilities and Tools
```bash
sudo apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
3.install the python
```bash
sudo apt install python3 python3-pip python3-venv python3-dev -y
```
4. Install Node
```bash
sudo apt update
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
sudo apt install -y nodejs
node -v
npm install -g yarn
yarn -v
```
5.install yarn
```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
```
```bash
export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```
```bash
source ~/.bashrc
```
### 2. clone official repositories 
```bash
git clone https://github.com/gensyn-ai/rl-swarm/
```
### 3.run the swarm
• If you are an existing user, you must have your node's swarm.pem present in rl-swarm directory before starting the node, to recover just copy your swarm.pem file to rl swarm directory 
if you use docker copy to
rl-swarm/users/keys paste here

# run the swarm
make screen
```bash
screen -S swarm
```
get into rl-swarm directory 
```bash
cd rl-swarm
```
install swarm
# (we will use docker here if you run especially trying with 4cpu like me i have already try with venv and cli but it crashed and docker? its running smoothly its i really recommended you to use docker

```bash
snap install docker
```
```bash
docker compose run --rm --build -Pit swarm-cpu
```
wait for it to run till asking you to log in

# log in

we will use 2 option here local tunnel and ngrok (i prefer use ngrok)

1.local tunnel

duplicate your terminal
then
```npm install -g localtunnel```
```lt --port 3000```
copy the links to your browser and log in

2.ngrok

duplicate your terminal 
go to 
https://dashboard.ngrok.com/login
create ngrok account 
go to installation choice linux
scroll down(there is must be a command
back to your terminal
paste the command 
after you paste the ngrok authtoken command (dont paste the ngrok http 80)

write this on your terminal
```bash
ngrok http 3000
```
copy the link and log in
back to your terminal
wait till asking you to press something

press enter 2 times and done your nodes should be running

# NOTE I ALREADY SAYS TO YOU RUN ON BETTER SPECS THAN MINE FOR BETTER PERFORMANCE 

but if you want to try okay then hope its running well for you. me?
yes its running well hehe






