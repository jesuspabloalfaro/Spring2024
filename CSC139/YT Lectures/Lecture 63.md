# Page Replacement Policies
## What Happens if There is no Free Frame?
![[Pasted image 20240424190546.png]]

## Page Replacement
![[Pasted image 20240424190602.png]]

## Basic Page Replacement
![[Pasted image 20240424190640.png]]

## Page Replacement
![[Pasted image 20240424190723.png]]

## Page and Frame Replacement Algorithms
![[Pasted image 20240424190835.png]]
- We don't care about offsets because we are working at the page level

## Graph of Page Faults Versus The Number of Frames
![[Pasted image 20240424190930.png]]
- More memory = More frames
- More frames = less replacement = less page faults

## First In First Out Algorithm
![[Pasted image 20240424191029.png]]
- NOTE: Dirty bit can have performance issues
	- If a page was modified once a long time ago and is not used, its dirty bit will be set just as if a page that is frequently being used and modified will have its dirty bit set. This means that we can have performance issues if we continuously load from disk a page that is continuously being asked for
## FIFO Illustrating Belady's Algorithm
![[Pasted image 20240424191426.png]]
- As the number of frames increase, the number of page faults decrease
- Does *not* take into account how many times a page is referenced. 
- This algo is pretty bad
## Optimal Algorithm
![[Pasted image 20240424191434.png]]
- At index 3, we can see that 7 is referenced next at index 18 and 1 is referenced at index 14 and 0 is referenced next at index 4 so we can replace 7 in the page frames with index 3 (2) 
- Cycle cont...
- We don't know the future so it's not practical to do this but it's used for measuring algorithms performance
- This does take into account how many times the page is referenced, but again not practical due to future 