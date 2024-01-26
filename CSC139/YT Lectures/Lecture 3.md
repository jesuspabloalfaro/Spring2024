# Computer System Review
## Storage Structure
- **Main memory**: Only large storage media that the *CPU* can access directly
	- *Random access*
	- Typically *volatile*
- **Secondary Storage**: Extension of *main memory* that provides large *nonvolatile* storage capacity.
- **Hard Disks**: Rigid metal or glass platters covered with magnetic recording material
	- Disk surface is logically divided into *tracks* which are subdivided into *sectors*
	- The *disk controller* determines the logical interaction between the device and the computer
- **Solid-State Disks**: Faster than *hard drives* and *nonvolatile*
	- Various technologies
	- Becoming more popular
![[Pasted image 20240122175428.png]]

## Caching
- Important principle, performed at many levels in a computer (in hardware, *operating system*, software)
- Information in use copied from slower to faster storage temporarily
- Faster storage (*cache*) checked first to determine if information is there
	- If it is: Information used directly from the *cache* (fast)
	- If it is not: Data copied to *cache* and used there
- *Cache* is smaller than storage being cached
	- *Cache management* is an important design problem
	- *Cache size* and *replacement policy*
### Notes:
- *Caching* stores subset of data into smaller, faster device
	- Data that is needed more frequently is stored here
## Symmetric Multiprocessing Architecture
![[Pasted image 20240122175905.png]]
- All *CPU*'s share the same *memory*

## A Dual-Core Design
![[Pasted image 20240122180000.png]]
- Multi-chip and *multicore*
- System containing all chips

## Clustered System
![[Pasted image 20240122180028.png]]
- Multiple computers connected by an interconnect or over a network
