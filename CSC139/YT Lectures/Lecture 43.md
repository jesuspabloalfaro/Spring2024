# Scheduling in Linux
## Completely Fair Scheduler (CFS) - Linux Scheduling in Version 2.6.23+
![[Pasted image 20240331212248.png]]
- Two main process categories
	- Default
	- Real-time
		- Has priority over *default* processes
![[Pasted image 20240331212610.png]]
- **Virtual Run Time**: Function(actual running time, *nice* value)
	- **Actual Running Time**: Length of the last CPU burst or Estimated CPU burst length based on history of process
		- Based on **SJF**
	- **Nice Value**: Priority Number (Smaller values = higher priority)
		- Based on **Priority algorthim**
	- Technically, a combination of **SJF** and **Priority**

## CFS Performance
![[Pasted image 20240331213209.png]]
- Again, **CFS only applies to real-time** processes
## Linux Scheduling
![[Pasted image 20240331213304.png]]
- 