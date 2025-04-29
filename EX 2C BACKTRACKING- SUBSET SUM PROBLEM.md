# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE: 15/08/2025
## AIM: To demonstrate that the sum of the subset of a given set is equal to the given sum.


## Algorithm:

1. **Input Representation**  
   - Read an integer `size` representing the number of elements in the array.
   - Read the `size` elements into the array `arr`.
   - Read the integer `sum` (the target sum we need to find subsets for).

2. **Recursive Function (subsetSum)**  
   - **Base Case:**  
     - If `i == n` (i.e., we have considered all elements), check if `sum == 0`. If true, it means a valid subset was found, so increment the count.
   - For each element `arr[i]`, make two recursive calls:
     - One call includes `arr[i]` by subtracting `arr[i]` from `sum`.
     - The other call excludes `arr[i]` (no change to `sum`).
   - Return the total count of subsets found that sum up to the target.

3. **Output Result**  
   - Print the number of subsets that sum up to the given `sum`.


## Program:
```python
/*
Program to implement Subset sum problem.
Developed by: Nithilan S
Register Number: 212223240108
*/

def subsetSum(arr, n, i,sum, count):
#Write your code here
    if i == n:
        if sum == 0:
            count += 1
        return count
    
    count = subsetSum(arr, n, i + 1, sum - arr[i], count)
    count = subsetSum(arr, n, i + 1, sum, count)
    return count





arr=[]
size=int(input())
for j in range(size):
    value=int(input())
    arr.append(value)
sum = int(input())
n = len(arr)
 
print(subsetSum(arr, n, 0, sum, 0))
```

## Output:
![image](https://github.com/user-attachments/assets/2df35deb-3842-4ce4-a160-a00509a0d185)



## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
