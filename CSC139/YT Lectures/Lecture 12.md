# Processes States and Transitions P2
## Process Control Block (PCB)
Information associated with each process (also called **task control block**)
- Process state - running, waiting, etc
- Program counter - address of next instruction to execute
- CPU registers - contents of all CPU registers: general purpose, stack register, etc
- CPU scheduling information - priority, scheduling, queue pointers
- Memory-management information - memory allocated to the process
- Accounting information - CPU time used, clock time elapsed since start, time limits
- I/O status information - I/O devices allocated to process, list of open files
![[Pasted image 20240208154330.png]]

### Notes
- Each process has a **process control block** which keeps track of the register values so that when the CPU is taken away from the process, the process can remember where it was when it gets the CPU back

## Process Representation in Linux
![[Pasted image 20240208154739.png]]

## CPU Switch From Process to Process
![[Pasted image 20240208154920.png]]

![[Pasted image 20240208155336.png]]
### Notes
- **KAS**: Kernel Address Space
- Reason for saving state into PCB before anything is because the *kernel* needs the registers immediately after to perform its tasks
- Within the 3 dots in the above CPU Switch, the OS is doing a variety of things
	- State changes of processes
	- User mode to Kernel Mode and vice versa to processes
	- Updates *ready* queue with program
	- Invokes CPU Scheduler
	- Program counter is updated
- When I/O completes, the I/O buffer gets copied to user process address space
- 