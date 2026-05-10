# Minimum Cost Climbing Stairs | Dynamic Programming in Java

You are given an integer array `cost` where:

```text
cost[i] = cost of ith stair
```

After paying the cost of a stair, you can:
- climb 1 step
- or climb 2 steps

You may start from:
- index `0`
- or index `1`

Return the minimum cost required to reach the top floor.

---

# Problem Statement

Given an array `cost[]`, return the minimum cost to reach the top of the staircase.

The top is located just after the last index.

---

# Example 1

## Input

```text
cost = [10,15,20]
```

## Output

```text
15
```

## Explanation

Start from index `1`:

```text
15 → top
```

Total minimum cost = `15`

---

# Example 2

## Input

```text
cost = [1,100,1,1,1,100,1,1,100,1]
```

## Output

```text
6
```

---

# 🧠 Intuition

To reach stair `i`, we can come from:
- stair `i-1`
- stair `i-2`

If we stand at stair `i`,
we must pay:

```text
cost[i]
```

Therefore:

:contentReference[oaicite:0]{index=0}

The answer will be:

:contentReference[oaicite:1]{index=1}

because from the last or second last stair we can directly reach the top.

---

# 1️⃣ Recursive Approach

## Intuition

Define:

```text
f(i) = minimum cost to reach stair i
```

To reach stair `i`:
- come from `i-1`
- or from `i-2`

Take the minimum.

---

# Recursive Code

```java
public class MinCostClimbingStairsRecursion {

    static int solve(int[] cost, int n) {

        // Base Cases
        if (n == 0)
            return cost[0];

        if (n == 1)
            return cost[1];

        return cost[n] + Math.min(
                solve(cost, n - 1),
                solve(cost, n - 2)
        );
    }

    public static void main(String[] args) {

        int[] cost = {10, 15, 20};

        int n = cost.length;

        int ans = Math.min(
                solve(cost, n - 1),
                solve(cost, n - 2)
        );

        System.out.println(ans);
    }
}
```

---

# Recursive Tree

```text
solve(4)
├── solve(3)
│   ├── solve(2)
│   └── solve(1)
└── solve(2)
```

Notice:
- `solve(2)` repeats multiple times

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

Same states are solved repeatedly.

Example:
- `solve(2)` gets recomputed
- `solve(3)` also repeats

This wastes time.

---

# Optimization Idea

Store already computed answers inside a DP array.

Before computing:
- check if answer already exists
- if yes → reuse it

---

# 2️⃣ Top-Down DP (Memoization)

# Memoization Code

```java
import java.util.Arrays;

public class MinCostClimbingStairsMemoization {

    static int solve(int[] cost, int n, int[] dp) {

        // Base Cases
        if (n == 0)
            return cost[0];

        if (n == 1)
            return cost[1];

        // Step 1: Return if already computed
        if (dp[n] != -1)
            return dp[n];

        // Step 2: Store and return
        dp[n] = cost[n] + Math.min(
                solve(cost, n - 1, dp),
                solve(cost, n - 2, dp)
        );

        return dp[n];
    }

    public static void main(String[] args) {

        int[] cost = {10, 15, 20};

        int n = cost.length;

        int[] dp = new int[n];

        Arrays.fill(dp, -1);

        int ans = Math.min(
                solve(cost, n - 1, dp),
                solve(cost, n - 2, dp)
        );

        System.out.println(ans);
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
- works top-down
- uses recursion

Tabulation:
- works bottom-up
- removes recursion completely

---

# Steps to Convert

## Step 1
Create DP array

```java
int[] dp = new int[n];
```

---

## Step 2
Initialize base cases

```java
dp[0] = cost[0];
dp[1] = cost[1];
```

---

## Step 3
Fill DP table iteratively

For every stair:

```text
current cost + minimum(previous two states)
```

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
public class MinCostClimbingStairsTabulation {

    public static void main(String[] args) {

        int[] cost = {10, 15, 20};

        int n = cost.length;

        int[] dp = new int[n];

        // Base Cases
        dp[0] = cost[0];
        dp[1] = cost[1];

        // Build DP Table
        for (int i = 2; i < n; i++) {

            dp[i] = cost[i] + Math.min(
                    dp[i - 1],
                    dp[i - 2]
            );
        }

        int ans = Math.min(
                dp[n - 1],
                dp[n - 2]
        );

        System.out.println(ans);
    }
}
```

---

# DP Array Visualization

For:

```text
cost = [10,15,20]
```

DP table becomes:

```text
Index : 0   1   2
DP    : 10  15  30
```

Answer:

```text
min(30,15) = 15
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

To compute current state:
we only need:
- previous stair
- second previous stair

Entire DP array is unnecessary.

---

# From

```java
dp[i] = cost[i] + min(dp[i-1], dp[i-2])
```

We only need:
- prev1
- prev2

---

# 4️⃣ Space Optimized Solution

# Space Optimized Code

```java
public class MinCostClimbingStairsSpaceOptimization {

    public static void main(String[] args) {

        int[] cost = {10, 15, 20};

        int n = cost.length;

        int prev2 = cost[0];
        int prev1 = cost[1];

        for (int i = 2; i < n; i++) {

            int current = cost[i] + Math.min(prev1, prev2);

            prev2 = prev1;
            prev1 = current;
        }

        int ans = Math.min(prev1, prev2);

        System.out.println(ans);
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

# 🧠 Key Observations

## Why Answer is:

```java
min(dp[n-1], dp[n-2])
```

Because:
- from last stair → reach top
- from second last stair → also reach top

without paying additional cost.

---

# Important DP Pattern

This problem follows:

```text
Take current cost
+
best among previous choices
```

Pattern:

:contentReference[oaicite:2]{index=2}

This pattern appears in many:
- minimum path
- staircase
- grid
- energy minimization problems

---

# 🚀 Conclusion

This is one of the most important beginner DP problems.

It teaches:
- decision making
- minimizing cost
- state transition
- Fibonacci-style DP
- space optimization

Optimization journey:

```text
Recursion
   ↓
Memoization
   ↓
Tabulation
   ↓
Space Optimization
```

Mastering this transition is essential for advanced Dynamic Programming problems.
