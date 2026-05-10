# Climbing Stairs | Dynamic Programming in Java

You are given `N` stairs.

Initially, you are standing at stair `0` and your goal is to reach stair `N`.

At every move:
- you can climb `1 step`
- or `2 steps`

Return the total number of distinct ways to reach the `Nth` stair.

Since the answer can be very large, return it modulo:

:contentReference[oaicite:0]{index=0}

---

# Problem Statement

Given an integer `N`, count the number of distinct ways to reach the `Nth` stair if:
- at every step you may climb either `1` stair or `2` stairs.

---

# Example

## Input

```text
N = 3
```

## Output

```text
3
```

## Explanation

Possible ways:

```text
1 → 1 → 1
1 → 2
2 → 1
```

Total ways = `3`

---

# 🧠 Intuition

To reach stair `n`:
- either come from `(n-1)` using 1 step
- or come from `(n-2)` using 2 steps

Therefore:

:contentReference[oaicite:1]{index=1}

This is exactly similar to the Fibonacci pattern.

---

# 1️⃣ Recursive Approach

## Intuition

At every stair:
- take 1 step
- or take 2 steps

Recursively calculate all possible ways.

---

## Recursive Code

```java
public class ClimbingStairsRecursion {

    static int MOD = 1000000007;

    static int countWays(int n) {

        // Base Cases
        if (n == 0)
            return 1;

        if (n < 0)
            return 0;

        return (countWays(n - 1) + countWays(n - 2)) % MOD;
    }

    public static void main(String[] args) {

        int n = 3;

        System.out.println(countWays(n));
    }
}
```

---

# Recursive Tree

```text
countWays(3)
├── countWays(2)
│   ├── countWays(1)
│   └── countWays(0)
└── countWays(1)
```

Notice:
- `countWays(1)` is repeated
- many states repeat multiple times

This causes exponential complexity.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(2^n) |
| Space | O(n) recursion stack |

---

# 🔄 Converting Recursion → Memoization

## Problem in Recursion

The same subproblems are solved repeatedly.

Example:
- `countWays(3)` calls `countWays(2)`
- `countWays(2)` again calls `countWays(1)`

Repeated calculations waste time.

---

## Optimization Idea

Store already computed answers inside a DP array.

Before solving:
- check if answer already exists
- if yes → reuse it

This avoids recomputation.

---

# 2️⃣ Top-Down DP (Memoization)

## Memoization Code

```java
import java.util.Arrays;

public class ClimbingStairsMemoization {

    static int MOD = 1000000007;

    static int countWays(int n, int[] dp) {

        // Base Cases
        if (n == 0)
            return 1;

        if (n < 0)
            return 0;

        // Step 1: Return if already computed
        if (dp[n] != -1)
            return dp[n];

        // Step 2: Store and return
        dp[n] = (countWays(n - 1, dp) + countWays(n - 2, dp)) % MOD;

        return dp[n];
    }

    public static void main(String[] args) {

        int n = 5;

        int[] dp = new int[n + 1];

        Arrays.fill(dp, -1);

        System.out.println(countWays(n, dp));
    }
}
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) + recursion stack |

---

# 🔄 Converting Memoization → Tabulation

## Observation

Memoization:
- works recursively
- solves states top-down

Tabulation:
- removes recursion
- solves states bottom-up

---

# Steps to Convert

## Step 1
Create DP array

```java
int[] dp = new int[n + 1];
```

---

## Step 2
Initialize base case

```java
dp[0] = 1;
```

Why?

Because there is exactly ONE way to stay at stair `0`.

---

## Step 3
Build answers iteratively

For every stair:
- add ways from previous stair
- add ways from two stairs behind

---

# 3️⃣ Bottom-Up DP (Tabulation)

## Tabulation Code

```java
public class ClimbingStairsTabulation {

    static int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 5;

        int[] dp = new int[n + 1];

        // Base Case
        dp[0] = 1;

        for (int i = 1; i <= n; i++) {

            int oneStep = dp[i - 1];

            int twoStep = 0;

            if (i > 1)
                twoStep = dp[i - 2];

            dp[i] = (oneStep + twoStep) % MOD;
        }

        System.out.println(dp[n]);
    }
}
```

---

# DP Array Visualization

For `n = 5`

```text
Index : 0 1 2 3 4 5
Value : 1 1 2 3 5 8
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) |

---

# 🔄 Converting Tabulation → Space Optimization

## Observation

To compute current stair:
- we only need:
  - previous stair
  - second previous stair

So storing entire DP array is unnecessary.

---

# From

```java
dp[i] = dp[i - 1] + dp[i - 2]
```

We only require:
- previous
- second previous

---

# 4️⃣ Space Optimized Solution

## Space Optimized Code

```java
public class ClimbingStairsSpaceOptimization {

    static int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 5;

        // Base Case
        if (n == 0) {
            System.out.println(1);
            return;
        }

        int prev2 = 1; // dp[0]
        int prev1 = 1; // dp[1]

        for (int i = 2; i <= n; i++) {

            int current = (prev1 + prev2) % MOD;

            prev2 = prev1;
            prev1 = current;
        }

        System.out.println(prev1);
    }
}
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(1) |

---

# 📊 Final Comparison

| Approach | Time | Space |
|---|---|---|
| Recursion | O(2^n) | O(n) |
| Memoization | O(n) | O(n) + recursion stack |
| Tabulation | O(n) | O(n) |
| Space Optimization | O(n) | O(1) |

---

# 🧠 Important Observations

## Why `dp[0] = 1`?

Because:
- there is exactly one way to stand at stair `0`
- by doing nothing

---

## Relation with Fibonacci

The recurrence:

:contentReference[oaicite:2]{index=2}

is identical to Fibonacci.

Therefore:
- Climbing Stairs follows Fibonacci pattern
- many DP problems are modified Fibonacci problems

---

# 🚀 Conclusion

This problem is one of the best beginner Dynamic Programming problems.

It teaches:
- recursion
- overlapping subproblems
- memoization
- tabulation
- space optimization

Flow of optimization:

```text
Recursion
   ↓
Memoization
   ↓
Tabulation
   ↓
Space Optimization
```

Mastering this pattern is essential for solving advanced DP problems.
