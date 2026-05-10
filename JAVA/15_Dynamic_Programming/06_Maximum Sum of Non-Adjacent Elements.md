# Maximum Sum of Non-Adjacent Elements | Dynamic Programming in Java

You are given an array of integers.

Find the maximum possible sum of a subsequence such that:
- no two chosen elements are adjacent.

---

# Problem Statement

Given an array `nums[]` of size `N`,
return the maximum sum of a subsequence where no two selected elements are adjacent.

---

# Example

## Input

```text
nums = [2, 1, 4, 9]
```

## Output

```text
11
```

## Explanation

Possible valid subsequences:

```text
[2,4] = 6
[2,9] = 11
[1,9] = 10
```

Maximum sum = `11`

---

# 🧠 Intuition

At every index, we have two choices:

## Choice 1 → Include Current Element

If we include current element:
- we cannot include adjacent element

So move to:

```text
index + 2
```

---

## Choice 2 → Exclude Current Element

Skip current element and move to:

```text
index + 1
```

---

Therefore:

```text
answer = max(include, exclude)
```

Recurrence:

```text
f(i) = max( nums[i] + f(i+2), f(i+1) )
```

---

# 1️⃣ Recursive Approach

# Intuition

For every index:
- either pick current element
- or skip it

Take maximum among both choices.

---

# Recursive Code

```java
public class MaximumNonAdjacentSumRecursion {

    static int solve(int[] nums, int index) {

        // Base Case
        if (index >= nums.length)
            return 0;

        // Include current element
        int include = nums[index] + solve(nums, index + 2);

        // Exclude current element
        int exclude = solve(nums, index + 1);

        return Math.max(include, exclude);
    }

    public static void main(String[] args) {

        int[] nums = {2, 1, 4, 9};

        System.out.println(solve(nums, 0));
    }
}
```

---

# Recursive Tree

```text
solve(0)
├── include → solve(2)
│   ├── include → solve(4)
│   └── exclude → solve(3)
└── exclude → solve(1)
```

Notice:
- `solve(2)`
- `solve(3)`

can repeat multiple times.

This creates overlapping subproblems.

---

# Complexity

| Complexity | Value |
|---|---|
| Time | O(2^n) |
| Space | O(n) recursion stack |

---

# 🔄 Converting Recursion → Memoization

# Problem in Recursion

Same indices are solved repeatedly.

Example:
- `solve(2)` gets recomputed
- `solve(3)` also repeats

This increases time complexity exponentially.

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

public class MaximumNonAdjacentSumMemoization {

    static int solve(int[] nums, int index, int[] dp) {

        // Base Case
        if (index >= nums.length)
            return 0;

        // Step 1: Return if already computed
        if (dp[index] != -1)
            return dp[index];

        // Include current element
        int include = nums[index] + solve(nums, index + 2, dp);

        // Exclude current element
        int exclude = solve(nums, index + 1, dp);

        // Step 2: Store and return
        dp[index] = Math.max(include, exclude);

        return dp[index];
    }

    public static void main(String[] args) {

        int[] nums = {2, 1, 4, 9};

        int[] dp = new int[nums.length];

        Arrays.fill(dp, -1);

        System.out.println(solve(nums, 0, dp));
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
- works recursively
- top-down approach

Tabulation:
- removes recursion
- solves bottom-up

---

# Steps to Convert

## Step 1
Create DP array

```java
int[] dp = new int[n];
```

---

## Step 2
Base Case

```java
dp[0] = nums[0];
```

---

## Step 3
For every index:
- include current element
- exclude current element
- store maximum

---

# Important Transition

If we include current element:

```text
nums[i] + dp[i-2]
```

If we exclude:

```text
dp[i-1]
```

Therefore:

```text
dp[i] = max(
    nums[i] + dp[i-2],
    dp[i-1]
)
```

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
public class MaximumNonAdjacentSumTabulation {

    public static void main(String[] args) {

        int[] nums = {2, 1, 4, 9};

        int n = nums.length;

        // Edge Case
        if (n == 1) {
            System.out.println(nums[0]);
            return;
        }

        int[] dp = new int[n];

        // Base Cases
        dp[0] = nums[0];

        dp[1] = Math.max(nums[0], nums[1]);

        // Build DP Table
        for (int i = 2; i < n; i++) {

            int include = nums[i] + dp[i - 2];

            int exclude = dp[i - 1];

            dp[i] = Math.max(include, exclude);
        }

        System.out.println(dp[n - 1]);
    }
}
```

---

# DP Array Visualization

For:

```text
nums = [2,1,4,9]
```

DP table:

```text
Index : 0 1 2 3
DP    : 2 2 6 11
```

Answer:

```text
11
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

To compute current state:
we only need:
- previous state
- second previous state

We do NOT need the entire DP array.

---

# From

```text
dp[i] = max(nums[i] + dp[i-2], dp[i-1])
```

We only require:
- `prev1`
- `prev2`

---

# 4️⃣ Space Optimized Solution

# Space Optimized Code

```java
public class MaximumNonAdjacentSumSpaceOptimization {

    public static void main(String[] args) {

        int[] nums = {2, 1, 4, 9};

        int n = nums.length;

        // Edge Case
        if (n == 1) {
            System.out.println(nums[0]);
            return;
        }

        int prev2 = nums[0];

        int prev1 = Math.max(nums[0], nums[1]);

        for (int i = 2; i < n; i++) {

            int include = nums[i] + prev2;

            int exclude = prev1;

            int current = Math.max(include, exclude);

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

# 🧠 Important DP Pattern

This problem follows:

```text
Include Current Element
OR
Exclude Current Element
```

Transition:

```text
dp[i] = max(
    nums[i] + dp[i-2],
    dp[i-1]
)
```

This pattern appears in:
- House Robber
- Stickler Thief
- Robbery problems
- Maximum subsequence problems

---

# 🚀 Conclusion

This is one of the most important 1D DP problems.

It teaches:
- decision making
- include/exclude pattern
- optimization
- state transitions
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

Mastering this pattern is essential for advanced Dynamic Programming problems.
