
# EX 4E Longest Increasing Subsequence - Dynamic Programming.
## DATE:29/10/2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return the length of the longest strictly increasing subsequence.
Example 1:
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
## Algorithm
1.Read the array and create a DP array dp[] where each element starts with value 1.

2.Traverse the array with two loops: outer index i, inner index j from 0 to i-1.

3.If nums[i] > nums[j], update dp[i] = max(dp[i], dp[j] + 1).

4.Track the maximum value in the DP array during the process.

5.The final answer is the maximum value in dp[], representing the length of the LIS.   

## Program:
```
Longest Increasing Subsequence - Dynamic Programming.
Developed by: Karthick K
Register Number: 212222040070
```

```
import java.util.*;

public class LongestIncreasingSubsequence {

    public static int lengthOfLIS(int[] nums) {

        int n = nums.length;
        int[] dp = new int[n];

        // Every element is at least an LIS of length 1
        Arrays.fill(dp, 1);

        int maxLen = 1;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[j] < nums[i]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}
```

## Output:
<img width="1221" height="385" alt="image" src="https://github.com/user-attachments/assets/05f59db1-6e8c-4431-8513-ee1f036f9b6a" />



## Result:
The program successfully implemented and the expected output is verified.
