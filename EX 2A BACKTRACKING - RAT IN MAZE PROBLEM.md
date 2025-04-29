# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE: 8/3/2025
## AIM: To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.

## Algorithm:

1. **Input Representation**  
   - The maze is represented as a 2D grid of size `N x N`, where:
     - `1` represents an open path.
     - `0` represents a blocked path.

2. **Print Solution Function**  
   - Iterate through the solution grid (`sol`) and print the path (represented by `1`s) taken to reach the destination.

3. **Safety Check (isSafe)**  
   - Check if the position `(x, y)` is within the bounds of the maze and if the cell is not blocked (`maze[x][y] == 1`).

4. **Solve Maze Function**  
   - Create a 2D list `sol` of size `N x N` to store the solution path.
   - Call `solveMazeUtil` to find the path from the start `(0, 0)` to the destination `(N-1, N-1)`.

5. **Backtracking (solveMazeUtil)**  
   - **Base Case:** If the current position `(x, y)` is the destination `(N-1, N-1)`, mark the cell as part of the solution and return `True`.
   - If the current cell `(x, y)` is safe (`isSafe`), mark it as part of the path (`sol[x][y] = 1`).
   - Recursively attempt to move:
     - First, try moving down to `(x+1, y)`.
     - If that fails, try moving right to `(x, y+1)`.
   - If both moves fail, backtrack by marking the current cell as `0` and return `False`.

6. **Output the Result**  
   - If a path exists, print the solution grid showing the path.
   - If no path exists, print "Solution doesn't exist".
   

## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: Nithilan S
Register Number: 212223240108
*/

N = 4

def printSolution( sol ):
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 
def isSafe( maze, x, y ):
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
    return False
 
def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
     
# Write your code here
    if(x == N-1 and y == N-1):
        sol[x][y] = 1
        return True
    
    if(isSafe(maze, x, y) == True):
        
        sol[x][y] = 1
        if(solveMazeUtil(maze, x+1, y, sol) == True):
            return True
            
        if(solveMazeUtil(maze, x, y+1, sol) == True):
            return True
            
        sol[x][y] = 0
    return False
        
# Driver program to test above function
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```

## Output:
![image](https://github.com/user-attachments/assets/1450f2a3-a515-4f2b-87fa-11168758d621)



## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
