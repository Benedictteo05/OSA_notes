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
	- Instruction Register (IR)
		- Contains a copy of the current instruction.
	- Program Counter register (PC)
		- Contains the memory address of the next instruction the unit is to load.
- Works based on fetch-execute cycle.
- When the computer is powered up, the control unit begins to execute the **fetch-execute** cycle until the computer is shut down.

### Fetch-execute cycle
- Fetch phase
	- Instruction retrieved from memory at location specified by Program Counter (PC)
	- Loaded into Instruction Register (IR)
	- PC is incremented
- Execute phase
	- ALU operation
	- Cause memory data reference, I/O operation

### Control Unit Operation
**Fetch phase**
- Instruction retrieved from memory.

**Execute phase**
- ALU op, memory data reference, I/O, etc.

### Primary Memory Unit
- Stores both programs and data while they are being operated on by the CPU.
- Interface between CPU and memory consists of 3 registers:
	- Memory address register (MAR)
		- Stores address of data to be read from or written to.
	- Memory data register (MDR)
		- Stores data that is read of to be written.
	- Command register (CMD)
		- Stores the command to be executed.
- Stores programs and data in binary format.
- Often referred to as random access memory (RAM).

**Read Operation:**
1. Load MAR with address
2. Load Command with "read"
3. Data will then appear in the MDR

**Write Operation:**
1. CPU puts data into MDR
2. CPU puts location into MAR
3. Load Command with "write"

### Input/Output (I/O) Devices
- Each device operation is controlled by a device controller.
- Device controller connects device to the computer's address and data bus.
- Provides an interface which the OS (Device manager) can use to manipulate device.
- Interfaces varies among controllers.
- OS provides abstraction to hide differences from programmer.

### Device Controller Interface
- Device may need constant attention/monitoring during operation.
- Device controller does this with mainly hardware algorithms.
- Software interface (device driver) provided by controller allow OS to operate and synchronize controller allows OS to operate and synchronize its behavior with the device operation.
- Device controller include the following as part of the interface:
	- Data registers
	- Command registers
	- Status flags with includes done, busy and error code
