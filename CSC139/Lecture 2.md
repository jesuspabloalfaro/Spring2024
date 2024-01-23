# CPU, I/O, and Interrupts
---
## Computer-System Operation
- *I/O* devices and the *CPU* can execute concurrently
- Each device controller is in charge of a particular device type
- Each device controller has a local buffer
- *CPU* moves data from/to main memory to/from local buffers
- *I/O* is from the device to local buffer of controller
- Device controller informs *CPU* that it has finished its operation by causing an *interrupt*

### Notes
- **Running State***: Refers to *process* being in the *CPU*
- **Waiting State**: Refers to a *process* waiting for something (e.g. *I/O* device)
- **Ready State**: Refers to a *process* being ready to take the *CPU*. A *process* marked as *ready* does not guarantee the *CPU* will take it right away.
- **Exception**: A type of *interrupt*. Generated if a *process* does something wrong (invalid operations), runs into a stack overflow, floating point overflow, or out of bounds memory access. 
- **Device Controller**: Hardware based. Electronic circuit that controls the device.
- **Device Driver**: Software based. Controls the device from a piece of software that belongs to the *operating system*. Talks to the *Device Controller*
- Transferring data from the *I/O* devices local buffer and the main computer *memory* is done by the *CPU*.
	- *I/O* device will send the *CPU* an *interrupt* that it has completed the transfer of data.
- **CPU Scheduler**: Selects what process will get the *CPU* next. Selects based on scheduling algorithm (In CH.6)
- Timing Diagram when system starts:
	- *Bootstrap Program* starts the *kernel*
	- *Kernel* selects process to get the *CPU*
		- Invokes *CPU Scheduler*
	- *Process* requests* I/O* from kernel via *System Call*
	- *System Call* implemented by *interrupt* 
		- **Whenever an interrupt is created, control is given to the** *kernel* **because the** *Interrupt Service Routine* **is invoked that services the interrupt** 
	- *I/O* device may be unavailable since the *I/O* device has a queue filled with other requests. If queue is empty, then it can service the *process* immediately. 
	- If *process* is waiting, *CPU scheduler* will task the *CPU* another *process* 
	- When *I/O* device completes request, it will notify the *kernel* by generating an *interrupt*.
	- *Kernel* regains *running state* in *CPU*.
	- *CPU Scheduler* will decide which *process* will get the CPU* next. This includes *processes* that are now marked *ready* instead of *waiting*.
	- Assume *process P2* wants to access *I/O* while *process P1* is waiting. 
		- *Process P2* will try to access an empty queue *I/O* device or the one with the least amount of requests.
	- Assume *CPU Scheduler* decided to let *process P3* use *CPU*. 
![[Pasted image 20240122174629.png]]

## Common Functions of Interrupts
- **Interrupt Vector**: Contains the addresses of all the *service routines*
- **Trap or Exception**: A software-generated *interrupt* caused either by an error or a user request
- *Interrupt* transfers control to the *interrupt service routine* generally, through the *interrupt vector*.
- Interrupt architecture must save the address of the interrupted instruction
- An *operating system* is *interrupt driven*.