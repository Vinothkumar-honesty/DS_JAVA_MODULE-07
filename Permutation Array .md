# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 04/08/2026
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm

1.Create a visited array to mark elements already used in any set.

2.For each index k, if it is not visited, start building the set S[k].

3.Keep moving to nums[current], marking each element as visited.

4.Count each step until you reach a visited element (duplicate).

5.Update the maximum count found so far and return it.  

## Program:
```
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: VINOTHKUMAR R
RegisterNumber:  212224040361
*/

import java.util.*;

public class ArrayNestingMain {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String input = sc.nextLine().trim();
        input = input.replace("nums =", "")
                     .replace("[", "")
                     .replace("]", "")
                     .trim();

        String[] parts = input.split(",");
        int[] nums = new int[parts.length];

        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        Solution sol = new Solution();
        int result = sol.arrayNesting(nums);

        System.out.println(result);
        sc.close();
    }
}

class Solution {
    public int arrayNesting(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {

            if (!visited[i]) {
                int current = i;
                int length = 0;

                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    length++;
                }

                maxLength = Math.max(maxLength, length);
            }
        }

        return maxLength;
    }
}

```

## Output:

<img width="883" height="187" alt="image" src="https://github.com/user-attachments/assets/7fbc52c9-1ee0-4b1b-a54d-29c38eb18482" />



## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
