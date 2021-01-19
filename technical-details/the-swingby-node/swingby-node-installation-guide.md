---
description: How to setup your own Swingby Metanode using our telegram deployment bot
---

# Swingby node installation guide

### 1. Swingby Node 101

The Swingby Metanode can be deployed on any reliable cloud service provider. We recommend Amazon AWS, Scaleway, Digital Ocean, Vultr, Hetzner, or GCP.

Once your Metanode has been fully deployed, it will begin using the skademia p2p messaging protocol to join the p2p network established by the other existing nodes.

#### 1.1 How to install Swingby node

The Swinby node can be installed in the following ways.

* Download & mannually build from github repository.
* [node-installer](https://github.com/SwingbyProtocol/node-installer) \(telegram bot\) -- **Availabe now**
* Third party node hosting provider \(coming soon\)

#### 1.2 Node dependencies

The Metanode relies on the Ethereum, Bitcoin, and Binance-chain states to form a consensus and perform swaps. For this reason, **your instance has to have multiple blockchain specific processes running in parallel on the same instance**. \(Total 4 docker containers\):

* Geth\(v1.9.25-stable\) 
  * A Ethereum full node 
* [_Blockbook_](https://github.com/trezor/blockbook) for Geth\(v0.3.4\) 
  * A Blockbook indexer for Geth
* Bitcoind\(v/Satoshi:0.20.1\) 
  * A Bitcoind full node
* [_Blockbook_](https://github.com/trezor/blockbook) for Bitcoind\(v0.3.4\) 
  * A Blockbook indexer for Bitcoind

### 2. Required resouces \[CPU/Memory/Storage/Network\]

Due to the resource-heavy dependencies needed by the Metanode, we recommend that you use an instance with **equal or greater** specs than below. If your node does not have enough resources available then it will not be able to stay in sync with the rest of the Metanodes in the network and will be dropped.

**\[Local Machine\]** \(Required to setup your **node-installer telegram bot**\)

* MacbookPro or Linux\(amd64\) 
* Docker 

**\[Server\]**

* 4 CPUs \(Dedicated\)
* 16G RAM
* 1.5TB Storage \(SSD\)
* 1Gbps Gigabit Network

### 3. The node-installer-bot

This is your personal assistant and will help you to deploy all of the necessary dependencies onto your server instance.

\(_Prerequisite: you have to create a Telegram bot via the_ [_@Botfather_](https://t.me/botfather) and obtain a BOT\_TOKEN. [Here's a tutorial](https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token)\)

#### 3.1 Setup

The following steps are for getting the installer-bot running.

1. Install Docker from [https://docker.io](https://docker.io) to your machine. \(MacOS recommended\)
2. Provision a new server instance that at least meets the Metanode hardware requirements above.
3. Ensure that your node has a static IP address \(otherwise known as a floating IP or elastic IP\).
4. Take a note of your server's IP address and SSH private key.
5. Run `echo "YOUR_SSH_KEY" >> ./data/ssh_key` to store your new instances SSH private key into a file that the installer bot can access. **\(This is important\)**
6. Run `$ export BOT_TOKEN={YOUR_BOT_TOKEN}` to store your new Telegram token in an environment variable that the installer bot can access.
7. Run `$ chmod +x scripts/start_build_and_install.sh && scripts/start_build_and_install.sh` for Mac User

#### 3.2 Configure your Metanode

Once you have completed the above setup steps, message your bot `/start` on telegram to see a list of commands that are available.

Also note, that the bot process running on your local machine has been killed. This is because the node-installer process has been uploaded to your server instance and is now running there.

Next, follow these steps:

* Step 1:

    Send your bot the `/setup_node` command. This command will start the process of generating your initial config and help you to time locking your Swingby tokens for bonding.

* Step 2:

    Send your bot the `/deploy_infura` command. This command will instruct your bot to deploy the necessary blockchain nodes and Blockbook indexers. You can check the syncing status using the `/check_status` command.

* Step 3:

    Send your bot the `/deploy_node` command. This command will instruct your bot to pull and build the latest source code from the master branch at the [SwingbyProtocol/swingby-node](https://github.com/SwingbyProtocol/skybridge-node) repo.

Provided that your infura dependencies have finished syncing and your Swingby token bond was accepted then your Metanode should be up and running!!

In the future when new Metanode updates are released, simply re-use the `/deploy_node` command and the node-installer bot will re-build your Metanode with the latest available source code. Don't worry, no state will be lost.

With node-installer updates, use the `/upgrade_your_bot` command.

