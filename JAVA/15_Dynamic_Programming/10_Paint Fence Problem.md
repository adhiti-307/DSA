# Paint Fence Problem | Dynamic Programming in Java

Ninja has:
- `N` fence posts
- `K` colors

He wants to paint the fence such that:

```text
No more than two adjacent fence posts have the same color.
```

Return the total number of ways to paint the fence.

Since the answer can be very large,
return the answer modulo:

```text
10^9 + 7
```

---

# Problem Statement

Given:
- `N` fence posts
- `K` colors

Find the total number of valid ways to paint the fence such that:
- at most two adjacent posts have the same color.

---

# Example

## Input

```text
N = 3
K = 2
```

## Output

```text
6
```

---

# 🧠 How to Reach the Recursive Relation

This is the MOST IMPORTANT part of the problem.

Instead of memorizing the formula,
understand how it is formed.

---

# Let's Think About the Last Fence Post

Suppose we are painting the `nth` fence post.

There are TWO possibilities.

---

# Case 1 → Last Two Posts Have Same Color

If:
- post `n`
- and post `n-1`

have the SAME color,

then:

```text
post (n-1) and post (n-2)
CANNOT have same color
```

Otherwise:
- 3 adjacent posts become same
- which is invalid.

So:
- number of ways comes from:

```text
ways(n-2)
```

And:
- current post has only:

```text
(k-1)
```

choices.

Why?

Because:
- it must match post `(n-1)`
- but differ from `(n-2)`.

Therefore:

```text
Same Color Case =
ways(n-2) × (k-1)
```

---

# Case 2 → Last Two Posts Have Different Colors

If:
- post `n`
- and post `n-1`

have DIFFERENT colors,

then:
- previous arrangement can be anything valid.

So:
- number of ways comes from:

```text
ways(n-1)
```

And:
- current post has:

```text
(k-1)
```

choices.

Why?

Because:
- it must differ from previous post.

Therefore:

```text
Different Color Case =
ways(n-1) × (k-1)
```

---

# Final Recursive Relation

Add both cases:

```text
ways(n) =
(k-1) × (ways(n-1) + ways(n-2))
```

---

# Base Cases

## For One Fence

```text
ways(1) = k
```

Because:
- any of the `k` colors can be chosen.

---

## For Two Fences

Two possibilities:
- same color
- different colors

```text
Same Color  → k ways
Different   → k × (k-1)
```

Therefore:

```text
ways(2) = k + k×(k-1)
```

or:

```text
ways(2) = k²
```

---

# 1️⃣ Recursive Approach

# Recursive Code

```java
public class PaintFenceRecursion {

    static final int MOD = 1000000007;

    static long solve(int n, int k) {

        // Base Cases
        if (n == 1)
            return k;

        if (n == 2)
            return (k + (long)k * (k - 1)) % MOD;

        return ((k - 1) *
                ((solve(n - 1, k) +
                  solve(n - 2, k)) % MOD)
        ) % MOD;
    }

    public static void main(String[] args) {
        int n = 3;
        int k = 2;
        System.out.println(solve(n, k));
    }
}
```

---

# Recursive Tree

```text
solve(5)
├── solve(4)
│   ├── solve(3)
│   └── solve(2)
└── solve(3)
```

Notice:
- `solve(3)` repeats.

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
- `solve(3)`
- `solve(4)`

get recomputed multiple times.

---

# Optimization Idea

Store already computed answers inside DP array.

Before solving:
- check if answer already exists
- if yes → reuse it

---

# 2️⃣ Top-Down DP (Memoization)

# Memoization Code

```java
import java.util.Arrays;

public class PaintFenceMemoization {

    static final int MOD = 1000000007;

    static long solve(int n, int k, long[] dp) {

        // Base Cases
        if (n == 1)
            return k;

        if (n == 2)
            return (k + (long)k * (k - 1)) % MOD;

        // Step 1: Return if already computed
        if (dp[n] != -1)
            return dp[n];

        // Step 2: Store and return
        dp[n] = ((k - 1) *
                ((solve(n - 1, k, dp) +
                  solve(n - 2, k, dp)) % MOD)
        ) % MOD;

        return dp[n];
    }

    public static void main(String[] args) {

        int n = 3;

        int k = 2;

        long[] dp = new long[n + 1];

        Arrays.fill(dp, -1);

        System.out.println(solve(n, k, dp));
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
dp[i] = number of ways to paint i fences
```

---

# Transition

```text
dp[i] =
(k-1) × (dp[i-1] + dp[i-2])
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
dp[1] = k;

dp[2] =
k + k×(k-1)
```

---

## Step 3
Build DP table iteratively

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
public class PaintFenceTabulation {

    static final int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 3;

        int k = 2;

        long[] dp = new long[n + 1];

        // Base Cases
        dp[1] = k;

        dp[2] =
                (k + (long)k * (k - 1)) % MOD;

        // Build DP Table
        for (int i = 3; i <= n; i++) {

            dp[i] = ((k - 1) *
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
K = 2
```

DP table:

```text
Index : 1 2 3 4 5
DP    : 2 4 6 10 16
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

Entire DP array is unnecessary.

---

# From

```text
dp[i] =
(k-1) × (dp[i-1] + dp[i-2])
```

We only require:
- prev1
- prev2

---

# 4️⃣ Space Optimized Solution

# Space Optimized Code

```java
public class PaintFenceSpaceOptimization {

    static final int MOD = 1000000007;

    public static void main(String[] args) {

        int n = 5;

        int k = 2;

        // Base Cases
        if (n == 1) {
            System.out.println(k);
            return;
        }

        long prev2 = k;

        long prev1 =
                (k + (long)k * (k - 1)) % MOD;

        for (int i = 3; i <= n; i++) {

            long current =
                    ((k - 1) *
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
ways(n) =
(k-1) × (ways(n-1) + ways(n-2))
```

This pattern appears in:
- combinatorics DP
- arrangement counting
- painting problems
- coloring problems

---

# 🚀 Conclusion

This is a classic counting DP problem.

It teaches:
- forming recurrence relations
- combinatorial thinking
- memoization
- modulo arithmetic
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

# 🎨 Easy Understanding of Paint Fence Problem

Suppose:

```text
N = 3
K = 3
```

Colors are:

```text
R → Red
G → Green
B → Blue
```

Rule:

```text
More than 2 adjacent fences cannot have same color.
```

So these are valid:

```text
RRG ✅
RGR ✅
GGB ✅
```

But this is invalid:

```text
RRR ❌
```

because:
- 3 adjacent fences are same.

---

# 🧠 How to Think About the Relation

Suppose we are filling the LAST fence.

Example:

```text
Fence : 1 2 3
```

We focus only on fence `3`.

There are only TWO possibilities.

---

# Case 1 → Last Fence Same as Previous Fence

Example:

```text
R G G
```

Fence `2` and fence `3` are same.

Now think carefully:

Can fence `1` also be `G`?

```text
G G G ❌ invalid
```

NO.

So:
- if last two are same,
- then previous arrangement must already be valid till `(n-2)`.

That gives:

```text
ways(n-2)
```

Now for current fence:
- we can choose any color except previous previous fence color.

Choices:

```text
(k-1)
```

So:

```text
Same Case =
(k-1) × ways(n-2)
```

---

# Case 2 → Last Fence Different from Previous Fence

Example:

```text
R G B
```

or

```text
R R G
```

Last two fences are different.

Now:
- previous arrangement can be ANY valid arrangement.

That contributes:

```text
ways(n-1)
```

For current fence:
- choose any color except previous fence color.

Choices:

```text
(k-1)
```

So:

```text
Different Case =
(k-1) × ways(n-1)
```

---

# Final Answer

Add both cases:

```text
ways(n) =
(k-1) × (ways(n-1) + ways(n-2))
```

---

# 🔥 Small Example

## N = 3
## K = 2

Colors:

```text
R, G
```

All valid ways:

```text
RRG
RGR
RGG
GRR
GRG
GGR
```

Total:

```text
6 ways
```

Invalid:

```text
RRR ❌
GGG ❌
```

because 3 adjacent fences become same.

---

# 🧠 Main Idea

At every fence:
- either make it SAME as previous
- or DIFFERENT from previous

That creates:

```text
ways(n-1)
ways(n-2)
```

which forms the DP relation.Mastering recurrence derivation is one of the most important DP skills.
