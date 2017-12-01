Blockchain Cryptography
=====

Hashing Functions: [https://emn178.github.io/online-tools/](https://emn178.github.io/online-tools/)
Blockchain Demo: [https://anders.com/blockchain/](https://anders.com/blockchain/)

#### Hashing function

Basics

* takes in an arbitrary input of data and produces a number as output
* output will always have the same size as the input
* the same input will always give the same output
* should be impossible (or close to) to determine the input from only the output

General Usage

* typical usage in crypto is to ensure that data has not been tampered with by comparing hashes
* hash collisions are possible, where two different inputs can have the same output
* SHA1 has been broken by Google Researches and proven weak: [http://shattered.io/](http://shattered.io/)

Usage in Blockchain

* most common blockchain use of hash functions is to chain blocks together
* header of block N contains the hash of block N-1
* anything that changes in block N-1 will also change the block's hash and will also effect the hash of block N
* each block contains an arbitrary nonce and difficulty target
* valid blocks must have a hash below or equal to the difficulty target
* Bitcoin uses SHA-256
* Ethereum uses Keccak-256 or Keccak-512


#### Asymmetric Cryptography

* generally used in authentication and data confidentially

Usage

* public key encryption takes a key and some input and produces an obfuscated output
* only way to decrypt is to use a public key generated from the private key used to encrypt
* cannot recover the private key based on the public key (one way function)

Blockchain usage

* use Eliptic Curve Cryptography (ECDSA) instead of RSA
* Eliptic Curve allows for higher levels of security with smaller keys 
* ECDSA extracts public key (PK) from message and signature and compares the recovered PK to the one it takes as input
* used by users to sign transactions and certifies that they are authorized to create the transaction
* in Bitcoin the wallet address is a hash of the users public key
* if the private key is compromised the wallet and all crypto can be stolen

Wallets

* when using Coinbase the private key is stored in a database (dangerous)
* when using a software wallet, you must make sure the computer running the software is never compromised
* most secure storage is with hardware wallet or printing the private key on paper and storing in safe deposit box1


#### Merkle Tree (Hash Tree)

* used exstensively in P2P applications such as BitTorrent, GitHub and cryptocurrencies

Blockchain usage

* run hashes recursively on pairs of transactions to derive root hash instead of running hash on whole block
* if one transaction is changed the root hash will no longer be the same
* only root hash is stored on the blockchain
* intermediary hashes are stored in the application cache of the client software when necessary

Ethereum

* 3 different Merkle Tree roots: transactions, state and transactions receipts
* uses special kind of Merkle Tree, the Patricia Tree
