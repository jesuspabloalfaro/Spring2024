# Banker's Algorithm Cont.
## Resource-Request Algorithm for Process $P_i$
---
![[Pasted image 20240407202101.png]]
- Step 1 check needed because if the Request is *more* than the Need, that means that the Max that was declared by the process was wrong and the whole analysis is incorrect
- Step 2 check needed because if the Request exceeds the amount of Available resources, then we simply don't have the resources to accommodate the request
- Step 3 is a simulated allocation of the request 
- In reality, this is not practical because you would not know the actual Max resources for a process so we couldn't run the simulation

