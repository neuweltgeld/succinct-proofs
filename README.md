# Succinct using SP1 examples

![image](https://github.com/user-attachments/assets/39d95a07-bdc8-48a3-919e-14404eba0ead)


By using https://testnet.succinct.xyz/ UI and playing games, we both earned stars and increased the number of proofs on the network. 

The stars were the showcase part of our work. The real work was done in the kitchen, thanks to proofs. 

Now let's go deeper and produce proofs ourselves. 

### Minimum requirements

x86 or ARM 4CPU

16GB RAM (minimum 16GB required)

Disk 10+GB

I used Ubuntu 22.04

You need USDC tokens for paying proof fees, for this we will use credits provided by succinct. You need the private key of this wallet.
Do not share it with anyone. Only use content downloaded from official repos. 
This guide contains official repo links.

### Let's move on to the steps

Update and upgrade OS
```
apt update && apt upgrade -y
apt install build-essential git curl gcc make jq clang protobuf-compiler pkg-config libssl-dev -y
```

Install rust and set sources
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source ~/.profile
source ~/.cargo/env
```

Install Docker, enter combined commands in once
```
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Install SP1UP from Prebuilt Binaries.
```
curl -L https://sp1up.succinct.xyz | bash

source /root/.bashrc
```

Install the toolchain and the cargo prove CLI
```
sp1up
```

You can verify the installation of the CLI by running 
```
cargo prove --version
```


```console
# Output sample 
cargo-prove sp1 (9312c7c 2025-04-17T19:03:23.801341994Z)
```

Create an SP1 Project
We will use example projects to generate proofs, but you can improve these projects and create your own unique projects.

In this example we will use `fibonacci` because it is both fast and cheap.

```
cargo prove new --bare fibonacci
cd fibonacci
```

Moving into the final stages
In the command below, where it says `NETWORK_PRIVATE_KEY=<YOUR_PRIVATE_KEY>`

Replace `<YOUR_PRIVATE_KEY>` with your private key and start the execute process

The first compile will take some time. Subsequent executions will not take much time.

```
SP1_PROVER=network NETWORK_PRIVATE_KEY=<YOUR_PRIVATE_KEY> NETWORK_RPC_URL=https://rpc.production.succinct.xyz RUST_LOG=info cargo run --release -- --execute
```

### Output sample 

![Screenshot 2025-04-28 220135](https://github.com/user-attachments/assets/bc5369d7-3fd7-4db2-9136-b09e7964f8b8)

We then start the prove process.

Replace `<YOUR_PRIVATE_KEY>` with your private key and start the execute process

```
SP1_PROVER=network NETWORK_PRIVATE_KEY=<YOUR_PRIVATE_KEY> NETWORK_RPC_URL=https://rpc.production.succinct.xyz RUST_LOG=info cargo run --release -- --prove
```
### Output sample 

![Screenshot 2025-04-28 220216](https://github.com/user-attachments/assets/b03b3f6c-8560-46c0-8116-3719ddd1c45f)

You can check your proofs in https://testnet.succinct.xyz/explorer/account explorer. 

![Screenshot 2025-04-28 220320](https://github.com/user-attachments/assets/c8b31772-f181-4455-adf4-3d7d1fd0394d)

# Show your love to Succinct!
### If you like the guide, don't forget to support it on X! Thank you
