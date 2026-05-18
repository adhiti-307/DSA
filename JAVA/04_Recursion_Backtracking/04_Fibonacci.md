# Fibonacci Using Recursion in Java

# 📘 Problem Statement

Given a number `N`,
find the `Nth Fibonacci number` using recursion.

---

# What is Fibonacci Series?

Fibonacci series is a sequence where:

```text
Every number is the sum of previous two numbers.
```

---

# Fibonacci Sequence

```text
0 1 1 2 3 5 8 13 21 ...
```

---

# Fibonacci Values

| N | Fibonacci(N) |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 1 |
| 3 | 2 |
| 4 | 3 |
| 5 | 5 |
| 6 | 8 |

---

# 🧠 Recursive Thinking

Suppose we want:

```text
fib(5)
```

We know:

```text
fib(5) = fib(4) + fib(3)
```

Again:

```text
fib(4) = fib(3) + fib(2)
```

Again:

```text
fib(3) = fib(2) + fib(1)
```

This creates a recursive relation.

---

# Recursive Relation

```text
fib(n) = fib(n-1) + fib(n-2)
```

---

# Base Cases

We already know:

```text
fib(0) = 0
fib(1) = 1
```

So:

```java
if(n == 0)
    return 0;

if(n == 1)
    return 1;
```

These stop recursion.

---

# 📌 Recursive Flow

Suppose:

```java
fib(5)
```

Calls happen like:

```text
fib(5)
= fib(4) + fib(3)

= (fib(3) + fib(2)) + (fib(2) + fib(1))

= ((fib(2)+fib(1)) + fib(2))
  + (fib(2)+fib(1))
```

Eventually base cases return values.

---

# 🌳 Recursive Tree

```text
fib(5)
├── fib(4)
│   ├── fib(3)
│   │   ├── fib(2)
│   │   └── fib(1)
│   └── fib(2)
└── fib(3)
    ├── fib(2)
    └── fib(1)
```

---

# 🧠 Important Observation

Notice:

```text
fib(3)
fib(2)
```

are calculated multiple times.

This creates:

```text
Overlapping Subproblems
```

which leads to:

```text
Dynamic Programming
```

---

# ✅ Java Code

```java
public class FibonacciRecursion {

    static int fib(int n){

        // Base Cases
        if(n == 0)
            return 0;

        if(n == 1)
            return 1;

        // Recursive Relation
        return fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {

        int n = 6;

        System.out.println(fib(n));
    }
}
```

---

# Output

```text
8
```

because:

```text
fib(6) = 8
```

---

# 🧪 Dry Run

Suppose:

```java
fib(4)
```

---

## Step 1

```text
fib(4)
= fib(3) + fib(2)
```

---

## Step 2

```text
fib(3)
= fib(2) + fib(1)
```

---

## Step 3

```text
fib(2)
= fib(1) + fib(0)
```

---

# Base Cases

```text
fib(1) = 1
fib(0) = 0
```

---

# Returning Answers

```text
fib(2) = 1

fib(3) = 2

fib(4) = 3
```

---

# 📦 Call Stack Visualization

```text
fib(4)
fib(3)
fib(2)
fib(1)
fib(0)
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
- recursion stack depth is `n`.

---

# ⚠️ Problem with Recursive Fibonacci

Recursive solution is:

```text
Very Slow
```

because same states repeat many times.

Example:

```text
fib(3)
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

Store already calculated Fibonacci values.

Before calculating:
- check if already computed.

---

# 📌 Space Optimized Idea

Instead of storing whole DP array:

```text
Only previous two values are needed.
```

because:

```text
fib(n) = fib(n-1) + fib(n-2)
```

---

# ✅ Space Optimized Fibonacci

```java
public class FibonacciOptimized {

    static int fib(int n){

        if(n == 0)
            return 0;

        int prev2 = 0;

        int prev1 = 1;

        for(int i = 2; i <= n; i++){

            int curr = prev1 + prev2;

            prev2 = prev1;

            prev1 = curr;
        }

        return prev1;
    }

    public static void main(String[] args) {

        System.out.println(fib(6));
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
fib(n) = fib(n-1) + fib(n-2)
```

---

# 🚀 Conclusion

Fibonacci is one of the MOST IMPORTANT recursion problems because it teaches:

- recursive relation
- base cases
- recursion tree
- overlapping subproblems
- dynamic programming intuition

It forms the foundation for:
- DP
- Memoization
- Tabulation
- Space Optimization
- Tree Recursion
