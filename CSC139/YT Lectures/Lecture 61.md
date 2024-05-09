# Virtual Memory Basic Concepts, Demand Paging, and Page Faults
## Background
![[Pasted image 20240423124242.png]]
- **Pure Demand Paging**: Strictly load pages on demand/need. Program *needs* to request/reference that page
- Pages are *on-disk* and a **subset** is in *memory*

![[Pasted image 20240423125711.png]]

![[Pasted image 20240423125900.png]]

## Virtual Memory That is Larger Than Physical Memory
![[Pasted image 20240423125938.png]]
- *Virtual* Memory is interchangeable with *Logical* Memory
- All pages are *on-disk* 
- A subset of pages are *in physical memory*
- *Memory Map* maps virtual memory space with physical memory space

## Virtual Address Space
![[Pasted image 20240423130104.png]]
- Virtual Memory Advantages
	- Only need to allocate more frames *on-demand*
	- Program can continuously grow until the virtual memory space is full
		- Once program virtual memory space is full, new page is allocated and more physical memory is allocated

## Demand Paging
![[Pasted image 20240423130305.png]]
- **Demand Paging**: Pages are fetched on-demand (Can be based on predicted page needs)
- **Pure Demand Paging**: Pages are fetched *strictly* on-demand (**NO PREDICTION**)
- In virtual memory, rather than swapping in and out the address space of a whole process, we swap in and out the *pages* 

## Basic Concepts
![[Pasted image 20240423130604.png]]

## Valid-Invalid Bit
![[Pasted image 20240423130618.png]]
- Additional bit that is added to each frame that indicates if that frame is in physical memory or not

## Page Table When Some Pages Are Not in Main Memory
![[Pasted image 20240423130700.png]]
- **System** fetches page from disk to memory if invalid bit is set (*Page Fault*)
	- This is why we need hardware support for interrupts
- *Page Fault* *handling* is extremely **slow**
	- While the system is dealing with a page fault, the system can give the CPU to other processes

## Page Fault
![[Pasted image 20240423131047.png]]
- The concept of **locality** makes virtual memory work. Otherwise, performance would be terrible

