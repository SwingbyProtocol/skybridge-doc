---
description: How to setup your own Swingby node using our telegram deployment bot
---

# Swingby node installation guide

### 1. Skybridge Node 101

The Skybridge Metanode can be deployed on any reliable cloud service provider. We recommend Amazon AWS, Scaleway, Digital Ocean, Hetzner, or GCP.

Once your Metanode has been fully deployed, it will begin using the S/Kademia P2P messaging protocol to join the network established by the other existing nodes.

#### 1.1 How to install a Skybridge node

The Skybridge node can be installed in the following ways:

* Download & manually build from the Github repository.
* [node-installer](https://github.com/SwingbyProtocol/node-installer) \(telegram bot\) 

#### 1.2 Node dependencies

Swingby node relies on the Ethereum, Bitcoin, and Binance-chain states to form a consensus and perform swaps. For this reason, **your instance has to have multiple blockchain-specific processes running in parallel on the same instance**. \(Total 4 docker containers\):

* Geth\(v1.10.1\)  or Binance Smart Chain node \(v1.1.0-beta\)
  * A Ethereum full node 
* [_Blockbook_](https://github.com/trezor/blockbook) for Geth\(v0.3.4\) 
  * A Blockbook indexer for Geth
* Bitcoind\(v/Satoshi:0.20.1\) 
  * A Bitcoind full node
* [_Blockbook_](https://github.com/trezor/blockbook) for Bitcoind\(v0.3.4\) 

  * A Blockbook indexer for Bitcoind

  \*\*\*\*

**1.3  The node-installer-bot**

The Swingby installer bot is an assistant bot for installing Swingby nodes. The node setup process and checking the status of a node can all be done through its bot command.

The node-installer bot accesses the server via ssh key. You need to prepare a **local** __**machine** __based on Linux or MAC OS X as an initial installation. \(See below\)

After installing the bot on the server, the bot will be moved to the server itself and will continue to connect ssh and the bot chat group

```perl
Local machine (MAC OSX or Linux), 

         TG_BOT ----------------- SSH ----------> Server 
                                      |---------- TG_BOT (in Server)
                                  SSH |
                                      |---------> Server
```

### 2. Required hardware specs \[CPU/Memory/Storage/Network\]

Due to the resource-heavy dependencies needed by the Swingby node, we recommend that you use an instance with **equal or greater** specs than below. If your node does not have enough resources available then it will not be able to stay in sync with the rest of the Swingby node in the network and will be dropped.

**\[Local Machine\]** \(Required to install your **node-installer telegram bot**\)

* MacbookPro or Linux \(Ubuntu 20.04 LTS is recommended\) 
* Docker 

**\[Server\]**

* 4 CPUs \(Dedicated\)
* 16G RAM
* 1.5TB Storage \(SSD\) for **BTC-ETH** bridge, 1.6 TB storage \(SSD\) for **BTC-BSC** bridge
* 500Mbps+ Uplink
* **A static IP address that is binding on your Server NIC**

### 3. Staking SWINGBY on timelock transaction

* SWINGBY-BEP2 tokens \(held in a cold wallet\) staked for a **minimum of 1 month** with a total quantity that must be **above 50,000 SWINGBY tokens.**
* time lock transaction can be controlled in the timelock portal [https://timelock.swingby.network/](https://timelock.swingby.network/)

### 4. Disk mount structure

The Swingby node requires to use high I/O rate disk and enough spaces. all mounting path is under `/var/swingby`

| Target | Path |
| :--- | :--- |
| Main path | /var/swingby |
| Infrastructure directory path | /var/swingby/mainnet |
| BOT configure & Node configure path | /var/swingby/node |
| Nginx configure & TLS certificate data path  | /var/swingby/nginx\_data |

After completing the bot setup procedure, the bot will automatically build some directories under **/var/swingby** and start downloading the required snapshots. 

### 5. DNS subdomain configuration. 

The Swingby node has an Nginx container which is for support to use HTTPS for your node endpoint. to enable a DNS subdomain with an alias to your server, basically, you have to add an 'A' record to your DNS record. 

Example::   test1.swingby.network   A   42.24.147.214 60

* /setup\_domain \(This command is for setup your domain on your BOT chat\)
* /enable\_domain \(This command is for deploying Nginx with your DNS configure on your BOT chat\)

In the last command process, An SSL certification will be generated through the [Let's Encrypt](https://letsencrypt.org/) automatically

