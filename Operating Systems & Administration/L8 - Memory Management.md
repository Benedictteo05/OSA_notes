### Memory Management
- Memory in a computer system is divided into primary and secondary memory.
- Primary memory holds information (data and programs) while the CPU is using it.
- Secondary memory refers to storage devices that stores information when the CPU is not using it.
- Memory manager is responsible for allocating and deallocating  primary memory.
- It ensures that the memory is not abused and is used efficiently.

### Memory Manager
- Requirements
	- Minimize executable memory access time
	- Maximize executable memory size
	- Executable memory must be cost-effective
- Today's memory manager
	- Allocates primary memory to processes 
	- Maps process address space to primary memory
	- Minimizes access time using cost-effective memory configuration
	- May use static or dynamic techniques

### Storage Hierarchies
- Memory in a computer system can be divided into a hierarchy based on their characteristics.
- It also reflects how we work in the real world.
- At the top of the hierarchy is faster, but more expensive memory. e.g. Registers.
- At the bottom is slower, but cheaper memory. e.g. Hard disk, tape drives.

### Managing Address Space
 - When a program is converted (compiled) into executable form, there is no need to attach addresses to every single instruction in the program.

**Why?**
- Program instructions need to be stored in a particular order in order for the CPU to execute in the correct way.
- Programs involve many 'jumps' to different parts of the program. In order to do this, there has to be a concept of addresses for every part of the program.
- Imagine someone asking you to go to a person's house. Unless the address is given to you, there is no way you can get to that house.
- This process is called Address Binding.

### Creating an Executable Program
- Compile time: Translate elements
- Link time: Combine elements
- Load time:
	- Allocate primary memory
	- Adjust addresses in address space
	- Copy address space from secondary to primary memory