# Thread Creation and Cancellation
## Pthreads Example
![[Pasted image 20240222135016.png]]
![[Pasted image 20240222135436.png]]
- `pthread_create(...,function_name,....)`
	- You define `function_name` and this is where the thread will start executing
- Parent thread will execute from first line of code and the child thread will execute from the first line of whatever `function_name` is
- `pthread_t tid` is just an integer value
- `pthread_attr_t attr` is a set of attributes for the *child* thread 
- void pointers are *generic* meaning you can pass anything you want. not really a good practice but whatever
- `pthread_join` is basically a call to wait for the *child* thread to exit
	- This is also used for synchronization between threads because there is no reason to print the sum before the threads are finished completing the calculations
- **In Assignment 2, make sure to have `pthread_join` in a loop**

## Pthreads Code for Joining 10 Threads
![[Pasted image 20240222140619.png]]

## Windows Multithreaded C Program
![[Pasted image 20240222140659.png]]
![[Pasted image 20240222140719.png]]

## Implicit Threading
- Growing in popularity as numbers of threads increase, program correctness more difficult with explicit threads
- Creation and management of threads done by compilers and run-time libraries rather than programmers
- Two methods explored
	- **Thread Pools**
	- **OpenMP**

## Thread Pools
- Create a number of threads in a pool where they await work
- **Advantages**
	- Slightly faster if existing thread instead of creating new thread
	- Limits number of threads that exist at the same time
	- Separating task to be performed from mechanics of creating task means different strategies for running task
		- e.g. tasks could be scheduled to run after a delay/periodically
	- Windows API supports thread pools

## OpenMP
- Set of compiler directives and an API for C, C++, FORTRAN
- Provides support for parallel programming in shared-memory env
- **Parallel Regions**
	- Blocks of code that can run in parallel
![[Pasted image 20240222141549.png]]
![[Pasted image 20240222141554.png]]

## Thread Cancellation
- Terminating a thread before it has finished (e.g. multithreaded DB search)
- **Target Thread**
	- Thread to be canceled
- Two general approaches
	- **Asynchronous Cancellation**
		- Terminates the target thread immediately (difficulty reclaiming resources)
	- **Deferred Cancellation**
		- Allows the target thread to periodically check if it should be cancelled and terminates itself cleanly
- Asynch cancellation *not* recommended in Pthread documentation
![[Pasted image 20240222141824.png]]
- Invoking thread cancellation requests cancellation but actual cancellation depends on *thread state*
- If thread has cancellation disabled, cancellation remains pending until thread enables it
- Default type is **deferred**
	- Cancellation only occurs when thread reaches **cancellation point**
		- Invoke `pthread_testcancel()`
		- Then invoke **cleanup handler** if there is a cancellation request

## Thread-Local Storage
- **Thread-local Storage (TLS)**
	- Allows each thread to have its own copy of data
- Different from local variables
	- Local variables visible only *during single function invocation*
	- **TLS** visible *across function invocations*
- Similar to `static` data unique to each thread
- Supported in Pthreads, Windows, and JAVA

## Windows Threads
- Implements **one-to-one** mapping, kernel-level
- Each thread contains
	- **A thread id**
	- **Register set representing state of processor**
	- **Stack**
	- **Private data storage area** used by *runtime libraries* and *dynamic link libraries (DLLs)*
- The register **set**, stack, **and** **private storage** area are known as the **context** of the thread

## Linux Threads
- Linux refers to them as **tasks** rather than **threads**
- Thread creation is done through `clone()` system call
- `clone()` allows child task to share address space of parent task (*process*)
	- Flag control behavior
![[Pasted image 20240222142637.png]]
- `struct task_struct` points to process data structures (shared or unique)

