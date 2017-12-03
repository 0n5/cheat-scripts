Ethereum Truffle Framework
=======

* Framework to write tests and smart contracts


Installation

    npm install -g truffle@3.4.11

Usage

    mkdir -p ~/contract/GreetingsTruffle
    cd ~/contract/GreetingsTruffle
    truffle init

Directory structure

    contracts/
    # all solidity contracts live here
    # sample contract is created here, but is not compatible with any real tokens
    # safely delete the ConvertLib.sol and MetaCoin.sol
    # Migrations.sol is used to track with versions of the contracts have been deployed

    migrations/
    # contains files that hold logic used during deployment process

    tests/
    # tests scripts used to test contracts before deploying main network
    # can use JS (Chai/Mocha) or Solidity for testing
    # safely delete metacoin.js and TestMetacoin.sol

    truffle.js
    # file that configures the environment


Create new Contract

    cd ~/contract/GreetingsTruffle
    nano Greetings.sol

``` js

pragma solidity ^0.4.11;


contract Greetings {
    // defines the contract name
    
    string message;

    function Greetings() {
    // constructor, has the same name as contract
    // called only once when the contract is deployed to blockchain
    // returns no value

        message = "ready";
        // initialize with actual message
    }

    function setGreetings(string _message) public {
        // set greeting function
        // takes message string as parameter
        // public function, can be called by any other contract
        message = _message;
    }

    function getGreetings() constant returns (string) {
        // get greeting function
        // returns the message
        // must be a constant
        return message;
    }
}
```

    cd ~/contract/GreetingsTruffle/migrations
    nano 2_deploy_contracts.js

``` js

var Greetings = artifacts.require("./Greetings.sol");

module.exports = function(deployer) {
  deployer.deploy(Greetings);
};

```

Start Test RPC network

    testrpc
    cd ~/contract/GreetingsTruffle

Truffle Migrations

    truffle migrate
    # deploys contracts and runs migrations
    # in the testrpc tab you can see 4 transactions were executed
    # 1st transaction deploys the migration contract
    # 2nd transaction updated the migration state
    # 3rd transaction deployed the greetings contract
    # 4th transaction updates the migration state 
    # if you run truffle migrate again it will show that the network is up to date

    truffle migrate --reset
    # ignores the value of the last completed migration and runs all migrations again

Truffle Console

    truffle console

In Console

    Greetings.address    # prints out contract address
    web3.eth.accounts    # prints out all the account addresses

    Greetings.deployed().then(function(instance) {app = instance;})
    # Using a promise deploys the contract and creates an app instance
    # will return undefined

    app   # will print out the app instance code
    
    app.getGreetings.call()  
    # runs the getGreetings function, 
    # does not change the state of the blockchain
    # no transaction required

    app.setGreetings("changing the message", {from: web3.eth.accounts[0]})
    # changes the state of the blockchain and the message stored
    # requires an account address to execute the transaction
    # if you run app.getGreetings.call() you should see new message


#### TestRPC and Geth

    testrpc   # starts up TestRPC network
    geth attach http://localhost:8545   # connect geth to TestRPC network
    truffle migrate # compiles and deploys migrations to network
    
In the Geth Console:

    eth.getTransaction([TRANSACTION_ID])
    # prints out the transaction details including the hash, the gas price etc
    # `blackHash` is the hash of the block contract is on
    # `from` is the sender who deployed the contract
    # `gas` is what was provided by the sender (maximum amount, defualt value usually)
    # `gasPrice` is the price provided by the sender reflected in Wei per 1 unit of gas
    # `input` is the bytecode that was deployed
    # `nonce` increases by 1 for every transaction a given sender sends to the network
    # this nonce creates a unique address for the contract (not the same as the block nonce)
    # `to` if recipient of the contract is the blockchain will always be "0x0"
    # `transactionIndex` will always be 0 on the testRPC network
    # `value` expressed in Wei sent along with the transaction

    eth.getBlock([BLOCK_HASH])
    # prints out the details of the block
    # `difficulty` is the difficulty integer used to validate the block (always 0 on TestRPC)
    # `gasLimit` is the maximum gas allowed for this block
    # `gasUsed` is the gas used by all transactions on the block
    # `logsBloom` holds data regarding the events
    # `miner` is the address of the account that mined the block (0 on TestRPC)
    # `nonce` is the nonce of the block itself, using for mining algorithm
    # `number` is the number of the block in the blockchain
    # `transactionRoot`, `receiptRoot` and `stateRoot` represent 3 tree roots of Merkle Tree
    # `totalDifficulty` is the difficulty of the whole chain up until this block (0 on TestRPC)
    # `size` is the size of the block in bytes
    # `timeStamp` is the time the block was built in seconds since unix epoch
    # `transactions` array of transactions



#### Gas Transactions

[https://etherconverter.online/](https://etherconverter.online/)

* unit of complexity that is used to set the price of code execution inside the EVM
* gas is paid by the accounts completing the operation
* the account must have enough ether in their account to pay for the operations
* primary node is the first account in the 
* gas usage limits protect you from wasting all ether on poorly written code
* fees will go to the miner of the block containing the transaction
* miners will be interested in transactions with higher gas prices (more payout)
* unspent gas from provisioned limits will be returned
* if the code cannot execute because it runs out of gas, an error is thrown and gas is lost
* constant functions cost no ether (no computation needed, no state change)
<!-- -->

    testrpc   # starts up TestRPC network
    geth attach http://localhost:8545   # connect geth to TestRPC network
    truffle migrate # compiles and deploys migrations to network
    
In the Geth Console:

    eth.accounts  # prints out accounts
    
    web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
    # prints out the balance for first account

    eth.coinbase  # prints address of the primary node