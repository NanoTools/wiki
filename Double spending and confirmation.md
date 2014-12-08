# Usual confirmation
In the typical case of a block created by a well behaved client, the block is received by all peers in the network, checked for validity, and republished if they haven't been seen before.

# What are forks
A fork is when a misbehaved client creates two or more specifically crafted blocks which breaks the one-follows-another pattern of a block chain.  Ledgers can only have one block following another so peers need to figure out which block to agree on.  Forks can never happen accidentally so we don't give a preference as to which block survives, any extra forks are forgotten and anything that derives from them is rolled back.  

# Simple fork resolution
Forks are easier to resolve the more time there there is from the first observed branch.  If one branch of a fork is published, every peer in the network receives a copy, and then a second branch of the fork is published, resolution of the fork is trivial because all peers will reject the second branch and in the first confirmation round the vote for the first branch will be 100%.  Simple fork resolution is entered after 1 network propagation period which is the time it takes for network packets to arrive to all peers; in practice this is probably less than a couple seconds.

# Complex fork resolution
In the worst case if multiple branches of a fork are published simultaneously, votes for each branch could be near equal in which case multiple resolution rounds could be needed to choose the winning branch.  The time window of opportunity for propagating multiple forks is very small, less than 1 network propagation period.  Someone crafting a fork would also have to simultaneously distribute different fork branches to different representatives who control the largest portion of vote control within this very limited period of time.

# Fork avoidance
The vulnerable accounts in a fork situation are the forked account itself as well as any account that receives from the malicious account after the fork.  During the vote process if an existing block is voted out, all dependent blocks are rolled back in order to accommodate the winning block.  Unlike existing cryptocurrency systems, this rollback only affects the account involved in the fork instead of affecting all transactions during a time period.  
Recipients can avoid issues by having a client designed to wait at least a full network propagation period before receiving a send in to its block chain.  If a recipient sees a majority of the votes counted and there are no forks, it's statistically impossible that if a new fork was introduced it would succeed in gaining a majority vote.  If a recipient observes *any* forks during the confirmation period it should immediately add more time to wait for the sender's block to settle before attempting to receive it.  Note that the waiting receiver can still process other transactions while it waits for a fork to settle.

# Fork creation
It's important to point out that unlike existing cryptosystems where forks can be created by mining and transaction race conditions, in our system forks cannot be created by network delays, race conditions, message duplication, or by any other accidental means.  Forks can only be created by clients that been crafted to digitally sign blocks in an incorrect way so any observed fork should be treated with extreme skepticism.