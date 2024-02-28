# Deadlocks, Starvation and Priority Inversion
## Deadlock and Starvation
- **Deadlock**
	- Two or more processes are waiting indefinitely for an event that can be caused by only one of the waiting processes
- Let *S* and *Q* be two semaphores init to 1
![[Pasted image 20240227001045.png]]
- This scenario results in a **deadlock** because both processes are holding both semaphores indefinitely

- **Starvation - Indefinite Blocking**
	- A process is not guaranteed to be removed from the semaphore wait list in which it is suspended
- **Priority Inversion**
	- Scheduling problem when lower priority process holds a lock needed by higher priority process
		- Solved via **priority-inheritance protocol**

![[Pasted image 20240227202821.png]]
- Intended Mechanic:
	- Process `M` has the CPU after time quantum expires while Process `L` has the CPU
- Unintended Mechanic:
	- If Process `M` becomes ready while Process `L` has the CPU, Process `M` will get the CPU after the time quantum expires and puts Process `L` in the *waiting* state even if its in the critical section
	- Process `H` is waiting for Process `M` even though it is a higher priority level
- Fix
	- If a high priority process is in the *waiting* state, *temporarily* boost the priority of Process `L` to **high** while Process `L` is in the critical section