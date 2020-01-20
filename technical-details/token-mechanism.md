# Token mechanism

Swingby Skybridge node operators incur two costs: 

1. Operational costs for running a node - server costs.
2. Staking costs - they have to initially buy SBY to stake. 

There are two types of staking to cover these expenses:

1. SBY staking - nodes that stake SBY to participate in swaps will receive swap _fee / n_. 
2. Float staking - nodes that deposit bridge currency will get swap fees proportional to their deposited amount of tokens. 

Float staking is specific to Swingby Skybridges that uses deposits on both source blockchain and target blockchain to allow for computational simple swaps, limiting swap fee to as low as possible for users. Larger deposits allow frictionless swaps, and possibly more important, comfortability in using the bridged token on the target blockchain, as the user is able to swap back to source blockchain at any desired time. In essence, these deposits are “lent” to the bride, and opportunity cost for depositing tokens need to be considered. Thus, deposit based Skybridges need to provide sufficient interest on tokens so make it an attractive option for token holders. An extra swap fee dedicated to depositors is thus needed in these cases.

**The SBY token**

The token used in Swingby Skybridge is called "Swingby Token" \(or "SBY"\). SBY will be deployed as a BEP-2 token on Binance Chain. It is used to prove eligibility to participate in a TSS group. It will also be distributed for the growth of the Swingby network ecosystem. In addition to the Binance Chain, SBY may be issued on other blockchains \(as peg, not affecting token supply\) that can be connected to Swingby Skybridge.

**Utility as a staking instrument** 

Swingby Skybridge is designed as a permissionless network with no central authority that can determine who can participate in a group or not. The way this is achieved is that Swingby Skybridge node operators must prove that they own SBY tokens on Binance Chain, and lock \(or stake\) them for as long as they intend to participate in a TSS group. To join a TSS group, a participant must acquire SBY and have owned it for a period of time. They are then able to prove this when TSS rounds \(public key creation, signing events\) occur.

Nodes are selected to participate in signing \(and earn fees\) based on their seniority, that is how long time the node has been operational. A node will start accrue up-time once it fulfills the peer requirements and is connected to the network. It is a simple seniority prioritization and thus different from coin-age; a node need to fulfill the stake required, but adding more tokens on top of that will not affect its priority. Furthermore, removing tokens so that the node goes below staking threshold will reset the seniority to zero. The trade-off is that early adopter nodes are difficult to out-compete as long as they stay honest, but it prevents late joiners to attack the network or get Sybil control by buying up tokens alone. 

