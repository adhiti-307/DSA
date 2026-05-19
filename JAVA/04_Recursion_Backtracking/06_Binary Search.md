# Binary Search Using Recursion in Java

# 📘 Problem Statement

Given a sorted array and a target element,
find the index of the target using:

```text
Recursive Binary Search
```

If target does not exist,
return:

```text
-1
```

---

# Example

## Input

```text
arr = [1,3,5,7,9,11]
target = 7
```

## Output

```text
3
```

because:

```text
arr[3] = 7
```

---

# 🧠 What is Binary Search?

Binary Search is a searching algorithm that works on:

```text
Sorted Arrays
```

It repeatedly:
- finds middle element
- eliminates half of the search space

---

# 🔥 Main Idea

At every step:

```text
Search space becomes half
```

This makes Binary Search very fast.

---

# 🧠 Recursive Thinking

Suppose:

```text
arr = [1,3,5,7,9]
target = 9
```

---

# Step 1

Find middle:

```text
mid = 2
arr[mid] = 5
```

Since:

```text
9 > 5
```

Target must exist in:

```text
Right Half
```

Now recursively search:

```text
[7,9]
```

---

# Step 2

Again find middle:

```text
mid = 3
arr[mid] = 7
```

Since:

```text
9 > 7
```

Search right half again.

---

# Step 3

```text
arr[mid] = 9
```

Target found.

---

# 📌 Recursive Relation

If:

```text
arr[mid] < target
```

Search:

```text
mid+1 → high
```

---

If:

```text
arr[mid] > target
```

Search:

```text
low → mid-1
```

---

# 📌 Base Case

When:

```text
low > high
```

search space becomes empty.

Meaning:
- target does not exist.

So return:

```java
return -1;
```

---

# 🌳 Recursive Flow

Suppose:

```text
arr = [1,3,5,7,9]
target = 7
```

Recursive calls:

```text
bs(0,4)
→ bs(3,4)
→ found
```

---

# ✅ Java Recursive Code

```java
public class Solution {

    public static int bs( int low, int high, int target, int[] arr){

        // Base Case
        if(low > high){
            return -1;
        }

        int mid = low + (high - low) / 2;

        // Element Found
        if(arr[mid] == target){
            return mid;
        }

        // Search Right Half
        else if(arr[mid] < target){
            return bs( mid + 1, high, target, arr );
        }

        // Search Left Half
        else{
            return bs(low, mid - 1, target, arr );
        }
    }

    public static int search( int[] nums, int target ) {
        return bs( 0, nums.length - 1, target, nums );
    }
}
```

---

# 🧪 Dry Run

Suppose:

```text
arr = [1,3,5,7,9]
target = 7
```

---

## Step 1

```text
low = 0
high = 4

mid = 2
arr[mid] = 5
```

Since:

```text
7 > 5
```

Search:

```text
mid+1 → high
```

Call:

```text
bs(3,4)
```

---

## Step 2

```text
mid = 3
arr[mid] = 7
```

Target found.

Return:

```text
3
```

---

# 📦 Call Stack Visualization

```text
bs(0,4)
bs(3,4)
```

Then recursion returns answer upward.

---

# ⚠️ Important Formula

Instead of:

```java
int mid = (low + high) / 2;
```

prefer:

```java
int mid = low + (high - low) / 2;
```

to avoid:

```text
Integer Overflow
```

for large values.

---

# ⏱️ Complexity Analysis

# Time Complexity

```text
O(log n)
```

Why?

Because:
- search space becomes half at every step.

Example:

```text
n
n/2
n/4
n/8
...
```

This creates logarithmic complexity.

---

# Space Complexity

```text
O(log n)
```

because:
- recursive calls use stack memory.

Recursion depth becomes:

```text
log n
```

---

# 📊 Iterative vs Recursive Binary Search

| Feature | Iterative | Recursive |
|---|---|---|
| Time | O(log n) | O(log n) |
| Space | O(1) | O(log n) |
| Easier to Understand | Medium | Easy |
| Stack Usage | No | Yes |

---

# ⚠️ Common Mistakes

# ❌ Missing Base Case

Without:

```java
if(low > high)
```

recursion never stops.

---

# ❌ Wrong Mid Formula

Using:

```java
(low + high)/2
```

can overflow.

---

# ❌ Forgetting Sorted Array Requirement

Binary Search only works on:

```text
Sorted Arrays
```

---

# 🔥 Why Binary Search is Fast

Linear Search:

```text
O(n)
```

checks every element.

Binary Search:

```text
O(log n)
```

removes HALF array every step.

This makes it extremely efficient.

---

# 🧠 Main Recursive Formula

```text
Search Left Half
OR
Search Right Half
```

Recursive relation:

```text
T(n) = T(n/2) + O(1)
```

which gives:

```text
O(log n)
```

---

# 🚀 Conclusion

Recursive Binary Search is one of the MOST IMPORTANT recursion problems because it teaches:

- divide and conquer
- recursive thinking
- shrinking search space
- logarithmic complexity
- recursion on arrays

It forms the foundation for:
- advanced searching
- divide & conquer
- recursion optimization
- tree algorithms
- competitive programming
