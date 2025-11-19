
# EX 4C Coin Change Problem - Dynamic Programming.
## DATE:25/10/2025
## AIM:
To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm
1.Read the coin denominations and the target amount, and initialize a DP array of size amount + 1 with a large value.

2.Set dp[0] = 0 because zero coins are needed to make amount 0.

3.For each coin, update the DP array by checking if using that coin reduces the number of coins needed for each amount.

4.Compute dp[i] = min(dp[i], dp[i - coin] + 1) for all valid i.

5.If dp[amount] is still larger than the amount, return -1; otherwise return dp[amount].  

## Program:
```
Coin Change Problem - Dynamic Programming.
Developed by: Karthick K
Register Number: 212222040070
```
```java
import java.util.*;

public class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); // initialize with a large value
        dp[0] = 0;

        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }


    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();
        String coinsLine = scanner.nextLine(); 
        String amountLine = scanner.nextLine();
        coinsLine = coinsLine.replaceAll("[^0-9,]", ""); 
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);

        scanner.close();
    }
}


```

## Output:
<img width="1282" height="360" alt="image" src="https://github.com/user-attachments/assets/1b98ef64-540a-4ab6-a796-102f9521da2b" />



## Result:
The program successfully implemented and the expected output is verified.
