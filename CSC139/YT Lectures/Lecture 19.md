# Threads
## Motivation
- Multiple tasks within the application ca be implemented by separate threads
	- Update display
	- Fetch data
	- Spell checking
	- Answer a network request
- Process creation = Heavy Weight vs Thread creation = Light Weight
- Kernels and servers are usually *multithreaded*

### Multiprocessing vs Multithreading
- Multiprocessing
	- Every created process creates a ***new*** address space
	- Each process has its **own** data and its **own** code
- Multithreading
	- Creating a thread takes less time and resources
	- Threads are created within a process within ***one*** address space
	- Can share code and data between threads
		- **Global** and **static** variables. Variables *must* be synchronized in some way
		- Each thread has its own stack so **local** variables are separate
	- Threading an application can make the application feel **responsive**

## Single and Multithreaded Processes
![[Pasted image 20240221184416.png]]

## Client-Server Model with Threading
![[Pasted image 20240221184810.png]]
- There is a main thread that handles client connections
- When a client makes a request, a new thread is created to handle that request

## Benefits and Advantages of Multithreading
- **Responsiveness**
	- May allow continued execution if part of process is blocked, especially important for user interfaces
- **Scalability**
	- Process can take advantage of multiprocessor architectures

**Advantages of threads relative to processes**:
- **Resource Sharing**
	- Threads share resources of a process. Sharing global variables makes communication easier and faster than shared memory or message passing
- **Economy and Speed**
	- Cheaper than process creation
	- Thread context switching lower overhead than process context switching

## Concurrency vs Parallelism
![[Pasted image 20240221192859.png]]
![[Pasted image 20240221193418.png]]

## Multicore Programming
- **Parallelism**
	- Implies a system can perform more than one task simultaneously
- **Concurrency**
	- Supports more than one task making progress
	- Single processor/core, scheduler providing concurrency
- **Multicore**/**Multiprocessor**
	- Systems putting pressure on programmers.
	- Challenges include
		- Dividing activities
		- Data splitting
		- Data Dependency
		- Balance
		- Testing and Debugging

## Task and Data Parallelism
![[Pasted image 20240221194838.png]]
- The array listed on the right is for *Data Parallelism*

