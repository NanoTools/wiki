The wallet is a database of 256bit key -> 256bit value pairs.  The primary wallet is stored inside the node's database and backup copies are written to a directory "backup".  
  
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
Salt: A random 256 bit value used generate uniqueness in wallets with identical passwords  
Encrypt_AES_CTR: A function using the AES encryption algorithm in CTR mode  

The wallet key is encrypted by the result of the [[Key derivation function]] applied to the wallet password.

All pairs besides the special pairs and key/value pairs mapping the public key a.k.a. account number, to the encrypted private key.