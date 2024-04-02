# Main Goals
- Generate large array of random numbers
	- 1-`MAX_RANDOM_NUMBER`
	- Check if valid
- Compute products of all the numbers in the array mod `NUM_LIMIT`
- if `arg[4]` is non-negative int, set the value at that index to **zero**
- Compute the product of all the numbers in the array mod NUM_LIMIT without creating any new threads and print the computation time. Your single threaded multiplier must terminate as soon as a zero is found.
- 
# Test Cases
- Check argument 3 for non-negative index
When your program is working correctly, run the following tests on a dedicated machine:  
1. Array size = 100M, T=2, index for zero =50M+1  
2. Array size = 100M, T=4, index for zero =75M+1  
3. Array size = 100M, T=8, index for zero =88M  
4. Array size = 100M, T=2, index for zero =-1 (no zero)  
5. Array size = 100M, T=4, index for zero =-1 (no zero)  
6. Array size = 100M, T=8, index for zero =-1 (no zero)  
The tests must be run on a dedicated machine to ensure the accuracy of the timing results.
# Good To Knows
- When computing the modular product of the array you **MUST** mod by `NUM_LIMIT` after each multiplication or the variable that you are using to store the product will overflow
- Three CLI Arguments
	1) The array size (a positive integer between 1 and 100 000 000)  
	2. The number of threads (a positive integer between 1 and 16)  
	3. The index at which a zero must be placed in the input array. If this index is negative, don’t put a zero in the array
- 