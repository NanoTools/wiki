The goal of the key derivation function is to ensure work has been applied to a low-entropy source e.g. a password. We want to provide proof of both computation and more-so a proof of memory capacity since memory scales in a less parallel fashion than computing power.

The function builds an array of 'n' 64bit numbers and uses an extremely fast pseudo random number generator seeded with a hash of the password and salt as a data source for fill numbers.  We iteratively assign array elements according to the formula:  
  
`  from (i = 0 to n)
  data [rand (i - 1) mod n] = rand (i)`
  
Using this algorithm we fill entries in the array in a random walk determined by the seeded random number generator.  The final step is to take a SHA3 hash of the entire array contents and use the output as the derived key.

In order to attack this function, an attacker would have to devise a series [s(0), s(n)) which they could feed in to the SHA3 hash function which would give the exact same output as the series [data(0), data(n)) but with fewer computing and memory resources.

Our conjecture is that an attacker cannot generate a series 's' that can be computed faster than building an array-backed lookup table.  Furthermore our conjecture is that an attacker cannot trade off memory usage for computation in a sub-exponential fashion.