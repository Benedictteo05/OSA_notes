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
- Detection and Recovery
- Manual intervention

