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

### Turnaround time
- Time from when it arrives till the 