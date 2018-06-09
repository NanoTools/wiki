# Rebroadcasting & Elections
 
## Terminology & Basics
* Circulating supply = 133,248,290.903662 NANO (Mxrb)
* Rebroadcasting requirement = 0.1% (133,248.290903662 NANO)
* Representative: an account with > 0 delegated voting weight
* Voting weight (stake) = the amount of Nano delegated to the representative
* Rebroadcasting account = a representative account with > 0.1% voting weight
* Peers = nodes connected over the public internet to share Nano network data
* Voting = each node votes on every block by appending their rep signature and a sequence number to the block
* Quorum = when 50% of the online voting weight votes in one direction
* Active transaction = a newly downloaded block to the node
* Root = the account if the block is an open block otherwise the previous hash the block lists

## New Blocks & Unchecked
There are several checks undergone when a new block is received by a node prior to it being committed to the ledger.
A block is outright rejected and not moved to Unchecked if it has a bad signature or bad POW.
A block will be moved to Unchecked if any of the following occur: a gap in the chain (either previous or source), a negative spend attempt, a block already received, an invalid balance, a fork, or an attempt to open the burn account.
If the block does not have these issues then it is committed to the ledger as an active transaction.
From a wallet standpoint, the transaction will move from pending to pocketed.
Now as an active transaction, it will be subject to announcement rounds.
The only types of blocks in Unchecked that will also be subject to announcement rounds are forks.

## Announcement Rounds
Currently an announcement round lasts 16 seconds, although there is a proposal to reduce this to 4 seconds.
During an announcement round, a loop occurs iterating through all roots within registered active transactions.
If the root already exists on the ledger and has had election confirmation, then the block is removed from the active transaction list and stays committed to the ledger. 
If the root is new or exists on the ledger but does not have election confirmation, then the broadcast-winner logic is run.

#### Interpreting this in a different way - all new blocks committed to the ledger (and therefore pocketed to wallets) will be subject to election confirmation eventually, but not until it is recognized as a root who does not yet have election confirmation.

## Broadcast-Winner & Elections
Broadcast-winner includes the election process as well as republishing blocks if necessary. 
An election is conducted where votes are tallied based weight at time of election from > 0.1% peers until quorum is achieved. 
If the node determines quorum on the root of a new block at any point during the election, it rolls back the block currently in the ledger and its dependents then adds the new one. 
The active transaction is closed once quorum is achieved regardless of whether quorum is for the existing block or a new block. 
If the active transaction stays open while quorum is waiting to be achieved for longer than the announcement round threshold (currently 16 seconds), then it moves to unconfirmed (Unchecked). 
These unconfirmed blocks may be confirmed eventually when quorum is met or will remain Unchecked until cleared if they are invalid blocks from a fork.
The total online weight used for quorum is determined every five minutes based on the online weight of the > 0.1% representatives. 
If the total online weight is determined to be less than 60,000,000 NANO, then 60,000,000 is used by default. 
Both the minimum voting weight and quorum percentage are configurable by node. 
The defaults are 60,000,000 NANO and 50% respectively.

## Rebroadcasting
Rebroadcasting occurs when one node shares vote based information it has received from a peer to the rest of its peers. 
The decision to rebroadcast a vote is made if the representative account that authored the vote has over 0.1% voting weight. 
The weight of the node’s account rebroadcasting a peer account’s vote does not play a factor. 
You can find detailed stats on rebroadcasting accounts here: https://nanonode.ninja/active and here: https://nano.meltingice.net/network.
 
## Accounts with > 0.1% online voting weight (Rebroadcasting Accounts)
Peers that receive votes from these accounts rebroadcast the votes to their peers. 
When a global decision is required, the election process begins. 
The votes from > 0.1% peers are tallied until quorum is reached. 
For a more detailed description of elections, please see the Broadcast-Winner and Elections section above.

## Accounts with < 0.1% online voting weight
The voting process inside the node is the same regardless of voting weight. 
Votes from these nodes are also broadcast to directly connected peers. 
That being said, peers, regardless of voting weight, do not rebroadcast these votes or use them during elections. 
This helps to reduce network congestion and increase the efficiency of the election process. 
The main purpose of voting from < 0.1% accounts is to allow directly connected peers to determine the node’s health/uptime. 
A good example of this use case can be found on https://nanonode.ninja.
Trusted nodes with < 0.1% voting weight also help the network by being used as peers for bootstrapping.

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
Eventually the official representatives will be shut down and additional measures will be put in place to spread voting weight more easily. 
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
* Community members on Discord including (but not limited to) @bbalaska, @cryptocode, @DESRT, @renesq
