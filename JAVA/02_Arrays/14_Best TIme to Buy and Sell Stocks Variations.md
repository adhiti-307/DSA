# Best Time to Buy and Sell Stock Variations (LeetCode)

---

## 1. Best Time to Buy and Sell Stock (Single Transaction)

### Problem Statement

You are given an array where `prices[i]` is the price of a stock on day `i`.
Find the maximum profit you can achieve with **only one transaction** (buy once and sell once).

### Input

prices = [7,1,5,3,6,4]

### Output

5

### Explanation

Buy at price 1 and sell at price 6 → profit = 5

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

### Java Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for(int i = 0; i < prices.length; i++){
            if(prices[i] < minPrice){
                minPrice = prices[i];
            } else {
                int profit = prices[i] - minPrice;
                maxProfit = Math.max(maxProfit, profit);
            }
        }

        return maxProfit;
    }
}
```

---

## 2. Best Time to Buy and Sell Stock II (Unlimited Transactions)

### Problem Statement

You may complete as many transactions as you like but hold only 1 stock at a time.
Find the maximum profit.

### Input

prices = [7,1,5,3,6,4]

### Output

7

### Explanation

Buy at 1 → sell at 5
Buy at 3 → sell at 6
Total profit = 7

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

### Java Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) {
                profit += prices[i] - prices[i - 1];
            }
        }

        return profit;
    }
}
```

---

## 3. Best Time to Buy and Sell Stock III (At Most 2 Transactions)

### Problem Statement

You may complete at most **two transactions**.

### Input

prices = [3,3,5,0,0,3,1,4]

### Output

6

### Explanation

Buy at 0 → sell at 3
Buy at 1 → sell at 4
Total profit = 6

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/

### Java Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buy1 = Integer.MIN_VALUE;
        int sell1 = 0;
        int buy2 = Integer.MIN_VALUE;
        int sell2 = 0;

        for (int price : prices) {
            buy1 = Math.max(buy1, -price);
            sell1 = Math.max(sell1, buy1 + price);
            buy2 = Math.max(buy2, sell1 - price);
            sell2 = Math.max(sell2, buy2 + price);
        }

        return sell2;
    }
}
```

---

## 4. Best Time to Buy and Sell Stock IV (At Most K Transactions)

### Problem Statement

You may complete at most **k transactions**.

### Input

k = 2, prices = [2,4,1]

### Output

2

### Explanation

Buy at 2 → sell at 4 → profit = 2

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/

### Java Code

```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        int n = prices.length;
        if (n == 0) return 0;

        // Optimization: behaves like unlimited transactions
        if (k >= n / 2) {
            int profit = 0;
            for (int i = 1; i < n; i++) {
                if (prices[i] > prices[i - 1]) {
                    profit += prices[i] - prices[i - 1];
                }
            }
            return profit;
        }

        int[] buy = new int[k + 1];
        int[] sell = new int[k + 1];

        Arrays.fill(buy, Integer.MIN_VALUE);

        for (int price : prices) {
            for (int t = 1; t <= k; t++) {
                buy[t] = Math.max(buy[t], sell[t - 1] - price);
                sell[t] = Math.max(sell[t], buy[t] + price);
            }
        }

        return sell[k];
    }
}
```

---

## 5. Best Time to Buy and Sell Stock with Cooldown

### Problem Statement

After selling a stock, you must wait **one day** before buying again.

### Input

prices = [1,2,3,0,2]

### Output

3

### Explanation

Buy → Sell → Cooldown → Buy → Sell

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/

### Java Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length == 0) return 0;

        int hold = -prices[0];
        int sold = 0;
        int rest = 0;

        for (int i = 1; i < prices.length; i++) {
            int prevSold = sold;

            sold = hold + prices[i];              // sell today
            hold = Math.max(hold, rest - prices[i]); // buy or keep holding
            rest = Math.max(rest, prevSold);      // cooldown or stay idle
        }

        return Math.max(sold, rest);
    }
}
```

---

## 6. Best Time to Buy and Sell Stock with Transaction Fee

### Problem Statement

Each transaction has a fixed fee.
Find the maximum profit.

### Input

prices = [1,3,2,8,4,9], fee = 2

### Output

8

### Explanation

Profit after accounting for fee on each transaction

### Link

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/

### Java Code

```java
class Solution {
    public int maxProfit(int[] prices, int fee) {
        int hold = -prices[0];
        int cash = 0;

        for (int i = 1; i < prices.length; i++) {
            int prevCash = cash;

            cash = Math.max(cash, hold + prices[i] - fee); // sell
            hold = Math.max(hold, prevCash - prices[i]);   // buy
        }

        return cash;
    }
}
```

---

# Summary

| Problem | Constraint     | Approach |
| ------- | -------------- | -------- |
| 121     | 1 transaction  | Greedy   |
| 122     | Unlimited      | Greedy   |
| 123     | 2 transactions | DP       |
| 188     | K transactions | DP       |
| 309     | Cooldown       | DP       |
| 714     | Fee            | DP       |

---

# Key Pattern

```
Stock Problems → State Machine (Buy / Sell / Profit)
```
