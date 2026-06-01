
# EX 3D Sudoku solver - Backtracking.
## DATE: 01/05/2026
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Start the program and read the Sudoku puzzle into a 9 × 9 matrix, where 0 represents empty cells.
2. Traverse the board to find an empty cell.
3. For the empty cell, try placing numbers from 1 to 9 and check whether the number is safe by verifying the row, column, and 3 × 3 subgrid.
4. If a valid number is found, place it in the cell and recursively solve the remaining puzzle; if no number works, backtrack by resetting the cell to 0.
5. When all cells are filled successfully, print the solved Sudoku board; otherwise, print "No solution exists" and stop the program.  

## Program:
```
Program to implement Reverse a String
Developed by: Krishna Prasad S
Register Number: 212223230108
```
```java
import java.util.Scanner;

public class SudokuSolver {

    static boolean isSafe(int[][] board, int row, int col, int num) 
    {
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    static boolean solveSudoku(int[][] board, int row, int col) 
    {
        if(row == 8 && col == 9) return true;
        if(col == 9)
        {
            row++; col = 0;
        }
        if(board[row][col] != 0)
        {
            return (solveSudoku(board, row, col+1));
        }
        for(int num = 1; num <= 9; num++)
        {
            if(isSafe(board, row, col, num))
            {
                board[row][col] = num;
                if(solveSudoku(board, row, col+1)) return true;
                board[row][col] = 0;
            }
        }
        return false;
        
    }

    static void printBoard(int[][] board) 
    {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

      //  System.out.println("\nSolving...\n");

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```

## Output:

<img width="678" height="612" alt="outpu4" src="https://github.com/user-attachments/assets/839a56fc-24c8-4bf0-a306-63618f1fe473" />


## Result:
The program successfully implemented and the expected output is verified.
