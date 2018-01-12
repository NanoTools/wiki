The wallet is a database of the 256-bit key -> 256-bit value pairs. The primary wallet is stored inside of the node's database and backup copies are written to a directory "backup".  
  
## Special Pairs:  
0 -> Version number  
1 -> Encrypted wallet key  
2 -> Wallet salt  
3 -> Check key  
4 -> Wallet representative
  
## Wallet accounts  
pub(i) -> encrypt_aes_ctr (wallet_key, prv(i), salt)
  
## Details:  
Wallet Key: A 256 random number that's to encrypt all key entries in the database.  
Salt: A random 256-bit value used generate uniqueness in wallets with identical passwords  
Encrypt_AES_CTR: A function using the AES encryption algorithm in CTR mode  

The wallet key is encrypted bypassing the password through the Argon2 key derivation function.

All pairs besides the special pairs and key/value pairs mapping the public key a.k.a. account number, to the encrypted private key.