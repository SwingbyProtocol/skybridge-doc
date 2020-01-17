# Peer communication

When a new transaction needs to be created and signed by the TSS group, the process is as follows:

1. Each Swingby node independently builds up a list of peers that they are aware of on the Swingby network.
2. Each Swingby node independently advertises to other nodes on that list the message that they would like the TSS group to sign.  This is called the “Sign List Building” round.
3. Each Swingby node independently but deterministically creates a set of \(t\) signers meeting the criteria.  This is called the “Sign List Voting” round.
4. Each Swingby node independently runs the TSS rounds in parallel, and each one collects “signature shares” from other peers.  At this stage there is a lot of communication and cross-checking.
5. Using the signature shares, each Swingby node can independently create the full ECDSA signature for the message.
6. Any of the Swingby nodes can broadcast the signed transaction to the relevant blockchain \(Bitcoin or Binance Chain\).  This means that the blockchain will receive multiple similar transactions, all of which are identical - and only one of which will get through.

![](https://lh6.googleusercontent.com/in67Lg0Z81iAkt_AbYr58F0IWMj0VpZ2-3RkfQVpYKgiECFpf6YrAqNGbrkxKOHm7kG11kWqO8aSbupsuQsmvBc87cHJigr7BQ7Mdg4CDefLPDlp9Wy3PEX90vqTlNvIOJAFFprJ)

