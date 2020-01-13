# Leaderless consensus

**Parameter consensus**

Nodes need to agree on the TSS parameters they wish to use when creating the addresses.  The key parameters from the TSS protocol are:

* n - the total number of parties in the group who is able to partially sign a transaction, and
* t - the threshold \(minimum\) number of parties who need to collaboratively sign the transaction.

Nodes would agree t and n out of band, then broadcast their intention to use them. Nodes will only attempt form groups with other nodes that use the same parameters.

In our first implementation we will use n = 100 and t = 60.  That is, a group will be created where 100 parties will be needed to create the TSS public key, and where 60 of those 100  parties will need to come together to sign transactions.

#### Transaction Signing

When do transactions need to be signed?  Here are two scenarios:

* Some 3rd party wants BTC.S \(BinanceChain\).  He uses the Swingby website and enters the amount of BTC.S \(BinanceChain\) he wants, and his address on Binance Chain where he wants to receive it.  The website tells him how much BTC to send from his Bitcoin address to the TSS Group’s custodial BTC address. This requires the TSS Group to create BTC.S \(BinanceChain\) in its custodial Binance Chain address and send it to the 3rd party’s Binance Chain address.
* Some 3rd party wants to redeem his BTC.S \(BinanceChain\) for real BTC on Bitcoin.  He sends BTC.S \(BinanceChain\) to the TSS Group’s custodial Binance Chain address. The TSS Group must send BTC from their custodial Bitcoin address to the 3rd party’s bitcoin address.

Each of the TSS nodes monitors the two custodial addresses on the two blockchains they are building a bridge between.  In our first implementation, this is Bitcoin and Binance Chain.

