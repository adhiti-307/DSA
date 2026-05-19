# Check if Array is Sorted Using Recursion in Java

# 📘 Problem Statement

Given an array,
check whether the array is sorted in:

```text
Non-decreasing order
```

using recursion.

Return:

```text
true  → if sorted
false → otherwise
```

---

# Example 1

## Input

```text
arr = [1,2,3,4,5]
```

## Output

```text
true
```

because every element is smaller than or equal to next element.

---

# Example 2

## Input

```text
arr = [1,5,3,4]
```

## Output

```text
false
```

because:

```text
5 > 3
```

---

# 🧠 Recursive Thinking

To check if array is sorted:

We need to verify:

```text
arr[i] <= arr[i+1]
```

for every index.

---

# Important Observation

If:
- current pair is sorted
AND
- remaining array is sorted

then whole array is sorted.

---

# Recursive Relation

```text
isSorted(arr, i)
=
(arr[i] <= arr[i+1])
AND
isSorted(arr, i+1)
```

---

# 📌 Base Case

When:

```text
i == n-1
```

or:

```text
i == n
```

only one element remains.

A single element array is always sorted.

So:

```java
return true;
```

---

# 🌳 Recursive Flow

Suppose:

```text
arr = [1,2,3,4]
```

Calls happen like:

```text
check(0)
→ check(1)
→ check(2)
→ check(3)
```

Then recursion returns back.

---

# ✅ Java Recursive Code

```java
public class CheckSorted {

    static boolean isSorted(int[] arr, int i){

        // Base Case
        if(i == arr.length - 1){

            return true;
        }

        // Current pair not sorted
        if(arr[i] > arr[i + 1]){

            return false;
        }

        // Recursive Relation
        return isSorted(arr, i + 1);
    }

    public static void main(String[] args) {

        int[] arr = {1,2,3,4,5};

        System.out.println(isSorted(arr, 0));
    }
}
```

---

# Output

```text
true
```

---

# 🧪 Dry Run

Suppose:

```text
arr = [1,2,3,4]
```

---

## Step 1

```text
1 <= 2 ✅
```

Call:

```text
isSorted(1)
```

---

## Step 2

```text
2 <= 3 ✅
```

Call:

```text
isSorted(2)
```

---

## Step 3

```text
3 <= 4 ✅
```

Call:

```text
isSorted(3)
```

---

# Base Case

```text
i == n-1
```

Return:

```text
true
```

---

# Returning Back

Every recursive call returns:

```text
true
```

Final Answer:

```text
true
```

---

# ❌ Example of Unsorted Array

Suppose:

```text
arr = [1,5,3]
```

---

## Step 1

```text
1 <= 5 ✅
```

---

## Step 2

```text
5 <= 3 ❌
```

Immediately return:

```text
false
```

---

# 📦 Call Stack Visualization

For:

```text
[1,2,3,4]
```

Stack grows like:

```text
isSorted(0)
isSorted(1)
isSorted(2)
isSorted(3)
```

Then returns upward.

---

# ⏱️ Complexity Analysis

# Time Complexity

```text
O(n)
```

because:
- every element is checked once.

---

# Space Complexity

```text
O(n)
```

because:
- recursion stack stores recursive calls.

---

# ⚠️ Important Concept

Recursion works by:
- checking current pair
- trusting recursion for remaining array

This is the key recursive mindset.

---

# 🔥 Alternative Recursive Style

Instead of index,
we can reduce array size recursively.

---

# Example

```java
static boolean isSorted(int[] arr, int n){

    // Base Case
    if(n == 0 || n == 1){

        return true;
    }

    if(arr[n-1] < arr[n-2]){

        return false;
    }

    return isSorted(arr, n-1);
}
```

---

# 🧠 Main Recursive Formula

```text
Current Pair Sorted
AND
Remaining Array Sorted
```

---

# 🚀 Conclusion

This is a very important beginner recursion problem because it teaches:

- recursion on arrays
- recursive relation
- base case thinking
- reducing problem size
- recursive trust

It builds foundation for:
- array recursion
- binary search recursion
- divide and conquer
- recursion tracing
