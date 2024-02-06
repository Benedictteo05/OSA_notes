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
	- [[L7 - Deadlocks#^5837c5|Avoidance]]
		- Construct a model of system states, then choose a strategy that will not allow the system to go a deadlock state. Disallow process if predicts a deadlock.
	- [[L7 - Deadlocks#^8bbd82|Detection & Recovery]]
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

**Allow Preemption**
- If a process requests for a resource and the resource is not available, its currently held resources can be preempted by the OS and given to other processes.

### Avoidance
^5837c5
- Manage deadlocks by allowing resource allocation only if it satisfied that deadlock will not occur (safe state).
- The mechanism is [[L7 - Deadlocks#^2f8e26|Banker's algorithm]].

### Banker's algorithm
^2f8e26

Finds our how much resources is needed, then allocate enough resource for it. If the OS predicts that there might be a deadlock, the OS will reschedule the resources for the processes.
### Detection and Recovery
^8bbd82
- OS detects that CPU has capacity to run but processes are not running.
- Take one of the resource from one process for another process, allowing the OS to break the deadlock.
- An aggressive strategy.
- Disregards deadlocks, but aims to detect when it does occur and takes additional steps to remove it. (recovery)
- Therefore, we need both a detection mechanism and a recovery mechanism.
- For detection, an algorithm similar to Banker's algorithm can be used.

### Deadlock Detection
- When should the detection algorithm be invoked?
1. Invoke each time a request for allocation cannot be granted immediately.
	- Advantage: 
		- Able to identity the specific process that cause the deadlock.
	- Disadvantage:
		- Overhead in computational time.
2. Invoke at regular time intervals.
	- e.g. once per hour.
3. Invoke when CPU utilization drops below 40%

- Note: Resources allocated to deadlocked processed will be idle until the deadlock is broken

### Deadlock Recovery
- Inform operator to deal with deadlock manually.
- Two options for breaking deadlock to recover system from deadlock automatically:
	1. [[L7 - Deadlocks#^f3ae14|Process Termination]]
	2. [[L7 - Deadlocks#^0c48b3|Resource Preemption]]

### Process Termination
^f3ae14
- Abort all deadlocked processes 
	- This method is expensive since processes may have computed for a long time, and all results must be discarded, and recomputed again.
- Abort one process at a time until deadlock cycle is broken.
	- This method incurs overhead since after each process is aborted, deadlock detection algorithm must be invoked to check whether any process is still deadlocked.
- Note: 
	- Aborting a process may not be simple. e.g. Process may be in the midst of updating a file.
	- For partial termination method, a policy must be defined as to which process to terminate.

**Factors to determine which process is chosen:**
- The priority of process (Kill lower in priority).
- How long the process has computed and how much longer to go (Kill just started).
- How many and what type of resources the process has used (Kill less important).
- How many more resources the process needs in order to complete (Avoid killing interactive process).
- How many processes will need to be terminated.
- Whether the process is interactive or batch.

### Resource Preemption
^0c48b3
- Preempt some resources from processes and give these resources to other processes until the deadlock cycle is broken:
	- Note: For both process termination or resource preemption methods, the system reclaims all resource allocated to the terminating processes.
- Three issues to be addressed:
	- Selecting a victim
		- Q: Which resources and processes to preempt?
		- A: Depends on cost. e.g. amount of time process executed thus far, number of resources holding, etc.
	- Rollback
		- Q: If we preempt a resource from a process, what should be done to the process?
		- A: Either total rollback or rollback enough to break deadlock.
	- Starvation
		- Q: How to ensure starvation will not occur? That is, how can we guarantee that resources will not always be preempted from the same process?
		- A: A common solution is to include the number of rollbacks in the cost factor.

### Combined Approach to Deadlock Handling
- None of the basic approaches alone is appropriate to handle deadlock.
- For different classes of system resources, use different approaches:
	- Internal resources:
		- Used by the system. e.g. PCB.
		- Prevention through resource ordering.
	- Central memory:
		- Memory used by a user job.
		- Prevention through preemption.
	- Job resources:
		- Devices that can be assigned. e.g. tape drive, files.
		- Avoidance.
	- Swappable space
		- Space on backing store for each user job.
		- Preallocation

