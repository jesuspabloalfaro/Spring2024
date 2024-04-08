# Deadlock Avoidance and Safe States
## Deadlock Avoidance
![[Pasted image 20240407190121.png]]

## Safe State
![[Pasted image 20240407190258.png]]

## Safe State Example
![[Pasted image 20240407190308.png]]
- **Safe State**
	- Since there are 3 instances available *after* allocation, P1 has to go first because it is the only Process that needs <=3 instances (2).
	- After P1 finishes, we will have 5 (3+2) instances available  which means only P0 can go next because its needs are <= 5
	- After P0 finishes, we will have 10 (5+5) instances available which means P2 can go next since it requires <=10 instances 
	- After P2 finishes, we will have 12 (10 + 2) instances available but there are no other processes
- **Unsafe State**
	- Since we only have 2 available instances *after* current allocations...
	- P1 can go first. Once P1 finishes, we will have 4 (2+2) instances available but P0 and P2 both need >4 instances
	- Because P2 requests one more instance and we were able to see that this would lead to an unsafe state, the system will **deny** P2's request for one more instance.

## Basic Facts
![[Pasted image 20240407191859.png]]

## Safe, Unsafe, Deadlock Facts
![[Pasted image 20240407191956.png]]
- **Deadlock** is a *subset* of **unsafe**

