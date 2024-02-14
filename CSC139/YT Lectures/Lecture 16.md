# Inter-process Communication
## Interprocess Communication
- Processes within a system may be *independent* or *cooperating*
- Cooperating process can affect or be affected by other processes, including sharing data
- Reasons for cooperating processes
	- Information sharing
	- Computation speedup
	- Modularity
	- Convenience
- Cooperating processes need *interprocess communication (IPC)*
- Two models of IPC
	- Shared memory
	- Message passing
## Communications Models
![[Pasted image 20240213151946.png]]

### Notes
- Message Passing
	- Messages are maintained and managed by the kernel
	- Everything goes through the kernel
- Shared Memory
	- One process created a *shared memory block* that physically belongs to the address space of the process who creates it
		- Special memory block that can be accessed by multiple system processes
	- System gives other processes access to the shared memory block instead of managing the memory themselves
	- Faster than message passing because less context switching
		- Can be slower in certain cases in multiprocessor systems due to cache coherence 
