---
description: What are the requirements to operate a metanode?
---

# Node requirements

The following minimum requirements \(hardware and wallets\) are required to run the full node software:

1. Runs in a Docker container \(STC preferred\) with good hardware specifications
2. Fast and stable network connection that can be located anywhere.
3. Your node must have sufficient storage, CPU speed, and RAM to run the software. 

{% hint style="warning" %}
The suggested setup is an instance with at least **4 CPU cores, 16 GB RAM, 1.5 TB SSD storage  and 500Mbps+ uplink.**
{% endhint %}

    4. SWINGBY tokens \(held in a cold wallet\) staked for a **minimum of 1 month** with a total quantity that  must be **above 50,000 SWINGBY tokens.**

    5. A valid Ethereum address to interact with the LP contract to collect transaction fees.

Other requirements are:

* Running the Skybridge Daemon. [It is available here.](https://github.com/SwingbyProtocol/skybridge-node)
* Running a Binance Chain node.
* Running an Ethereum node.
* Running an Ethereum Blockbook instance.
* Running a Bitcoin node.
* Running a Bitcoin Blockbook instance.

### How to run the Skybridge Daemon?

{% hint style="warning" %}
The process uses a Telegram bot to run you through all the necessary steps and configuration requirements. If you don't have a Telegram messenger account, [please visit the official website to create one](https://telegram.org/).
{% endhint %}

1. Fork and clone the repository available at [https://github.com/SwingbyProtocol/skybridge-node](https://github.com/SwingbyProtocol/skybridge-node) 
2. Input your SSH key of the instance \(e.g., AWS, DigitalOcean\) into the config.



