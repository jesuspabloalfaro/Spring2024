# The Bounded Buffer Problem P2
## Bounded Buffer Problem Cont.
### Semaphore Solution
![[Pasted image 20240314194238.png]]
![[Pasted image 20240314194433.png]]
### Busy Waiting Solution
![[Pasted image 20240314195200.png]]
- **Disadvantages**
	- wastes CPU cycles
	- only one process can increment/decrement the counter at a time (i.e. the producer and consumer.) 
		- what happens if we have multiple producers and consumers?
			- If one producer locks the critical section, then the consumers cannot increment their shared variable and vice versa

