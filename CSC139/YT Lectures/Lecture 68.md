# Mass Storage Systems
## Moving-Head Disk Mechanism
![[Pasted image 20240505181521.png]]
- **Cylinder** is biggest unit
- Each *cylinder* consists of multiple *tracks*
- Each *Track* consists of multiple *sectors*
	- Track rotates in a circular manner
- **Sector** is the smallest unit
- In order to do a read or write, the *head* must be above the target *sector*
	- *Head* moves linearly back and fourth


![[Pasted image 20240505181935.png]]
- Files are divided into blocks
	- Each *block* gets mapped to a *sector*
- In virtual memory...
	- *Files* = Physical
	- *Blocks* = Logical
	- Critical sector size: Half a kb

## Overview of Mass Storage Structure
![[Pasted image 20240505181951.png]]
- We use magnetic disk drives because its cheaper in bulk than SSD's

## Hard Disk Performance
![[Pasted image 20240505182117.png]]
- *Seek Time* is very slow
- 6 orders of magnitude slower than CPU
- 4 orders of magnitude slower than main memory

## Solid-State Disks
![[Pasted image 20240505182218.png]]

## Magnetic Tape
![[Pasted image 20240505182227.png]]

## Disk Structure
![[Pasted image 20240505182238.png]]
