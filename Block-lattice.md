Raiblocks has one block chain for each account which is controlled by the account's private key and each block chain is replicated to all peers in the network, we call this arrangement a block lattice.

Balances are transferred between block chains through send and receive blocks.  Send blocks reduce the balance of an account and marks the delta as receivable by an account number.  At a later time the receiving account creates a receive block which increases the balance of their account by the delta.

Distributed agreements like proof of work or proof of stake are unnecessary since the account owner has authoritative control over transactions.

See also [[Double spending and confirmation]] for handling of misbehaved clients.