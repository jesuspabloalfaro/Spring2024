# Disk Scheduling
## FCFS
![[Pasted image 20240505182522.png]]
- Not efficient due to a bunch of cylinder accesses all over the place

## SSTF
![[Pasted image 20240505182635.png]]
- Starvation occurs here due to a possibility that longer distance requests don't get fulfilled due to incoming shorter distance requests

## Scan
![[Pasted image 20240505182826.png]]
- Will scan one side and choose shortest distance to service that request on that side, then scan the other side and do the same
- Problem
	- When the head changes directions back, it will start to service the most recent requests instead of requests that have been waiting for a long time

## C-Scan
![[Pasted image 20240505183108.png]]
![[Pasted image 20240505183216.png]]
- Scanning in a circular manner.
- If we folded the disk to a cylinder, the two ends would meet
