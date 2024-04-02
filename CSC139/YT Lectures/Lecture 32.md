# The Dining-Philosophers Problem, a Semaphore-Based Solution
## Dining-Philosophers Problem
![[Pasted image 20240304192241.png]]
![[Pasted image 20240304192537.png]]
- Each philosopher will need 2 chopsticks but philosopher 4 needs philosopher 0's chopstick so we use `i` and `(i+1) % # of philosophers`
## Dining-Philosophers Problem Algorithm
![[Pasted image 20240304192611.png]]
- Problem is this may cause a **deadlock**
	- If philosopher `i` gets `i` chopstick and loses CPU
	- Although its *possible*, it is very *unlikely* because we are counting on every philosopher losing the CPU at the same point where they only have 1 chopstick.
	- Although unlikely, it is *still considered a **deadlock** solution*
- Solving the deadlock problem
	- If we *take away a philosopher*, then there will be 4 philosophers fighting for 5 chopsticks meaning there will always be a chopstick unused that is not part of the fighting for sticks
	- Keep the number of resources to +1 that of those who need the resource
- Another solution to the deadlock problem
	- Put the `wait`'s in another mutex semaphore so that the chopstick hand-off becomes its own critical section as well

![[Pasted image 20240304193654.png]]
- Another solution is an *asymmetric solution*
	- We can have processes pick their semaphores in a different order
		- An **even** numbered process gets the **right** chopstick before the **left** and an odd **numbered** process gets the **left** chopstick before the **right**.
- We can think of the *waiting* processes as philosophers **not** competing for the chopsticks