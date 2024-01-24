# OS Introduction
## What is an Operating System?
- Program that acts as an intermediary between a user of a computer and the computer hardware
- Operating System Goals:
	- Execute user programs and make solving user problems easier
	- Make the computer system convenient to use
	- Use the computer hardware in an efficient manner (resource management)

# Computer System Structure
- Computer system can be divided into four components:
	- Hardware
		- CPU. memory, disk, I/O devices
	- Operating System
		- controls and coordinates use of hardware among various applications and users
	- Application Programs
		- Word processors, compilers, web browsers, database systems, video games
	- Users
![[Pasted image 20240122163017.png]]

## What Operating Systems Do
- Depends on the type of system
- Users want convenience, ease of use, and good performance
	- Don't care about resource utilization
- But shared computers such as mainframes must keep all users happy
- Users of dedicated systems such as workstations have dedicated resources but frequently use shared resources from servers
- Handheld computers are resource poor, optimized for usability and battery life
- Some computers have little or no user interface, such as embedded computers in devices and automobiles

### Notes
- **Embedded System**: Part of another system to help support the main system

## Operating System Definition
- OS is a resource allocator
	- Manages all resources
	- Decides between conflicting requests for efficient and fair resource use
- OS is a control program
	- Controls execution of programs to prevent errors and improper use of the computer (protection)
		- Some protections include **memory management**
- No universally accepted definition
- "Everything a vendor ships when you order an operating system" is a good approximation
	- But varies widely
- "The one program running at all times on the computer" is the *kernel*.
- Everything else is either
	- A system program (ships with the operating system)
	- An application program

### Notes
- **Kernel**: Can be thought of as the 'main' program of the *Operating System*
	- Kernel provides memory protection not allowing memory that is allocated to other user processes/kernel itself. Will terminate application/process trying to access memory not allocated to itself.
- **Interrupt Service Routine (ISR)**: Hardware exception. Hardware traps into memory system. Belongs to *Operating System*. 
- **DOS**: Early *Operating System* that does **not** provide memory protection. 
	- Coding in DOS (specifically in C) is difficult because declaring pointers without initializing the memory address can lead to parts of the *kernel* being overwritten.

## Computer Startup
- *Bootstrap Program* is loaded at power-up or reboot
	- Typically stored in ROM or EPROM, generally known as *firmware*
- Initializes all aspects of system
- Loads *operating system kernel* and starts execution