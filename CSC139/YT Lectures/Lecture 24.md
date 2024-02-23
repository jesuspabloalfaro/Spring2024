# Peterson's Solution
## Critical-Section Handling in OS
Two approaches depending on if kernel is preemptive or non-preemptive
- **Preemptive**
	- Allows preemption of process when running in kernel mode
- **Non-preemptive**
	- Runs until exits kernel mode, blocks, or voluntarily yields CPU
		- Essentially free of race conditions in kernel mode
- Preemptive kernel is more responsive (reduces the risk that one kernel-mode process occupies the CPU for a long time)
- Preemptive kernel is more suitable for real-time programming

## Peterson's Solution
- Good algo description of a solution to the problem. Cannot be implemented in real life.
- Two-Process Solution
	- `int turn;`
	- `Boolean flag[2]`
- The variable `turn` indicates whose turn it is to *enter the critical section*
- The `flag` array is used to indicate if a process is *ready to enter the critical section*
	- `flag[i] = true` indicates that process P$_i$ is ready
- Assume that changes to variables `turn` and `flag` are **atomic** meaning it cannot be interrupted

## Algo for Process P$_i$
![[Pasted image 20240222210841.png]]
- In a forever loop...
	- P$_i$ is interested in the critical section
	- The turn is for process P$_j$
	- While the other process (P$_j$) is interested and its P$_j$ turn, then wait
	- Do the rest of the code

## Algo for Process P$_j$
![[Pasted image 20240222210900.png]]
- In a forever loop...
	- P$_j$ is interested in the critical section
	- The turn is for process P$_i$
	- While the other process (P$_i$) is interested and its P$_i$ turn, then wait
	- Do the rest of the code

## Peterson's Solution Cont.
Provable that all three CS requirements are met
- **Mutual exclusion** is preserved
	- P$_i$ enters CS only if 
		- either `flag[j] = false` or `turn = i`
		- `turn` is either `i` or `j` but not both
- **Progress** requirement is satisfied
	- The process in its remainder section will have its `flag` set to *false*; therefore it cannot be selected
	- The other process will necessarily be selected if `flag` is *true*
- **Bounded-waiting** requirement is met.
	- After executing its CS, each process sets its `flag` to *false*. If it tries to enter its CS again, it will set `turn` to the other process number

