# House Robber II | Dynamic Programming in Java

Mr. X is a professional robber planning to rob houses along a street.

Each house contains some money.

But there is a constraint:

```text
Adjacent houses cannot be robbed together.
```

Additionally:

```text
The houses are arranged in a circle.
```

This means:
- first house and last house are also adjacent.

Return the maximum amount of money Mr. X can rob without alerting the police.

---

# Problem Statement

Given an array `arr[]` where:
- `arr[i]` represents money in the `ith` house

Find the maximum money that can be robbed such that:
- no two adjacent houses are robbed
- first and last houses cannot both be robbed

---

# Example 1

## Input

```text
arr = [2,3,2]
```

## Output

```text
3
```

## Explanation

Cannot rob:
- first house
- and last house together

Best choice:

```text
Rob house 2 → money = 3
```

---

# Example 2

## Input

```text
arr = [1,2,3,1]
```

## Output

```text
4
```

## Explanation

Rob:
- house 1 → 1
- house 3 → 3

Total:

```text
4
```

---

# 🧠 Key Observation

This problem is almost identical to:

```text
Maximum Sum of Non-Adjacent Elements
```

BUT there is one extra condition:

```text
First and Last houses are adjacent.
```

So:
- we cannot take both together.

---

# 🔥 Main Idea

We divide the problem into TWO cases.

---

## Case 1 → Exclude First House

Rob houses from:

```text
index 1 → n-1
```

---

## Case 2 → Exclude Last House

Rob houses from:

```text
index 0 → n-2
```

---

Final Answer:

```text
max(case1, case2)
```

---

# Recurrence Relation

For linear robbery:

```text
dp[i] = max( arr[i] + dp[i-2], dp[i-1] )
```

---

# 1️⃣ Recursive Approach

# Intuition

At every house:
- either rob current house
- or skip it

Take maximum answer.

We solve:
- excluding first house
- excluding last house

and take maximum.

---

# Recursive Code

```java
import java.util.ArrayList;

public class HouseRobber2Recursion {

    static int solve(ArrayList<Integer> nums, int index) {

        // Base Case
        if (index >= nums.size())
            return 0;

        // Include current house
        int include = nums.get(index) + solve(nums, index + 2);

        // Exclude current house
        int exclude = solve(nums, index + 1);

        return Math.max(include, exclude);
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 1};

        int n = arr.length;

        // Edge Case
        if (n == 1) {
            System.out.println(arr[0]);
            return;
        }

        ArrayList<Integer> first = new ArrayList<>();
        ArrayList<Integer> second = new ArrayList<>();

        for (int i = 0; i < n; i++) {

            if (i != 0)
                first.add(arr[i]);

            if (i != n - 1)
                second.add(arr[i]);
        }

        int ans = Math.max(
                solve(first, 0),
                solve(second, 0)
        );

        System.out.println(ans);
    }
}
```

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
- `solve(2)`
- `solve(3)`

get recomputed multiple times.

---

# Optimization Idea

Store already computed answers inside DP array.

Before solving:
- check if answer exists
- if yes → reuse it

---

# 2️⃣ Top-Down DP (Memoization)

# Memoization Code

```java
import java.util.ArrayList;
import java.util.Arrays;

public class HouseRobber2Memoization {

    static int solve(ArrayList<Integer> nums, int index, int[] dp) {

        // Base Case
        if (index >= nums.size())
            return 0;

        // Step 1: Return if already computed
        if (dp[index] != -1)
            return dp[index];

        int include = nums.get(index) + solve(nums, index + 2, dp);

        int exclude = solve(nums, index + 1, dp);

        // Step 2: Store and return
        dp[index] = Math.max(include, exclude);

        return dp[index];
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 1};

        int n = arr.length;

        // Edge Case
        if (n == 1) {
            System.out.println(arr[0]);
            return;
        }

        ArrayList<Integer> first = new ArrayList<>();
        ArrayList<Integer> second = new ArrayList<>();

        for (int i = 0; i < n; i++) {

            if (i != 0)
                first.add(arr[i]);

            if (i != n - 1)
                second.add(arr[i]);
        }

        int[] dp1 = new int[first.size()];
        int[] dp2 = new int[second.size()];

        Arrays.fill(dp1, -1);
        Arrays.fill(dp2, -1);

        int ans = Math.max(
                solve(first, 0, dp1),
                solve(second, 0, dp2)
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

# Observation

Memoization:
- recursive
- top-down

Tabulation:
- iterative
- bottom-up

---

# Transition

For every index:

```text
Include current house
OR
Exclude current house
```

Transition:

```text
dp[i] = max( arr[i] + dp[i-2], dp[i-1] )
```

---

# Helper Function

We solve linear robbery problem separately.

---

# 3️⃣ Bottom-Up DP (Tabulation)

# Tabulation Code

```java
public class HouseRobber2Tabulation {

    static int solve(int[] nums) {

        int n = nums.length;

        // Edge Case
        if (n == 1)
            return nums[0];

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

        return dp[n - 1];
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 1};

        int n = arr.length;

        // Edge Case
        if (n == 1) {
            System.out.println(arr[0]);
            return;
        }

        int[] first = new int[n - 1];
        int[] second = new int[n - 1];

        for (int i = 0; i < n; i++) {

            if (i != 0)
                first[i - 1] = arr[i];

            if (i != n - 1)
                second[i] = arr[i];
        }

        int ans = Math.max( solve(first), solve(second) );

        System.out.println(ans);
    }
}
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

Entire DP array is unnecessary.

---

# From

```text
dp[i] = max(
    arr[i] + dp[i-2],
    dp[i-1]
)
```

We only require:
- prev1
- prev2

---

# 4️⃣ Space Optimized Solution

# Space Optimized Code

```java
public class HouseRobber2SpaceOptimization {

    static int solve(int[] nums) {

        int n = nums.length;

        // Edge Case
        if (n == 1)
            return nums[0];

        int prev2 = nums[0];

        int prev1 = Math.max(nums[0], nums[1]);

        for (int i = 2; i < n; i++) {

            int include = nums[i] + prev2;

            int exclude = prev1;

            int current = Math.max(include, exclude);

            prev2 = prev1;

            prev1 = current;
        }

        return prev1;
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 1};

        int n = arr.length;

        // Edge Case
        if (n == 1) {
            System.out.println(arr[0]);
            return;
        }

        int[] first = new int[n - 1];
        int[] second = new int[n - 1];

        for (int i = 0; i < n; i++) {

            if (i != 0)
                first[i - 1] = arr[i];

            if (i != n - 1)
                second[i] = arr[i];
        }

        int ans = Math.max(
                solve(first),
                solve(second)
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
    arr[i] + dp[i-2],
    dp[i-1]
)
```

Special Trick:

```text
Circular Array
↓
Break into two linear arrays
```

This pattern appears in:
- House Robber II
- Circular DP problems
- Ring-based optimization problems

---

# 🚀 Conclusion

This problem is an advanced variation of:

```text
Maximum Sum of Non-Adjacent Elements
```

Main learning:
- circular dependency handling
- include/exclude DP
- reducing circular problems into linear problems

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

Mastering this pattern helps solve many:
- circular DP
- robbery
- scheduling
- optimization problems.
