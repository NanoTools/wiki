# Mnemonic Seed
Nano's private key(s) from mnemonic derivation follows the BIP[39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)/[44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki) standard. Only hardened paths are defined. Nano's [coin-type](https://github.com/satoshilabs/slips/blob/master/slip-0044.md) is 165' (0x800000a5)

`44'/165'/0'` derives the first private key, `44'/165'/1'` derives the second private key, and so on.


# Test Vectors
Given 24-Word Mnemonic:
```
edge defense waste choose enrich upon flee junk siren film clown finish luggage leader kid quick brick print evidence swap drill paddle truly occur
```
Given Passphrase:
```
some password
```
Derived BIP39 Seed:
```
0dc285fde768f7ff29b66ce7252d56ed92fe003b605907f7a4f683c3dc8586d34a914d3c71fc099bb38ee4a59e5b081a3497b7a323e90cc68f67b5837690310c
```
Derived Private Key for `44'/165'/0'`:
```
3be4fc2ef3f3b7374e6fc4fb6e7bb153f8a2998b3b3dab50853eabe128024143
```
Derived Public key:
```
5b65b0e8173ee0802c2c3e6c9080d1a16b06de1176c938a924f58670904e82c4
```
Derived Address:
```
xrb_1pu7p5n3ghq1i1p4rhmek41f5add1uh34xpb94nkbxe8g4a6x1p69emk8y1d
```