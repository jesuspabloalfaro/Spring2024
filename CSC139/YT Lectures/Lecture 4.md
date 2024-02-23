# Multiprogramming vs Time Sharing
## Comparisons
- **Multiprogramming (Batch System)** needed for efficiency
	- Single user cannot keep *CPU* and *I/O* devices busy at all times
	- *Multiprogramming* organized jobs (code and data) so *CPU* always has one to execute
	- One job selected and run via *job scheduling*
- **Timesharing (multitasking)**: Logical extension in which *CPU* switches jobs so frequently that users can interact with each job while it is *running*, creating *interactive* computing
	- *Response time* should be <1 second
	- Each user has at least one program executing in memory -> *Process*
	- If several jobs ready to run at the same time -> *CPU Scheduling*
	- If *processes* don't fit in memory, *swapping* moves them in and out to run
	- *Virtual memory* allows execution of *processes* not completely in memory

### Notes
- If a process goes into the *waiting state*, *operating system* will give *CPU* to another *process* in *multiprogramming*
- In *timesharing* then the kernel will keep switching between *processes* even if the process doesn't need to *wait*, the *operating system* will give the *CPU* to another *process*
- User feels like *timesharing* is faster but in reality, multiprocessing is faster(?) in certain circumstances. Really depends on how fast *I/O* is.
	- Timesharing is good for user responsiveness
	- Multiprogramming is good for process throughput
- Timing Diagrams on *CPU* for *multiprocessing and timesharing*
	- *Multiprocessing*:
		- Kernel initialized
		- Kernel give CPU to process P1
		- Process P1 initiates an interrupt, giving control back to the kernel
	- *Timesharing*: 
		- Kernel initialized
		- Kernel gives CPU to process P1
		- Kernel takes CPU from process P1 and gives it to process P2
			- Kernel gives process P1 a certain condition (like time which uses a *time interrupt*) to run before it takes back control
		- Kernel takes CPU from process P2 and gives it to some other process (can be process P1)
	- *Multiprocessing* waits for interrupt to give *kernel* control while *timesharing* can just take *CPU* regardless of process state
![[Pasted image 20240122181118.png]]
- Hardware needs a way to distinguish between the kernel and a user process.
	- Implemented by *dual-mode*
	- *Dual-mode* uses a *mode bit* to check if the process is the kernel

## Interrupts and Timers
- Timer to prevent infinite loop/process hogging resources
	- Timer is set to interrupt the computer after some time period
	- Keep a counter that is decremented by the physical clock
	- Operating system sets the counter (privileged instruction)
	- When counter reaches zero, generate an interrupt
	- Set up before scheduling process to regain control or terminate program that exceeds allotted time

## Operating-System Operations
- **Interrupt Driven**: 
	- Hardware and Software
	- Hardware interrupt by one of the devices
	- Software interrupt (*exception* or *trap*)
		- Software error (e.g. division by zero, invalid memory access, etc)
		- Request for operating system service (*system call*)
		- Time slice (quantum) of a process expires
- An *interrupt service routine* is provided to deal with the interrupt
- Interrupts are used to prevent processes from modifying each other or the operating system
- **Dual-Mode**: Operation that allows OS to protect itself and other system components
	- *User mode* and *kernel mode*
	- *Mode bit* provided by hardware
		- Provides ability to distinguish between user code and kernel code
		- Some instructions designated as *privileged*, only executable in kernel mode
		- System call changes mode to kernel, return resets it to user
	- Lack of Hardware Supported dual mode can cause serious problems (e.g. DOS on Intel 8088)
	- Some modern machines support multiple modes (e.g. third mode for virtual machine manager)

# Transition from User to Kernel Mode
![[Pasted image 20240122183038.png]]

### Notes
- 4 types of interrupts
	- Exceptions
	- I/O Completion
	- Timed interrupts
	- System call