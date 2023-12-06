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
	- Have a situation in which there are K processes holding units of K resources.
- No preemption
	- Resources can be released only by the explicit action in a process, rather than by the action of an external authority. This assumption includes the case in which a process places a request for a resource and the resource is not available. Then the process cannot withdraw its request.

### Addressing Deadlock
- 4 Approaches to managing deadlock
	- [[L7 - Deadlocks#^e9ba08|Prevention]]
		- Design the system so that deadlock is impossible.
	- Avoidance
		- Construct a model of system states, then choose a strategy that will not allow the system to go a deadlock state.
	- Detection & Recovery
		- Check for deadlock (periodically or sporadically), then recover.
	- Manual intervention
		- Have the operator reboot the machine if it seems too slow.

### Prevention
^e9ba08
- Address the 4 conditions so that at least one of them does not hold.
	- Namely, mutual exclusion, hold and wait, circular waiting, no preemption.
- Most common strategy is to design the resource managers so that they are guaranteed to violate at least one of the conditions.
- Windows NT/2000 assures there can be no circular wait.

**Hold and Wait**
- Two ways:
	- Require a process to request all of its resources when it is created.
		- Easy implementable in batch systems.
		- Not easy in interactive systems as processes do not 'announce' their resource requirements at runtime.
	- Require the process to release all currently held resources prior to requesting any new ones.
		- More suitable for interactive systems.
		- Have processes request for resources based on a particular operation and then release it when proceeding onto another operation with a new set of resources.
		- Or, when a process requires a new resource, it releases all of it current resources and then acquires the old resources along with the new one.

**Circular Wait**
- Technique 1
	- Use a process-resource model to detect cycles in the graph.
	- Choose a resource request strategy by which no cycle will be introduced.
	- Cycle condition will reflect circular wait if each resource type has only one instance (non-sharable).
- Technique 2
	- Total order on all resources, then can only ask for $Rj$ if $Ri$ < $Rj$ for all $Ri$ the process is currently holding.
	- Number each resource uniquely.
	- A process wishing to obtain resources must obtain them in ascending or decreasing order.
	- If new resource is not in the correct order, release all currently held resources and re-obtain them in the correct order.


### Banker's algorithm
Finds our how much resources is needed, then allocate enough resource for it. If the OS predicts that there might be a deadlock, the OS will reschedule the resources for the processes.

### Detection and Recovery
- OS detects that CPU has capacity to run but processes are not running.
- Take one of the resource from one process for another process, allowing the OS to break the deadlock.