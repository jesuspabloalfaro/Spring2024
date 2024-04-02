# The Readers-Writers Problem
## Readers-Writers Problem
![[Pasted image 20240314200140.png]]
![[Pasted image 20240314202559.png]]
- If you are the **first** reader, check for writer before you read
- If you are **not first** reader, do your reading
- If you are **last** reader, unlock semaphore and let a writer or reader in

## Readers-Writers without Starvation
![[Pasted image 20240314202826.png]]
![[Pasted image 20240314202851.png]]
- Fairness semaphore makes it so **both** readers and writers have to wait in a queue. 