# Fragmentation
## Dynamic Storage-Allocation Problem
![[Pasted image 20240422190054.png]]
- **Worst Fit Advantage**: Larger leftover is likely to be useful
- **First Fit Advantage**: Speed. 

![[Pasted image 20240422190834.png]]
- **External Fragmentation**: There is more total free space than a process needs however the free space is not necessarily sequential. 
	- Unutilized space that does not belong to *any* process
- **Internal Fragmentation**: When a process gets an allocated free block for their needs but doesn't use the entire block, the *left over free memory* is called *internal fragmentation*
	- Unutilized space that belong to *a single* process
	- *NOTE: Even if a process needs 25, it will be allocated the entire block of 30 which makes 5 internal fragmentation*

- **Disadvantages of Internal Fragmentation**:
	- Small partitions of memory (like the 5 we see above) will fill up the *free memory block list* with unusable memory space (due to processes generally needing more than the internal fragmentation sizes)

![[Pasted image 20240422191115.png]]

![[Pasted image 20240422191410.png]]
- Example of memory *compaction*
- Reasons why this is **not** practical
	- Time spent moving blocks around causes unnecessary overhead




