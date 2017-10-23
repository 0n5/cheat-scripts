Distributed Systems
======

A collection of entities, each of which is autonomous, 
programmable, asynchronous and failure prone, and which 
communicates thru an unreliable medium. 

* Cloud is a fancy term for distributed systems
* Also known as P2P systems, grids, clusters and timeshares

#### Leader Election

* elect one leader only among non-faulty processes
* all non-faulty processes agree who the leader is

Ring Leader Election

* N processes organized in a logical ring
* Similar to ring in Chord p2p system
* All messages sent clockwise around ring from earlier process to successor
* if process p<sub>i</sub> discovers old leader has failed it initiates an election

1. The p<sub>i</sub> compares the attr in the message with its own attr
2. If the attr is greater, p<sub>i</sub> forwards the message
3. If smaller, and p<sub>i</sub> has not forwarded an election message it overwrites message with its on id:attr and fowards it
4. If the arrived id:attr matches that p<sub>i</sub>'s then it is the greatest
5. This process will then send the "elected" message to its neighbour
6. When p<sub>i</sub> recieved an elected message it sets its elected<sub>i</sub> variable to the id of the message
7. p<sub>i</sub> then forwards this message until it reaches the new elected cooridinator/leader

