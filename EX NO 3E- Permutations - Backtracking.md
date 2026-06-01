
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 01/05/2026
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Start the program and read the array elements from the user.
2. Create an empty list to store all possible permutations.
3. Use a backtracking function to build permutations by adding elements that are not already included in the current permutation.
4. When the size of the current permutation becomes equal to the array length, store it in the result list; otherwise, continue exploring other possibilities by backtracking.
5. Print all generated permutations and stop the program.   

## Program:
```
Program to implement Reverse a String
Developed by: Krishna Prasad S
Register Number: 212223230108
```
```java
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) 
    {
        
        List<List<Integer>> result = new ArrayList<>();
        backtrack(new ArrayList<>(), result, nums);
        return result;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> result, int[] nums) 
    {
        if(curr.size() == nums.length)
        {
            result.add(new ArrayList<>(curr));
            return;
        }
        for(int num : nums)
        {
            if(!curr.contains(num))
            {
                curr.add(num);
                backtrack(curr, result, nums);
                curr.remove(curr.size()-1);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}

```

## Output:

<img width="1148" height="167" alt="output5" src="https://github.com/user-attachments/assets/a94cf8f4-9e79-475f-8b99-4405d4f2c924" />


## Result:
The program successfully implemented and the expected output is verified.
