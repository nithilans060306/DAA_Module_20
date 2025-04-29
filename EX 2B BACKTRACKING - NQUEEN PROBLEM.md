# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE: 11/8/2025
## AIM: To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm:

1. **Input Representation**  
   - Read the integer `N` (size of the chessboard and number of queens).
   - The board is represented as an `N x N` grid, initialized with `0` (no queens placed).

2. **Safety Check (isSafe)**  
   - For a given cell `(row, col)`, check if placing a queen at that position is safe:
     - Ensure no queens exist in the same row on the left side.
     - Ensure no queens exist in the upper diagonal on the left side.
     - Ensure no queens exist in the lower diagonal on the left side.
   
3. **Backtracking (solveNQUtil)**  
   - **Base Case:** If `col >= N`, all queens have been placed, and the solution is valid.
   - For each row, check if placing a queen is safe. If safe, place the queen and recursively try placing queens in subsequent columns.
   - If placing a queen doesn't lead to a solution, backtrack by removing the queen (set it back to `0`).

4. **Solution Printing (printSolution)**  
   - If the solution exists, print the `N x N` board where `1` represents a queen's position, and `0` represents an empty cell.
   
5. **Output Result**  
   - If a solution is found, print the board.
   - If no solution exists, print "Solution does not exist".
   

## Program:
```python
/*
Program to implement N-Queen problem using backtracking.
Developed by: Nithilan S
Register Number: 212223240108
*/

global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      # Write your code here
    if col >= N:
        return True
        
    for i in range(N):
        if isSafe(board, i, col):
            board[i][col] = 1
            if solveNQUtil(board, col + 1) == True:
                return True
            board[i][col] = 0
    
    return False
        
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()

```

## Output:
![image](https://github.com/user-attachments/assets/90f5e3bf-44ac-44de-9a2d-207b486eeaf7)



## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
