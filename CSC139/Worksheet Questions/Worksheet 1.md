1) The OS is interrupt-driven. Name the four kinds of interrupts studied in class, and explain how each interrupt drives the system? (Limit: 2 lines for each interrupt, 8 lines in total)
	1) **Exception**: Occurs when you divide by zero, stack overflow, invalid memory address, floating point overflow
	2) **I/O Completion**: The buffer is empty and has been copied down into main memory
	3) **Timed Interrupts**: The time quantum expired
	4) **System Calls**: Requests operating system services
2) The length of the time quantum (slice) given to each process by the scheduler of a time-sharing OS must be selected carefully. What's the negative consequence of making this time slice too long and what's the negative consequence of making it too short?
	1) Problem with too long time quantum (Limit: 2 lines)
		1) The system will feel less responsive to the user. If there are lots of processes, then a single process must wait for each other process to finish using their allocated time quantum.
	2) Problem with too short time quantum (Limit: 2 lines)
		1) There will be too much time wasted in the kernel context switching.