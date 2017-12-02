Ethereum Smart Contracts
=========


#### Smart Contracts

* Code and data that is stored on the blockchain and executed by the EVM
* Solidity (similar to JS) and Viper (similar to Python) are langauges that can be used to create smart contracts
* can be thought of as a microservice, has its own state and an API to modify that state

DApp Browser

* HTML CSS and JS frontend combined with the Web3 JS library

Web3 JS

[https://github.com/ethereum/web3.js/](https://github.com/ethereum/web3.js/)

* wrapper around RPC endpoints exposed by Ethereum nodes
* performs all RPC calls to interact with nodes

Backend

* runs the smart contract code and only reachable thru its address and via web3 library
* state of the smart contracts are modified by its functions which are included in the transactions
* functions of the smart contracts are executed by the EVM of every node on the network
* when the state of the smart contract changes, this change propagates to all nodes on the network

#### Creating Smart Contract

Dependencies

    npm init
    npm install web3@0.20.0 
    npm install solc  # solidity compiler

Application

    mkdir -p ~/contract/greetings && cd ~/contract/greetings
    touch greetings.sol 

add to the file:

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

#### Deploying the Contract

* use the test RPC network (recommended)
* each transaction is automatically mined
* ten accounts are created, with 100 ether
* in memory Ethereum node, contract must be re-deployed when restarted

Launch Test RPC node

    testrpc   # launches node on localhost:8545
    cd ~/contract/greetings
    node      # drop into node.js shell

in Node Shell

    Web3 = require('web3')
    web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"))
    web3.eth.accounts  # test that web3 objects were created
    
    solc = require('solc')
    sourceCode = fs.readFileSync('Greetings.sol').toString()  
    # reads contract file into a string

    compiledCode = solc.compile(sourceCode)  # compile the contract code into a JSON object with alot of fields