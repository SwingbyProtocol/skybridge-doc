# Threshold-Signature-Scheme

The Threshold Signature Scheme \(TSS\) is a protocol where private keys, and therefore cryptocurrency addresses, can be created by multiple parties. A threshold number \(ie a subset\) of those parties can then follow the protocol to collaboratively produce valid signatures to sign cryptocurrency transactions, without the parties needing to share any secrets with each other.  No trusted dealer is needed - the protocol is fully decentralized.

While TSS coordinates between multiple parties to create digital signatures for cryptocurrency transactions, an advantage of TSS is that it creates a single valid signature that accompanies a cryptocurrency transaction.  This differs from multi-sig \(and similar\) script implementations in Bitcoin that require multiple signatures.  It also means that this single signature mechanism can be used on any ECDSA signature chain, irrespective of if the chain natively has multi-sig capabilities or not.

An additional benefit of TSS transactions over multi-sig transactions is that TSS transactions are data-light - they contain no more signature data than normal transactions.  This means that they are cheap to verify. Any transaction fees \(sometimes known as mining fees, transaction fees, or gas\) needed to compensate miners to process these transactions is kept to a minimum as there is only one signature accompanying the transaction.

