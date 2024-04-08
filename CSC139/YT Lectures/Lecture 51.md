# Banker's Algorithm
## Data Structures for the Banker's Algorithm
---
![[Pasted image 20240407193511.png]]

## Example of Banker's Algorithm
---
![[Pasted image 20240407193529.png]]
- Convention is to take the **first** process who's needs can be satisfied with the resources available (in this example, it is P1)

![[Pasted image 20240407194414.png]]
## Example: P1 Requests (1,0,2)
---
![[Pasted image 20240407194332.png]]
- P4's request cannot be granted 
- P0's request cannot be granted
### New Data With P1 New Request
![[Pasted image 20240407194640.png]]
- The order will be the same as before P1's request

### Steps to check requests
- Change *Allocation* to fit Process request (**Add** *request* to *current Allocation*)
- Change *Need* based on new *Allocation* (**Subtract** *request* from *current Need*)
- Change *Available* based on new *Allocation* (**Subtract** *request* from *current Available*)
- Go through sequentially and see if any process's needs can be fulfilled with the new *Available* instances
	- If yes, **all** processes can
		- Safe State
	- If no, there is a >= one process that cannot fit the needs in the available instances
		- Unsafe State

### Assumptions
- We know all the needs for all the processes
- If a new process comes, the process will declare its maximum needs and the algorithm will be ran again
## Safety Algorithm
---
![[Pasted image 20240407195917.png]]

## Safety Algorithm Pseudo-Code
---
![[Pasted image 20240407200000.png]]

## Resource-Request Algorithm for Process $P_i$
---
![[Pasted image 20240407201132.png]]
