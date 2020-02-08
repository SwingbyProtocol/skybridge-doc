---
description: This is a tutorial for setting up a local testnet node cluster (3 nodes)
---

# Starting a local testnet

Overview:

1. Git clone [**https://github.com/SwingbyProtocol/swapd-go**](https://github.com/SwingbyProtocol/swapd-go)\*\*\*\*
2. **Check your app setting**
3. **Run your test node 1**
4. **Run your test node 2 & 3**

You should start by opening 3 terminals; each one will be used to run one node process. 

Step 1. Git clone [**https://github.com/SwingbyProtocol/swapd-go**](https://github.com/SwingbyProtocol/swapd-go)\*\*\*\*

```text
$ git clone https://github.com/SwingbyProtocol/swapd-go
```

Step 2. Check your app settings. The configuration files for the local testnet are in **configs/local\_1/config.toml, configs/local\_2/config.toml, configs/local\_3/config.toml**

```text
[p2p]
moniker = "local_node_1"
listen = "127.0.0.1"
port = 12121

[rest]
listen = "127.0.0.1"
port = 8067
tls_enabled = false

[logger]
level = "INFO"
max_file_size_MB = 100
max_backup_files = 100
max_retain_files_days = 28
use_console_logger = true
use_file_logger = true
compress = true

[swaps]
testnet = true
coin_1 = "BTC.B-918"
coin_2 = "BTC"
stake_coin = "FUEL-F7D"
# stake_amount must be boosted by 10^8 for BNB Chain (this is 100,000)
stake_amount = 10000000000000
fee_percent = 0.1

[tss]
threshold = 2
participants = 3
keygen_until = "2019-12-31T00:00:00Z"

[bnb]
rpc_uri = "tcp://data-seed-pre-0-s3.binance.org:80"
http_uri = "https://testnet-explorer.binance.org"
stake_tx = "E2082A38EE937F922862B8DB24A8A1ACB2AADC1A394C617EEAF5D828136F4660"
stake_addr = "tbnb1m0qzkump83n7rwst78mrvhad5tlp45afqyum0v"
reward_addr = "tbnb1m0qzkump83n7rwst78mrvhad5tlp45afqyum0v"
fixed_out_fee = 500

[btc]
rpc_uri = ""
indexer_uri = "wss://testnet-indexer.swingby.network/ws"
reward_addr = "2N8hwP1WmJrFF5QWABn38y63uYLhnJYJYTF"
fixed_out_fee = 30000
```

Step 3. **Run your test node**

```text
$ go run ./cmd/swapd --home ./configs/local_1 --p2p.port 12121
```

Step 4. **Run your test node 2 & 3**

```text
$ go run ./cmd/swapd --home ./configs/local_2 --p2p.port 12122 --p2p.connect 127.0.0.1:12121 --rest.port 8068
```

```text
$ go run ./cmd/swapd --home ./configs/local_3 --p2p.port 12123 --p2p.connect 127.0.0.1:12122 --rest.port 8069
```



