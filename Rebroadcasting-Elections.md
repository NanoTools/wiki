# Rebroadcasting & Elections
 
## Terminology & Basics
* Circulating supply = 133,248,290.903662 NANO (Mxrb)
* Rebroadcasting requirement = 0.1% (133,248.290903662 NANO)
* Representative: an account with > 0 delegated voting weight
* Voting weight (stake) = the amount of Nano delegated to the representative
* Rebroadcasting account = a representative account with > 0.1% voting weight
* Peers = nodes connected over the public internet to share Nano network data
* Quorum = when 50% of the online voting weight votes in one direction

## Defining Rebroadcasting
Rebroadcasting occurs when one node shares vote based information it has received from a peer to the rest of its peers. 
The decision to rebroadcast a vote is made if the representative account that authored the vote has over 0.1% voting weight. 
The weight of the node’s account rebroadcasting a peer account’s vote does not play a factor. 
You can find detailed stats on rebroadcasting accounts here: https://nanonode.ninja/active.

## Defining Voting
Each node votes on every block by appending their signature and a sequence number to the block. 
When the network needs to make a global decision (ex: fork resolution), your wallet software performs a balance-weighted vote to determine the outcome based on quorum.

## Elections
The election process happens internal to each node. 
Any unique incoming block is validated and added to the nodes ledger immediately.
If the network detects a need for a global decision (ex: fork resolution), an election is triggered.
During the election, votes are tallied from > 0.1% peers until quorum is reached. 
If the node determines quorum on a new block at any point during the election, it rolls back the block currently in the ledger and adds the new one. 
The total online weight used for quorum is determined dynamically based on the online weight of the > 0.1% representatives. 
If the total online weight is determined to be less than 60,000,000 NANO, then 60,000,000 is used by default. 
Both the minimum voting weight and quorum percentage are configurable by node. 
The defaults are 60,000,000 NANO and 50% respectively.
 
## Accounts with < 0.1% online voting weight
The voting process inside the node is the same regardless of voting weight. 
Votes from these nodes are also broadcast to directly connected peers. 
That being said, peers, regardless of voting weight, do not rebroadcast these votes or use them during elections. 
This helps to reduce network congestion and increase the efficiency of the election process. 
The main purpose of voting from < 0.1% accounts is to allow directly connected peers to determine the node’s health/uptime. 
A good example of this use case can be found on https://nanonode.ninja.
 
## Accounts with > 0.1% online voting weight (Rebroadcasting Accounts)
Peers that receive votes from these accounts rebroadcast the votes to their peers. 
When a global decision is required, the election process begins. 
The votes from > 0.1% peers are tallied until quorum is reached. 
For a more detailed description of elections, please see the Elections section above.

## Should you run a node, especially with < 0.1% voting weight?
This is not an easy yes or no question. 
An abundance of nodes that are not maintained properly will become detrimental to the network. 
Therefore, regardless of your voting weight, you should consider the following prerequisites for running a node:

1. Keep the node software up to date in a timely fashion
2. Maintain the proper hardware and bandwidth required
3. Address issues proactively and patch as needed
4. Become and stay an active member of the Nano technical community

If you have < 0.1% voting weight, but will commit to the above, then running a node is worthwhile to further decentralize the network. 
These points become even more critical as you amass voting weight or become a rebroadcasting account. 

## Closing Thoughts
Eventually the official representatives will be shutdown and additional measures will be put in place to spread voting weight more easily. 
Having existing, trustworthy, well maintained representative nodes will be critical as the voting weight is redistributed. 
We will see those with < 0.1% grow to become rebroadcasting accounts over time. 
Nano’s vision to become truly decentralized cannot be realized without the community’s dedication to the cause.

## Sources
* https://github.com/nanocurrency/raiblocks/blob/master/rai/node/node.cpp#L2483
* https://github.com/nanocurrency/raiblocks/blob/master/rai/node/node.cpp#L3133
* https://nano.org/en/explore/summary
* https://nano.meltingice.net/network
* https://github.com/nanocurrency/raiblocks/wiki/Representatives-and-decentralization
* https://youtu.be/PgHUA8TGaXY
