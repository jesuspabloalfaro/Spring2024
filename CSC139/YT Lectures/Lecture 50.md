# Deadlock Avoidance Using the Resource Allocation Graph
## Avoidance Algorithms
![[Pasted image 20240407192509.png]]

## Claim Edge
![[Pasted image 20240407192538.png]]

## Resource Allocation Graph
![[Pasted image 20240407192657.png]]
- The dotted lines are meant to imply a process may be requesting an instance
- The system will attempt to temporarily grant a process an instance of a resource to test if it puts the system in an unsafe state, and if it does, the system will not allow that process to be granted an instance of a resource

## Unsafe State in Resource Allocation Graph
![[Pasted image 20240407192848.png]]

## Resource Allocation Algorithm
![[Pasted image 20240407192916.png]]

## Banker's Algorithm
![[Pasted image 20240407192928.png]]

