# Real-Time Scheduling
## Real-Time CPU Scheduling
![[Pasted image 20240331203453.png]]
- **Hard Real-Time System**: Certain deadline for processes. If process doesn't complete on time, system will fail. Usually in embedded systems
- **Soft Real-Time System**: Supports real-time priority without a defined deadline for each process. Usually general purpose computers (desktops, laptops, servers, etc)
	- **Needs**: Priority-based *preemptive* scheduler
		- Preemptive so you can preempt the current process and give the CPU to a real time process that has a higher priority level

![[Pasted image 20240331203716.png]]

## Priority Based Scheduling
![[Pasted image 20240331204014.png]]
- **Periodic Processes**: Processes that have CPU bursts arriving on a regular basis with a certain period. i.e. CPU bursts arriving periodically.
- Deadline **cannot exceed** *P* but **must exceed** *T* 

## Rate Monotonic Scheduling
![[Pasted image 20240331204344.png]]
- Think of *T* as being the time period where a new CPU burst of process spawns
- Order of system operations
	- P1 gets CPU because it has a higher priority
	- P1 loses CPU because the first burst finishes at time 20
	- P2 gets CPU because it is the only process in the ready queue
	- P1 gets put back in the ready queue in preparation for the second CPU burst
	- P2 is in the middle of its first CPU burst but P1's second CPU burst arrives at time 50
		- CPU Scheduler will give the CPU to P1 because it *preempts* P2
	- Second burst of P1 finishes at time 70
	- P2 gains CPU again and finishes the rest of the CPU burst at time 75
	- etc....

## Missed Deadlines with Rate Monotonic Scheduling
![[Pasted image 20240331205615.png]]
- *P1 doesnt get another burst at time 75 because it just finished and P2 was the only process in the ready queue*
- Order of system operations
	- P1 preempts P2 so P1 get the CPU first
	- P1 first CPU burst finishes at time 25
	- P2 gets CPU because its the only process in the ready queue
	- P2 starts first CPU burst and runs for 25 (time 50) but since P1 second CPU burst arrives and P1 preempts P2, CPU scheduler gives CPU to P1
	- P1 second CPU burst finishes at time 75
	- P2 gets CPU because its the only process in the ready queue
	- P2 finishes its first CPU burst at time 85 (35-25 = 10 ; time 75 + 10 = time 85)
		- P2 has deadline of time 80 but finishes at time 85, P2 misses deadline.

## Earliest Deadline First Scheduling (EDF)
![[Pasted image 20240331210517.png]]
- P1 gets the CPU first because the deadline of P1 is 50 and the deadline of P2 is 80
- Second burst of P1 comes at time 50
	- P2 keeps CPU because the deadline for the first burst of P2 is 30 and the deadline for the second burst of P1 is 100
- P2 finishes at time 60
- No processes in the ready queue at this time so P1 gets the CPU again for a third burst 
- Second burst of P2 comes at time 80 
	- P1 keeps CPU because deadline of third CPU burst of P1 is 150 and deadline for second CPU burst of P2 is 160
- Second CPU burst of P1 finishes at time 85
- P2 gets CPU because it is the only process in the ready queue
- Third burst of P1 comes at time 100
	- P1 gets the CPU because deadline for third burst of P1 is 150 and deadline for second burst of P2 is 160
- Third burst of P1 finishes at time 125
- P2 regains CPU to finish third CPU burst because it is the only process in the ready queue
- P2 finishes third CPU burst at time 145

## POSIX Real-Time Scheduling
![[Pasted image 20240331211709.png]]
- Soft real time scheduling

## POSIX Real-Time Scheduling API
![[Pasted image 20240331212047.png]]
- 