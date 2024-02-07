### The Need for Files
- A computer system requires to store data in a non-volatile storage system.
- Although the computer system is good at computation, stable storage of data is required in order to perform meaningful tasks, e.g. storing company data, application programs, etc.
- Files are the OS mechanism for organizing and managing the data in a computer system for storage.
- Types of files include executable, data, text (including html), among many others.

### Files
- Almost every application needs to read from or write to files.
- To support file handling, almost all programming languages provide file handling routines.
- These routines, when activated, execute the OS system calls to handle the files.
- The manager in the OS that handles files is the file manager.

### View of the File Manager
![[Pasted image 20240207004906.png]]

### Block Management
- In an actual storage system, data is stored in blocks, usually of equal size.
- Three well-known techniques of organizing these blocks:
	- As a contiguous set of blocks.
	- As a list of blocks interconnected with links.
	- As a collection of blocks interconnected by a **file index**

### Contiguous Allocation
- This method requires each file to occupy a set of contiguous blocks on the disk.
- Disk addresses define a linear ordering on the disk.
- Disk addresses define a linear ordering on the disk
- Contiguous allocation of a file is defined by the disk address and length (in block units) of the file.
- Directory entry for each file indicates the address of starting block and length of the area allocated to this file.
- If the file is n blocks long and start at location b, then it occupies b, b+1, b+2,.., b+n-1.

### Contiguous Allocation Advantages
- Support both sequential and direct access
	- For sequential access, the file system remembers the disk address of the last block referenced, and, when necessary, reads the next block.
	- For direct access to block i of a file that stars at block b