Ledger:  
Big circles are nodes and the number inside is their vote stake  
Small circles are block messages and the associated vote stake  
The icon next to a node represents its view of the network state about a block  
* Zero - Unaware  
* Question - Received but not confirmed  
* Check - Confirmed  
* Exclamation - Fork observed  

# Usual confirmation
In the typical case of a block created by a well behaved client, the block is received by all peers in the network, checked for validity, and republished if it hasn't been seen before.

![Simple confirmation](https://raw.githubusercontent.com/clemahieu/raiblocks/master/images/confirmation%20-%20simple.gif)

# What are forks
A fork is when a misbehaved client creates two or more specifically crafted blocks which breaks the one-follows-another pattern of a block chain.  Ledgers can only have one block following another so peers need to figure out which block to agree on.  Forks can never happen accidentally so we don't give a preference as to which block survives, any extra forks are forgotten and anything that derives from them is rolled back. RaiBlocks resolves forks via a weighted voting system where representative nodes vote for the block they observe to have > 50% of the vote total and change their vote if they see their block has < 50% support. 

# Simple fork resolution
Forks are easier to resolve when more time has passed between publishing branches.  If all nodes in the network have seen a block and a fork is published, the fork is quickly rejected.

![Easy confirmation](https://github.com/clemahieu/raiblocks/blob/master/images/confirmation%20-%20easy.gif)

# Complex fork resolution
Forks are the worst when there is very little time between when they're published.  Fork resolution exponentially converges over time and fork existence can be detected within a couple seconds.  Upon detection, receivers can insert a delay or elect to never receive blocks that have a fork.

![Complex confirmation](https://github.com/clemahieu/raiblocks/blob/master/images/confirmation%20-%20complex.gif)

# Fork avoidance
The vulnerable accounts in a fork situation are the forked account itself as well as any account that receives from the malicious account after the fork.  During the vote process if an existing block is voted out, all dependent blocks are rolled back in order to accommodate the winning block.  Unlike existing cryptocurrency systems, this rollback only affects the account involved in the fork instead of affecting all transactions during a time period.  
Recipients can avoid issues by having a client designed to wait at least a full network propagation period before receiving a send in to its block chain.  If a recipient sees a majority of the votes counted and there are no forks, it's statistically impossible that if a new fork was introduced it would succeed in gaining a majority vote.  If a recipient observes *any* forks during the confirmation period it should immediately add more time to wait for the sender's block to settle before attempting to receive it.  Note that the waiting receiver can still process other transactions while it waits for a fork to settle.

# Fork creation
It's important to point out that unlike existing cryptosystems where forks can be created by mining and transaction race conditions, in our system forks cannot be created by network delays, race conditions, message duplication, or by any other accidental means.  Forks can only be created by clients that have been crafted to digitally sign blocks in an incorrect way so any observed fork should be treated with extreme skepticism.
