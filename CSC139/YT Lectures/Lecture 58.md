# Segmentation
## Segmentation
![[Pasted image 20240422191614.png]]
- **Segment**: Has a specific purpose and a specific meaning. Can have *unequal* sizes
- **Paging**: No meaning. Divide or slice memory space into *equal pieces* known as *pages*

## User's View of a Program
![[Pasted image 20240422191715.png]]

## Logical View of Segmentation
![[Pasted image 20240422191727.png]]

## Segmentation Hardware
![[Pasted image 20240422191757.png]]
- To implement, we need hardware support for a *segment table*
- **Segment Table**
	- Does mapping between segment base address and physical address
	- Indexed by the *segment number* 
	- Each segment will have its own entry
		- Within the entry, there will be a *base* and a *limit*
- **Segment Base Address**: An address that consists of a segment number and a displacement (offset)
- **Base**: Start address of that segment
- **Limit**: The size of the segment/max offset of segment

### Process Routine of Segmentation Hardware
- First check offset/displacement and compare with the limit of that particular segment
	- If within limit, OK
	- If **not** within limit, **crash**
- Next, add *base* to the *offset* which gets you the **physical address**

## Segmentation Architecture
![[Pasted image 20240422192508.png]]