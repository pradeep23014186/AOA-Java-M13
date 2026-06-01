
# EX 3A N Queens Problem - Backtracking Approach.
## DATE: 01/05/2026
## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm
1. Start the program and read the value of N from the user.
2. Create an N × N chessboard initialized with 0s to represent empty cells.
3. Place queens column by column and check whether each position is safe by verifying the row, upper diagonal, and lower diagonal.
4. If a safe position is found, place the queen and recursively move to the next column; if no safe position exists, backtrack and try another position.
5. If all queens are placed successfully, print the board configuration; otherwise, print "Solution does not exist" and stop the program.   

## Program:
```
Program to implement Reverse a String
Developed by: Krishna Prasad S
Register Number: 212223230108
```
```java
import java.util.Scanner;

public class NQueens {
    static int N;

    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    static boolean isSafe(int[][] board, int row, int col) {
        // Check left side of current row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

       
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    // Recursive utility function to solve N-Queens
    static boolean solveNQUtil(int[][] board, int col) 
    {
        if(col >= N) return true;
        
        for(int i=0; i<N; i++)
        {
            if(isSafe(board, i, col))
            {
                board[i][col] = 1;
                if(solveNQUtil(board, col+1)) return true;
                board[i][col] = 0;
            }
        }
        return false;
    }

    
    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

   
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt(); // Accept board size
        solveNQ();
    }
}

```

## Output:

<img width="661" height="270" alt="output1" src="https://github.com/user-attachments/assets/e3fe6c23-26f7-45f1-a9d2-344bf8dd324f" />


## Result:
The program successfully implemented and the ouput is verified. 
