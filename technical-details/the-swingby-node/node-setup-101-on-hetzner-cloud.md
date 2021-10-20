---
description: A guide for installing your Swingby node on Hetzner dedicated servers.
---

# Node on Hetzner server

## Getting Started guide to deploy Swingby Nodes in the Hetzner server

1. Create your Hetzner account and Order an [AX-61-NVMe](https://www.hetzner.com/dedicated-rootserver/ax61-nvme/configurator) server&#x20;
2. Setup your telegram BOT with following this readme:\
   \=> [https://github.com/SwingbyProtocol/node-installer](https://github.com/SwingbyProtocol/node-installer)
3. Install your telegram BOT to your AX-61-NVMe server.
4.  Bonding your Swingby Tokens (on Binance chain) on Staking portal:\
    \=> [https://timelock.swingby.network](https://timelock.swingby.network)

    For more details about "staking", let's see here 👇

{% content-ref url="../../getting-start/how-to-timelock-swingby-tokens/" %}
[how-to-timelock-swingby-tokens](../../getting-start/how-to-timelock-swingby-tokens/)
{% endcontent-ref %}

{% hint style="info" %}
Why we choose the Hetzner server?\
\
The Hetzner Cloud is one of the most cost-effective servers for running swingby nodes in your local infrastructure package. I have a root user who has RSA key authentication as a bootstrap. Disk mounts are basically mounted at / (root). Basically, telegram BOT uses root to connect to the server, so this choice is much easier than other cloud services.
{% endhint %}

### Step 1. Generate your SSH private key \[on local machine]

```bash
$ git clone https://github.com/SwingbyProtocol/node-installer && cd node-installer
```

```bash
$ ssh-keygen -t rsa -b 4096 -f ./data/ssh_key   
```

```bash
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): <- (should be empty)

```

There are 2 files are generated on your local machine.&#x20;

* ./data/ssh\_key  <- (this is a SSH **private** key, it should be backed up)
* ./data/ssh\_key.pub   <- (this is a SSH **pubkey** for access to your server)

Also, you have to **grant permissions** with this command.

```bash
$ chmod 600 ./data/ssh_key   
```

### Step 2. Order your Hetzner account and Order an AX-61-NVMe server&#x20;

![](<../../.gitbook/assets/image (25).png>)

{% hint style="info" %}
&#x20;AX-61 NVMe has a 1.92TB disk (RAID1), The Swingby node requires 1.3TB for the **BTC-ETH bridge**, 1.4TB for the **BTC-BSC**_ _**bridge**_ _ (full installation using with your _**local\_infura **_)\
\
**local\_infura** means your node will be connected to self-hosting Geth (BSC) and 2 blockbooks containers, therefore, your server has to total 6 containers running. (bitcoind, geth/bsc, blockbook-btc, blockbook-eth/bsc, swingby node)
{% endhint %}

### Step 3. Setup your Server with your generated SSH public key

* You can put **./data/ssh\_key.pub** file texts into the server setup interface.

![](<../../.gitbook/assets/image (34).png>)

### Step 4. Make a new directory on your server \[on your server]

* you have to make a new directory&#x20;
  * /var/swingby

```bash
$ ssh -i ./data/ssh_key root@<YOUR_SERVER_IP> "mkdir /var/swingby" 
```

### Step 5. Setup your telegram BOT  \[on local machine]

* (_Prerequisite: you have to create a telegram BOT via the _[_@Botfather_](https://t.me/botfather) and obtain a BOT\_TOKEN. [Here's a tutorial](https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token))&#x20;
* COPY and PASTE to your command line like this

```bash
$ export BOT_TOKEN=1716737416:ACEoPHFFlCAGiD2xGQl3Zk_wCoOD9P3Igk0
```

### Step 6. Install Docker to your local machine

Install `Docker` from [https://docker.io](https://docker.io) to your local machine.&#x20;

![Example of Docker for MAC OSX ](<../../.gitbook/assets/image (31).png>)

### Step 7. Run your telegram BOT on your \[on local machine]

```
$ chmod +x scripts/install.sh && scripts/install.sh
```

![](<../../.gitbook/assets/image (30).png>)

### Step 8. Talk to your telegram BOT with /start

![](<../../.gitbook/assets/image (33).png>)

### Step 9. Set your IP address and login username&#x20;

![](<../../.gitbook/assets/image (29).png>)

* Hetzner cloud always uses **root** to log in via SSH session. then, your can going forward with type 'none'&#x20;

### Step 10. Install your telegram BOT to your server

![](<../../.gitbook/assets/image (28).png>)

* `/setup_your_bot  `
  * This command will start the process of move out your telegram BOT to your server

![](<../../.gitbook/assets/image (32).png>)

{% hint style="success" %}
Finally, you are ready to install on the Swingby node!!
{% endhint %}

![](<../../.gitbook/assets/image (35).png>)
