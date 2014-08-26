# Signing algorithm - ED25519
ED25519 is an elliptic curve algorithm developed in an academic setting with a focus on security from side channel attack, performance, and fixing a lot of the little annoyances in most elliptic curve systems.  The main site is here http://ed25519.cr.yp.to/

# Hashing algorithm - SHA3
Compared to existing cryptocurrencies, the hash algorithm chosen is much less important since it's not being used in a proof of work context.  In our implementation hashing is used purely as a digest algorithm against block contents.

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