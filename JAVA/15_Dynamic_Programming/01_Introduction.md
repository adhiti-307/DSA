# Dynamic Programming in Java

Dynamic Programming (DP) is a powerful algorithmic technique used to solve problems by breaking them down into smaller overlapping subproblems and storing their results to avoid redundant computations.

It is widely used in coding interviews, competitive programming, and real-world software optimization problems.

---

# 📌 Why Use Dynamic Programming?

Dynamic Programming helps improve the efficiency of recursive solutions by reducing time complexity.

Without DP:
- Recursive solutions may repeat the same calculations many times.
- Time complexity can become exponential.

With DP:
- Previously computed results are stored.
- Problems are solved much faster.

---

# 🧠 Key Concepts

Dynamic Programming is based on two important properties:

## 1. Overlapping Subproblems
The problem can be divided into smaller subproblems that are solved multiple times.

## 2. Optimal Substructure
The optimal solution of the main problem depends on optimal solutions of its smaller subproblems.

---

# ⚙️ Approaches in Dynamic Programming

## 1. Memoization (Top-Down)
- Uses recursion
- Stores computed results in memory

### Example: Fibonacci using Memoization

```java
import java.util.Arrays;

public class FibonacciMemo {
    static int[] dp = new int[100];

    static int fib(int n) {
        if (n <= 1)
            return n;

        if (dp[n] != -1)
            return dp[n];

        return dp[n] = fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {
        Arrays.fill(dp, -1);
        System.out.println(fib(10));
    }
}
````

---

## 2. Tabulation (Bottom-Up)

* Uses iteration
* Builds solutions step by step

### Example: Fibonacci using Tabulation

```java
public class FibonacciTabulation {
    public static void main(String[] args) {
        int n = 10;
        int[] dp = new int[n + 1];

        dp[0] = 0;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        System.out.println(dp[n]);
    }
}
```

---

# 📊 Time Complexity Comparison

| Approach    | Time Complexity | Space Complexity |
| ----------- | --------------- | ---------------- |
| Recursion   | O(2^n)          | O(n)             |
| Memoization | O(n)            | O(n)             |
| Tabulation  | O(n)            | O(n)             |

---

# 🔥 Common Dynamic Programming Problems

* Fibonacci Sequence
* Knapsack Problem
* Longest Common Subsequence (LCS)
* Coin Change
* Matrix Chain Multiplication
* Longest Increasing Subsequence
* Edit Distance
* DP on Trees
* DP on Graphs

---

# 🛠 Tips for Solving DP Problems

1. Identify the subproblems.
2. Define the DP state clearly.
3. Find the recurrence relation.
4. Decide between memoization and tabulation.
5. Optimize space if possible.

---

# 🚀 Advantages of Dynamic Programming

* Reduces time complexity significantly
* Avoids repeated calculations
* Helps solve complex optimization problems efficiently

---

# ❌ Disadvantages

* Can use extra memory
* Sometimes difficult to design DP states
* Not every problem requires DP

---

# 📚 Conclusion

Dynamic Programming is one of the most important problem-solving techniques in computer science. Mastering DP in Java requires practice and understanding patterns rather than memorizing solutions.

Start with simple problems like Fibonacci and gradually move to advanced topics like DP on Trees and Bitmask DP.

Happy Coding! 🚀

```
```
