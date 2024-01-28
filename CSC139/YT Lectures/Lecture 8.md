# System Calls
## User Operating System Interface - CLI
- CLI or **command interpreter** allows direct command entry
	- Sometimes implemented in kernel, sometimes as special programs (Windows and Linux)
	- Sometimes multiple flavors implemented - **shells** (e.g. C-, Shell, Korn Shell, Bourne Shell)
	- Primarily fetches a command from user and executes it
	- Sometimes commands are built-in, sometimes they are just names of programs (used in Unix)
		- If the latter, adding new features doesn't require shell modification

## User Operating System Interface - GUI
- User friendly desktop metaphor interface
	- Usually mouse, keyboard, and monitor
	- **Icons** represent files, programs, actions, etc
	- Various mouse buttons over objects in the interface cause various actions (provide information, options, execute function, open directory (known as a **folder**)
	- Invented at Xerox PARC (1973)
- Many systems now include both CLI and GUI interfaces
	- Microsoft Windows is a GUI with CLI shell
	- Apple Max OS X is "Aqua" GUI interface with UNIX kernel underneath and shells available
	- Unix and Linux have CLI optional GUI interfaces (CDE, KDE, GNOME)

## System Calls
- Programming interface to the services provided by the OS
- Typically written in a high level language (C or C++)
- Mostly accessed by programs via a high level **Application Programing Interface (API)** rather than direct system call use. Why?
	- Portability
	- More convenient, as they hide system call details
- Three most common APIs are Win32 API for Windows, **POSIX** (Portable Operating System Interface) API for POSIX based systems (including virtually all versions of UNIX, Linux, and Mac OS X), and Java API for the Java virtual machine (JVM)
- *Note that the system call names used through this text are generic*
### Notes
- System call is a special kind of *function call*
	- **System calls** are *interrupt based* and when an application makes a system call, CPU control is returned back to the kernel virtually make it so that the hardware is in *kernel mode*
- Typically, we do not interact with system calls directly. They are wrapped with APIs because:
	- Convenience
		- API more user friendly and easier to use
		- Fewer parameters
		- Wrapper for one or more system calls
	- Portability

## Example of System Calls
- System call sequence to copy the content of one file to another file
![[Pasted image 20240127173951.png]]

## Example of Standard API
![[Pasted image 20240127174213.png]]

### Notes
- Dynamically allocate the buffer when making a system call
- File descriptor comes from using the function **open()** where you pass the file name and returns the file descriptor
	- Make sure to **close()** once you are done

## System Call Implementation
- Typically, a number associated with each system call
	- **System call interface**: Maintains a table indexed by these numbers
- The system call interface invokes the intended system call in OS kernel and returns status of the system call and any return values
- The caller need know nothing about how the system call is implemented
	- Just needs to obey API and understand what OS will do as a result call
		- Most details of OS interface hidden from programmer by API
			- **Runtime Support Library**: Set of functions built into libraries included with compiler
			- Managed by *Runtime Support Library*

## API - System Call - OS Relationship
![[Pasted image 20240127175001.png]]
### Notes
- System call interface is just a giant table
	- Implementation is a table indexed by the system call number
	- For each system call number there is an entry with the address of the corresponding function within the system that implements that
	- System calls are implemented in *kernel mode* but the call (the API) is issued in *user mode*.

## System Call Parameter Passing
- Often, more information is required than simply identity of desired system call
	- Exact type and amount of information vary according to OS and call
- Three general methods used to pass parameters to the OS
	- Simplest: Pass the parameters in registers
		- In some cases, may be more parameters than registers
	- Parameters stored in a block, or table, in memory, and address of block passed as a parameter in a register
		- This approach taken by Linux and Solaris
	- Parameters placed, or *pushed* onto the *stack* by the program and *popped* off the stack by the operating system
	- Block and stack methods do not limit the number or length of parameters being passed

### Notes
- When utilizing the push pop method, the *caller* pushes the parameters while the *callee* pops the parameters and in this example, the *callee* is the operating system

## Types of System Calls
- Process control
	- create process, terminate process
	- end, abort
	- load, execute
	- get process attributes, set process attributes
	- wait for time
	- wait event, signal event
	- allocate and free memory
	- Dump memory if error
	- **Debugger** for determining *bugs, single step* execution
	- **Locks** for managing access to shared data between processes
- File Management
	- create file, delete file
	- open, close file
	- read, write, reposition
	- get and set file attributes
- Device Management
	- request device, release device
	- read, write, reposition
	- get device attributes, set device attributes
	- logically attach or detach devices
- Information Maintenance
	- get time or date, set time or date
	- get system data, set system data
	- get and set process, file, or device attributes
- Communications
	- create, delete communication connection
	- send, receive messages if *message passing model* to *host name* or *process name*
		- From *client* to *server*
	- **Shared memory model** create and gain access to memory regions
	- transfer status information
	- attach and detach remote devices
- Protection
	- Control access to resources
	- Get and set permissions
	- Allow and deny user access

## Example of Windows and Unix System Calls
![[Pasted image 20240127180351.png]]

## Standard C Library Example
- C program invoking `printf()` library call, which calls `write()` system call
![[Pasted image 20240127180528.png]]
### Notes
- `printf()` function is implemented as a *system call* because it is accessing the `write()` function which is a kernel mode function

## System Programs
- System Programs provide a convenient environment for program development and execution. They can be divided into:
	- File manipulation
	- Status information such as date, time, memory available, etc
	- Programming language support
	- Program loading and execution
	- Communications
	- Background Services
- Most users' view of operating system is defined by system programs, not the actual system calls
- **File Management**: Create, delete, copy, rename, print, dump, list, and generally manipulate files and directories
- **Status Information**
	- Some ask the system for info - date, time, amount of available memory, disk space, number of users
	- Others provide detailed performance, logging, and debugging information
	- Typically, these programs format and print the output to the terminal or other output devices
	- Some systems implement a *registry*
		- **Registry**: Used to store and retrieve configuration information
- **File Modification**
	- Text editors to create and modify files
	- Special commands to search contents of files or perform transformations of the text
- **Programming Language Support**: Compilers, assemblers, debuggers and interpreters sometimes provided
- **Program Loading and Execution**: Absolute loaders, relocatable loaders, linkage editors, and overlay loaders, debugging systems for higher level and machine language
- **Communications**: Provide the mechanism for creating virtual connections among processes, users, and computer systems
	- Allow users to send messages to one another's screens, browse web pages, send electronic mail messages, log in remotely, transfer files from one machine to another
- **Background Services**
	- Launch at boot time
		- Some for system startup, then terminate
		- Some from system boot to shutdown
	- Provide facilities like disk checking, error logging, printing
	- Run in user context not kernel context
	- Known as *services, subsystems, daemons*
### Notes
- **System Programs**: Programs that belong to the operating system but are not part of the kernel
	- Kind of like an extension of the operating system
	- May run in user mode
	- May involve many *system calls*
- Text editor is an example are system programs and make lots of system calls but run in *user mode*
	- Uses *loaders*. You actually click it in the GUI or invoke it in the CLI
- Some examples of background services that stay from system boot to shutdown are
	- Programs to check on memory
- 