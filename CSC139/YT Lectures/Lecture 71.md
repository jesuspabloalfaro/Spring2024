# Allocation Methods
## Allocation Methods - Contiguous
![[Pasted image 20240507210200.png]]

## Contiguous Allocation
![[Pasted image 20240507210246.png]]
- **Sequential Access**: Accessing blocks in a sequential manner
- **Random Access**: Getting a certain block. 
	- Able to calculate the sector of the target block by checking the sector of the starting block

## Extent-Based Systems
![[Pasted image 20240507210812.png]]
![[Pasted image 20240507210909.png]]
- Example of 2 extends
	- End of extend 1 will *point* to beginning of extend 2
	- Solves fragmentation

## Linked Allocation
![[Pasted image 20240507211013.png]]
- Just link the blocks between the start and end blocks 
- Advantages
	- no external fragmentation at the block level
- Disadvantages
	- Sequential access is worse than contiguous since in contiguous, the blocks are adjacent so less head movement is required
	- Random access is worse than contiguous because you need to traverse the list to get to the desired block

## Allocation Methods
![[Pasted image 20240507211342.png]]
![[Pasted image 20240507211640.png]]
- Linked: 
	- Actual data blocks pointing to other blocks
- FAT:
	- Block numbers pointing to other block numbers
	- Better random access because the head does not need to move as much in the limited section of the disk where the FAT is (FAT is very small)

## Example of Indexed Allocation
![[Pasted image 20240507211703.png]]
- File consists of blocks scattered all over disk but there is an index block that contains the block numbers of all the blocks that make that file (In Order)
- Random access even better than FAT since you only need to go to a single block (index block) to find the block you are looking for
- Disadvantage: 
	- If the file is huge, you *cannot* fit all the indexes in a single (index) block.