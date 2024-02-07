A deadlock is a situation where in a group of 2 or more processes/threads. Each process holds a resource while requesting for another. The request cannot be fulfilled because the requested resource is held by another process which is being blocked, waiting for a another resource.

- Mutual exclusion
- Hold and wait
- Circular wait
- No preemption

Prevent deadlock
- Prevention
	- By design
	- Hold and wait
		- Make processes request all resources when it is created
		- Make process release all resources before requesting for new ones.
	- Circular wait
		- Process-resource model to detect cycle in the graph
		- Uniquely identify each resource, only allow processes to request for resources that are higher then what the process is holding.
	- Preemption
		- If a process is required and cannot be fulfilled, the OS is able to preempt the resource
- Avoidance
	- Manage deadlock by allowing resource allocation only if it determines that a deadlock will not occur. (safe state)
	- Banker's algorithm
- Detection and Recovery
	- Disregards deadlock, but aims to detect when it does occur and takes additional steps to remove it.
	- banker's algorithm for detection
		1. Invoke each time a request of allocation cannot be granted immediately.
			- Able to identify the specific process that is causing the deadlock.
			- Overhead in computational time.
		2. Invoke a regular time intervals.
		3. Invoke when CPU utilization drops below 40%.
	- Recovery
		- Inform operator to deal with deadlock manually.
		- Two options to break automatically:
			1. Process termination
				- Priority of process
				- How long and how much longer to go
				- How many and what type
				- How many more resources to complete
				- How many needs to be terminated.
				- interactive or batch
			1. Resource preemption
				- Selective a victim
				- Rollback
				- Starvation
- Manual intervention
	- 

Compile time
