---
description: This page describe that bot commands are how it works
---

# BOT Commands list

![Bot commdand list](../../.gitbook/assets/image%20%2835%29.png)

### Command list \[only local machine\]

\[Setup Node\]

* **/setup\_server\_config**  
  * This command sets the IP address and login name of the server used by your bot.
* **/setup\_your\_bot**  
  * This command installs your bot to your server.

### Command list \[only server\]

\[Setup Node\]

* **/setup\_node**
  * This command sets all node configurations and gets the "description" set for the timelock transaction.  For more details about "staking", let's see here 👇

{% page-ref page="../../getting-start/how-to-timelock-swingby-tokens.md" %}



\[Deploy Node\] 

* **/deploy\_node** 
  * deploy your node 
* **/setup\_domain** 
  * configure domain 
* **/enable\_domain** 
  * attach domain to your server
* **/stop\_node** 
  * stop your node

\[Deploy Infura\] 

* **/setup\_infura** 
  * This command will remove all your blockchain data on **/var/swingby/mainnet** 
  * And **Downloading all of the new snapshots for infra packages.**
    * BTC-ETH network =&gt;  _bitcoind, bb\_btc, geth, bb\_eth_
    * BTC-BSC network =&gt;  _bitcoind, bb\_btc, bsc, bb\_bsc_
* **/resync\_infura** 
  * re-syncing snapshot 
* **/deploy\_infura** 
  * deploy infura services

\[System management\] 

* **/check\_status**
  * checking status of system 
* **/upgrade\_bot**
  * upgrade bot to latest version 
* **/get\_node\_logs**
  * getting the latest logs of node

