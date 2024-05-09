# Thrashing P2
## Random Note
![[Pasted image 20240505174555.png]]
- No idea why, but apparently every iteration access 4 pages so LRU with 4 frames has 4/4000 page faults or 1/1000

## Thrashing Cont.
![[Pasted image 20240505174909.png]]
- Degree of Multiprogramming = Number of processes that are loaded into memory
- CPU Utilization goes up as DoM goes up because the CPU scheduler will have more choices on which process to give the CPU to while another is waiting for I/O
- Thrashing occurs because at some point where there are *N* processes, the processes start to spend most of their time in the waiting state waiting for frames to be switched in and out of disk to memory

## Demand Paging and Thrashing
![[Pasted image 20240505175153.png]]
![[Pasted image 20240505175359.png]]
- Example of two working sets and 2 localities 

![[Pasted image 20240505175431.png]]
- Example of two working sets overlapping

## Working-Set Model
![[Pasted image 20240505175509.png]]
- Solutions to thrashing
	- Suspend or swap out one of the processes

## Page-Fault Frequency
![[Pasted image 20240505175937.png]]
- System can count how many page faults and memory accesses to calculate page fault rate
	- If page fault rate too high (above upper bound), system needs *more* frames
	- If page fault rate low (below lower bound), system needs *less* frames
	- Between lower bound and upper bound is *acceptable state*

## Working Sets and Page Fault Rates
![[Pasted image 20240505180207.png]]

## OS Example: Windows
![[Pasted image 20240505181212.png]]