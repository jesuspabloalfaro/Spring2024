# Multiple-Processor Scheduling
## Multiple-Processor Scheduling
![[Pasted image 20240326203801.png]]

![[Pasted image 20240326205259.png]]
- CPU0 Starts P1 and loads data into main memory
	- Known as a **Cold Start**
- **Hardware** loads data from main memory into L1 cache
	- This means the process can load faster
- If OS decides to move P1 to CPU1
	- Another *Cold Start* occurs leading to performance degradation until hardware loads data into L1 cache
- If there are too many processes running on CPU0/1
	- There can be a cache storage issue since the cache has a limited amount of space
	- It is good practice to *load balance* processes between CPU's
- If there becomes an out-of-balance correlation between CPU's, the *CPU Scheduler* must rebalance the system
	- **Push Migration**
		- Detects a CPU is *under-utilized* and *pushes* processes onto that CPU
	- **Pull Migration**
		- Detects a CPU is *overloaded* and *pulls* processes onto another CPU
- *Load balancing* and *Processor Affinity* **conflict** with each other
	- Due to the fact that load balancing doesn't care if a process has its' data in a cache. It will migrate processes at will with the determining factor being its load 
	- Affinity cares about the processes data being in a cache. *Soft Affinity* will do its' best to keep that process on the CPU where its' data is being cached while *Hard Affinity* will **require** a process be on a certain CPU

## Multiple-Processor Scheduling - Load Balancing
![[Pasted image 20240326205216.png]]

## Multicore Processors
![[Pasted image 20240326205230.png]]
![[Pasted image 20240326205434.png]]
- *CPU Scheduler* don't care if they are on the same chip or different chip. Just care about how *many* CPU's there are.
- Hardware Threads: Two cores on the same chip but each core has multiple threads 

## Multithreaded Multicore System
![[Pasted image 20240326205446.png]]
- Multithreads allow for the most efficient way of processing data since while one thread is waiting on memory, another thread can make progress with its computation
- 