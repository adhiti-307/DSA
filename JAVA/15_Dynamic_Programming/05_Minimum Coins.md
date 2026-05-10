# Minimum Coins | Dynamic Programming in Java

You are given:
- an array of distinct integers `coins[]`
- a target sum `X`

You have an infinite supply of every coin.

Return the minimum number of coins required to make the target sum `X`.

If it is not possible to make the target, return `-1`.

---

# Problem Statement

Given:
- `N` distinct coin denominations
- target sum `X`

Find the minimum number of coins needed to make sum `X`.

You may use any coin unlimited times.

---

# Example

## Input

```text
coins = [1, 2, 3]
X = 7
```

## Output

```text
3
```

## Explanation

Possible ways:

```text
2 + 2 + 2 + 1 = 7  → 4 coins
3 + 3 + 1 = 7      → 3 coins
```

Minimum coins required = `3`

---

# 🧠 Intuition

At every step:
- choose a coin
- reduce target by that coin value

Then recursively solve for the remaining target.

If we pick coin `c`:

```text
remaining target = target - c
```

Therefore:

```text
answer = 1 + minimum coins needed for remaining target
```

Recurrence:

```text
f(target) = 1 + min(f(target - coin))
```

for all valid coins.

---

# 1️⃣ Recursive Approach

# Intuition

Try every possible coin:
- subtract coin value from target
- recursively solve remaining target
- take minimum answer

---

# Recursive Code

```java
public class MinimumCoinsRecursion {

    static int solve(int[] coins, int target) {

        // Base Case
        if (target == 0)
            return 0;

        int mini = Integer.MAX_VALUE;

        for (int coin : coins) {

            if (target - coin >= 0) {

                int ans = solve(coins, target - coin);

                // Valid Answer Check
                if (ans != Integer.MAX_VALUE) {

                    mini = Math.min(mini, 1 + ans);
                }
            }
        }

        return mini;
    }

    public static void main(String[] args) {

        int[] coins = {1, 2, 3};

        int target = 7;

        int ans = solve(coins, target);

        if (ans == Integer.MAX_VALUE)
            System.out.println(-1);
        else
            System.out.println(ans);
    }
}
```

---

# Recursive Tree

For target = `7`

```text
solve(7)
├── solve(6)
├── solve(5)
└── solve(4)
```

States repeat multiple times:
- `solve(4)`
- `solve(3)`
- `solve(2)`

This causes exponential complexity.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | Exponential |
| Space | O(target) recursion stack |

---

# 🔄 Converting Recursion → Memoization

# Problem in Recursion

The same target values are solved repeatedly.

Example:
- `solve(4)` computed many times
- `solve(3)` also repeats

This creates unnecessary work.

---

# Optimization Idea

Store already computed answers inside a DP array.

Before solving:
- check if answer already exists
- if yes → reuse it

---

# 2️⃣ Top-Down DP (Memoization)

# Memoization Code

```java
import java.util.Arrays;

public class MinimumCoinsMemoization {

    static int solve(int[] coins, int target, int[] dp) {

        // Base Case
        if (target == 0)
            return 0;

        // Step 1: Return if already computed
        if (dp[target] != -1)
            return dp[target];

        int mini = Integer.MAX_VALUE;

        for (int coin : coins) {

            if (target - coin >= 0) {

                int ans = solve(coins, target - coin, dp);

                if (ans != Integer.MAX_VALUE) {

                    mini = Math.min(mini, 1 + ans);
                }
            }
        }

        // Step 2: Store and return
        dp[target] = mini;

        return dp[target];
    }

    public static void main(String[] args) {

        int[] coins = {1, 2, 3};

        int target = 7;

        int[] dp = new int[target + 1];

        Arrays.fill(dp, -1);

        int ans = solve(coins, target, dp);

        if (ans == Integer.MAX_VALUE)
            System.out.println(-1);
        else
            System.out.println(ans);
    }
}
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(N × target) |
| Space | O(target) + recursion stack |

---

# 🔄 Converting Memoization → Tabulation

# Observation

Memoization:
- solves states recursively
- top-down approach

Tabulation:
- solves iteratively
- bottom-up approach

---

# Steps to Convert

## Step 1
Create DP array

```java
int[] dp = new int[target + 1];
```

---

## Step 2
Initialize all values as infinity

```java
Arrays.fill(dp, Integer.MAX_VALUE);
```

---

## Step 3
Base Case

```java
dp[0] = 0;
```

Why?

Because:
- zero coins are needed to make target `0`

---

## Step 4
Build DP table from smaller targets to larger targets

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
import java.util.Arrays;

public class MinimumCoinsTabulation {

    public static void main(String[] args) {

        int[] coins = {1, 2, 3};

        int target = 7;

        int[] dp = new int[target + 1];

        Arrays.fill(dp, Integer.MAX_VALUE);

        // Base Case
        dp[0] = 0;

        // Build DP Table
        for (int i = 1; i <= target; i++) {

            for (int coin : coins) {

                if (i - coin >= 0 && dp[i - coin] != Integer.MAX_VALUE) {

                    dp[i] = Math.min( dp[i], 1 + dp[i - coin] );
                }
            }
        }

        if (dp[target] == Integer.MAX_VALUE)
            System.out.println(-1);
        else
            System.out.println(dp[target]);
    }
}
```

---

# DP Array Visualization

For:

```text
coins = [1,2,3]
target = 7
```

DP table:

```text
Index : 0 1 2 3 4 5 6 7
DP    : 0 1 1 1 2 2 2 3
```

Answer:

```text
dp[7] = 3
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(N × target) |
| Space | O(target) |

---

# 🔄 Converting Tabulation → Space Optimization

# Observation

Unlike Fibonacci-style problems:
- every target depends on many previous states

Example:

```text
dp[7] depends on:
dp[6], dp[5], dp[4]
```

So we cannot reduce DP array into just:
- two variables
- or few variables

Because:
- many previous states are needed.

---

# 🚫 Space Optimization Not Possible

For Coin Change Minimum Coins problem:

```text
1D DP array is already the optimized solution.
```

Further optimization is generally not possible.

---

# 4️⃣ Optimized Solution

The tabulation solution itself is the most optimized version.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(N × target) |
| Space | O(target) |

---

# 📊 Final Comparison

| Approach | Time | Space |
|---|---|---|
| Recursion | Exponential | O(target) |
| Memoization | O(N × target) | O(target) + recursion stack |
| Tabulation | O(N × target) | O(target) |
| Optimized | O(N × target) | O(target) |

---

# 🧠 Important DP Pattern

This problem follows:

```text
Take one choice
+
solve remaining target
```

Transition:

```text
dp[target] =
1 + min(dp[target - coin])
```

This pattern appears in:
- Coin Change
- Minimum Cost problems
- Unbounded Knapsack
- Rod Cutting
- Integer Partition problems

---

# 🚀 Conclusion

This is one of the most important unbounded DP problems.

It teaches:
- infinite choices
- minimization DP
- state transition
- target reduction pattern

Optimization journey:

```text
Recursion
   ↓
Memoization
   ↓
Tabulation
```

For this problem:
- 1D DP is already optimal.

Mastering this problem helps in solving advanced:
- knapsack
- partition
- target sum
- unbounded DP problems.
