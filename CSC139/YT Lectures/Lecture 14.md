# Context Switching
## Addition of Medium-Term Scheduling
- **Medium-Term Scheduler**: Added if degree of multiprogramming needs to be decreased
	- Remove process from memory, store on disk, bring back in from disk to continue execution: **swapping**
	- Reasons: Improving the mix or freeing memory
![[Pasted image 20240208163749.png]]

## Context Switch
- When CPU switches to another process, the system must *save the state* of the current process and load the *saved state* for the new process via a **context switch**
- **Context** of a process represented in the PCB
- Context-switching time is overhead; the system does no useful work while switching
- Time depends on OS complexity and design (e.g. memory management techniques)
- Time depends on hardware support
	- Memory speed, number of registers, existence of special instructions, such as a single instruction to load and store all registers
	- Some hardware provides multiple sets of registers per CPU
- Typical switching time is a few milliseconds
![[Pasted image 20240208165015.png]]
### Notes
- PCB's are stored in memory and the register values, program counter, and process states are all transferred to the CPU when context switching occurs
- Context switching is hardware dependent, as hardware determines how fast the memory can be copied to the CPU

## Multitasking in Mobile Systems
- Some mobile systems (e.g. early versions of iOS) allow only one user process to run, others suspended
- iOS 4 allows:
	- Single *foreground* process - controlled via user interface
	- Multiple *background* processes - in memory, running but not on display, and with limits
		- Limits include short task, receiving notification of events, specific long-running tasks like audio playback
		- Limitation due to battery life and memory usage concerns
- Android runs foreground and background with fewer limits
	- Background process uses a *service* to perform tasks
	- Service has no user interface, little memory usage
