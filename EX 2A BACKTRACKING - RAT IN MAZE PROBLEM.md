# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1.Initialize a solution matrix sol of the same size as the maze, filled with zeros.
2.Start from cell (0, 0) and attempt to reach the destination cell (N-1, N-1).
3.Check if the current cell is safe (i.e., within bounds and not blocked). If safe, mark it as part of the path.
4.Recursively move either right or down, trying to find a path to the goal. If neither move works, backtrack by unmarking the current cell.
5.If a path is found, print the solution matrix; otherwise, print that no solution exists.


```
/*
Program to implement Rat in a Maze.
Developed by: Jayaseelan U
Register Number:  212223220039
*/
```
## Program:
```
N = 4
 
def printSolution(sol):
    for i in sol:
        for j in i:
            print(str(j) + " ", end="")
        print("")

def isSafe(maze, x, y):
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
    return False

def solveMaze(maze):
    sol = [[0 for j in range(4)] for i in range(4)]
    
    if not solveMazeUtil(maze, 0, 0, sol):
        print("Solution doesn't exist")
        return False
    
    printSolution(sol)
    return True

def solveMazeUtil(maze, x, y, sol):
    if x == N - 1 and y == N - 1 and maze[x][y] == 1:
        sol[x][y] = 1
        return True
    
    if isSafe(maze, x, y):
        sol[x][y] = 1
        
        if solveMazeUtil(maze, x + 1, y, sol):
            return True
        
        if solveMazeUtil(maze, x, y + 1, sol):
            return True
        
        sol[x][y] = 0
        return False
    
    return False

if __name__ == "__main__":
    maze = [
        [1, 0, 0, 0],
        [1, 1, 0, 1],
        [0, 1, 0, 0],
        [1, 1, 1, 1]
    ]
    
    solveMaze(maze)

```

## Output:

![437671256-047c22b5-2ec1-45e1-b1a5-0ff9e5364f93](https://github.com/user-attachments/assets/c2dbd290-93b4-400d-b75d-6b4019559894)




## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
