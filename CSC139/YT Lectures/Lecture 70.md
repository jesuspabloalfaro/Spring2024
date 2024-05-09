# File System Implementation
## File-System Structure
![[Pasted image 20240507203812.png]]

## Layered File System
![[Pasted image 20240507203911.png]]
- **Devices** in *Filesystems*: Disk

## File System Layers
![[Pasted image 20240507204037.png]]
- File level layers
- The only layer that knows about *files* is the *File Organization Module*. The rest of the layers only know about *blocks*

## File System Layers
![[Pasted image 20240507204226.png]]
![[Pasted image 20240507204314.png]]
- Directory level layer

## File-System Implementation
![[Pasted image 20240507204402.png]]
![[Pasted image 20240507204530.png]]
- Two places data structures are kept
	- Data Structures that are kept *on disk*
	- Data Structures that are kept *in memory*

## In-Memory File System Structures
![[Pasted image 20240507204557.png]]
- **Open-File Table**: Table that has information about open files on the system
- **FCB**: File Control Block
![[Pasted image 20240507204826.png]]

![[Pasted image 20240507204851.png]]

## Directory Implementation
![[Pasted image 20240507205106.png]]
