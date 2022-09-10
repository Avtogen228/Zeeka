# Instruction to install your own Zeeka node

First you need to update necessary packages — `sudo apt update && sudo apt upgrade -y`

Then install necessary packages — `sudo apt install wget jq git libssl-dev cmake -y`

Install Rust — `. <(wget -qO- https://raw.githubusercontent.com/letsnode/Utils/main/installers/rust.sh)`

Clone repository — `git clone https://github.com/zeeka-network/bazuka`

Get in *Bazuka* directory — `cd bazuka`

Install this — `cargo build`

Initialize node — `bazuka init --seed [your seed phrase] --network debug --node 127.0.0.1:8765`

**IMPORTANT**

Change *your seed phrase* to your new wallet that you should create specially for Zeeka. Just create a new wallet in Metamask (for example) and past the seed phrase to the command in ''. Example `bazuka init --seed 'avtogen is the best crypto user ever for sure i promise you' --network debug --node 127.0.0.1:8765`

Create a system file and don't forget to change [your ip] to your ip — 

`sudo tee <<EOF >/dev/null /etc/systemd/system/zeeka.service`
`[Unit]`
`Description=Zeeka node`
`After=network.target`

`[Service]`
`User=$USER`
`ExecStart=`RUST_LOG=info which bazuka` node --listen 0.0.0.0:8765 --external [your ip]:8765 --network debug --db ~/.bazuka-debug --bootstrap 5.161.152.123:8765 --bootstrap 65.108.201.41:8765 --bootstrap 185.213.25.229:8765 --bootstrap 45.88.106.199:8765 --bootstrap 148.251.1.124:8765 --bootstrap 195.54.41.115:8765 --bootstrap 195.54.41.130:8765`
`Restart=on-failure`
`RestartSec=3`
`LimitNOFILE=65535`

`[Install]`
`WantedBy=multi-user.target`
`EOF`

Run the service — `sudo systemctl daemon-reload` 
                  `sudo systemctl enable zeeka`
                  `sudo systemctl restart zeeka`

To add a command to check node logs type this — `. <(wget -qO- https://raw.githubusercontent.com/AlexM-dev/Utils/main/commands/insert_variable.sh) -n zeeka_log -v "sudo journalctl -fn 100 -u zeeka" -a`

Check logs — `zeeka_log`

If your current height is 1 that's ok.


sudo tee <<EOF >/dev/null /etc/systemd/system/zeeka.service
[Unit]
Description=Zeeka node
After=network.target

[Service]
User=$USER
ExecStart=`RUST_LOG=info which bazuka` node --listen 0.0.0.0:8765 --external [your ip]:8765 --network debug --db ~/.bazuka-debug --bootstrap 5.161.152.123:8765 --bootstrap 65.108.201.41:8765 --bootstrap 185.213.25.229:8765 --bootstrap 45.88.106.199:8765 --bootstrap 148.251.1.124:8765 --bootstrap 195.54.41.115:8765 --bootstrap 195.54.41.130:8765
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
