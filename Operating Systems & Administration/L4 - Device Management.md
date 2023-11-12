### I/O System
- In the early days of computing, input and output is at a speed similar to that of processing.
- When processors became electronic, I/O devices still remain mechanical.
	- e.g. hard disk vs CPU
- Today, I/O systems are designed to handle I/O devices which are of many magnitudes slower than  the slowest CPU.
	- To provide simple, abstract software interfaces to manage the I/O operations needed.
	- Ensure that there is as much overlap as possible between the operation of the I/O devices and the CPU.


### Device Manager Abstraction
- Different devices require different operations in order to work them.
	- What kinds of operations? E.g.?
- It is important to create device drivers, which takes on the task of working these devices, but requiring only a standard set of functions to make them (the devices) work.
- The device manager, in turn, manages the collection of device drivers.
- The manager makes it possible for the OS to then provide a standard set of system calls to application programs, which use the devices.

### System Call Interface
- Functions available to application programs.
- Abstract all devices (and files) to a few interfaces.
- Make interfaces as similar as possible 
	- Block vs Character
	- Sequential vs direct access
- Device driver implements functions (one entry point per API function)

### Examples
### BSD UNIX Driver
|Commands| Description|
|---|----|
|open| Prepare dev for operation|
|close| No longer using the device|
|ioctl| Character dev specific info|
|read| Character dev input op|
|write| Character dev output op|
|strategy| Block dev input/output ops|
|select| Character dev check for data|
|stop| Discontinue a stream output op|

### Windows system calls and low-level-I/O 
|Commands| Description|
|---|---|
|`_close`| Close file|
|`_commit`| Flush file to disk|
|`_creat, _wrcreat`| Create file|
|`_dup`| Return next available file descriptor for given file|
|`_dup2`| Create second descriptor for given file|
|`_eof`| Test for end of file|
|...|...|

### Device Status Table
- Device Manager keeps track of the status of the various devices using a **Device Status Table**, which consists of these info:
	- Device ID
	- Device Status (busy, done, idle)
	- Queue of processes waiting for Device

### Overlapping the Operation of a Device and the CPU
- Programs which perform IO expects IO operations to complete before the next statement is executed.
- However, performance gains can be gained if we can make the program execute instructions while the IO is taking place.
- This should be done without violating the serial execution order of the program.
- To maximize IO, we can have the CPU operate on another process when the IO is busy with the original process.