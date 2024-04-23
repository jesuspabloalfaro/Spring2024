# Page Table, TLB and Effective Access Time
## Free Frames
![[Pasted image 20240422194634.png]]
- Page 0 gets put into the first free-frame (14)
- Page Table will add the entry (0, 14)
- Page 1 will get the next free-frame (13)
- Page Table will add the entry (1, 13)
- etc....

![[Pasted image 20240422200430.png]]
- *Note: The free-frame list is not in order because in the real world, we don't know when each frame will be free next.*
	- Some advantages of having adjacent frames is **caching**.  
- Time delta and space delta are different small values

## Implementation of Page Table
![[Pasted image 20240422200452.png]]

- With every access of the page table, you are going to have to go to memory twice. Once for looking up the frame number that corresponds to the page number and then again to look at the contents of the frame number
	- This is slow because main memory is 2 orders of magnitude *slower than the processor (for caching)*
- **Translation Look-Aside Buffer (TLB)**: A *small subset* of the *page table* that is stored in CPU *Cache*.
	- Has key (page number) and value (frame number)
	- Cant use the index as the page number because the TLB is only a *subset* of the entire list thus it is necessary to keep page numbers as an actual key

![[Pasted image 20240422200923.png]]
- TLB's can either use an *ASID* for multiple processes *OR* make it so that the TLB can only store information about a *single* process at a time
	- If you choose to only store a single process at a time, there will need to be some sort of context switching overhead to flush and rewrite the TLB when changing processes

## Associative Memory
![[Pasted image 20240422201359.png]]

## Paging Hardware With TLB
![[Pasted image 20240422201420.png]]
- First go to the TLB and look up the page number in the TLB
	- Parallel searching of the page numbers
- Next, if you get the page number,
	- Get frame number and add it to the offset and get the physical address
- Else, if you don't get the page number in the TLB
	- Go to the full page table in memory and get the frame number and load the entry into the TLB

## Effective Access Time
![[Pasted image 20240422201639.png]]
- Hit = one TLB access + memory access
- Miss = one TLB access + 2 memory access