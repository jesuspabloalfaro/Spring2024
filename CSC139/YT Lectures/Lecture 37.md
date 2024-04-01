# Determining the Length of  the Next CPU Burst
## Determining Length of Next CPU Burst
![[Pasted image 20240320234447.png]]
![[Pasted image 20240320234537.png]]
- Length of the **next cpu burst** can be estimated by calculating a weighted sum of the length of the **last** **cpu burst** + the **last estimate**  

## Prediction of the Length of the Next CPU Burst $\alpha$ = 0.5
![[Pasted image 20240320234924.png]]
- Since there is no history of CPU bursts when a process first starts, there will be a *random* guess on the first CPU burst
- (10 + 6) / 2 = 8 | (8 + 4) / 2 = 6 | (6 + 6) / 2 = 6 | etc... We divide by 2 because $\alpha$ = 0.5
- 
