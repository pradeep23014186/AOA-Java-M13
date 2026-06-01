
# EX 3B Rat in Maze- Backtracking 
## DATE: 01/05/2026
## AIM:
To write a Java program to for given constraints.
There is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm
1. Start the program and read the maze dimensions, maze elements, start position, and destination position.
2. Create a visited array to keep track of already explored positions in the maze.
3. From the current position, roll the ball in all four directions (up, down, left, right) until it hits a wall or boundary.
4. Use Depth First Search (DFS) recursively to explore each stopping position and check whether the destination is reached.
5. If the destination is reached, return true; otherwise, after exploring all possible paths, return false and stop the program.   

## Program:
```
Program to implement Reverse a String
Developed by: Krishna Prasad S
Register Number: 212223230108
```
```java
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read maze dimensions
        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        // Read start position
        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

        // Read destination position
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    
    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        
        int x = curr[0];
        int y = curr[1];
        
        if (visit[x][y]) {
            return false;
        }
        
        visit[x][y] = true;
        
        if (x == destination[0] && y == destination[1]) 
        {
            return true;
        }
        
        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
        
        for (int[] dir : dirs) 
        {
            int nx = x;
            int ny = y;
            
            while (nx + dir[0] >= 0 && nx + dir[0] < m &&
                   ny + dir[1] >= 0 && ny + dir[1] < n &&
                   maze[nx + dir[0]][ny + dir[1]] == 0) {
                
                nx += dir[0];
                ny += dir[1];
            }
            
            if (dfs(m, n, maze, new int[]{nx, ny}, destination, visit)) 
            {
                return true;
            }
        }
        
        return false;
    }
    
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        
        boolean[][] visit = new boolean[m][n];
        
        return dfs(m, n, maze, start, destination, visit);
    }
}

```

## Output:

<img width="368" height="539" alt="output2" src="https://github.com/user-attachments/assets/62bc3cf1-cab4-43ec-bf49-f3a9fc64b68f" />


## Result:
The program successfully implemented and the expected output is verified.
