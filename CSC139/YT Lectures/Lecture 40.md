# Multilevel Feedback Queue
## Multilevel Queue
![[Pasted image 20240326201508.png]]
- We use **RR** for foreground because it gives the most responsive feel
- We use **FCFS** for background because it requires the least amount of overhead

## Multilevel Queue Scheduling
![[Pasted image 20240326202104.png]]

## Multilevel Feedback Queue
![[Pasted image 20240326202128.png]]
- **Promotion** (Increasing priority of process) Criteria
	- Shorter CPU Bursts (*SJF*) 
		- Will minimize waiting time
		- More interactive process (requires I/O more frequently)
		- *Note: Processes who don't use entire time quantum are typically under the Short CPU Burst category*
	- Aging
		- Longer the process is in the *Ready* queue, the more promotions we want to give it
- **Demotion** (Decreasing priority of process)
	- Long CPU Bursts

## Example of Multilevel Feedback Queue
![[Pasted image 20240326202823.png]]

## Thread Scheduling
![[Pasted image 20240326203218.png]]

## Pthread Scheduling AP
![[Pasted image 20240326203317.png]]
![[Pasted image 20240326203332.png]]
- **attr** can be used to set the scope of your process/thread