# Count Distinct Ways to Climb Stairs Using Recursion in Java

# 📘 Problem Statement

You are given a staircase with `N` stairs.

Initially:
- you are standing at stair `0`
- you need to reach stair `N`

At every move:
- you can climb `1 stair`
- or `2 stairs`

Find the total number of distinct ways to reach the top.

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

---

# Explanation

Possible ways:

```text
1 + 1 + 1
1 + 2
2 + 1
```

Total ways:

```text
3
```

---

# 🧠 Recursive Thinking

To reach stair `N`,
there are only TWO possibilities.

---

# Case 1 → Come from `(N-1)`

Take:

```text
1 step
```

Example:

```text
0 → 1 → 2 → 3
```

---

# Case 2 → Come from `(N-2)`

Take:

```text
2 steps
```

Example:

```text
0 → 1 → 3
```

---

# Important Observation

To reach stair `N`:

```text
Ways(N)
=
Ways(N-1)
+
Ways(N-2)
```

because:
- every path must come from one of these two stairs.

---

# Recursive Relation

```text
f(n) = f(n-1) + f(n-2)
```

This is exactly the Fibonacci pattern.

---

# Base Cases

## Stair 0

```text
1 way
```

Why?

```text
Do nothing
```

You are already at stair `0`.

---

## Stair 1

```text
1 way
```

Take one step.

---

# Therefore

```java
if(n == 0)
    return 1;

if(n == 1)
    return 1;
```

---

# 📌 Recursive Flow

Suppose:

```java
countWays(4)
```

Then:

```text
countWays(4)
=
countWays(3)
+
countWays(2)
```

Again:

```text
countWays(3)
=
countWays(2)
+
countWays(1)
```

Again:

```text
countWays(2)
=
countWays(1)
+
countWays(0)
```

Eventually base cases return answers.

---

# 🌳 Recursive Tree

```text
countWays(4)
├── countWays(3)
│   ├── countWays(2)
│   │   ├── countWays(1)
│   │   └── countWays(0)
│   └── countWays(1)
└── countWays(2)
    ├── countWays(1)
    └── countWays(0)
```

---

# 🧠 Important Observation

Notice:

```text
countWays(2)
```

gets calculated multiple times.

This creates:

```text
Overlapping Subproblems
```

which leads to:

```text
Dynamic Programming
```

---

# ✅ Java Recursive Code

```java
public class CountStairsRecursion {

    static int countWays(int n){

        // Base Cases
        if(n == 0)
            return 1;

        if(n == 1)
            return 1;

        // Recursive Relation
        return countWays(n - 1)
                + countWays(n - 2);
    }

    public static void main(String[] args) {

        int n = 4;

        System.out.println(countWays(n));
    }
}
```

---

# Output

```text
5
```

---

# Why Output is 5?

Ways to climb 4 stairs:

```text
1 1 1 1
1 1 2
1 2 1
2 1 1
2 2
```

Total:

```text
5 ways
```

---

# 🧪 Dry Run

Suppose:

```java
countWays(3)
```

---

## Step 1

```text
countWays(3)
=
countWays(2)
+
countWays(1)
```

---

## Step 2

```text
countWays(2)
=
countWays(1)
+
countWays(0)
```

---

# Base Cases

```text
countWays(1) = 1
countWays(0) = 1
```

---

# Returning Answers

```text
countWays(2) = 2

countWays(3) = 3
```

---

# 📦 Call Stack Visualization

```text
countWays(3)
countWays(2)
countWays(1)
countWays(0)
```

Then recursive calls return upward.

---

# ⏱️ Complexity Analysis

# Time Complexity

```text
O(2^n)
```

Why?

Because:
- every function makes 2 recursive calls.

Recursive tree grows exponentially.

---

# Space Complexity

```text
O(n)
```

because:
- recursion stack depth becomes `n`.

---

# ⚠️ Problem with Recursive Solution

Recursive solution is:

```text
Slow
```

because:
- same states repeat many times.

Example:

```text
countWays(2)
```

gets recalculated repeatedly.

---

# 🔥 Optimization Using DP

We can optimize using:

- Memoization
- Tabulation
- Space Optimization

This reduces complexity to:

```text
O(n)
```

---

# 📌 Memoization Idea

Store already computed answers.

Before calculating:
- check if answer already exists.

---

# 📌 Space Optimization Idea

Instead of storing full DP array:

```text
Only previous two answers are needed.
```

because:

```text
f(n) = f(n-1) + f(n-2)
```

---

# ✅ Space Optimized Solution

```java
public class CountStairsOptimized {

    static int countWays(int n){

        if(n == 0 || n == 1)
            return 1;

        int prev2 = 1;

        int prev1 = 1;

        for(int i = 2; i <= n; i++){

            int curr = prev1 + prev2;

            prev2 = prev1;

            prev1 = curr;
        }

        return prev1;
    }

    public static void main(String[] args) {

        System.out.println(countWays(4));
    }
}
```

---

# Complexity of Optimized Version

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(1) |

---

# 📊 Comparison

| Approach | Time | Space |
|---|---|---|
| Recursion | O(2^n) | O(n) |
| Memoization | O(n) | O(n) |
| Tabulation | O(n) | O(n) |
| Space Optimization | O(n) | O(1) |

---

# 🧠 Main Formula

```text
f(n) = f(n-1) + f(n-2)
```

---

# 🚀 Conclusion

This is one of the MOST IMPORTANT beginner recursion problems because it teaches:

- recursive relation
- base cases
- recursion tree
- overlapping subproblems
- Fibonacci pattern
- dynamic programming intuition

It forms the foundation for:
- DP
- Memoization
- Tabulation
- Space Optimization
- staircase problems
