NodeJs scripts
===

#### Command Line arguments

* available in the process.argv array
* first two elements of the array are node & the name of program
* access the arguments by calling `process.argv[2]`

``` javascript

'use strict';
const MongoClient = require('mongodb');

function usage() {  
    console.log('Usage:');  
    console.log('node', __filename, '< option >');  
    console.log('Where option is one of:');  
    console.log('1');  
    console.log('2');  
    console.log('3');  
    console.log('4');
}
if (process.argv.length < 3) {  
    console.log(" Incorrect number of arguments");  
    usage();
} else {  
    if (process.argv[2] === '1') {    
        someFunctionA();  
    } else if (process.argv[2] === '2') {    
        someFunctionB();  
    } else if (process.argv[2] === '3') {    
        someFunctionC();  
    } else if (process.argv[2] === '4') {    
        someFunctionD();  
    } else {    
        console.log(" Invalid option:", process.argv[2]);    
        usage();  
    }
}

function sopmeFunctionA() {
    console.log('Ran function A')
}
function sopmeFunctionB() {
    console.log('Ran function B')
}
function sopmeFunctionC() {
    console.log('Ran function C')
}
function sopmeFunctionD() {
    console.log('Ran function D')
}

```