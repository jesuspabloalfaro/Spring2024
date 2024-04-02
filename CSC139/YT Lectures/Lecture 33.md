# Monitors and a Monitor Solution to the Dining-Philosophers Problem
## Schematic View of a Monitor
![[Pasted image 20240314231537.png]]
- Can think of Monitor as an object
- Has a queue that guarantees only 1 thread/process can be in the monitor at any given time

## Condition Variables
![[Pasted image 20240314231726.png]]
- Can think of *Condition* variables as *semaphores inside the monitor*

![[Pasted image 20240315015156.png]]

## Monitor Solution to Dining Philosopher
![[Pasted image 20240315015333.png]]
![[Pasted image 20240315020636.png]]
- Each *phil* has its own state (Thinking, hungry, eating) in the array of `states`
- Each *phil* has its own `condition` variables
- We need to `signal()` when checking on neighbors 
- We check if `state[i]` is hungry because when the neighbors of the caller call `test()` it will see that no one is currently eating and change its state to `eating` even though it is not hungry. (We are assuming *phil* 0 pickup, then eats, the putsdown.) This will be a waste of resources and you may not get it back if the processes that has it never calls monitor leading to *starvation*.
- No *deadlock* problem because *monitors* only allow one process in the monitor at any given time
- **Starvation Scenario**: 0 pickup (eating), 4 pickup (wait in *condition variable queue*), 3 pickup (eating), 0 putdown (thinking), 0 pickup (eating), 3 putdown (thinking).
	- 4 is *starving* because 0 and 3 can eat forever while 4 is stuck waiting for chopstick

![[Pasted image 20240315015457.png]]
- 