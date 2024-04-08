# Deadlock Prevention
## Methods for Handling Deadlocks
![[Pasted image 20240407115612.png]]

## Deadlock Prevention
![[Pasted image 20240407115807.png]]
![[Pasted image 20240407120226.png]]
- Reasons why Deadlock Prevention is not practical
- Mutual Exclusion
	- Semaphores and locks exist for the purpose of mutual exclusion so taking them out defeats the purpose
- Hold and Wait
	- Poor utilization of resources (making processes hold resources they do not need for X amount of time)
	- Can cause starvation
- No Preemption


## Deadlock Example
![[Pasted image 20240407120437.png]]
- If we force the locking to go in order, we can eliminate deadlocks because it will be impossible for processes to hold the resource each other needs

## Deadlock Example with Lock Ordering
![[Pasted image 20240407120614.png]]
- Deadlock possible since we are going from A to B and B to A. We want them to go in the **same** order

