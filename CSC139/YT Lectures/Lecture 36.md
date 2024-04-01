# CPU Scheduling First-Come, First-Served (FCFS) & Shortest-Job-First (SJF)
## First-Come, First-Served Scheduling
![[Pasted image 20240320232338.png]]
- **Gantt Chart** (Here for searchable term)
- In order to prioritze waiting times, we can use **Shortest-Job-First** instead of **FCFS**

## Shortest-Job-First Scheduling
![[Pasted image 20240320232617.png]]

## Example of SJF
![[Pasted image 20240320232645.png]]
- Optimal for prioritizing shortest waiting times
- SJF is a priority-based algorithm
	- **Starvation Problem**
		- **Definition**: There is no limit to the amount of processes that can get the CPU while another process is **waiting** 
		- Processes with longer CPU bursts will have lower priorities and may wait a long time in the queue
- Problems with SJF in a real-world OS
	- How would we know the burst time for the **next** CPU burst?
		- System knows the history of the previous CPU bursts for the process.
		- Based on the lengths of the previous CPU bursts, the system may predict the length of the **next** CPU burst.
		- Lengths of the **last CPU bursts** can be tracked in the processes **PCB**