# Process Creation and Termination
## A Tree of Processes in Linux
![[Pasted image 20240208201006.png]]

### Notes
- Almost all processes are children of another process

## Process Creation 
- Address Space
	- Child duplicate of parent
	- Child has a program loaded into it
- UNIX examples
	- **fork()** system call creates a new process
	- **exec()** system call used after a **fork()** to replace the process's memory space with a new program
	- Child inherits privileges, scheduling attributes and other resources (open)
![[Pasted image 20240208201756.png]]
![[Pasted image 20240208203032.png]]
![[Pasted image 20240208203239.png]]
![[Pasted image 20240208203252.png]]
### Notes
- Producer and Consumer communicate through a *shared memory block*
- Producer launches the Consumer
- On single CPU with a single core, there is context switching between the Producer and Consumer running *concurrently*
	- If there is more cores, they would run *parallelly*
- Parent and Child have *different* address spaces
- Parent and Child run the same code (unless `exec` is called specifying a specific file path)

## Process Termination
- Process executes last statement and then asks the operating system to delete it using **exit()** system call
	- Return status data from child to parent (via **wait()**)
	- Process's resources (memory, files, I/O) are deallocated by operating system
	- Process entry in the process table remains until parent calls wait
- Parent may terminate the execution of children processes using a system call like **TerminateProcess()** on Windows. Some reasons for doing so:
	- Child has exceeded allocated resources
	- Task assigned to child is no longer required
	- The parent is exiting and the operating system does not allow a child to continue if its parent terminates
- Some operating systems do not allow child to exist if its parent has terminated. If a process terminates, then all its children must also be terminated
	- **Cascading Termination**: All children, grandchildren, etc are terminated
	- Termination is initiated by the operating system
- The parent process may wait for termination of a child process by using the **wait()** system call. The call returns status information and the pid of the terminated process.
	- **pid = wait(&status);**
- If process terminates but no parent waiting (has not invoked **wait()**) process is a **zombie**
- If process terminates but parent terminated without invoking **wait()**, process is an **orphan**
	- Unix and Linux assign the *init* process as the new parent
### Notes
- Example of a *child* process becoming a *zombie*
![[Pasted image 20240208204912.png]]

## Multiprocess Architecture - Chrome Browser
- Many web browsers ran as single process (some still do)
	- If one website causes trouble, entire browser can hang or crash
- Google Chrome Browser is *multiprocess* with 3 different types of processes
	- **Browser**: Process manages user interface, disk, and network I/O
	- **Renderer**: Process renders webpages, deals with HTML and JavaScript. A new renderer created for each website opened
	- **Plug-in**: Process for each type of plug-in (e.g. Flash, QuickTime, etc)
## Interprocess Communication
- Processes within a system may be **independent** or **cooperating**
- *Cooperating* process can affect or be affected by other processes, including sharing data
- Reasons for cooperating processes:
	- Information Sharing
	- Computation speedup
	- Modularity
	- Convenience
- Cooperating processes need **interprocess communication (IPC)**
- Two models of *IPC*
	- **Shared Memory**
	- **Message Passing**
### Notes
- 