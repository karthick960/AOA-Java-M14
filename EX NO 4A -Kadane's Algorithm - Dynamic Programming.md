
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## DATE:21/10/2025
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6
## Algorithm
1. Read n and the energy array, and compute the total sum.

2.Apply Kadane’s algorithm to find the maximum subarray sum (maxKadane).

3.Apply modified Kadane’s algorithm to find the minimum subarray sum (minKadane).

4.Compute circular maximum sum as totalSum - minKadane.

5.Final answer = max(maxKadane, circularMax) unless all numbers are negative, then answer = maxKadane.
   

## Program:

Kadane's Algorithm - Dynamic Programming.
Developed by: Karthick K
Register Number: 212222040070
```java
import java.util.*;

public class Main {

    public static int kadaneMax(int[] arr) {
        int maxEnding = arr[0];
        int maxSoFar = arr[0];
        for (int i = 1; i < arr.length; i++) {
            maxEnding = Math.max(arr[i], maxEnding + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEnding);
        }
        return maxSoFar;
    }

    public static int kadaneMin(int[] arr) {
        int minEnding = arr[0];
        int minSoFar = arr[0];
        for (int i = 1; i < arr.length; i++) {
            minEnding = Math.min(arr[i], minEnding + arr[i]);
            minSoFar = Math.min(minSoFar, minEnding);
        }
        return minSoFar;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }

        int maxKadane = kadaneMax(energy);   
        int minKadane = kadaneMin(energy);  
        int totalSum = 0;

        for (int x : energy) {
            totalSum += x;
        }

        int result;
        if (totalSum == minKadane) {
            result = maxKadane;
        } else {
            int circularMax = totalSum - minKadane;
            result = Math.max(maxKadane, circularMax);
        }

        System.out.println(result);
        sc.close();
    }
}


```

## Output:
<img width="1282" height="407" alt="image" src="https://github.com/user-attachments/assets/6f15aa07-9e2d-4232-ac99-b2b3df5edc06" />


## Result:
The program successfully Implemented and the output is verified. 
