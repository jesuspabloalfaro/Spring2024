# Shared Memory and the Bounded-Buffer Problem
## Interprocess Communication - Shared Memory
- An area of memory shared am`ong the processes that wish to communicate
- Typically shared memory resides in the address space of the process creating the shared memory segment
- The communication is under the control of the user processes not the operating system
- Major issue is to provide mechanism that will allow the user processes to synchronize their actions when they access shared memory
- Synchronization is discussed in great details in Chapter 5
- Shared memory can be faster than message passing because the latter is implemented by system calls (there is more kernel intervention with message passing)
- Shared memory is not necessarily faster than message passing on systems with several processing cores, due to cache coherency issues
## Producer-Consumer Problem
- Paradigm for cooperating processes, *producer* process produces information that is consumed by a *consumer* process
	- **Unbounded-Buffer**: Places no practical limit on the size of the buffer
		- Consumer must wait if buffer is empty, but producer never has to wait
	- **Bounded-Buffer**: Assumes that there is a fixed buffer size
		- Consumer must wait if buffer is empty
		- Producer must wait if buffer is full
![[Pasted image 20240213154203.png]]
### Notes
- Condition for empty: **in = out**
- Condition for full: **in+1 % buffer_size=out**

## Bounded-Buffer - Producer
![[Pasted image 20240213154324.png]]
### Notes
- This is called the **busy loop** because its always waiting for the condition to be false (which it wont be ever)

## Bounded-Buffer - Consumer
![[Pasted image 20240213154439.png]]
### Notes
- Increments out in a **circular** manner

## Examples of IPC Systems - POSIX
- POSIX Shared Memory
	- Process first creates shared memory segment
```
shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666);
```
- Also used to open an existing segment to share it
- Set the size of the object
```
ftruncate(shm_fd, 4096);
```
- Map file to memory
```
ptr = mmap(0, 4096, PORT_WRITE, MAP_SHARED, shm_fd, 0);
```
- Now the process could write to shared memory
```
sprintf(ptr, "Writing to shared memory");
```

## IPC POSIX Producer
![[Pasted image 20240213154846.png]]

### Notes
- Producer for **Hello World**
- `void*` is a *generic* pointer that can be *type-casted* to any type
	- In this example, `*ptr` is being type-casted to an array (memory map)

## IPC POSIX Consumer
![[Pasted image 20240213155056.png]]
### Notes
- Name of *shared* memory object in this example is `name`

## Interprocess Communication - Message Passing
- Mechanism for processes to communicate and to synchronize their actions
- **Message System**: Processes communicate with each other without resorting to shared variables
- IPC facility provides two operations
	- **send()**
		- send(*message*)
	- **receive()**
		- receive(*message*)
- The *message* size is either fixed or variable

## Assignment 1 Stuff
- Shared memory space model
![[Pasted image 20240213155313.png]]
- Need to change above code example to have *write* privileges as well because we are changing `out` in the header which modified by the *consumer*
