### Virtual Memory
- Sole use of primary memory to run programs is not sufficient
	- Because large portions of most programs are not executed most of the time.
	- Therefore, large portions of programs need not be in memory.
	- Need to maximize the use of primary memory by loading as many programs as possible so as to increase CPU utilization.
- The availability of fast secondary memory (hard disk) allows for its use to supplement primary memory.
- Virtual memory allows the execution of processes that are not completely in memory.
- Each process's address space is partitioned into parts that can be loaded into primary memory.
- Partitions which are not needed are written to secondary memory.
- Allows program that are larger than physical memory to be executed.

### Locality
- Every process has code and data locality
	- Code tends to execute in a few fragments are one time.
	- Tend to reference same set of data structures.
- As computation moves to a different phase, it changes locality.
- Address space is logically partitioned
	- Text, data, stack
	- Initialization, main, error handle
- Different parts have different reference patterns:
	- Initialization code (used once)
	- Code for phase 1
	- Code for phase 2
	- Code for phase 3
	- Code for error 1
	- Code for error 2
	- Code for error 3
	- Data & stack
