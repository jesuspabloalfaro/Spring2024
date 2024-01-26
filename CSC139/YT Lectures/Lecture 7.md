# OS Services
## A View of Operating System Services
![[Pasted image 20240126134236.png]]

### Notes
- A user program will issue a *system call* to access a certain *operating system service*

## Operating System Services
- One set of operating system services provides functions that are helpful to the user
	- **User Interface**: Almost all operating systems have a user interface (UI)
		- Varies between *Command Line (CLI)*, *Graphical User Interface (GUI)*, *Batch*
	- **Program Execution**: The system must be able to load a program into memory and to run that program, end execution, either normally or abnormally (indicating error)
	- **I/O Operations**: A running program may require *I/O*, which may involve a file or an *I/O* device
	- **File System Manipulation**: The file system is of particular interest. Programs need to read and write files and directories, create and delete them, search them, list file information, permission management
	- **Communications**: Processes may exchange information, on the same computer or between computers over a network
		- Communications may be via shared memory (*Check assignment 1*) or through message passing (packets moved by the OS)
	- **Error Detection**: OS needs to be constantly aware of possible errors
		- May occur in the CPU and memory hardware, in I/O devices, in user program
		- For each type of error, OS should take the appropriate action to ensure correct and consistent computing
		- Debugging facilities can greatly enhance the user's and programmer's abilities to efficiently use the system

### Notes
- Reasons for limiting access to I/O devices to the operating system and **not** to user programs
	- Hide details of I/O devices from the application program
	- Application can just say they want to *read* from I/O and the operating system will handle all the low level details
	- Manage access and resolve conflicts
		- If he allow user programs to access I/O directly, there will be lots of conflicts