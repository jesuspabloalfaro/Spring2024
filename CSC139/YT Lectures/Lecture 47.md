# Deadlock Characterization
## Deadlock Characterization
![[Pasted image 20240407113719.png]]

## Deadlock with Mutex Locks
![[Pasted image 20240407114224.png]]
- Deadlock Condition
	- If Thread 1 locks `first_mutex` and then loses the CPU then Thread 2 locks `second_mutex`. 
	- If there are *2 CPUs*, then its possible for Thread 2 to lock the `second_mutex` before Thread 1 can lock the `second_mutex`

## Resource-Allocation Graph
![[Pasted image 20240407114515.png]]
![[Pasted image 20240407114523.png]]
- **Resource-Allocation Graph**: Which processes have which resources

## Example of a Resource-Allocation Graph
![[Pasted image 20240407114635.png]]
- P1 is loading an instance of R2 while waiting for an instance of R1
- P2 is loading an instance of R1 while waiting for instance of R3
- P3 is loading an instance of R3
- R4 is not being used
- Do we have a deadlock?
	- No we do not have a deadlock because P3 is not waiting for anything. All processes will eventually make progress

## Resource Allocation Graph with a Deadlock
![[Pasted image 20240407114927.png]]
- **Deadlock** because there is circular dependance. 
- P3 is waiting for *either* P1 or P2 to make progress so it can load the instance of R2 that P1 and P2 are loading

## Graph with a Cycle but No Deadlock
![[Pasted image 20240407115242.png]]
- If P4 finishes, P3 can load R2 and when P3 finishes, P1 can load R1 
- If P2 finishes, P1 can load R1 

## Basic Facts
![[Pasted image 20240407115500.png]]
- 