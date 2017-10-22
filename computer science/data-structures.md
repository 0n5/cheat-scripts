Data Structures
====


#### Queue 

* first in first out (FIFO)
* removes from the head and inserts at the tail
* insertions and removals can occur concurrently

    3, 4, 5, 6 10
    # 3 would be dequeued next, then 4, then
    # new element would be inserted after 10


#### Stack

* first in last out (FILO)
* elements are push to the top of stack
* elements are popped off the top of the stack

```
    3
    5
    7
    9
    11
    
    Pushing (inserting) 13 above 3
    Popping (removing) 13 from the top
```