Nano has one blockchain for each account which is controlled by the account's private key, and each blockchain is replicated to all peers in the network. We call this arrangement a **block lattice**.

Balances are transferred between blockchains through **send** and **receive** blocks.  **Send** blocks reduce the balance of an account and marks the delta as receivable by an account number.  At a later time, the receiving account creates a **receive** block, which increases the balance of their account by the delta.

Distributed agreements like Proof-of-Work or Proof-of-Stake are unnecessary, since the account owner has authoritative control over transactions.

![Transaction animation](https://raw.githubusercontent.com/clemahieu/raiblocks/master/images/transaction.gif)

See also: [[Double spending and confirmation]] for handling of misbehaved clients.