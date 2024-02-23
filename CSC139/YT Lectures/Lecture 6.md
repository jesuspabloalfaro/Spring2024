# OS is a Resource Manager
## Process Management
- A process is a program in execution. It is a unit of work within the system. Program is a *passive entity*, process is an *active entity*
- Process needs resources to accomplish its task
	- CPU, memory, I/O files
	- initialization data
- Process termination requires reclaim of any reusable resources
- Single-threaded process has one *program counter* specifying location of next instruction to execute
- Multi-threaded process has one program counter per thread
- Typically system has many processes, some user, some operating system running concurrently on one or more CPUs
	- Concurrency by multiplexing the CPUs among processes/threads

## Process Management Activities 
- Creating and deleting both user and system processes (Ch.3)
- Suspending and resuming processes (Ch.3)
- Providing mechanisms for *process synchronization* (Ch.5)
- Providing mechanisms for *process communication* (Ch.3)
- Providing mechanisms for *deadlock handling* (Ch.7)

## Memory Management
- To execute a program, all (or part) of the instructions must be in memory
- All (or part) of the data that is needed by the program must be in memory
- **Memory management**: Determines what is in memory and when
- *Memory management* activities
	- Keeping track of which parts of memory are currently being used and by whom
	- Deciding which processes (or parts) and data to move into and out of memory
	- Allocating and deallocating memory space as needed

## Storage Management
- OS provides uniform, logical view of information storage
	- Abstracts physical properties to logical storage unit - *file*
	- Each medium is controlled by a device (e.g. disk drive, tape drive)
		- Varying properties including *access speed, capacity, data-transfer rate, access method* (sequential or random)
- File System management
	- Files usually organized into directories
	- Access control on most systems to determine who can access what
	- OS activities include
		- Mapping files onto secondary storage
		- Creating and deleting files and directories
		- Primitive to manipulate files and directories
		- Backup files onto stable (non-volatile) storage media

### Notes
- File systems store files in *blocks*. **Blocks** are chunks of storage that can hold whole or parts of files. Files can be stored in different *blocks* that are in different parts of the storage media but you as the end user do not see this. See diagram below. 
![[Pasted image 20240123194217.png]]

## Performance of Various Levels of Storage
![[Pasted image 20240123194238.png]]

### Notes
- 1 nanosecond(ns) corresponds to (1Ghz or 10^9) or (10^-9 seconds/cycle)
- *Cache management* is done by the *hardware*
	- Deciding what to put in the cache
	- Hardware will start with empty cache, then when a memory location is accessed, the hardware will check if its in the cache. If its not in the cache, hardware will load the data from main memory to the cache.
	- When cache is full, hardware will overwrite a piece of the cache to start storing new data from main memory
		- **Replacement Policy**: *Least Recently Used* (LRU)
- *Register management* is done by the *compiler*
	- *Compiler* maps variables into *registers*
	- Limited number of *registers*
		- **Register Allocation**: Mapping as many program variables into CPU *registers*

## I/O Subsystem
- One purpose of the OS is to hide peculiarities of hardware devices from the user
- I/O subsystem responsible for
	- General device-driver interface
	- Drivers for specific hardware devices
	- Memory management of I/O

## Kernel Data Structures
- Many similar to standard programming data structures
- See picture below for *singly linked list, doubly linked list, and circular linked list*
![[Pasted image 20240123195634.png]]

### Notes
- An *operating system* is basically just a really complex program.
- A *program* is just a combination of algorithms and data structures using some kind of programming language.
	- The more complex a program is, the more complex the algorithms and data structures

## Open-Source Operating Systems
- Operating systems made available in source-code format rather than just binary *closed-source*
- Counter to the *copy protection* and *Digital Rights Management (DRM)* movement
- Started by *Free Software Foundation (FSF)*, which has "copyleft" *GNU Public License (GPL)*
- Examples include *GNU/Linux* and *BSD Unix* (including code of *Mac OS X*), *Open Solaris* and many more
- Good for academic purposes (education and research)