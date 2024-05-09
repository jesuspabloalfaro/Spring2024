# Page Fault Handling
## Steps in Handling a Page Fault
![[Pasted image 20240423131652.png]]
- First, it will check to see if address *M* is in physical memory
	- It is not, as denoted by the *i* for the invalid bit in the page table which results in a page fault (*ISR* is called) 
- Then, it will check if the page number is a valid page number
	- If it is, query the disk for the page
		- If there is a free frame, load the page into the frame
		- If there is *no* free frame, drop a frame to make space for the incoming page
			- Before dropping the frame, we check to see if the page if the page has been changed since its been loaded (Check the *dirty* bit)
				- If it *has* been changed, then we load the new page back on disk
				- If it *has not* been changed, then we can just drop the frame entirely because a copy of the frame is still on disk 
	- If it is not, throw an exception and exit
- Then, we update the page table to reflect the new valid-invalid bit to *v*
- Then, we restart the instruction that loads *M* 
	- Must have *hardware* support that supports starting and restarting

## Aspect of Demand Paging
![[Pasted image 20240423132754.png]]

## Performance of Demand Paging
![[Pasted image 20240423133206.png]]
![[Pasted image 20240423133936.png]]

## Demand Paging Example
![[Pasted image 20240423133956.png]]
