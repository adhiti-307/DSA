# Count Derangements | Dynamic Programming in Java

A **Derangement** is a permutation of `N` elements such that no element appears in its original position.

---

# Problem Statement

Given an integer `N`,
find the total number of possible derangements of `N` elements.

Since the answer can be very large,
return the answer modulo:

```text
10^9 + 7
```

---

# What is a Derangement?

Suppose we have:

```text
{0,1,2,3}
```

A valid derangement:

```text
{2,3,1,0}
```

Why valid?

| Element | Original Position | New Position |
|---|---|---|
| 0 | 0 | 3 |
| 1 | 1 | 2 |
| 2 | 2 | 0 |
| 3 | 3 | 1 |

No element remains in its original position.

---

# Example

## Input

```text
N = 3
```

## Output

```text
2
```

## Explanation

Possible derangements:

```text
[2,3,1]
[3,1,2]
```

Total derangements = `2`

---

# 🧠 Intuition

Suppose there are `n` people and `n` positions.

Take one person.

They cannot stay in their original position.

So:
- they have `(n-1)` possible positions.

Now two cases arise.

---

# Case 1 → Swap

Suppose:
- person `1` goes to position `2`
- and person `2` goes to position `1`

Now remaining problem becomes:

```text
D(n-2)
```

---

# Case 2 → No Swap

Person `2` does NOT go to position `1`.

Now remaining problem becomes:

```text
D(n-1)
```

---

# Therefore

Total recurrence becomes:

```text
D(n) = (n-1) × (D(n-1) + D(n-2))
```

---

# Base Cases

```text
D(1) = 0
```

Because:
- one element can never be displaced.

---

```text
D(2) = 1
```

Only one derangement exists:

```text
[2,1]
```

---

# 1️⃣ Recursive Approach

# Intuition

Recursively calculate:
- derangements of `(n-1)`
- derangements of `(n-2)`

Then apply recurrence relation.

---

# Recursive Code

```java
public class CountDerangementsRecursion {

    static final int MOD = 1000000007;

    static long solve(int n) {

        // Base Cases
        if (n == 1)
            return 0;

        if (n == 2)
            return 1;

        return ((n - 1) *
                ((solve(n - 1) + solve(n - 2)) % MOD)
        ) % MOD;
    }

    public static void main(String[] args) {

        int n = 4;

        System.out.println(solve(n));
    }
}
```

---

# Recursive Tree

```text
D(5)
├── D(4)
│   ├── D(3)
│   └── D(2)
└── D(3)
```

Notice:
- `D(3)` repeats multiple times.

This creates overlapping subproblems.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | Exponential |
| Space | O(n) recursion stack |

---

# 🔄 Converting Recursion → Memoization

# Problem in Recursion

Same states are recalculated repeatedly.

Example:
- `D(3)`
- `D(4)`

get recomputed multiple times.

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

public class CountDerangementsMemoization {

    static final int MOD = 1000000007;

    static long solve(int n, long[] dp) {

        // Base Cases
        if (n == 1)
            return 0;

        if (n == 2)
            return 1;

        // Step 1: Return if already computed
        if (dp[n] != -1)
            return dp[n];

        long first = solve(n - 1, dp) % MOD;

        long second = solve(n - 2, dp) % MOD;

        // Step 2: Store and return
        dp[n] = ((n - 1) *
                ((first + second) % MOD)
        ) % MOD;

        return dp[n];
    }

    public static void main(String[] args) {

        int n = 4;

        long[] dp = new long[n + 1];

        Arrays.fill(dp, -1);

        System.out.println(solve(n, dp));
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

# Observation

Memoization:
- recursive
- top-down

Tabulation:
- iterative
- bottom-up

---

# DP Meaning

```text
dp[i] = number of derangements for i elements
```

---

# Transition

```text
dp[i] =
(i-1) × (dp[i-1] + dp[i-2])
```

---

# Steps to Convert

## Step 1
Create DP array

```java
long[] dp = new long[n+1];
```

---

## Step 2
Initialize base cases

```java
dp[1] = 0;
dp[2] = 1;
```

---

## Step 3
Build DP table iteratively

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
public class CountDerangementsTabulation {

    static final int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 4;

        long[] dp = new long[n + 1];

        // Base Cases
        dp[1] = 0;

        dp[2] = 1;

        // Build DP Table
        for (int i = 3; i <= n; i++) {

            dp[i] = ((i - 1) *
                    ((dp[i - 1] + dp[i - 2]) % MOD)
                    ) % MOD;
        }

        System.out.println(dp[n]);
    }
}
```

---

# DP Array Visualization

For:

```text
N = 5
```

DP table:

```text
Index : 1 2 3 4 5
DP    : 0 1 2 9 44
```

Answer:

```text
44
```

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) |

---

# 🔄 Converting Tabulation → Space Optimization

# Observation

Current state depends only on:
- previous state
- second previous state

Therefore:
- entire DP array is unnecessary.

---

# From

```text
dp[i] =
(i-1) × (dp[i-1] + dp[i-2])
```

We only require:
- `prev1`
- `prev2`

---

# 4️⃣ Space Optimized Solution

# Space Optimized Code

```java
public class CountDerangementsSpaceOptimization {

    static final int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 5;

        // Base Cases
        if (n == 1) {
            System.out.println(0);
            return;
        }

        if (n == 2) {
            System.out.println(1);
            return;
        }

        long prev2 = 0; // D(1)

        long prev1 = 1; // D(2)

        for (int i = 3; i <= n; i++) {

            long current =
                    ((i - 1) *
                    ((prev1 + prev2) % MOD)
                    ) % MOD;

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
| Recursion | Exponential | O(n) |
| Memoization | O(n) | O(n) + recursion stack |
| Tabulation | O(n) | O(n) |
| Space Optimization | O(n) | O(1) |

---

# 🧠 Important DP Pattern

This problem follows:

```text
Current Answer =
Current Choices × Previous Answers
```

Transition:

```text
D(n) =
(n-1) × (D(n-1) + D(n-2))
```

This pattern appears in:
- combinatorics DP
- permutation counting
- arrangement problems
- counting DP

---

