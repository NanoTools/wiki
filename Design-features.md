# Signing algorithm - ED25519
ED25519 is an elliptic curve algorithm developed in an academic setting with a focus on security from side channel attack, performance, and fixing a lot of the little annoyances in most elliptic curve systems.  The main site is here http://ed25519.cr.yp.to/

# Hashing algorithm - SHA3
Compared to existing cryptocurrencies, the hash algorithm chosen is much less important since it's not being used in a proof of work context.  In our implementation hashing is used purely as a digest algorithm against block contents.

# Block interval - Instant
With raiblocks, each account has its own block chain and can update this chain independent of anyone else in the network.  This metric is actually non-applicable however we include it since it's a standard metric for other cryptocurrencies.

# UDP message protocol
Our system is designed to operate indefinitely using the minimum amount of computing resources as possible.  All messages in the system were designed to be stateless and fit within a single UDP packet.  This also makes it easier for lite peers with intermittent connectivity to participate in the network without reestablishing short-term TCP connections.  TCP is used only for new peers when they want to bootstrap the block chains in a bulk fashion.

# IPV6 addressing
The system is build completely support both IPV4 and IPV6.

# Distributed agreement minimization
Existing cryptocurrency systems are largely known for their proof of work schemes which are used to come to a fair distributed agreement about ledger changes.  Our system was designed to eliminate the need for distributed agreements in almost all circumstances.  Each account maintains its own block chain which is replicated to all peers in the network.  Only the account owner is able to sign transactions to modify their own chain and as such, no agreements are necessary.

# Permanent storage minimization
A lot of work was put in to eliminating redundant data in the block chain in order to minimizing the long-term storage footprint of the ledger.
* Blocks in the ledger store balance values rather than balance deltas which allows much more aggressive pruning in lite clients.
* Balances are only stored when necessary e.g. send blocks and inferred when possible e.g. receive blocks.
* Blocks are fixed size to minimize framing overhead and storing counts.

# Proof of stake agreements
It's possible for the network to see a block chain fork in the case of someone crafting a malicious ledger client or possibly a client that hasn't been tested well enough.  Unlike existing cryptocurrency systems, forks are an almost non-existent event and are designed to only affect one account instead of the entire ledger.  We use a simple proof of stake weighted by account balance for peers in the network to come to consensus about which fork to choose.

# Proof of stake representatives
Many peers will not want to stay connected to the network in order to participate in proof of stake agreements if the need arises.  We also don't want to require a signature and network message from every account for every conflict.  Each account is able to select another account as its representative which is able to vote with the balance owned by the account and change the representative when desired.  In this way many small accounts can be consolidated to a single large proof of stake vote by a peer that is willing to stay well connected to the network.

# Divisibility
There are three important aspects of divisibility of the coin supply.
* The supply needs to be able to be divided up amongst a large number of users with users possibly wanting several accounts.
* Each account needs to be able to represent an adequate dynamic range of value
* The supply should be able to deal with deflation over time as accounts are abandoned

The supply starts with 2^128 coins which satisfies the three supply requirements.

# Lite peers and pruning
Since each account operates on its own block chain, lite peers are able to do much more selective and aggressive pruning of the block chains.  Only bootstrap or peers interested in doing full ledger validation actually need to store the full ledger history.
* For each account only the frontier block needs to be kept in order to validate a subsequent block via hash chaining.
* Since send blocks contain an account's balance, in order to calculate the balance from the block chain, only blocks up to the last send need to be kept.
* Chains for inactive or small balance accounts can be dropped and left for full-validating peers to track.

# Naming
RaiBlocks is pronounced like "ray blocks" and is named after [Rai Stones](https://en.wikipedia.org/wiki/Rai_stones) from Yap.  I always was facinated by the use of Rai Stones as currency and appreciate the irony of naming a practical cryptocurrency after a wildly impractical currency.