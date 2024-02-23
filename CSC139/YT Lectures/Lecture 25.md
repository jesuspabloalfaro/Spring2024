# Synchronization Hardware
## Synchronization Hardware
- Many systems provide hardware support for implementing the critical section code
- All solutions below are based on the idea of **locking**
	- Protecting critical regions via locks
- **Uniprocessors**
	- Could *disable* interrupts
	- Currently running code would execute without preemption
	- Generally too inefficient on *multiprocessor* systems bc you have to pass a message to all processors
- Modern machines provide special atomic hardware instructions
	- **Atomic**: Non-interruptible
	- Either test memory word and set value or swap contents of two memory words

## test_and_set Instruction
![[Pasted image 20240222214108.png]]

## Solution using test_and_set()
- Shared Bool variable `lock` init to *false*
![[Pasted image 20240222214310.png]]
- If CPU scheduling is unfair, it is possible for a process who's in the critical section to iterate in an *unbounded* number of times
	- Depends on how many CPU cycles the all processes get
- **Starvation vs Deadlock**
	- Starvation means there is no limit to how long the process can wait
	- Deadlock means there is literally waiting *forever*

## compare_and_swap Instruction
![[Pasted image 20240222215026.png]]

## Solution using compare_and_swap
![[Pasted image 20240222215116.png]]
- 0 is *unlocked*
- 1 is *locked*
- Waiting is *unbounded* here as well

## Bounded-waiting Mutual Exclusion with test_and_set
![[Pasted image 20240222215211.png]]
- When a process is done with the critical section, it will check on any other processes to see if any are *waiting*. 
	- If it finds any *waiting* processes, it will give it the critical section
	- If there are *no* other processes that are *waiting*, **only then** will the process retake the critical section
		- Implemented using the `waiting` flag
- Setting `key` to *true* ensures that we do `test_and_set()` at least once
- Checks in a circular pattern forwards for the first process that has `waiting` set to *true*
	- If *all* are *false*, it will take the critical section again