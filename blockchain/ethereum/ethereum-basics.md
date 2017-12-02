Ethereum
====


#### Geth (Go Ethereum Platform)

Requires Node, Xcode and Homebrew

Install

     brew tap ethereum/ethereum    # adds source
     brew install ethereum

Upgrade

    brew upgrade ethereum


#### Test RPC

* Simulator to run tests
* Recommended to run tests on full Ethereum node before deploying to public

Install:

    npm install -g ethereumjs-testrpc


#### Truffle

Framework to write tests and smart contracts

    npm install -g truffle@3.4.11



#### Private Network Installation

Create directories

    mkdr -p [TOP_LEVEL_FOLDER]/private

Choose network identifier (cannot be 1,2 or 3)

Create Genesis Block

    nano [TOP_LEVEL_FOLDER]/private/genesis.json

Add to the file:

``` js

{

 "nonce": "0x0000000000000042",
 "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
 "difficulty": "0x400",
 "alloc": {},
 "coinbase": "0x0000000000000000000000000000000000000000",
 "timestamp": "0x0",
 "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
 "extraData": "0x",
 "gasLimit": "0xffffffff",
 "config": {
    "chainId": 4224,
    "homesteadBlock": 0,
    "eip155Block": 0,
    "eip158Block": 0
 }
}

```

* `nonce` and `mixhash` are used by the consensus algorithm to ensure the minimum computation has been performed to validate block
* `difficulty` defines the difficulty / number of times it will take miner to solve consensus
* in development you should use a small number to reduce computation needed
* `alloc` is used to pre allocate funds to some wallet addresses
* `coinbase` address of the miner / wallet that coins will be sent after successful mining
* `timestamp` is used by the EVM to adjust difficulty that must be applied, the goal is to keep a fairly constant time between two blocks
* `parentHash` is the hash value of the parent block (zero in the genesis only)
* `gasLimit` is the maximum amount of gas that can be spent per block, limits processing requirements and size of each block

Initialize Private Network



    geth --datadir ~/[TOP_LEVEL_FOLDER]/private init genesis.json

* creates `geth` (chain data) and `keystore` (accounts) directories

Create Accounts

    geth --datadir ~/[TOP_LEVEL_FOLDER]/private account new

* will create a wallet address (hash of the public key) in the `keystore` directory
<!-- -->

    geth --datadir ~/[TOP_LEVEL_FOLDER]/private account list   # lists the accounts and sequence
    

#### Mining

Create startup script

    cd ~/[TOP_LEVEL_FOLDER]/private
    nano startnode.sh

```
    geth --networkid 4224 --mine --datadir "~/[TOP_LEVEL_FOLDER]/private" --nodiscover 
    --rpc --rpcport "8545" --port "30303" --rpccorsdomain "*"
    --nat "*" --rpcapi eth,web3,personal,net --unlock 0 
    --password ~/[TOP_LEVEL_FOLDER]/private/password.sec
```

* `--mine` specifies that this node should start mining as soon as it is launched
* `--nodiscover` tells the node not to start searching for peers
* `--port` is used by nodes to connect to one other (p2p)
* `--rpccorsdomain "*"` allows any node to connect to RPC endpoint
* `--nat "*"` allows any nat port to be used
* `--rpcapi eth,web3,personal,net` api's enabled in the RPC endpoint
* `--unlock 0` unlocks the first account
* `--password` specifies password file to use to unlock first account
by Mist, to tell if there is already a node running

Make script executable

    chmod a+x startnode.sh


#### Miner Console

    geth attach ipc:~[TOP_LEVEL_FOLDER]/private/geth.ipc

Console Commands

    eth.accounts   # lists all wallet addresses
    eth.coinbase   # displays current account that is mining
    
    eth.getBalance(eth.coinbase)  # dispalys this wallets balance of ETH currency expressed in Wei

    web3.fromWei(eth.getBalance(eth.coinbase), "ether")  # converts wei to ether

    miner.stop()   # node will stop mining
    miner.start()  # node will start mining
    miner.start(2) # node will mine with two threads

    net.version    # prints out the network ID

    personal.unlockAccount(eth.accounts[1], "[PASSWORD]", 300)  
    # unlocks an address / account for 300 seconds

    personal.unlockAccount(eth.accounts[1])  
    # unlocks account for default 10 minutes, will prompt for pwd

    eth.sendTransaction({from: eth.coinbase, to: eth.accounts[1], value: web3.toWei(100, "ether")})
    # transfers from current coinbase address to specified account
    # value must be defined in Wei
    # both accounts must be unlocked to send / recieve 
    # transactions will not be applied if mining has been stopped

    exit   # detaches console


#### Mist

[https://github.com/ethereum/mist](https://github.com/ethereum/mist)

* decentralized browser for DAPPS
* only secure DAPP is the Meteor DAPP Wallet
* wallet management UI for Ethereum
* geth and mist share the same keyfile directory

Launch Mist with custom IPC path:
    
    /Applications/Mist.app/Contents/MacOS/Mist --rpc /[TOP_LEVEL_FOLDER]/private/geth.ipc


#### MetaMask

[https://metamask.io/](https://metamask.io/)

* chrome extension that turns browser into DAPP compatible platform
* does not require a local Ethereum node, uses MetaMask server nodes
* connect to any test networks, main network or local and remote nodes