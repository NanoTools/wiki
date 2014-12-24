The goal of the key derivation function is to ensure work has been applied to a low-entropy source e.g. a password. We want to provide proof of both computation and more-so a proof of memory capacity since memory scales in a less parallel fashion than computing power.

The KDF operates in three phases:

## Phase 1)  
Using the hash of the password mixed with a salt value, the memory buffer is filled with values populated by a random number generator to serve as a consistent initialization point.

## Phase 2)  
We write random values to random places in the memory buffer to break the n = f(n - 1) dependency of the buffer.  Since values in the memory buffer depend on previous values, an attacker could trade off memory for computation by storing a subset of the buffer and computing subsequent values.  Randomly overwriting values in the buffer breaks this tradeoff.

## Phase 3)  
We hash the memory buffer in a random order to prevent an attacker from incrementally computing the result.  An attacker could dedicate a 1/N subset of the memory buffer and only store portions of phase 1 and 2 that fall in to this subset.  An attacker could then trade off memory by recomputing phase 1 and 2 N times to save memory.  Randomly hashing the memory buffer prevents this attack.

The wallet kdf is tuned to use a 64mb derivation table and the block work function is tuned to use a 64k derivation table.