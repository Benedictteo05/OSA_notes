### Scheduling
- Task of managing CPU sharing among a pool of ready processes/threads.
- Possible only with context switching facility.
- The scheduler chooses one of the ready threads to allocate to the CPU when it is available.
- The scheduling policy determines when it is time for a thread to be removed from the CPU and allocate it to another thread.
- The scheduling mechanism determines how the process manager can determine it is time to interrupt the CPU, and how a thread can be allocated to and removed from the CPU.