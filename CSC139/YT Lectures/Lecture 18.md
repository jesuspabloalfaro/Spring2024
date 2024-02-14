# Other Inter-process Communication Methods
## Direct vs Indirect
![[Pasted image 20240213205620.png]]
### Notes
- Processes are *P, Q, R, S, T, etc*
- Processes can communicate with multiple mailboxes

## Message Passing cont.
- Implementation of communication link
	- Physical
		- Shared memory
		- Hardware bus
		- network
	- Logical
		- Direct or indirect
		- Synchronous or asynchronous
		- Automatic or explicit buffering
	- Our focus here is on the logical implementation
## Direct Communication
- Processes must name each other explicitly
	- **send**(*P, message*): Sends a message to process *P*
	- **receive**(*Q, message*): Receive a massage from process *Q*
- Properties of communication link
	- Links are established automatically
	- A link is associated with exactly one pair of communicating processes
	- Between each pair there exists exactly one link
	- The link may be unidirectional, but is usually bi-directional
## Indirect Communication
- Properties of communication link
	- Link established only if processes share a common mailbox
	- A link may be associated with many processes
	- Each pair of processes may share several communication links
	- Link may be unidirectional or bi-directional
## Synchronization
- Message passing may be either *blocking* or *non-blocking*
- **Blocking** is considered *synchronous*
	- **Blocking Send**: The sender is blocked until the message is received
	- **Blocking Receive**: The receiver is blocked until a message is available
- **Non-Blocking** is considered *asynchronous*
	- **Non-Blocking Send**: The sender sends the message and continues
	- **Non-Blocking Receive**: The receiver receives
		- A valid message, or
		- Null message
- Different combinations possible
	- If both send and receive are blocking, we have a *rendezvous*, and the solution to the producer-consumer problem becomes trivial
![[Pasted image 20240213205902.png]]
![[Pasted image 20240213205829.png]]
## Buffering
- Temporary queue of messages attached to the link
- Implemented in one of three ways
	- **Zero Capacity**: No messages are queued on a link. Sender must block until the recipient receives the message (*rendezvous*)
	- **Bounded Capacity**: Finite length of *n* messages. Sender must wait if and only if link is full
	- **Unbounded Capacity**: Infinite length. Sender never waits
## Communications in Client-Server Systems
- Sockets
- Remote Procedure Calls
- Pipes
## Sockets
- A **socket** is defined as an endpoint for communication
- Sockets allow low-level unstructured communicatio0n
- Co0ncatenation of IP Address and **port** - a number included at start of message packet to differentiate network services on a host
- The socket 161.25.19.8:1625 refers to port 1625 on host 161.25.19.8
- Communication takes place between a pair of sockets
- All ports below 1024 are *well known*, used for standard services (telnet, FTP, HTTP, etc)
- Special IP Address 127.0.0.1 (*loopback*) refers to system on which process is running
## Remote Procedure Calls
- Remote procedure call (RPC) abstracts procedure calls between processes on networked systems
	- Again uses ports for service differentiation
- **Stubs**: Client-side proxy for actual procedure on the server
- The client-side *stub* locates the server and *marshalls* the parameters (packages the parameters into a form that can be transmitted over a network)
- The server-side *stub* receives this message, unpacks the marshalled parameters, and performs the procedure on the server
- OS typically provides a *matchmaker* service to connect client and server
- Data representation handled via *External Data Representation (XDL)*
	- *Big-endian vs Little-endian*
### Notes
- **Marshall**: packages the parameters into a form that can be transmitted over a network
## Execution of RPC
![[Pasted image 20240213211359.png]]
### Notes
- For each procedure, there is a port
- Matchmaker is kind of like a lookup table

## Pipes
- Acts as conduit allowing two processes to communicate
- Issues
	- Is communication unidirectional or bidirectional?
	- In the case of two-way communication, is it half or full-duplex?
	- Must there exist a relationship (i.e. parent-child) between the communicating processes?
- **Ordinary Pipes**: Cannot be accessed from outside the process that created it.
	- Typically a parent process creates a pipe and uses it to communicate with child process that it created
- **Named Pipes**: Can be accessed without a parent-child relationship

## Ordinary Pipes
- Ordinary Pipes allow communication in standard producer-consumer style
- Producer writes to one end (the *write-end* of the pip)
- Consumer reads from the other end (the *read-end* of the pipe)
- Ordinary pipes are therefore *unidirectional*
- Constructed using `pipe(int fd[]);`
	- `fd[0]` is the *read end* and `fd[1]` is the *write end*
- Communicating processes use ordinary read() and write() system calls
- Required parent-child relationship between communicating processes
- Windows calls these *anonymous pipes*
![[Pasted image 20240213211912.png]]
## Named Pipes
- Named Pipes are more powerful than ordinary pipes
- Communication is *bidirectional*
- No parent-child relationship is necessary between the communicating processes
- Several processes can use the named pipe for communication
- Provided on both UNIX and Windows systems