# Paging
## Paging
![[Pasted image 20240422192543.png]]
- *Pages* map to a *frame*
	- *Pages* are *logical* and *frames* are *physical*
	- The page to frame correlation is equal. 10 frames = 10 pages and vice versa

## Address Translation Scheme
![[Pasted image 20240422192706.png]]

## Paging Hardware
![[Pasted image 20240422192821.png]]
- Page table is indexed by the page number
- Entry is the corresponding frame number
- Adding frame number to the offset will give us the physical address
- No limit required in paging because all pages have the same size

## Paging Model of Logical and Physical Memory
![[Pasted image 20240422193036.png]]

## Paging Example
![[Pasted image 20240422193152.png]]
- Calculating Frame Number for given Pages
	- Page 5 * 4 bytes  = 20 (Frame Number)
	- Page 6 * 4 bytes = 24 (Frame Number)
	- Page 1 * 4 bytes = 4 (Frame Number)
	- Page 2 *  4 bytes = 8 (Frame Number)
- **External Fragmentation** is completely eliminated using paging
	- Frame size is constant
	- Never have a useless block of memory. 
		- Every free block of memory will have a set amount of pages that are useful
- **Internal Fragmentation** is **not** completely eliminated
	- There is a chance that a process is *not using the entire allocated page*

## Internal Fragmentation
![[Pasted image 20240422194005.png]]
- 2600 bytes = 2048 bytes (4 pages) + 12 bytes

![[Pasted image 20240422194333.png]]
- To reduce internal fragmentation, you can *reduce the page size* (in this example, we can make the pages smaller to 256 bytes)
	- Consequences for this is your *page table size* will become *bigger* and since the page table itself is stored in memory, you are losing memory storing the page table

## Addressing
![[Pasted image 20240422194505.png]]


