# Shortest-Remaining-Time-First and Priority Scheduling

## Shortest-Remaining-Time-First
![[Pasted image 20240320235900.png]]
- More dynamic and more adaptive than *SJF*
- We give the CPU to P2 after 1 second because at time 1, P1 still has 7 units left in their burst while P2 only has 4 units left. P3 and P4 have yet to arrive
- Once P3 arrives at time 2, P1 still has 7 units remaining, P2 has 3 units remaining and P3 has 9 units remaining so P2 keeps the CPU
- Once P4 arrives at time 3, P1 still has 7 units remaining, P2 has 2 units remaining, P3 still has 9 units remaining, and P4 has 5 units remaining so P2 keeps the CPU
- Once P2 finishes at time 5, P4 gets the CPU because it has the lowest unit count remaing and the process continues

## Priority Scheduling
![[Pasted image 20240321000641.png]]
- Being put at the head of the ready queue doesn't mean the process will *immediately* get the CPU, but rather it will get the CPU next.

## Example of Priority Scheduling
![[Pasted image 20240321001237.png]]
- When arrival times are not specified, we assume all processes arrive at the same time