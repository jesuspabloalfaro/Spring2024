# Page Replacement Policies (2)
## Least Recently Used (LRU) Algorithm
![[Pasted image 20240424192807.png]]
![[Pasted image 20240424193354.png]]
### How LRU Works in Theory
![[Pasted image 20240424193146.png]]

## Use of a Stack to Record Most Recent Page References
![[Pasted image 20240424193617.png]]
- Whenever a page is referenced, move the page to the top of the stack
	- This means the least recently used will always be at the bottom of the stack
- Not practical because creating a stack and doing updates cause too much overhead
	- Still good for assignment

## LRU Approximation Algorithms
![[Pasted image 20240424193829.png]]
- Reference Bit
	- Associate a reference bit for each page to check if a page has been referenced
	- 0 = No reference
	- 1 = Reference
	- Pick any page with 0

## Second-Chance (Clock) Page-Replacement Algorithm
![[Pasted image 20240424193952.png]]
- Use reference bit
	- If 0, replace
	- If 1, reset reference bit to 0
		- Check if the page will be referenced between now and the next pass

