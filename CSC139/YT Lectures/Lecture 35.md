# CPU Scheduling Basic Concepts
## Basic Concepts
![[Pasted image 20240320212749.png]]
- During execution of `store`, the CPU may be *idle* and the **memory** is doing the work. However, in an *OS view*, this is **still considered CPU time**

## Histogram of CPU Bursts
![[Pasted image 20240320221120.png]]
- Average is 2ms CPU bursts
	- Hundreds of thousands of operations
- Rare to have CPU bursts *longer* than 8ms
	- Very long time for a process to go without I/O (e.g. reading from keyboard, accessing a file, etc)
- 1Ghz Processor can have (10^9) 1 billion CPU cycles per second
	- 10-100 is the average number of cycles per operation

## CPU Scheduling
![[Pasted image 20240320223549.png]]
- **Preemptive Scheduling**: Timed interrupts for CPU

## Dispatcher
![[Pasted image 20240320230647.png]]
- Implements scheduling decisions

## Scheduling Criteria
![[Pasted image 20240320231006.png]]
- **Short time quantum**
	- Pros
		- Responsive system due to each program being able to have the CPU faster
		- Multiple processes making progress due to time quantum expiring and switching between processes frequently
	- Cons
		- Turnaround time is longer due to kernel having more time on CPU

## Scheduling Algorthm Optimization Criteria
![[Pasted image 20240320232114.png]]