# Mutex Locks and Spin Locks
## Mutex Locks
- Simple solution to the *critical section problem*
- Protect a critical section by first `acquire()` a lock then `release()` the lock
	- Boolean variable indicating if lock is available or not
- Calls to `acquire()` and `release()` must be atomic
	- Usually implemented via hardware atomic instructions
- High level OS languages provide ways to synchronize threads and variables by using constructs
	- Locks
	- Semaphores
	- Monitors
- **Locking**
	- When a process is in a *critical section*, no other process may be in the critical section
		- Managed by the OS
	- Same as the `acquire()` function but the POSIX API uses `lock()` and `unlock()`
	- If a process *locks* a variable and another process tries to *lock* the **same** variable, the second process will not be able to lock and access the *critical section*
		- Second process will be placed in a *queue* and its state will be *waiting* but **NOT** in the *ready* *queue* so the CPU scheduler *cannot* select it for the CPU
- **Unlocking**
	- `unlock()` will check if there is a process waiting for that *semaphore* and pick a process and change its state from *waiting* to *ready*
	- *Make sure to use `unlock()` when doing exception handling in the case that a process terminates preemptively*
- **Implementation**
	- Spin Lock
		- **Busy Waiting**
		- *Use this when the critical section is short and not expected to take a long time. Not efficient if only single CPU.*
	- **Mutex Lock**

## acquire() and release()
![[Pasted image 20240226202930.png]]
- This is a **conceptual** design. This is **NOT** how it is actually implemented