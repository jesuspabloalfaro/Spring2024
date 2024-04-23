# Main Memory Introduction and Basic Concepts
## Memory Management 
![[Pasted image 20240422181502.png]]
- **Disk** has *thousands* of cycles to access
- **Main Memory** has hundreds of cycles to access
- **L1 Cache** has 2-3 cycles to access

## Background
![[Pasted image 20240422181557.png]]

## Base and Limit Registers
![[Pasted image 20240422181725.png]]
- **Limit** = Max Address Space - Base Address Space

## Hardware Address Protection
![[Pasted image 20240422181932.png]]

## Address Binding
![[Pasted image 20240422182028.png]]
## Binding of Instructions and Data to Memory
![[Pasted image 20240422182155.png]]

![[Pasted image 20240422182814.png]]
- **Compiler** turns *source code* files into *machine code* files.
	- *Machine code* has only memory addresses and registers. I.e. **Assembly**
	- Generates *relocatable* code
		- Generates *offset* relative to a *base address* that is determined at either *load time* or *execution time*
			- Example above shows **int x** at **offset 0** and **int y** at **offset 4**.
- **Base address** can be created for a process at either *load time* or *execution time*
	- All further addresses that a process uses are at an offset relative to the base address
	- *Base addresses* of *processes* can be relocated **by the OS** so that the OS has more *flexibility in memory management*

## Multistep Processing of a User Program
![[Pasted image 20240422182758.png]]

![[Pasted image 20240422183651.png]]
- Process of compiling and linking a source file to create an executable
	- Linker (Usually a program like **gcc** will also act as a linker) will also link *libraries* for functions. This is **static linking**
	- **Dynamic linking** is when you have a file with functions that the linker can reference and load into memory so that *one* copy of the function is used across any application that loads that *dll*.  
		- **Advantages include**
			- Executables will be smaller
			- Many programs can use the same *dll*
			- Space efficiency
			- Updates are much easier because a new *dll* can just be loaded

## Logical vs Physical Address Space
![[Pasted image 20240422184110.png]]

## Memory-Management Unit (MMU)
![[Pasted image 20240422184159.png]]
- Does the translation from *logical address* to *physical address* using the *relocation register*
## Dynamic Linking Using a Relocation Register
![[Pasted image 20240422184248.png]]
- Relocation register *may be changed by the OS*
## Dynamic Linking
![[Pasted image 20240422184406.png]]
- `.dll` = dynamic linked library (Seen in Windows/Linux)
- `.so` = shared object (Seen in Windows)

## Swapping
![[Pasted image 20240422184448.png]]
- **Swapping**: Moving the memory block that belongs to a program from memory to disk because there is not enough memory

## Schematic View of Swapping
![[Pasted image 20240422184547.png]]

## Problems with Swapping
![[Pasted image 20240422184655.png]]
- Extremely slow CS. We do CS in *seconds* when it should be in *MICROSECONDS*
	- This is due to *slow transfer rates*, *process size*, and *I/O limitations*

## Swapping in Modern Systems
![[Pasted image 20240422185029.png]]

