The wallet is a LevelDB database of 256bit key -> 256bit value pairs.  
  
## Special Pairs:  
0 -> encrypt_aes_ctr (key_derivation_function (hash (password), salt), wallet_key)  
1 -> encrypt_aes_ctr (wallet_key, 0)  
2 -> salt  
  
pub(i) -> encrypt_aes_ctr (wallet_key, prv(i))
  
Wallet Key: A 256 random number that's to encrypt all key entries in the database.  
Salt: A random 256 bit value used generate uniqueness in wallets with identical passwords  
Encrypt_AES_CTR: A function using the AES encryption algorithm in CTR mode  
Key_Derivation_Function: A slowing function applied to the hash of the password used to slow down brute force cracking.  
  
All pairs besides the special pairs and key/value pairs mapping the public key a.k.a. account number, to the encrypted private key.