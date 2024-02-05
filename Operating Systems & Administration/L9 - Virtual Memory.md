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

### Addresses
- To support virtual memory, we need to implement an additional layer of abstraction.
- Need to implement:
	- Virtual address
		- Every program loaded into memory has a virtual address space.
		- Each space starts from 0x000000.
	- Physical address
		- Actual location in physical memory.
		- Virtual addresses need to be translated into physical addresses in order to access the contents of that memory location.

### Size of Blocks of Memory
- To support virtual memory, the computer system needs to manage memory in "blocks".
- Virtual memory system transfers "blocks" of the address space to/from primary memory.
- **Fixed size blocks (paging):**
	- System-defined pages are moved back and forth between primary and secondary memory.
- **Variable size blocks (segmentation)**:
	- Programmer-defined segments 
		- Corresponding to logical fragments - Are the unit of movement.
- Demand paging is the commercially dominant form of virtual memory today.

### Paging
- A page is a fixed size, $2^h$, block of virtual addresses, where h is an integer.
- A page frame is a fixed size, $2^h$, block of physical memory (the same size as a page).
- Size of a page is an exponent of 2 to minimize translation time between virtual and physical addresses.

### Demand Paging
- In demand paging, the pager brings the necessary pages into memory.
- Avoid reading in memory pages that will not be used, decreasing the swap time and the amount of physical memory needed.
- In a pure demand paging scheme, the system never bring a page into the memory until it is needed.

### Benefits
- Programs no longer constrained by the amount of physical memory.
- Each program takes less physical memory, allowing more to run at the same time, increasing CPU utilization/throughput.

### Page Fault
- What happens when a page is required but that page is not in memory but in the virtual memory.
- A page fault occurs.
- A page fault is an event when a page is required but is not found in the primary memory, but is in virtual memory.

### Page Table
- Page table is a hardware mechanism implemented to map the logical page of the program to the physical page frame where the page is loaded.
- It translate the logical page number to the physical page frame number.
**[[L9 - Virtual Memory (Valid-Invalid Bit)|Valid-Invalid Bit]]**
- The valid-invalid scheme is used to distinguished between those pages that are in memory and those that are on the disk.
- Each page table entry is associated with a bit (1 - in memory, 0 - not in memory).
- If the bit is set to "valid", the page is both legal and in memory. Otherwise, the page is either not valid or is valid but is on disk.
- Access to page marked invalid causes a page-fault trap.

### Performance of Demand Paging
- Page Fault Rate $0\le p \le1.0$
	- If p = 0, no page faults.
	- If p = 1, every reference is a fault.
- Effective Access Time (EAT)
	- EAT = $(1 - p) *$memory access time + p (page fault overhead + \[swap page out] + swap page in + restart overhead)

### Demand Paging Example
- Memory access time = 1 microsecond
- Average page fault service time = 10 milliseconds or 10,000 microseconds
- EAT = (1 - p) * 1 + p * (10000)
	- 1 + 9999p (in microseconds)
- EAT is directly proportional to page-fault rate.

### Page Replacement
- Locate the demand page in the disk.
- Find a free frame:
