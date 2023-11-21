### Processes and Threads
- A process is made of:
	- A binary program
	- Data on which the program will execute
	- Resources required for execution, including files, devices which contains or provides the data required.
- In a classic program design, there is only one execution engine for each process.
- That is, there is only one thread of execution in one process.
- In modern computers, the modern process can consists of multiple execution engines.
- In such a design, a process can contain multiple threads.

### Threads
- A threads is a single execution engine capable of performing a series of instructions in a computer program.
- In a multiple threaded process, each thread needs to maintain its own set of data in order to perform its own series of instructions.
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
- Windows Win32 API allows processes with multiple threads to be created through its CreateProcess() function.
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
	- Calls like fork() in UNIX and `CreateProcess()` in windows to create processes.
	- Calls like `pthread_create()` in Linux and `CreateProcess()` in Windows to support threading.
	- Calls like `close()` in Unix and `CloseHandle()` in Windows to close processes/threads to release resources.

