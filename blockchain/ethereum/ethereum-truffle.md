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

    testrc
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