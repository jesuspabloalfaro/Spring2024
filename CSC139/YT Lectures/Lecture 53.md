# Deadlock Detection with Resource Allocation Graph
## Deadlock Detection
---
![[Pasted image 20240407202503.png]]

## Single Instance of Each Resource Type
---
![[Pasted image 20240407202626.png]]

## Resource-Allocation Graph and Wait-for Graph
---
![[Pasted image 20240407202647.png]]
- By terminating P1, P2, or P4, we can resolve the deadlock
- DFS detects cycles in a graph 
	- Running Time: O(V+E)
	- E = O($V^2$)
	- DFS runs in O($V^2$) time