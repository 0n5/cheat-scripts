Multicast Protocols
==========

* Gossip tries to solve the multicast problem

### Multicast Problem

* Multicast messages are addressed to group of computers simultaneously
* Broadcast messages are sent to all nodes, multicast is more restrictive, must be a member of a group
* a group of nodes / processes on the internet that need talk to each other by sending / receiving messages
* a single node wants to share information with all members of a group of nodes
* there may be many multicast messages from many different senders going around the group

### Multicast Protocol

* fault tolerance and scalability are the most important aspects in regards to cloud computing 
* protocol sits at the application level, does not deal with the underlying network

Centralized

* simplest method of multicasting
* sender has a list of recipients and sends each of them a UDP or TCP packet via a loop.
* if transmission fails half way thru the loop, the rest of the nodes will not receive the message. 
* Overhead on the sender is very high, especially when there are many nodes. 
* Latency also increases the higher the number of nodes
* O(N) Linear scaling latency for messages to reach each node


Tree Based

* Spanning tree is developed among the nodes / processes
* Typically prefer IP multicast where available
* Includes network level protocols, spanning tree is amongst the switches and routers
* Also includes application level protocols SRM, RMTP, TRAM, TMTP
* O(log(N)) latency for each message to reach each node.
* Overhead on the sender is constant, especially if the number of children is constant
* If a node closer to the root fails, many descendents will not recieve message before tree is repaired
* Tree maintenance will be fairly continous to repair or replace broken nodes
* ACKs or NAKs (negative acknowledgements) are used to repair multicasts that are not received. 
* Big issue with tree multicast protocols is that there can be ACK and NAK storms

SRM (Tree based)

* Scalable Reliable Multicast
* Uses NAKs
* Adds random delays and exponential backoffs to avoid NAK storms
* Recievers dont immediately send a NAK when they realize they have missed a message
* Number of ACKs / NAKs grows linerally with size of group and is O(N)
* Not scalable

RMTP (Tree based)

* Reliable Multicast Transport Protocol
* Uses ACKs
* Receivers periodically send a digest or collection of ACKs for all multicasts received
* If there are missing messages in the digest, these messages are sent down towards receivers
* To avoid ACK storms, certain nodes are marked designated recievers, only they recieve the ACKs 
* Number of ACKs / NAKs grows linerally with size of group and is O(N)
* Not scalable

