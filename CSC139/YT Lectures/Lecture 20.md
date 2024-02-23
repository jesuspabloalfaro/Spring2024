# Amdahl's Law
## Amdahl's Law
- Performance gains from adding additional cores to an application that has both serial and parallel components
- *S* is serial portion
	- This portion is **NOT** *parallelizable* 
- *N* processing cores
![[Pasted image 20240221195311.png]]
- If application is 75% parallel/25% serial, moving rom 1 to 2 cores results in speedup of 1.6 times
- As *N* approaches infinity, speedup approaches 1/*S*
- In this, we are *ignoring* overhead. 

**Serial portion of an application has disproportionate effect on performance gained by adding additional cores**
![[Pasted image 20240221195638.png]]



