
# EX 4B Frog Jump - Dynamic Programming.
## DATE:23/10/2025
## AIM:
To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm
1.Read the number of steps n.

2.If n is 0 or 1, return 1 because there is only one way.

3.Create an array dp where dp[i] stores ways to reach step i.

4.Initialize dp[0] = 1 and dp[1] = 1, then fill the array using dp[i] = dp[i-1] + dp[i-2].

5.Output dp[n] as the total number of distinct ways to reach the top.   

## Program:
```
Frog Jump - Dynamic Programming.
Developed by: Karthick K
Register Number: 212222040070
```
```java
import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.close();
        System.out.println(countWays(n));
    }

    public static int countWays(int n) {
        if (n < 0) return 0;
        if (n == 0) return 1;
        if (n == 1) return 1;
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```
## Output:
<img width="1286" height="349" alt="image" src="https://github.com/user-attachments/assets/ace3ca72-5f63-473c-adfc-e174ba5995e6" />




## Result:
The program successfully implemented and the expected output is verified.
