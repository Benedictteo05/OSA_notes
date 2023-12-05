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
	- Once a process has been allocated a particular resource, the threads in the process have exclusive use of the resource. No other processes can use a resource while it is allocated to a process.
- Hold and wait 
	- A process may hold a resource at the same time it requests another one.
- Circular wait 
	- A situation can rise in which process p1 holds resource R1 while one of its threads requests resource R2, and process p2 holds R2 while one of its threads requests resource R1. There may be more than 2 processes involved in the circular wait.
- No preemption
	- Resources can be released only by the explicit action in a process, rather than by the action of an external authority. This assumption includes the case in which a process places a request for a resource and the resource is not available. Then the process cannot withdraw its request.