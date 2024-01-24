# The OS is Interrupt-Driven
## Interrupts and Timers Cont.
- Timer to prevent infinite loop/process hogging resources
	- Timer is set to interrupt the computer after some time period
	- Keep a counter that is decremented by the physical clock
	- Operating system sets the counter (privileged instruction)
	- When counter reaches zero, generate an interrupt
	- Set up before scheduling process to regain control or terminate program that exceeds allotted time

### Notes
- **Time quantum**: Period of time the *Operating System* gives to a *process* on the *CPU*. Determined by the *Operating System*. 
- **System Call**: A way for an application to ask the *Operating System* for a certain service that is *only* provided from the *Operating System*. Usually implemented using *interrupts*.
- 