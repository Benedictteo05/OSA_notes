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
	- For direct access to block i of a file that stars at block b, we can immediately access block b+i.
- Minimal disk seek time
	- As disk addresses are defined in a linear ordering on the disk, accessing block b+1 after block b normally requires no head movement. Moreover, when head movement is needed (from the last sector of one cylinder to the first sector of the next cylinder) it is only one track. Thus the number of disk seeks required for accessing contiguously allocated files is minimal.

### Contiguous Allocation Disadvantages
- External Fragmentation
	- As files are allocated and deleted, the free disk space is broken into little pieces thus resulting in non-contiguous blocks.
	- The solution to this problem is to perform compaction on the disk blocks. All the free space is compacted into one large hole. However, the cost of compaction is time.
- Unknown file size 
	- When a file is created, the total amount of space it needs must be allocated, but in some cases, example, output file, the size is not known and may be difficult to extend later.
- Known file size
	- Even if the file size is known in advance, pre-allocation may be insufficient because file will grow over a long period of time.

### Linked Allocation
- Linked allocation solves all problems of contiguous allocation. With linked allocation, each file is a linked list of blocks; the disk blocks may be scattered anywhere on the disk.
- The directory contains a pointer to the first and last blocks of the file. Each block contains a pointer to the next block. 
- To create a file, we simply create a new entry in the directory and the pointer to the first disk block of the file is initialized to nil (the end-of-list pointer value) to signify an empty file.
- A write to a file removes the first free block from the free-space list and linked to the end of the file.
- To read a file, simply follow the pointers from block to block.

### Linked Allocation Advantages
- Disk space need not be contiguous.
- No external fragmentation
	- Any free block on the free-space list can be used to satisfy a request, since all blocks are linked together.
	- There is no necessity to compact disk space.
- No need to declare the size of file
	- The size of a file can grow as long as there are free blocks.

### Linked Allocation Disadvantages
- Inefficient for direct access
	- To find the $ith$ block of a file, we must start at the beginning of that file, and follow the pointers until we get to the $ith$ block.
- Pointer space
	- Extra space in each block is required to store the pointers. Thus, each file would require slightly more space.
- Reliability problem
	- As the files are linked together by pointers scattered all over the disk, consider what would happen if a pointer was lost of damaged. A bug in the OS or disk hardware failure might result in picking up the wrong pointer thus accessing wrong block.
### Index Allocation
- Linked allocation does not support efficient direct access, since the pointers to the blocks are scattered with the blocks themselves all over the disk and need to be retrieved in order. Indexed allocation solves this problem by bringing all the pointers together into one location: The Index block.
- Each file has its own index block, which is an array of disk-block addresses. The $ith$ entry in the entry in the index block points to the $ith$ block of the file. The directory contains the address of the index block.
- To read the $ith$ block, use the pointer in the $ith$ index block entry to find and read the desired block.
- When the file is created, all pointers in the index block are set to nil. When the $ith$ block is first written, a block is removed from the free-space list and its address is put in the $ith$ index-block entry.
**How it works**
- Extract headers and put them in an index.
- Simplify seeks.
- May link indices together (for large files).

- **Example of Indexed Allocation**
	![[Pasted image 20240207133800.png]]

### Index Allocation Advantages
- Support direct access.
- No external fragmentation as any free block on the disk may satisfy a request for more space.

### Index Allocation Disadvantages
- Wasted space
	- The pointer overhead of index block is generally greater than the pointer overhead of linked allocation.
	- An entire index block is allocated to a file even if only one or two pointers are used.
	- Inevitably, we have to decide on the size of the index block (If index block is too large, space are wasted. Too small an index block will not be able to hold enough pointers for large file).

### File Descriptors
- The file manager, in addition to storing the files, also manages the various information that describe the files. (file descriptors).
- External name
- Current state
- Sharable
- Owner
- User
- Locks
- Protection settings
- Length
- Time of creation
- Time of last modification
- Time of last access
- Reference count
- Storage device details

### Directories
- File manager not only needs to provide mechanisms for applications to create, write, read files, it also needs to provide ways to manage *collections* of files.
- A file directory is a set of logically associated files and other sub-directories of files.
- We use directories to help use organize logically the different files that we may handle.
- For e.g. We can store the files associated with a project in one direct and those with another project in another directory.
- The file manager provides a set of commands to allow users to administer directories, including:
	- Enumerate: Returns a list of all the files and nested directories. E.g. `dir` in Windows, or `ls` in Unix/Linux.
	- Copy: Create a duplicate of an existing file. `cp`
	- Rename: Changes the name of the file. `mv`
	- Delete: Removes the file from the directory. Can also be used to delete directories. `rm`
	- Traverse: 