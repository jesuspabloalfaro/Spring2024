# Thrashing
## Thrashing
![[Pasted image 20240505172649.png]]
- Will spend lots of time in the waiting queue waiting for the system to handle a page fault

![[Pasted image 20240505173943.png]]
- Thrashing occurs with 3 frames and LRU as the page replacement policy because there will be 100% page faults. 
- Adding another frame for a total of 4 frames will result in only 4 page faults with a 99% efficiency rating. 
- Optimal vs LRU good example because Optimal wont have 100% page faults but its not possible to implement it real world because you cant know the future

