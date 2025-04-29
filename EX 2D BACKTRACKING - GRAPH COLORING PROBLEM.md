# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE: 18/03/2025
## AIM: To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.

## Algorithm:

1. **Input Representation**  
   - Read the number of vertices `vertices` in the graph.
   - The graph is represented as an adjacency matrix (`graph`) where `graph[i][j] == 1` means there is an edge between vertex `i` and vertex `j`.

2. **Safety Check (isSafe)**  
   - For a given vertex `vertices` and color `c`, check if it is safe to assign color `c`:
     - Check all adjacent vertices; if any adjacent vertex already has color `c`, then it is not safe.

3. **Graph Coloring Recursive Utility (graphUtil)**  
   - **Base Case:** If `vertices == self.vertices`, all vertices are colored, and the solution is found.
   - For each color `c` from 1 to `m` (maximum colors available), try assigning the color to the current vertex:
     - If it is safe to assign color `c`, assign the color and recursively try to color the next vertex.
     - If the coloring leads to an invalid configuration later, backtrack by removing the color (set it back to `0`).
   - If no color can be assigned to the current vertex, return `False` to backtrack.

4. **Graph Coloring Function (graphColouring)**  
   - Initialize the `color` list with all zeros (no color assigned).
   - Call `graphUtil` starting from vertex 0 to check if a solution is possible.
   - If a valid coloring is found, print the assigned colors for all vertices.
   - If no valid coloring is possible, return `False`.

5. **Output Result**  
   - If the solution exists, print the colors assigned to each vertex.
   - If no valid coloring is found, print that a solution does not exist.
 

## Program:
```python
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: Nithilan S
Register Number: 212223240108
*/
class Graph():
    def __init__(self, vertices):
        self.vertices = vertices
        self.graph = [[0 for j in range(self.vertices)] for i in range(self.vertices)]
        
    def isSafe(self, vertices, color, c):
        for i in range(self.vertices):
            if self.graph[vertices][i] == 1 and color[i] == c:
                return False
        return True
            
    def graphUtil(self, m, color, vertices):
        if vertices == self.vertices:
            return True
            
        for c in range(1, m+1):
            if self.isSafe(vertices, color, c):
                color[vertices] = c
                if self.graphUtil(m, color, vertices+1):
                    return True
                    
                color[vertices] = 0
        return False
        
    def graphColouring(self, m):
        color = [0] * self.vertices
        if not self.graphUtil(m, color, 0):
            return False
        print("Solution exist and Following are the assigned colours:")
        for c in color:
            print(c, end=" ")
        return True
```

## Output:
![image](https://github.com/user-attachments/assets/1f72d039-3bb5-4c6d-9a34-704d7ffd9394)



## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
