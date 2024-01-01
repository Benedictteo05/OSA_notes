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
- 