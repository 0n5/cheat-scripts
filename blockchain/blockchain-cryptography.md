Blockchain Cryptography
=====

#### Hashing function

* takes in an arbitrary input of data and produces a number as output
* output will always have the same size as the input
* the same input will always give the same output
* should be impossible (or close to) to determine the input from only the output

* typical usage in crypto is to ensure that data has not been tampered with by comparing hashes
* hash collisions are possible, where two different inputs can have the same output
* SHA1 has been broken by Google Researches and proven weak: [http://shattered.io/](http://shattered.io/)

* most common blockchain use of hash functions is to chain blocks together
* header of block N contains the hash of block N-1
* anything that changes in block N-1 will also change the block's hash and will also effect the hash of block N
* each block contains an arbitrary nonce
* valid blocks must have a hash below or equal to the difficulty target
* Bitcoin uses SHA-256
