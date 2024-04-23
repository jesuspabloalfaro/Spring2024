# Contiguous Memory Allocation
## Contiguous Allocation
![[Pasted image 20240422185120.png]]
- Each process has *one contiguous block of memory* that has all the code and data that constitutes that process
	- Does not give the system enough flexibility

![[Pasted image 20240422185231.png]]

## Hardware Support for Relocation and Limit Registers
![[Pasted image 20240422185359.png]]

## Multiple-Partition Allocation
![[Pasted image 20240422185426.png]]
- System will keep a list of *all allocated blocks* and a *list of free blocks* 
- When a process terminates, the allocated block is free'd and becomes a *hole*
- When new processes arrive, the system will check free memory (*holes*) to fit the processes needs

- Some schemes to allocate process memory to free holes
	- **First Fit** - Whichever block is found that fits the process needs first is allocated.
	- **Best Fit** - Whichever block is found that fits the process needs the *best* is allocated
	- **Worst Fit** - Whichever free block that has the *largest* hole will be allocated 



