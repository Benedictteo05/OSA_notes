### Deadlocks
- A deadlock is a situation where in a group of two or more processes/threads, each process holds at least one resource while making a request on another, and all requests cannot be satisfied because the requested resources is held by another process that is being blocked, waiting for another resource.

### When can deadlocks occur
- Deadlocks can occur in multiprogramming computer systems, which shares resources. 
- Deadlocks can also occur between threads in the same process.
- Resource manager (such as memory manager) can be involved in a deadlock with an application process.

### Four conditions for deadlocks
- A computer system needs to have 4 condition in order for deadlocks to be possible.
- Unfortunately, these 4 conditions occur in almost all resources allocation strategies used in modern OS.
- Although these 4 conditions are necessary for deadlocks to occur, their presence is not sufficient to say that a deadlock exists.

### Four Conditions
- Mutual exclusion (exclusive use)