# Leaderless consensus

**Parameter consensus**

Nodes need to agree on the TSS parameters they wish to use when creating the addresses.  The key parameters from the TSS protocol are:

* n - the total number of parties in the group who is able to partially sign a transaction, and
* t - the threshold \(minimum\) number of parties who need to collaboratively sign the transaction.

Nodes would agree t and n out of band, then broadcast their intention to use them. Nodes will only attempt form groups with other nodes that use the same parameters.

In our first implementation we will use n = 100 and t = 60.  That is, a group will be created where 100 parties will be needed to create the TSS public key, and where 60 of those 100  parties will need to come together to sign transactions.



