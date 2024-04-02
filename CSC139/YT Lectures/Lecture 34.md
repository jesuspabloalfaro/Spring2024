# Examples from Real Systems
## Windows Synchronization
![[Pasted image 20240315031424.png]]
- Mutex lock is like a busy waiting lock. Doesn't work well because you waste CPU cycles waiting for condition
- Spinlock works well on multiprocessor system because one process can be spinlocked and the other processes can be making progress

## Linux Synchronization
![[Pasted image 20240315034127.png]]
- Pre-emptive means there is a timed interrupt that takes the CPU from a process

## Pthread Synchronization Examples
Mutex Locks vs Semaphores
![[Pasted image 20240315034653.png]]

## Transactional Memory
![[Pasted image 20240315034816.png]]
- **Transactions** in the context of a database is *a sequence of operations that must be done as a package*
	- **Cannot** do just a subset of package because database will be inconsistent. Either complete whole transaction or no transaction
	- In **this** context, its just like a database transaction where we have to do everything in the `atomic` function

## OpenMP
![[Pasted image 20240315035134.png]]