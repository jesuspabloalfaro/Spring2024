# Process Synchronization - The Critical-Selection Problem
## Synchronization
- Code that modifies a *shared variable* is a **critical section** and must be handled carefully 

## Critical Section Problem
- Consider system of *n* processes
- Each process has a **critical section** segment of code
	- Process may be changing common variables, updating table, writing file, etc
	- When one process in *critical section*, no other may be in its *critical section*
- **Critical Section Problem**
	- Design a protocol to solve the above bullet points
- Each process must ask permission to enter critical section in **entry section**, may follow critical section with **exit section**, then **remainder section**

## Critical Section
![[Pasted image 20240222144521.png]]

## Solution to Critical-Section Problem
**Mutual Exclusion**
- If process P$_i$ is executing in its critical section, then no other processes can be executing in their critical sections
	- Want only **one** process in the *critical section at a time*. 
**Progress**
- If no process is executing in its critical section and there exists some process that wish to enter their critical section, then the selection of the processes that will enter the critical section next cannot be postponed indefinitely, and only those processes that are not in their remainder section are considered
	- If there is no progress, then we are in a **deadlock**
**Bounded Waiting**
- A bound must exist on the number of times that one processes are allowed to enter their critical sections after a process has made a request to enter their critical sections after a process has made a request to enter its critical section and before that request is granted
	- Assume that each process executes at a nonzero speed
	- No assumption concerning **relative speed** of the *n* processes
	- If there is waiting, there is a possibility for the process to go into **starvation**
	- If a process is waiting, there is a limit on the number of times other processes access the critical section while the process is waiting

