# Fibonacci Number | Dynamic Programming in Java

The Fibonacci sequence is one of the most common introductory problems in Dynamic Programming.

In Fibonacci:
- `F(0) = 0`
- `F(1) = 1`

For every other number:

`F(n) = F(n-1) + F(n-2)`

---

# Problem Statement

Given an integer `n`, return the `nth` Fibonacci number.

---

# Example

```text
Input: n = 6
Output: 8
```

Explanation:

```text
0 1 1 2 3 5 8
            ↑
         Fibonacci(6)
```

---

# 1️⃣ Recursive Approach

## Intuition

To calculate `fib(n)`:
- we need `fib(n-1)`
- and `fib(n-2)`

So the problem naturally breaks into smaller subproblems.

---

## Recursive Code

```java
public class FibonacciRecursion {

    static int fib(int n) {

        // Base Case
        if (n <= 1)
            return n;

        return fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {

        int n = 6;

        System.out.println(fib(n));
    }
}
```

---

## Recursive Tree

```text
fib(5)
├── fib(4)
│   ├── fib(3)
│   │   ├── fib(2)
│   │   └── fib(1)
│   └── fib(2)
└── fib(3)
```

Notice:
- `fib(3)` gets calculated multiple times
- `fib(2)` also repeats

This is called:

✅ Overlapping Subproblems

---

## Complexity

| Complexity | Value |
|---|---|
| Time | O(2^n) |
| Space | O(n) recursion stack |

---

# 🔄 Converting Recursion → Memoization

## Problem in Recursion

The recursive solution recomputes the same states again and again.

Example:
- `fib(3)` computed multiple times
- `fib(2)` computed multiple times

We can optimize this by storing already computed results.

This storage array is called:

✅ DP Array  
✅ Memo Table

---

# 2️⃣ Top-Down DP (Memoization)

## Intuition

Before computing a state:
- check if already computed
- if yes → return stored value
- otherwise compute and store it

---

## Memoization Code

```java
import java.util.Arrays;

public class FibonacciMemoization {

    static int fib(int n, int[] dp) {

        // Base Case
        if (n <= 1)
            return n;

        // Step 1: Check if already computed
        if (dp[n] != -1)
            return dp[n];

        // Step 2: Store and return
        dp[n] = fib(n - 1, dp) + fib(n - 2, dp);

        return dp[n];
    }

    public static void main(String[] args) {

        int n = 6;

        int[] dp = new int[n + 1];

        Arrays.fill(dp, -1);

        System.out.println(fib(n, dp));
    }
}
```

---

## Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) + O(n) recursion stack |

---

# 🔄 Converting Memoization → Tabulation

## Observation

Memoization:
- works top-down
- uses recursion stack

Tabulation:
- works bottom-up
- removes recursion completely

---

## Steps to Convert

### Step 1
Identify changing parameter:

```text
n
```

### Step 2
Create DP table

```java
int[] dp = new int[n + 1];
```

### Step 3
Initialize base cases

```java
dp[0] = 0;
dp[1] = 1;
```

### Step 4
Fill table from smaller states to larger states

```java
for(int i = 2; i <= n; i++)
```

---

# 3️⃣ Bottom-Up DP (Tabulation)

## Tabulation Code

```java
public class FibonacciTabulation {

    public static void main(String[] args) {

        int n = 6;

        int[] dp = new int[n + 1];

        // Base Cases
        dp[0] = 0;
        dp[1] = 1;

        // Build DP Table
        for (int i = 2; i <= n; i++) {

            dp[i] = dp[i - 1] + dp[i - 2];
        }

        System.out.println(dp[n]);
    }
}
```

---

## DP Array Visualization

```text
Index : 0 1 2 3 4 5 6
Value : 0 1 1 2 3 5 8
```

---

## Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) |

---

# 🔄 Converting Tabulation → Space Optimization

## Observation

To compute current Fibonacci:
- we only need previous 2 values

Instead of storing entire DP array:
- keep only 2 variables

---

## From

```java
dp[i] = dp[i - 1] + dp[i - 2];
```

We only require:
- `prev1`
- `prev2`

---

# 4️⃣ Space Optimized Solution

## Space Optimized Code

```java
public class FibonacciSpaceOptimization {

    public static void main(String[] args) {

        int n = 6;

        // Base Cases
        if (n <= 1) {
            System.out.println(n);
            return;
        }

        int prev2 = 0;
        int prev1 = 1;

        for (int i = 2; i <= n; i++) {

            int current = prev1 + prev2;

            prev2 = prev1;
            prev1 = current;
        }

        System.out.println(prev1);
    }
}
```

---

## Complexity

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

# 🧠 Key Learning

## Recursion
- Easy to think
- Expensive due to repeated work

## Memoization
- Stores repeated states
- Converts exponential → linear

## Tabulation
- Removes recursion stack
- Iterative DP

## Space Optimization
- Stores only necessary states
- Most optimized version

---

# 🚀 Conclusion

The Fibonacci problem teaches the complete Dynamic Programming journey:

```text
Recursion
   ↓
Memoization
   ↓
Tabulation
   ↓
Space Optimization
```

Mastering this transformation is the foundation for solving advanced DP problems efficiently.
