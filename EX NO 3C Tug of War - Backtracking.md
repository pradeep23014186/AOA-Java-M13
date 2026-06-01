
# EX 3C Tug of War problem - Backtracking.
## DATE: 01/05/2026
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Start the program and read the number of elements and array values from the user.
2. Calculate the total sum of all elements in the array.
3. If the total sum is odd, return false because the array cannot be divided into two equal subsets.
4. Use Dynamic Programming to check whether a subset with sum equal to total sum / 2 can be formed from the array elements.
5. If such a subset exists, print true; otherwise, print false and stop the program.   

## Program:
```
Program to implement Reverse a String
Developed by: Krishna Prasad S
Register Number: 212223230108
```
```java
import java.util.Scanner;
public class Solution 
{
    public boolean canPartition(int[] nums) 
    {
        if(nums.length == 0) return false;
        int tot = 0;
        for(int num : nums) tot += num;
        if(tot%2 != 0) return false;
        int subset_sum = tot/2;
        boolean dp[] = new boolean[subset_sum+1];
        dp[0] = true;
        for(int curr : nums)
        {
            for(int j=subset_sum; j>=curr; j--)
            {
                dp[j] = dp[j-curr];
            }
        }
        return dp[subset_sum];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:

<img width="417" height="240" alt="output3" src="https://github.com/user-attachments/assets/e0654107-d462-4883-95e8-43216c314ca4" />


## Result:
The program successfully implemented and the expected output is verified.
