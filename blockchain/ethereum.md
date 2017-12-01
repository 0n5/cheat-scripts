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

    npm install -g ethereumjs-testrpc


#### Truffle

Framework to write tests and smart contracts

    npm install -g truffle@3.4.11



#### Private Network Installation

1. Create directories

    mkdr -p [TOP_LEVEL_FOLDER]/private

2. Choose network identifier (cannot be 1,2 or 3)

3. Create Genesis Block

    nano [TOP_LEVEL_FOLDER]/private/genesis.json

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

4. Initialize Private Network

    geth --datadir ~/[TOP_LEVEL_FOLDER]/private init genesis.json

* creates `geth` (chain data) and `keystore` (accounts) directories

5. Create Accounts

    geth --datadir ~/[TOP_LEVEL_FOLDER]/private account new

* will create a wallet address (hash of the public key) in the `keystore` directory

    geth --datadir ~/[TOP_LEVEL_FOLDER]/private account list   # lists the accounts and sequence
    

#### Mining

1. Create startup script

    cd ~/[TOP_LEVEL_FOLDER]/private
    nano startnode.sh

```
    geth --networkid 4224 --mine --datadir "~/ether/private" --nodiscover 
    --rpc --rpcport "8545" --port "30303" --rpccorsdomain "*"
    --nat "*" --rpcapi eth,web3,personal,net --unlock 0 
    --password ~/[TOP_LEVEL_FOLDER]/private/password.sec
    --ipcpath "~/Library/Ethereum/geth.ipc"
```

* `--mine` specifies that this node should start mining as soon as it is launched
* `--nodiscover` tells the node not to start searching for peers
* `--port` is used by nodes to connect to one other (p2p)
* `--rpccorsdomain "*"` allows any node to connect to RPC endpoint
* `--nat "*"` allows any nat port to be used
* `--rpcapi eth,web3,personal,net` api's enabled in the RPC endpoint
* `--unlock 0` unlocks the first account
* `--password` specifies password file to use to unlock first account
* `--ipcpath "~/Library/Ethereum/geth.ipc"` only for Mac, flag used by Mist, to tell if there is already a node running

2. Make script executable

    chmod a+x startnode.sh