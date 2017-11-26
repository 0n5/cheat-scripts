Blockchain Basics
=====

* solves the Byzantine General's Problem, an agreement problem between a group of generals commanding a portion of army surrounding a city
* blockchain is more or less a design pattern

* genesis block is the first block (block 0) of a block chain and is hardcoded into the software
* process of creating genesis block and propagating to the network is called instantiation
* chain of blocks residing on the genesis block are called an instance

* a fork would occur when a single genesis block would diverge after certain block was added
* fork can be voluntary or because of a bug that needs to be fixed. 
* after a fork the currency can only be used in their respective implementations and both would lose value

* wallets are akin to user accounts and have an address than can be used as an ID
* wallet addresses can accept crytpocurrency

* miners either have a special wallet or enable mining function in their software
* to maximize hash rate you must have a highly optmized client that uses your hardware efficiently
* the higher the hash rate, the higher the probability of winning consensus competition rounds (proof of work)
* mining pools combine computing power of groups of computers to save resources
* most secure way to join network is to install wallet client on your machine and wait (days in some cases) to sync full db
* when downloading the full copy of the ledger (db) you can trace all transactions back to the genesis block
* less secure way is to create account on a website that manages remote node and makes transactions on your behalf
* coinbase, kraken and poloniex are examples of 3rd party sites that manage transactions

* to change a transaction in history you would need to recompute the block and all subsequent blocks in the ledger
* an attacker would need to be faster than 51% of the entire network to create a fraudulent transaction

* proof of stake algorithms are being researched to replace inefficnent proof of work (mining) algorithms
* users can have pseudonimity by hiding behind wallet addresses
* transactions per second are very limited, approx 7 to 20, credit cards can process 20,000 to 40,000

#### Consensus Algorithm

* user nodes do not need to utilize the consensus algorithm, can be disabled in the client software
* proof of work is current standard
* contribute power in the form computing capacity measured as hash rate
* mitigates race conditions of several nodes completing work and propagating across the network
* becoming slower an slower as the networks grow requiring more energy and computing power


#### Cryptocurrency Properties

Durability

* guaranteed by the traceability of its transactions and the distribution of its ledger
* only way to destroy it is to lose the key associated with the wallet address rendering it inaccessible

Portability

* can easily be transfered between wallets

Accessibility

* trust in all of the five properties of the cryptocurrency
* ability to spend the currency earned in transactions or convert them to fiat currency (via exchange)

Limited

* how the currency is created is known and controlled
* minting is controlled by the consensus algorithm when a miner appends block to the ledger

Uniformity

* 1 unit of currency is equivalent to any other unit of currency


#### Smart Contract Language

* code that is attacthed to each transaction
* Turing complete smart contracts can introduce infinite loops and bring network down


#### ZKSnarks

[https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)

* form of zero knowledge cryptography
* can prove that a transaction occured without having to reveal the content / payment history ledger
* implemented in Zcash [https://z.cash/](https://z.cash/)

#### Bitcoin

Bitcoin implementation source: [https://github.com/bitcoin/bitcoin](https://github.com/bitcoin/bitcoin)
Bitcoin White paper: [https://bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf)
Bitcoin wallets: [https://bitcoin.org/en/choose-your-wallet](https://bitcoin.org/en/choose-your-wallet)

* currency is BTC
* smallest unit of currency is 1 Satoshi (10 to the -8 BTC)
* uses proof of work algorithm
* transactions are grouped into blocks and appended to the ledger
* when a cryptographic problem is solved, the node is able to send themselves an amount of bitcoin
* amount of bitcoin sent how they are added to ledger is determined by the `consensus algorithm`
* Currently 12.5 bitcoins per block that will be divided by 2 every four years
* processes transactions every 10 minutes so new blocks can propagate across the internet
* transactions considered finalized after 6 blocks (1 hour)
* blocks are limited to 1MB, limits network speed to 7 transactions per second
* total blockchain size is approx 112GB with growth rate of 4GB per month

* purposely limits added smart contract code and prevents looping


#### Ethereum

Ethereum repo: [https://github.com/ethereum](https://github.com/ethereum)
Ethereum White paper [https://github.com/ethereum/wiki/wiki/White-Paper](https://github.com/ethereum/wiki/wiki/White-Paper)

* currency is ETH
* smallest currency is 1 Way (10 to the -18 ETH)
* uses proof of work algorithm
* processes transactions every 17 seconds due to a different implementation of the consensus algorithm
* current block value is worth 5 ETH
* every node will invoke a smart contract and execute the code
* transactions considered finalized after 12 blocks (3.5 minutes)
* blocks are limited to 4 million gas, limiting the network to 20 transactions per second
* total blockchain size is approx 40GB with growth rate of 2GB per month

* code runs in the EVM (Ethereum Virtual Machine)
* code that runs in the transaction is called EVM bytecode (similar to Assembly)
* smart contract code is Turing complete and can perform any type of computing logic (can do loops and jumps)
* to prevent DOS attacks each transaction will have a limit in the amount of `gas` used
* every instruction executed requires a payment in gas
* transaction sender pays for the execution
* current standard smart contract language is `Solidity` which is compiled down to EVM bytecode


#### Ethereum Classic

[https://ethereumclassic.github.io/](https://ethereumclassic.github.io/)

* currency is ETC
* in 2016 an attacker exploited a bug which caused a fork
* Ethereum decided to fix the bug, Ethereum classic kept the protocol pure (immutable) and created the fork

#### Hyperledger Fabric

Source: [https://github.com/hyperledger/fabric](https://github.com/hyperledger/fabric)

* permissioned blockchain implementation
* not a true decentralized network
* provides a membership identity service that manages user ID's across the network
* peers do not mine or share blocks