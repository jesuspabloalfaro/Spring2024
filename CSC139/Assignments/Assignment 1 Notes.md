## Overview
- Header should include the following
	- bufferSize
	- itemCount
	- in
	- out
- bufferSize and itemCount relation
	- itemCount must be *greater* than the bufferSize
	- bufferSize should always be n-1. Meaning if we have a bufferSize of 10, we only use 9 spaces in the buffer and the buffer is considered **full**
- Parent and Child will be running in *parallel*
- We always write to the shared memory buffer because if the consumer changes something, then the producer will not know about it if its not in the shared memory buffer (and vice versa)
	- Utilize the `SetIn` `SetOut` etc functions to set the shared memory buffer variables to that of the producer. Do the same to *get* the shared memory buffer variables uing the `GetIn` `GetOut` etc.

## Code Review - Producer
- `randSeed`: a random int that will be used for the random number generator
- Producer is *parent* that *forks* consumer which is *child*
- `initShm`: A function that creates shared memory object. We need to use 3 api's
	- shm_open()
		- Creates shared memory objects
	- ftrucate
		- sets the size of the shared memory object
	- mmap
		- maps shared memory object to a pointer in the pointer in the producers shared memory address space
			- pointer is `gShmPtr`
![[Pasted image 20240218185124.png]]
- We can assume that the `bufferSize` will be *greater* than 1
	- **Set a check for this**
- There are setters and getters for each field in the header
- There is a function provided to write an item at a given index in the body of the buffer (`WriteAtBufIndex`)
- There is a function provided to read an item as well (`ReadAtBufIndex`)
	- The `indx` variables in the write and read functions is going to the the `i` variable in our loop from the consumer
![[Pasted image 20240218190939.png]]

## Code Review - Consumer
- Will call the same 2 api's as the Producer
	- shm_open()
	- mmap
		- Maps to a pointer (NOT `gShmPtr`, any name works but this)
		- Will be set in the address space of the *consumer* process
- We can tell the OS to map the producer and the consumer to the same object by using shm_open() and passing the same *object name* to both calls of shm_open(). The object name *must* be `OS_HW1_jesuspablo_alfaro`
- Consumer will read the header to check the `bufferSize` and utilize that in a loop to read from 1-`bufferSize`
![[Pasted image 20240218191258.png]]
- We change the `in` value from the *producer* and the `out` value from the *consumer*

## Assignment Notes For Coding
### Test Cases
- itemCount < bufferSize
- itemCount > bufferSize
- itemCount == bufferSize
- bufferSize needs to be between 2-480
	- Print appropriate error message and terminate
- itemCount needs to work for any number > 0.
	- If itemCount is much greater than bufferSize, we need this to work
### Compile Instructions
- `gcc producer.c -lrt -o producer`
- `gcc consumer.c -lrt -o consumer`
### Command Line Arguments
- Producer Takes 3 CLI Arguments
	- **buffSize**: Size of the buffer. Cannot exceed 480
	- **itemCount**: The number of items that are within the buffer body. Must be greater than 0
	- **randSeed**: Random int value for seeding our random number generator
### Limits
- Shared memory block is a fixed size of 4K
- The producer must generate itemCnt random integers in the range 4 to 2200.
	- Can use `GetRand()` to do so
- The key point is that when the bounded buffer is full, the producer must wait until the consumer has consumed at least one item.

### Producer
- Calls function `InitShm()` to create shared memory block
- Initilizes header field values
- Forks child process (consumer) 
- Calls `Producer()` to generate items and write to bounded buffer

### Consumer
- Opens and maps shared memory block 
- Reads header field values
- Reads all items written by producer to the shared memory block

### Noteable Items To Do
- Whenever you read any of the shared variables (in and out), you must read the latest value from the shared buffer using the provided GetIn() and GetOut() functions.
- Whenever you update any of the shared variables (in and out), you must update their values in the shared buffer using the provided SetIn() and SetOut() functions.
- Reading from and writing into the shared buffer should be done using the provided ReadAtBufIndex() and WriteAtBufIndex() functions.
- Use the provided GetRand() function to generate a random number in the above-specified range.

## Submission Details
- Submit source files
- Producer and Consumer must be named `producer.c` and `consumer.c` respectively
- Header comment must include
	- Name
	- Section Number
	- OS you tested program on (including ECS env)

### Lecture 17 Recap
- Producer
	- Condition for buffer full
		- in = (in+1) % buffSize
	- Generates random numbers to populate buffer
	- Populates till n-1 of buffSize then consumer consumes
	- in = **index** of next item to produce
	- out = **index** of next item to consume
	- loop
		- producer creates value
		- value is set to shm (`GetIn()`)
		- increment *in* value
			- if buffer is full, set *in* to index 0
- Consumer
- Consumer will wait while buffer is empty
	- in = out
- loop
	- Consume (*out*)
	- set *out* (`GetOut()`)
	- increment *out*