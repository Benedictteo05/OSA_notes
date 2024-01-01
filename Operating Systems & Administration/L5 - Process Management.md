### Processes and Threads
- A process is a binary program in **execution**.
- A process ( != not a program) is made of:
	- A binary program
	- Data on which the program will execute
	- Resources required for execution, including files, devices which contains or provides the data required.
- In a classic program design, there is only one execution engine for each process.
- That is, there is only one thread of execution in one process.
- In modern computers, the modern process can consists of multiple execution engines.
- In such a design, a process can contain multiple threads.

### Threads
- A threads is a single execution engine capable of performing a series of instructions in a computer program.
- In a multiple threaded process (a process that is made up of multiple threads), each thread needs to maintain its own set of data in order to perform its own series of instructions.
- E.g.
	- A web browser might have one thread display images or text while another thread retrieve data from the network.
	- A word processor may have a thread for displaying graphics, another thread of responding to keystrokes from user and a third for performing spelling and grammar checking in the background.
- Thread specific data is private to the thread. This data is usually stored in a stack.
- Thread specific data includes:
	- Program counter
	- Status of the thread
	- Processor registers
	- Stack space
- Threads within the same process shares the same:
	- Program code
	- Data
	- Resources
- Sometimes threads are also called lightweight processes.

### UNIX Processes
- Each processes has its own address space
	- Subdivided into text, data, & stack segment
	- Program file describes the address space
- OS kernel creates a process descriptor to manage process
- Process identifier (PID): User handle for the process (descriptor)
- Try `ps` and `ps - aux` 
- Unix classic processes have not explicit notion of a thread.

### Threads - The NT Model
- Windows Win32 API allows processes with multiple threads to be created through its `CreateProcess()` function (privileged instructions).
- Options provided includes:
	- Creating a new child process with a single thread.
	- Creating new additional threads in the current process.

### Benefits
- Some benefits of multithreaded programming
	- Responsiveness
	- Resource sharing
	- Ease of memory and resource allocation
	- Utilization of multiprocessor architectures

### Process Manager
- To manage multiple processes, modern OS implement the process manager to manage the processes.
- The process manger implements:
	- Calls like `fork()` in UNIX and `CreateProcess()` in windows to create processes.
	- Calls like `pthread_create()` in Linux and `CreateProcess()` in Windows to support threading.
	- Calls like `close()` in Unix and `CloseHandle()` in Windows to close processes/threads to release resources.

**Process Manager Responsibilities**
- Define & implement the essential characteristics of a process and thread.
	- Algorithms to define the behavior
	- Data structures to preserve the state of the execution.
- Define what "things" threads in the process can reference - the address space (most of the "things" are memory locations)
- Manage the resources used by the processes/threads.
- Tools to create/destroy/manipulate processes & threads.
- Tools to schedule the processes on the CPU.
- Tools to allow threads to synchronization the operation with one another.
- Mechanisms to handle deadlock.
- Mechanisms to handle protection (security).

### Process Descriptors
- OS creates/manages process abstraction.
- Descriptor is data structure for each process:
	- Process ID
	- Program counter
	- Register values
	- Process states
	- Type & location of resources it holds
	- List of resources it needs
	- Security keys
- Also known as Process Control Block (PCB)

### Context Switching
- In a multiple process environment, each thread of execution is a context.
- When the CPU switches between two processes/threads, it is called a **context switch**.
- A context switch can only occur when the OS gets control of the CPU through [[L2 - Operating System Organization#^d743ab|trap]] or [[L3 - Computer Organization#^e0e780|interrupt]]. 

### Process States
- As a process executes, it changes state:
	- Running: Instructions are being executed.
	- Blocked: The process is waiting for some event to occur (e.g. I/O completion).
	- Ready: The process is waiting to be assigned to a processor.
	- Done: The process has finished execution.
- Modern OS implement additional states as required to support more complex features.

### Process State Diagram
![[Pasted image 20240101142347.png]]