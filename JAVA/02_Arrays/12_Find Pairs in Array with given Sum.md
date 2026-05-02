# Find Pairs in Array with Given Sum (Java)

## 📌 Introduction

A common array problem in coding interviews is:

👉 **Find all pairs in an array whose sum equals a given target**

This problem helps you understand:
- Arrays
- Nested loops
- Hashing (HashSet, HashMap)
- Optimization techniques

---

## 📌 Problem Statement

Given:
- An integer array `arr[]`
- A target sum `target`

Find all **unique pairs** such that:

```text
arr[i] + arr[j] = target
````

---

## 📌 Example

```text
Input:
arr = [1, 5, 7, -1, 5]
target = 6

Output:
(1, 5)
(7, -1)
```

---

## 📌 Approaches

### 1️⃣ Brute Force Approach

### 🔹 Algorithm

1. Use two nested loops
2. Check every pair
3. If sum equals target → print pair

---

### 🔹 Code

```java
public class FindPairsBruteForce {
    public static void main(String[] args) {
        int[] arr = {1, 5, 7, -1, 5};
        int target = 6;

        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] + arr[j] == target) {
                    System.out.println("(" + arr[i] + ", " + arr[j] + ")");
                }
            }
        }
    }
}
```

---

### 🔹 Complexity

* Time: **O(n²)**
* Space: **O(1)**

---

## 2️⃣ Using HashSet (Optimized)

### 🔹 Idea

Instead of checking all pairs, store elements in a set and check complements.

---

### 🔹 Algorithm

1. Create a HashSet
2. For each element:

   * Check if `(target - num)` exists
   * If yes → pair found
3. Otherwise, add element to set

---

### 🔹 Code

```java
import java.util.HashSet;

public class FindPairsUsingHashSet {
    public static void findPairs(int[] arr, int target) {

        HashSet<Integer> set = new HashSet<>();

        for (int num : arr) {
            int complement = target - num;

            if (set.contains(complement)) {
                System.out.println("(" + complement + ", " + num + ")");
            }

            set.add(num);
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 5, 7, -1, 5};
        int target = 6;

        findPairs(arr, target);
    }
}
```

---

### 🔹 Complexity

* Time: **O(n)**
* Space: **O(n)**

---

## 3️⃣ Using HashMap (Best for Duplicates)

### 🔹 Idea

Use a HashMap to store frequency of elements.

---

### 🔹 Algorithm

1. Traverse array
2. Check if complement exists in map
3. Add count of complement
4. Store/update frequency in map

---

### 🔹 Code

```java
import java.util.HashMap;

public class FindPairsUsingHashMap {

    public static void findPairs(int[] arr, int target) {

        HashMap<Integer, Integer> map = new HashMap<>();
        int count = 0;

        for (int num : arr) {
            int complement = target - num;

            if (map.containsKey(complement)) {
                count += map.get(complement);
                System.out.println("(" + complement + ", " + num + ")");
            }

            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        System.out.println("Total pairs = " + count);
    }

    public static void main(String[] args) {
        int[] arr = {1, 5, 7, -1, 5};
        int target = 6;

        findPairs(arr, target);
    }
}
```

---

### 🔹 Complexity

* Time: **O(n)**
* Space: **O(n)**

---

## 📊 Comparison

| Method      | Time  | Space | Use Case           |
| ----------- | ----- | ----- | ------------------ |
| Brute Force | O(n²) | O(1)  | Small arrays       |
| HashSet     | O(n)  | O(n)  | Unique pairs       |
| HashMap     | O(n)  | O(n)  | Duplicate handling |

---

## 📌 Important Interview Insight

👉 If array is **sorted**, use **Two Pointer Approach**:

* Time: **O(n)**
* Space: **O(1)**

---

## 📌 Related Problems

* Two Sum Problem
* Triplets with Given Sum
* Subarray with Given Sum
* Pair Difference Problems

---

## 📌 FAQs

### 1. Best approach?

➡️ HashSet / HashMap → O(n)

---

### 2. Handle duplicates?

➡️ Use HashMap

---

### 3. Unique pairs only?

➡️ Use Set to avoid duplicates

---

## 📌 Conclusion

* Start with brute force to understand logic
* Optimize using hashing
* Choose method based on constraints

---
