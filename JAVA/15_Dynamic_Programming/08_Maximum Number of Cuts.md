# Maximum Number of Cuts | Dynamic Programming in Java

You are given:
- a rod of length `N`
- three possible cut lengths:
  - `X`
  - `Y`
  - `Z`

You need to determine the maximum number of segments that can be obtained by cutting the rod such that:
- every segment length must be either `X`, `Y`, or `Z`.

If it is not possible to cut the rod exactly, return `0`.

---

# Problem Statement

Given:
- rod length `N`
- allowed cut lengths `X`, `Y`, `Z`

Return the maximum number of segments possible.

---

# Example 1

## Input

```text
N = 7
X = 5
Y = 2
Z = 2
```

## Output

```text
2
```

## Explanation

Possible cut:

```text
5 + 2 = 7
```

Total segments = `2`

---

# Example 2

## Input

```text
N = 8
X = 3
Y = 3
Z = 3
```

## Output

```text
0
```

## Explanation

It is impossible to form exactly `8`
using only segments of length `3`.

---

# 🧠 Intuition

At every step:
- cut a segment of length `X`
- OR cut `Y`
- OR cut `Z`

Then solve for the remaining rod.

If we choose cut `X`:

```text
remaining rod = n - X
```

Similarly for `Y` and `Z`.

---

# Recurrence Relation

```text
f(n) = 1 + max(
    f(n-X),
    f(n-Y),
    f(n-Z)
)
```

because:
- current cut contributes `1 segment`
- remaining answer comes recursively

---

# 1️⃣ Recursive Approach

# Intuition

For every rod length:
- try all three cuts
- recursively solve remaining rod
- take maximum answer

---

# Recursive Code

```java
public class MaximumCutsRecursion {

    static int solve(int n, int x, int y, int z) {

        // Base Case
        if (n == 0)
            return 0;

        // Invalid Case
        if (n < 0)
            return Integer.MIN_VALUE;

        int a = solve(n - x, x, y, z) + 1;

        int b = solve(n - y, x, y, z) + 1;

        int c = solve(n - z, x, y, z) + 1;

        return Math.max(a, Math.max(b, c));
    }

    public static void main(String[] args) {

        int n = 7;

        int x = 5;
        int y = 2;
        int z = 2;

        int ans = solve(n, x, y, z);

        System.out.println(ans < 0 ? 0 : ans);
    }
}
```

---

# Recursive Tree

```text
solve(7)
├── solve(2)
├── solve(5)
└── solve(5)
```

Notice:
- many states repeat
- `solve(5)` gets recomputed

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

The same rod lengths are solved repeatedly.

Example:
- `solve(5)`
- `solve(3)`
- `solve(2)`

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

public class MaximumCutsMemoization {

    static int solve(int n, int x, int y, int z, int[] dp) {

        // Base Case
        if (n == 0)
            return 0;

        // Invalid Case
        if (n < 0)
            return Integer.MIN_VALUE;

        // Step 1: Return if already computed
        if (dp[n] != -1)
            return dp[n];

        int a = solve(n - x, x, y, z, dp) + 1;

        int b = solve(n - y, x, y, z, dp) + 1;

        int c = solve(n - z, x, y, z, dp) + 1;

        // Step 2: Store and return
        dp[n] = Math.max(a, Math.max(b, c));

        return dp[n];
    }

    public static void main(String[] args) {

        int n = 7;

        int x = 5;
        int y = 2;
        int z = 2;

        int[] dp = new int[n + 1];

        Arrays.fill(dp, -1);

        int ans = solve(n, x, y, z, dp);

        System.out.println(ans < 0 ? 0 : ans);
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
dp[i] = maximum cuts possible for rod length i
```

---

# Transition

If cut `x` is chosen:

```text
1 + dp[i-x]
```

Similarly for:
- `y`
- `z`

Therefore:

```text
dp[i] = 1 + max(
    dp[i-x],
    dp[i-y],
    dp[i-z]
)
```

---

# Steps to Convert

## Step 1
Create DP array

```java
int[] dp = new int[n+1];
```

---

## Step 2
Initialize invalid states

```java
Arrays.fill(dp, Integer.MIN_VALUE);
```

---

## Step 3
Base Case

```java
dp[0] = 0;
```

Because:
- rod length `0`
- requires `0` cuts

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
import java.util.Arrays;

public class MaximumCutsTabulation {

    public static void main(String[] args) {

        int n = 7;

        int x = 5;
        int y = 2;
        int z = 2;

        int[] dp = new int[n + 1];

        Arrays.fill(dp, Integer.MIN_VALUE);

        // Base Case
        dp[0] = 0;

        for (int i = 1; i <= n; i++) {

            if (i - x >= 0 && dp[i - x] != Integer.MIN_VALUE) {

                dp[i] = Math.max( dp[i], 1 + dp[i - x] );
            }

            if (i - y >= 0 && dp[i - y] != Integer.MIN_VALUE) {

                dp[i] = Math.max( dp[i], 1 + dp[i - y] );
            }

            if (i - z >= 0 && dp[i - z] != Integer.MIN_VALUE) {

                dp[i] = Math.max( dp[i], 1 + dp[i - z] );
            }
        }

        System.out.println(dp[n] < 0 ? 0 : dp[n]);
    }
}
```
## Alternate java code

```java
import java.util.*;

public class Solution {
    public static int cutSegments(int n, int x, int y, int z) {
        // Write your code here.
        int[] parts = {x,y,z};
        int[] dp = new int[n+1];
        Arrays.fill(dp,Integer.MIN_VALUE);

        dp[0] = 0;

        for(int i=1; i <= n;i++ ){//0 1 2 3 4 5
            for(int part : parts ){
                if( i-part >= 0 && dp[i - part] != Integer.MIN_VALUE ){ 
                    dp[i] = Math.max(dp[i], 1 + dp[i-part]);
                }
            }
        }

        return dp[n] < 0 ? 0 : dp[n];
    }
}
```

---

# DP Array Visualization

For:

```text
N = 7
X = 5
Y = 2
Z = 2
```

DP table:

```text
Index : 0 1 2 3 4 5 6 7
DP    : 0 - 1 - 2 1 3 2
```

Answer:

```text
2
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

Current state depends on:

```text
dp[i-x]
dp[i-y]
dp[i-z]
```

These can be far behind current index.

So:
- we cannot reduce DP into only 2 variables
- many previous states are needed

---

# 🚫 Space Optimization Not Possible

For this problem:

```text
1D DP array is already the optimized solution.
```

Further optimization is generally not possible.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(n) |
| Space | O(n) |

---

# 📊 Final Comparison

| Approach | Time | Space |
|---|---|---|
| Recursion | Exponential | O(n) |
| Memoization | O(n) | O(n) + recursion stack |
| Tabulation | O(n) | O(n) |
| Optimized | O(n) | O(n) |

---

# 🧠 Important DP Pattern

This problem follows:

```text
Choose One Cut
+
Solve Remaining Rod
```

Transition:

```text
dp[i] =
1 + max(
    dp[i-x],
    dp[i-y],
    dp[i-z]
)
```

This pattern appears in:
- Rod Cutting
- Coin Change
- Unbounded Knapsack
- Integer Partition problems

---

# 🚀 Conclusion

This is an important unbounded DP problem.

It teaches:
- target reduction
- maximizing answers
- handling invalid states
- DP transitions

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

Mastering this pattern helps solve advanced:
- rod cutting
- partition
- unbounded DP problems.
