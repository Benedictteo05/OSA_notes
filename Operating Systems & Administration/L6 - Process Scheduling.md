### Scheduling
- Task of managing CPU sharing among a pool of ready processes/threads.
- Possible only with context switching facility.
- The scheduler chooses one of the ready threads to allocate to the CPU when it is available.
- The scheduling policy determines when it is time for a thread to be removed from the CPU and allocate it to another thread.
- The scheduling mechanism determines how the process manager can determine it is time to interrupt the CPU, and how a thread can be allocated to and removed from the CPU.

### Scheduling Mechanisms
- The scheduling mechanism is composed of three logical parts:
	- Enqueuer
	- Dispatcher
	- Context switcher

**Enqueuer**
- When a process/thread is changed into the ready state, the enqueuer enqueues the corresponding descriptor into a list of processes that are waiting for the CPU (or the ready list). The enqueuer may place the new process anywhere in the list, depending on the scheduling policy.

**Dispatcher**
- The dispatcher is invoked after the current process is removed from the CPU. The dispatcher removes one of the threads from the ready list and then allocates it to the CPU by loading its CPU registers in the thread's descriptor into the CPU.

**Context switcher**
- When the scheduler switchers the CPU from executing one process to another, the context switcher saves the contents of all CPU registers (PC, IR, condition status, processor status, and ALU status) for the thread being removed into its descriptor.

### Scheduling Performance
- Scheduler and its scheduling policy can have a dramatic effect on the performance of a multi-programmed computer.
- The time a process takes to finish execution is dependent on how often it gets to execute on the CPU as dispatched by the scheduler.
- Aim is to decrease average time a process takes to execute in the computer and to increase the throughput of a computer in terms of the number of processes that gets executed per unit time.

### Policy Considerations
- Policy can control/influence:
	- CPU utilization (To keep the CPU busy)
	- Average time a process waits for service (Reduce waiting time)
	- Average amount of time to complete a job (Reduce time in ready queue to finish state)

### Nonpreemptive scheduler
^4c17fe
- When a process gets the CPU, it will not be preempted (it will not be interrupted), it will have the opportunity to run until it is fully completed before the CPU is given to the next process.

### Preemptive scheduler
- Processes takes turns to share the CPU, they can be interrupted midway - the CPU is allocated to another process even before a process finishes


### First-Come-First-Served (FCFS)
- Concept:
	- The process to request first will be allocated the CPU first.
	- It is [[L6 - Process Scheduling#^4c17fe|non-preemptive]]
	- Using a FCFS queue, PCB of a new process will be linked to the tail of the queue.
	- When CPU is free, process at the head of the FCFS queue will be allocated the CPU.
- Advantages:
	- Simplest CPU scheduling algorithm.
- Disadvantages:
	- Convoy effect: Short process behind long process and waiting for the long process to finish. This results in lower CPU and device utilization.

### Shortest-Job-First (SJF)
- Concept:
	- Each process is associated with the length of its service time (total CPU time that is required by the process). When the CPU is available, it is assigned to the process that has the smallest (remaining) service time.
- Two methods:
	- Nonpreemptive - Once CPU is allocated to a process it cannot be preempted until it completes its service time.
	- Preemptive - A current process is preempted if a new process arrives with a service time length lesser than the current process's remaining service time.
	- This scheme is also known as the Shortest-Remaining-Time-First (SRTF).
- SJF is optimal 
	- It gives minimum average waiting time for a given set of processes.

### Priority Scheduling
- Concept:
	- A priority number (integer) is associated with each process. The CPU is allocated to the process with the highest priority. Equal-priority processes are scheduled in FCFS order.
		- Preemptive
		- Nonpreemptive
- Problem:
	- Starvation
	- Low priority processes may never be executed.
- Solution:
	- Aging
	- Increase the priority of the process as time progresses.

### Round-Robin (RR)
- Preemptive scheduling
- Each process gets a small unit of CPU time (time quantum), usually 10-100 milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue.
- New processes are added to the tail of the ready queue, which is a FCFS circular queue.
- Fast response time. It is good for time-sharing system.
- If service time is <1 time quantum, process release CPU voluntarily. 
- Performance. It depends on size of time quantum:
	- Large quantum (q). This is equivalent to FIFO.
	- Small quantum (q). It must be large with respect to the context switch, otherwise overhead is too high.

### Multilevel Queue
- Processes are classified into groups based on some property of the process.
- Ready queue is partitioned into separate queues such as foreground (interactive), background (batch).
- The processes are permanently assigned to one queue. 
- Each queue has its own scheduling algorithm. 
- E.g.
	- RR for foreground queue.
	- FCFS for background queue.

### CPU Schedules
- There is no practical way to determine which policy is the best.
- To study policy performance, we need to consider simplified model, based on a fixed order of processes, which reflect the actual kind of processes a computer can expect.
- To do so, we are provided with:
	- A schedule of processes, their arrival time and CPU service time.
- We need to analyze and produce the following:
	- Gantt chart
	- Average waiting and turnaround time.

**Gantt Chart**
- A 'chart' showing the actual execution of a series of processes by the CPU.
	- It shows the start and end of execution of each processes.
-  Waiting time is defined as the total time which a process spends waiting for the CPU in the ready list.
- Turnaround time is the time from the arrival of the process to its completion by the CPU.
	- It includes the time it spends waiting for the CPU.
 