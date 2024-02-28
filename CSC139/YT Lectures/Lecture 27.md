# Semaphores
## Semaphore
- Synchronization tool that provides more sophisticated ways (than *Mutex locks*) for processes to synchronize their activities
- Semaphore ***S*** - integer variable
	- **Number of available instances of a resource**
- Can only be accessed via two indivisible (atomic) operations
	- `wait()` and `signal()`
		- Originally called `P()` and `V()`
		- Signal is called **post** in *Pthreads*

- Definition of the `wait()` operation
![[Pasted image 20240226233758.png]]
- *This is a concept of the real implementation*

- Definition of the `signal()` operation (*`post()` in POSIX*)
![[Pasted image 20240226233811.png]]
- 

![[Pasted image 20240226235636.png]]
- The process that is `waiting` for that semaphore will be placed in a *waiting* queue for that semaphore

## Semaphore Usage
- **Counting Semaphore**
	- Integer value can range over an *unrestricted* domain
- **Binary Semaphore**
	- Integer value can range only between 0 and 1
	- Same as a *mutex lock*
![[Pasted image 20240227000028.png]]

## Semaphore Implementation with no Busy Waiting
- With each semaphore there is an associated wait list (FIFO?)
- Each entry in a waiting queue has two data items
	- **Value** (of type *integer*)
	- **Pointer** to next record in the list
- Two Operations
	- **Block**
		- Place the process invoking the operation in the appropriate waiting queue
	- **Wakeup**
		- Remove one of processes from the waiting queue and place it in the ready queue
![[Pasted image 20240227000439.png]]

## Pthreads Synchronization Examples
![[Pasted image 20240227000554.png]]
