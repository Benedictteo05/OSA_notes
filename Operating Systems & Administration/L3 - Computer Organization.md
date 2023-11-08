**Introduction**
- File of instructions (Source file)
- High level programming (e.g. C, Python, Java)
- Low level programming (e.g. Assembly - processor specific )
- Machine language (processor specific)
- Computers execute machine language 
- Programs must be complied into machine language (exe file)

### Program Specification
- High-level language translates to low-level language.
- Low-level language is compiled into machine language.

### Von Neumann Architecture
- Forms the basis for almost all modern computer systems. Most other specialized systems evolved from this architecture.
- Has a fixed set of electronic parts, which can be manipulated to perform various tasks determined by a variable program.
- Consists of the following parts:
	- A Central Processing Unit (CPU)
	- A primary memory unit
	- A collection of I/O Devices
	- Buses to interconnect the components
- How it is interconnected:
	- CPU
		- Arithmetical Logical Unit (ALU)
		- Control Unit (CU)
	- Primary Memory Unit (Executable Memory)
	- Device
	- Address Bus
	- Data Bus

### Central Processing Unit
- The CPU is the brain of the computer
- Made up of:
	- Arithmetical Logical Unit (ALU)
	- Control Unit (CU)

### Arithmetical Logical Unit (ALU)
- Can be thought of as a very fast calculator.
- Can perform various arithmetic and logical operations.
- Typically has a 32 to 64 registers (very fast memory).
- Responsible for performing arithmetic and logical operations
- Comprises of:
	- Functional unit
		- Performs the operations
	- Registers (Very fast memory)
		- Data, status registers
		- Loaded and saved to/from primary memory
		- 32 to 64 registers to hold 32-bit data
- Computations are accomplished by:
	- Loading binary values into registers.
	- Performing operations on the registers using the function unit.
	- Storing the result back into a general register.
	- Saving the register contents back to memory.

### Control Unit
- Causes a sequence of instructions stored into the memory to be retrieved and executed.
- Comprises of:
	- Fetch Unit
		- Fetches an instruction from memory.
	- Decode Unit
		- Decode an instruction.
	- Execute Unit
		- Signal ALU to execute instruction.
	- Instructin


### Fetch execution cycle
Program counter will take an address,
Instruction register (IR)
