# System Queues, CPU-Bound vs I/O-Bound Processes
## Threads
- So far, process has a single thread of execution
- A *Thread* is a lightweight process
- Consider having multiple program counters per process
	- Multiple locations can execute at once
		- Multiple threads of control -> *threads*
- Must then have storage for thread details, multiple program counters in PCB

## Process Scheduling
- Maximize CPU use, quickly switch processes onto CPU for time sharing
- **Process Scheduler**: Selects among available processes for next execution on CPU
- Maintains **scheduling queues** of processes
	- **Job Queue**: List of all processes in the system
	- **Ready Queue**: Processes residing in main memory, ready to execute
- **Device Queues**: Processes waiting for an I/O device
	- Each device has its own queue
- Processes migrate among the various queues

## Ready Queue and Various I/O Device Queues
![[Pasted image 20240208160711.png]]

### Notes
- Each device has its own queue

## Representation of Process Scheduling
- **Queueing Diagram**: Represents queues, resources, flows
![[Pasted image 20240208160927.png]]

### Notes
- If a process creates another process on a single CPU, the child process will be put in the *ready queue*

## Schedulers
- **Short-Term Scheduler** (**CPU Scheduler**):  Selects which process should be executed next and allocates CPU
	- Sometimes the only scheduler in a system (Unix and Windows)
	- Short-term scheduler is invoked *frequently* (milliseconds) -> (must be fast)
- **Long-Term Scheduler (Job Scheduler)**: Selects which processes should be brought into the ready queue (loaded into memory)
	- Long-term scheduler is invoked *infrequently* (seconds, minutes) -> (may be slow)
	- The long-term scheduler controls the **degree of multiprogramming** (number of processes in memory)
- Processes can be described as either:
	- **I/O Bound Process**: Spends more time doing I/O than computations, many short CPU bursts
	- **CPU Bound Process**: Spends more time doing computations; few very long CPU bursts
- Long-term scheduler strives for a good *process mix* to achieve balance

### Notes
- *Ready queue* is in memory
- We should focus on the *short term scheduler* which pulls from the *ready queue*
- Not all systems have a *long term scheduler*
- 