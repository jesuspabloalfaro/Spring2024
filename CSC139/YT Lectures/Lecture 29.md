# The Bounded Buffer Problem
## Bounded Buffer Problem
![[Pasted image 20240314192629.png]]
- Variables `in` and `out` become **shared variables** when there are multiple producers or multiple consumers respectively. **mutex** will be used to protect **BOTH** these variables. 
	- We can use *two* semaphores to protect `in` and `out` if we want to modify them at the same time.
- **Producer** *increments* **fullCnt** and *decrements* **emptyCnt**
- **Consumer** *decrements* **fullCnt** and *increments* **emptyCnt**
	- **wait()** == Decrement
	- **signal()/post()** == Increment
