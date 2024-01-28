# Basic Concepts and Process States
## Process Concept
- An operating system executes a variety of programs
	- Batch system (multiprogramming) - *jobs*
	- Time-shared (multitasking) systems - *processes* or *tasks*
- Textbook uses the terms *job* and *process* almost interchangeably
- **Process**: Program in execution; unit of work in modern time-sharing systems
- System is a collection of OS processes and user processes
- Program is *passive* entity stored on disk (*executable file*), process is *active* 
	- Program becomes process when executable file gets loaded into memory
- Execution of program started via GUI mouse click or name entry on CLI
- One program can be serveral processes
	- Consider multiple users executing the same program or one user executing multiple instances of the same program

## Process in Memory
- **Text Section**: Program code
- **Data Section**: Contains global and static variables
- **Stack**: Contains temporary data
	- Function parameters, local variables, return values, return addresses
- **Heap**: Contains memory dynamically allocated during runtime
![[Pasted image 20240127182612.png]]

## Process State
- As a program executes, it changes *state*
	- **New**: The process is being created
	- **Running**: Instructions are being executed on CPU
	- **Waiting**: The process is waiting for some event to occur (such as I/O completion, semaphore, message, child termination)
	- **Ready**: The process is waiting to be assigned to a processor
	- **Terminated**: The process has finished execution
- Only one process can be running on any processor at any instant
## Diagram of Process State
![[Pasted image 20240127182752.png]]
### Notes
- The interrupt that puts the process from the *ready* state to the *running state* is the *I/O completion* interrupt. 
-  The interrupt that puts a process from the *running* state to the *ready* state is the *timed interrupt*. The time quantum expired, putting the process back to the *ready* state and the kernel will take over
- If the process in a *running* state generates and exception, then the process will go to the *terminated* state
- If a process requests I/O by making a system call, the kernel takes over sending the request to the I/O device and marking the process to the *waiting* state until the I/O device completes processing the request and notifies the system through an I/O completion interrupt