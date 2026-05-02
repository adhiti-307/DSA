# Array Traversal Techniques in Java

## 📌 Introduction

**Array Traversal** means visiting each element of an array to:
- Read values
- Modify elements
- Apply operations (sum, max, search, etc.)

Traversal is one of the most **fundamental operations in DSA** and forms the base for:
- Searching
- Sorting
- Sliding Window
- Prefix Sum
- Two Pointer techniques

---

## 📌 What is Traversal?

Traversal is the process of accessing each element of an array **exactly once**.

---

## 📌 Example

```text
Array: [10, 20, 30, 40]

Traversal order:
10 → 20 → 30 → 40
````

---

## 📌 Basic Traversal Methods

---

## 1️⃣ Using For Loop (Most Common)

### 🔹 Code

```java
public class TraversalForLoop {
    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40};

        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

---

### 🔹 Key Points

* Full control over index
* Required when index is needed
* Most used in **interviews**

---

## 2️⃣ Using While Loop

### 🔹 Code

```java
public class TraversalWhileLoop {
    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40};

        int i = 0;
        while (i < arr.length) {
            System.out.println(arr[i]);
            i++;
        }
    }
}
```

---

### 🔹 Use Case

* When loop condition is dynamic
* Useful in pointer-based problems

---

## 3️⃣ Using For-Each Loop (Enhanced Loop)

### 🔹 Code

```java
public class TraversalForEach {
    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40};

        for (int num : arr) {
            System.out.println(num);
        }
    }
}
```

---

### 🔹 Key Points

* Cleaner syntax
* No index access
* Read-only traversal (cannot modify original array easily)

---

## 📌 Traversal Variations

---

## 4️⃣ Reverse Traversal

### 🔹 Code

```java
for (int i = arr.length - 1; i >= 0; i--) {
    System.out.println(arr[i]);
}
```

---

### 🔹 Use Cases

* Reverse array problems
* Stack-like operations

---

## 5️⃣ Traversal with Step Size

### 🔹 Code

```java
for (int i = 0; i < arr.length; i += 2) {
    System.out.println(arr[i]);
}
```

---

### 🔹 Use Cases

* Even/odd index problems
* Sampling elements

---

## 6️⃣ Conditional Traversal

### 🔹 Example: Even Numbers

```java
for (int num : arr) {
    if (num % 2 == 0) {
        System.out.println(num);
    }
}
```

---

### 🔹 Use Cases

* Filtering data
* Searching conditions

---

## 📌 Common Operations Using Traversal

---

## 1. Sum of Elements

```java
int sum = 0;

for (int num : arr) {
    sum += num;
}
```

---

## 2. Find Maximum Element

```java
int max = arr[0];

for (int num : arr) {
    if (num > max) {
        max = num;
    }
}
```

---

## 3. Find Minimum Element

```java
int min = arr[0];

for (int num : arr) {
    if (num < min) {
        min = num;
    }
}
```

---

## 4. Count Elements

```java
int count = 0;

for (int num : arr) {
    count++;
}
```

---

## 5. Search an Element (Linear Search)

```java
int target = 30;

for (int i = 0; i < arr.length; i++) {
    if (arr[i] == target) {
        System.out.println("Found at index: " + i);
    }
}
```

---

## 📌 Advanced Traversal Patterns

---

## 1. Two Pointer Traversal

### 🔹 Code

```java
int left = 0;
int right = arr.length - 1;

while (left < right) {
    System.out.println(arr[left] + " " + arr[right]);
    left++;
    right--;
}
```

---

### 🔹 Use Cases

* Reverse array
* Pair problems
* Palindrome checking

---

## 2. Sliding Window Traversal

### 🔹 Example (Window Size = 3)

```java
for (int i = 0; i <= arr.length - 3; i++) {
    int sum = 0;

    for (int j = i; j < i + 3; j++) {
        sum += arr[j];
    }

    System.out.println(sum);
}
```

---

### 🔹 Use Cases

* Subarray problems
* Maximum sum problems

---

## 📌 Traversal in 2D Arrays

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

---

## 📌 Time Complexity

* Traversing an array of size `n` → **O(n)**

---

## 📌 Common Mistakes

❌ Using `<=` instead of `<`

```java
for (int i = 0; i <= arr.length; i++) // WRONG
```

✔ Correct:

```java
for (int i = 0; i < arr.length; i++)
```

---

❌ Accessing invalid index

```java
arr[arr.length] // ERROR
```

---

## 📌 Interview Tips

* Always start with simple traversal
* Optimize using:

  * Two pointers
  * Sliding window
  * Prefix sum
* Be careful with boundaries

---

## 📌 Conclusion

Array traversal is the **foundation of almost every DSA problem**.

Mastering traversal helps in:

* Writing efficient code
* Understanding problem patterns
* Solving complex problems easily

---

## 🚀 Next Topics

* Prefix Sum Arrays
* Two Pointer Technique
* Sliding Window Problems
* Searching Algorithms

```
---
