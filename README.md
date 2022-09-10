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
