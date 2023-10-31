### Operating System Services (Clean notes during tut)
- An operating system provides an environment for the execution of programs.
- Different operating systems are organized along different lines.
- As such, specific services may differ, but common classes exist:
	- Those that provides convenience for user/programmer
	- Those that ensure efficient operations of the system
- Services that provides convenience to user/programmer
	- User interface
		- Batch interface, CLI, GUI
	- Program execution
		- Able to load, run and terminate a program
	- Input/ Output Operations
		- File, CD/DVD drive, Display device, Smart Card
	- File-system manipulation
		- Create/Read/Write/Delete files and directories
		- Permission management
	- Communications
		- Local/remote inter-process communication
	- Error detection
		- Able to detect error and take proper action to ensure consistent computing
- Services that ensures efficient operation of the system 
	- Resource allocation
		- Resources to be allocated among multiple users fairly 
		- Different algorithms for different resources
	- Accounting
		- Keep track of usage statistics. e.g. CPU, Printer, hard disk quota
		- Reconfigure system to improve computing services
	- Protection and security
		- Security of system from outsiders
		- Ensure access to all system resources is controlled
		- Audit trail of access

### Functions of an Operating System
- 4 Major group of basic functions common to all OS
	- Device management
	- Process, thread and resource management
	- Memory management
	- File management
- Close interactions between the 4 managers.

**Disk management**
- Refers to the way generic devices are handled. Includes disk, tapes, terminals, printers, etc
- Special management approaches for processor and memory
- Partitioning design simplifies adding and upgrading of devices

**Process, thread and resource management**
- Creates abstractions of processes, threads, resources
- Allocates processor resource equitably 
- Allocates and tracks abstract resource such as queues, semaphores (access control), messages
- Cooperates with memory manager to administer the primary memory

**Memory Management**
- Administer and allocate primary memory
- Enforces resource isolation
- Enables sharing between processes
- Provides virtual memory extensions
	- Abstract machine's memory appear larger than physical memory

**File Management**
- Creates abstraction of storage devices. i.e. I/O operations
- Range from byte stream files to indexed records
- Local and Remote file systems


### System Call
A system call is a call to the OS through the Supervisor mode to do service for the application program. 