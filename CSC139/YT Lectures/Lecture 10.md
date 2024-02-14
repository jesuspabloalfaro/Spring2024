# OS Structures
## Implementation
- Development in high-level language is more productive
	- Code can be written faster
	- Code is more compact
	- Code is easier to understand and debug
- High-level code can benefit from compiler technology (optimizations)
	- Compiler can automatically analyze the code and do better optimization than the human mind
	- Improvements in compiler technology can be applied by recompiling

### Notes
- Portability is a good example of why OS are written in high-level languages
	- Intel x86
	- PowerPC
	- Spock 
- Compiler does a better job at generating optimized code
- Some cases, Assembly makes sense
	- If its performance critical code
	- You have only a small size for code

## Operating System Structure
- General-purpose OS is very large program
- Various ways to structure it
	- Simple structure (Monolithic)
		- MS-DOS
		- Original Unix
	- Layered - an abstraction
	- Microkernel
		- Mach
	- Modules
	- Hybrid Systems
## Simple Structure (Monolithic) - MS-DOS
- MS-DOS written to provide the most functionality in the least space
	- Not divided into modules
	- Although MS-DOS has some structure, its interfaces and levels of functionality are not well separated
	- Application programs can access BIOS to write directly to the display and disk drives
![[Pasted image 20240206153827.png]]
## Limited Structuring - Unix
Unix - limited by the hardware functionality. The original UNIX operating system had limited structuring. The UNIX OS consists of two separable parts
- System programs
- The Kernel
	- Consists of everything below the system call interface and above the physical hardware
	- Provides the file system, CPU scheduler, memory management, and other operating system functions. A large number of functions for one level
- Difficult to implement and maintain
- Performance advantage due to little overhead in system call interface and communication within the kernel
## Traditional UNIX System Structure
![[Pasted image 20240206154120.png]]

### Notes
- Sometimes OS are based on other OS
	- Android is based on Linux
- This is a monolithic structure in the picture above

## Layered Approach
- The operating system is divided into a number of layers, each built on top of lower layers. The bottom layer (layer 0), is the hardware and the highest (layer *N*) is the user interface
- With modularity, layers are selected such that each uses functions (operations) and services of only lower-level layers
- Simplifies construction and debugging
- Hard to define layers
	- backing-store driver and CPU Scheduler
- Less efficient due to the overhead of passing and modifying parameters through multiple layers
![[Pasted image 20240206154418.png]]
### Notes
- Services in layer *N* may **only** call services in layer *N-1*. Not any above nor any below.
	- Monolithic approach is better for performance for this reason
- Layered systems design pros and cons
	- Pros
		- Simplified and segregated services
	- Cons
		- Understanding which services needs to be above or below other services
![[Pasted image 20240206154537.png]]

## Microkernel Design
![[Pasted image 20240206160703.png]]
### Notes
- If a program in user mode wants to communicate with a program in kernel mode, it must send messages to the kernel for a response and this is done via **message passing**
- Pros of Microkernel
	- Easier to define. No hierarchy that was in layered approach and different services can talk to each other (despite needing to go through kernel)
	- Security. Minimized code that is running in privileged mode/kernel mode
	- Can swap out parts without updating the kernel. No need to recompile kernel.
	- If a service fails, it wont crash the machine because the kernel will not be affected
## Microkernel System Structure
- Moves nonessential components from the kernel into user space
- **Mach** is an example of a microkernel
	- Mac OS X kernel (Darwin) partly based on Mach (CMU, 80s)
- Communication takes place between modules using **message passing** through the kernel
- Benefits
	- Easier to extend OS without recompiling the kernel
	- Easier to port the operating system to new architectures
	- More secure (less code is running in kernel mode)
	- More reliable (if a service fails, the rest of the OS remains intact)
- Disadvantages
	- Performance overhead of user space to kernel space communication
		- Win NT was microkernel but grew into monolithic Win XP
## Modules
- Kernel provides core services, other services are provided as **loadable kernel modules** (boot time or run time)
	- Each core component is seperate
	- Each talks to others over known interfaces
	- Each is loadable as needed within the kernel
- Overall, similar to layered but more flexible, because any module can call any other module (no hierarchy)
- Also similar to microkernel but more efficient because modules do not need to invoke *message passing*
- Perhaps the best current methodology for OS design
- Common design in modern Unix systems
	- Solaris
	- Linux
	- Mac OS
	- Windows
## Solaris Modular Approach
![[Pasted image 20240206161238.png]]
### Notes
- Services are loaded as modules that are added to the kernel rather than being separate processes/services. Loaded as DLL and sticking them to the kernel
- There is a difference in the **source code** between **monolithic** and **layered**
![[Pasted image 20240206161654.png]]
- Advantages of loadable modules vs layered
	- Memory
	- No need to recompile kernel when adding/deleting DLL's
	- Performance. Any module can talk to any module without having to go through the hierarchy
## Hybrid Systems
- Most modern operating systems do not adopt one pure model
	- Hybrid combines multiple approaches to address performance, security, usability needs
	- Linux and Solaris are *monolithic* because the OS runs in a single address space (for performance) but modular for dynamic loading of some functionalities
	- Windows mostly monolithic (for performance), but with microkernel features such as providing support for different subsystems (*personalities*) in user mode, it also supports loadable kernel modules
- Apple Mac OS X hybrid, layered, Aqua UI plus Cocoa programming environment
	- Below is kernel consisting of Mach microkernel and BSD Unix parts, plus I/O kit and dynamically loadable modules called **kernel extensions**
## Mac OS X Structure
![[Pasted image 20240206162304.png]]
## IOS
- Apple mobile OS for iPhone and iPad
	- Structured on Mac OS X added functionality
	- Does not run OS X applications natively
		- Also runs on different CPU architecture (ARM vs Intel)
	- *Cocoa Touch* Objective-C API for developing mobile apps
	- *Media services* layer for graphics, audio and video
	- *Core services* provides cloud computing databases
	- Core operating system based on Mac OS X kernel 
## Android
- Developed by Open Handset Alliance (mostly Google)
	- Open source
	- Runs on a variety of mobile platforms
- Similar stack to IOS
- Based on Linux kernel but modified
	- Provides process, memory, device-driver management
	- Adds power management
- Runtime environment includes core set of libraries and Dalvik virtual machine
	- Apps developed in Java plus Android API
		- Java class files compiled to Java bytecode then translated to executable that runs Dalvik VM
- Libraries include framework for web browser (webkit), database (SQLite), multimedia, smaller libc

## Android Arch
![[Pasted image 20240206162858.png]]