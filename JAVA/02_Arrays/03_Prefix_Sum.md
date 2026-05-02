# Prefix Sum (Cumulative Sum) in Arrays

## 📌 Introduction

**Prefix Sum** is a powerful technique used to efficiently compute the sum of elements in a subarray.

Instead of calculating sum repeatedly using loops, we **precompute cumulative sums** to answer queries in **O(1)** time.

---

## 📌 Why Prefix Sum?

👉 Without prefix sum:
- Each query takes **O(n)**

👉 With prefix sum:
- Preprocessing: **O(n)**
- Each query: **O(1)**

---

## 📌 Basic Idea

Given an array:

```text
arr = [2, 4, 6, 8]
````

Prefix sum array:

```text
prefix = [2, 6, 12, 20]
```

---

## 📌 Formula

```text
prefix[i] = prefix[i - 1] + arr[i]
```

---

## 📌 Code to Build Prefix Array

```java id="build_prefix"
public class PrefixSum {

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8};
        int n = arr.length;

        int[] prefix = new int[n];

        prefix[0] = arr[0];

        for (int i = 1; i < n; i++) {
            prefix[i] = prefix[i - 1] + arr[i];
        }

        for (int val : prefix) {
            System.out.print(val + " ");
        }
    }
}
```

---

## 📌 Range Sum Query

### 🔹 Problem

Find sum from index `L` to `R`

---

### 🔹 Formula

```text
sum(L, R) = prefix[R] - prefix[L - 1]
```

👉 Special case:

```text
if L == 0 → sum = prefix[R]
```

---

## 📌 Code for Range Sum Query

```java id="range_query"
public class RangeSum {

    public static int rangeSum(int[] prefix, int L, int R) {
        if (L == 0) return prefix[R];
        return prefix[R] - prefix[L - 1];
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8};
        int n = arr.length;

        int[] prefix = new int[n];
        prefix[0] = arr[0];

        for (int i = 1; i < n; i++) {
            prefix[i] = prefix[i - 1] + arr[i];
        }

        System.out.println(rangeSum(prefix, 1, 3)); // Output: 18
    }
}
```

---

## 📌 Example

```text
arr = [2, 4, 6, 8]
prefix = [2, 6, 12, 20]

Query: sum(1, 3)

= prefix[3] - prefix[0]
= 20 - 2
= 18
```

---

## 📌 In-Place Prefix Sum

Instead of extra array:

```java id="inplace_prefix"
for (int i = 1; i < arr.length; i++) {
    arr[i] = arr[i - 1] + arr[i];
}
```

---

## 📌 Applications of Prefix Sum

* Range sum queries
* Subarray sum problems
* Finding equilibrium index
* Counting subarrays
* Sliding window optimization
* Competitive programming problems

---

## 📌 Important Problems

---

### 1. Subarray Sum Equals K

#### 🔹 Idea

Use prefix sum + HashMap

---

```java id="subarray_sum_k"
import java.util.HashMap;

public class SubarraySumK {

    public static int countSubarrays(int[] arr, int k) {

        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);

        int sum = 0;
        int count = 0;

        for (int num : arr) {
            sum += num;

            if (map.containsKey(sum - k)) {
                count += map.get(sum - k);
            }

            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }

        return count;
    }
}
```

---

### 2. Equilibrium Index

Find index where:

```text
Left sum == Right sum
```

---

```java id="equilibrium"
public class EquilibriumIndex {

    public static int findIndex(int[] arr) {

        int total = 0;
        for (int num : arr) total += num;

        int leftSum = 0;

        for (int i = 0; i < arr.length; i++) {
            total -= arr[i];

            if (leftSum == total)
                return i;

            leftSum += arr[i];
        }

        return -1;
    }
}
```

---

## 📌 Prefix Sum in 2D (Advanced)

Used in matrix problems.

### 🔹 Formula

```text
prefix[i][j] =
matrix[i][j]
+ prefix[i-1][j]
+ prefix[i][j-1]
- prefix[i-1][j-1]
```

---

## 📌 Complexity

| Operation    | Time |
| ------------ | ---- |
| Build prefix | O(n) |
| Query sum    | O(1) |

---

## 📌 Common Mistakes

❌ Forgetting edge case `L = 0`

❌ Wrong indexing:

```text
prefix[R] - prefix[L] ❌
prefix[R] - prefix[L-1] ✔
```

---

## 📌 Interview Tips

* Always think: "Can prefix sum optimize this?"
* Combine with:

  * HashMap → subarray problems
  * Sliding window → optimization
* Works best for **static arrays (no updates)**

---

## 📌 Limitations

* Not suitable for dynamic updates
* Use Segment Tree / Fenwick Tree instead

---

## 📌 Conclusion

Prefix sum is one of the **most important DSA techniques**:

* Reduces time complexity drastically
* Widely used in interviews and contests
* Foundation for advanced concepts

---
refix sum problems (must-do for placements)**
```
