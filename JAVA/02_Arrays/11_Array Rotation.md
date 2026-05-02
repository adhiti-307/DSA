# Array Rotation in Java

## 📌 Introduction

**Array Rotation** is a fundamental operation where elements of an array are shifted:

- **Left Rotation** → Elements move toward the beginning
- **Right Rotation** → Elements move toward the end

---

## 📌 Problem Statement

Given an array and an integer `k`, rotate the array:

- Left rotate by `k`
- Right rotate by `k`

---

## 📌 Example

```text
Input:
arr = [1, 2, 3, 4, 5]
k = 2

Left Rotation:
[3, 4, 5, 1, 2]

Right Rotation:
[4, 5, 1, 2, 3]
````

---

## 📌 Types of Rotation

* Left Rotation
* Right Rotation

---

## 📌 Approaches to Solve

### ✔️ 1. Naive Method (One by One Rotation)

### 🔹 Algorithm

1. Repeat `d` times:

   * Store first element
   * Shift all elements left
   * Place stored element at end

---

### 🔹 Complexity

* Time: **O(n × d)**
* Space: **O(1)**

---

### 🔹 Code

```java id="naive_rot"
public class NaiveRotation {
    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;

        for (int i = 0; i < d; i++) {
            int temp = arr[0];

            for (int j = 0; j < n - 1; j++) {
                arr[j] = arr[j + 1];
            }

            arr[n - 1] = temp;
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        leftRotate(arr, 2);
        System.out.println(java.util.Arrays.toString(arr));
    }
}
```

---

## ✔️ 2. Using Temporary Array

### 🔹 Algorithm

1. Store first `d` elements in temp array
2. Shift remaining elements left
3. Copy temp elements to end

---

### 🔹 Complexity

* Time: **O(n)**
* Space: **O(d)**

---

### 🔹 Code

```java id="temp_rot"
public class TempArrayRotation {
    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;
        int[] temp = new int[d];

        for (int i = 0; i < d; i++)
            temp[i] = arr[i];

        for (int i = d; i < n; i++)
            arr[i - d] = arr[i];

        for (int i = 0; i < d; i++)
            arr[n - d + i] = temp[i];
    }
}
```

---

## ✔️ 3. Juggling Algorithm

### 🔹 Key Idea

Divide array into **GCD(d, n)** sets and rotate each set.

---

### 🔹 Complexity

* Time: **O(n)**
* Space: **O(1)**

---

### 🔹 Code

```java id="juggling_rot"
public class JugglingRotation {

    public static int gcd(int a, int b) {
        return (b == 0) ? a : gcd(b, a % b);
    }

    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;
        d = d % n;

        int g = gcd(d, n);

        for (int i = 0; i < g; i++) {
            int temp = arr[i];
            int j = i;

            while (true) {
                int k = j + d;

                if (k >= n)
                    k = k - n;

                if (k == i)
                    break;

                arr[j] = arr[k];
                j = k;
            }

            arr[j] = temp;
        }
    }
}
```

---

## ✔️ 4. Reversal Algorithm (Most Important ⭐)

### 🔹 Algorithm

1. Reverse first `d` elements
2. Reverse remaining `n-d` elements
3. Reverse entire array

---

### 🔹 Complexity

* Time: **O(n)**
* Space: **O(1)**

---

### 🔹 Code

```java id="reversal_rot"
public class ReversalRotation {

    public static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start++] = arr[end];
            arr[end--] = temp;
        }
    }

    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;
        d = d % n;

        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }
}
```

---

## 📌 Right Rotation Logic

Right rotation by `k` can be done as:

```text
Right Rotation = Left Rotation by (n - k)
```
```
public class RightRotationUsingLeft {

    public static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    // Left rotation using reversal
    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;
        d = d % n;

        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }

    // Right rotation using left rotation
    public static void rightRotate(int[] arr, int k) {
        int n = arr.length;
        k = k % n;

        leftRotate(arr, n - k);
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        rightRotate(arr, 2);

        System.out.println(java.util.Arrays.toString(arr));
    }
}
```

## ✔️ Right Rotation (Direct Method - Reversal Algorithm) ⭐

### 🔹 Algorithm

To rotate the array to the **right by k positions**:

1. Reverse the entire array  
2. Reverse the first `k` elements  
3. Reverse the remaining `n - k` elements  

---

### 🔹 Code

```java
public class RightRotation {

    public static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    public static void rightRotate(int[] arr, int k) {
        int n = arr.length;
        k = k % n;

        // Step 1: Reverse entire array
        reverse(arr, 0, n - 1);

        // Step 2: Reverse first k elements
        reverse(arr, 0, k - 1);

        // Step 3: Reverse remaining elements
        reverse(arr, k, n - 1);
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        rightRotate(arr, 2);

        System.out.println(java.util.Arrays.toString(arr));
    }
}
```

---

### 🔹 Example

```text
Input:  [1, 2, 3, 4, 5], k = 2

Step 1: Reverse all       → [5, 4, 3, 2, 1]
Step 2: Reverse first k   → [4, 5, 3, 2, 1]
Step 3: Reverse rest      → [4, 5, 1, 2, 3]

Output: [4, 5, 1, 2, 3]
```

---

### 🔹 Complexity

* Time Complexity: **O(n)**
* Space Complexity: **O(1)**

---

### 🔹 Why This Method is Important?

* Most **interview-preferred solution**
* Works **in-place (no extra space)**
* Efficient and easy to remember once understood

---

## 📌 Important Notes

* Always handle:

```java
d = d % n;
```

(to avoid unnecessary rotations)

---

## 📌 When to Use Which Approach?

| Method     | Best For                         |
| ---------- | -------------------------------- |
| Naive      | Small inputs                     |
| Temp Array | Easy implementation              |
| Juggling   | Optimal without extra space      |
| Reversal ⭐ | Most commonly used in interviews |

---

## 📌 Applications

* Circular queues
* Buffer rotation
* String rotation problems
* Sliding window problems

---

## 📌 FAQs

### 1. What is array rotation?

Shifting elements left or right by `k` positions.

---

### 2. What if `k > n`?

➡️ Use `k % n`

---

### 3. Is rotation in-place?

* Yes (Reversal, Juggling)
* No (Temp array)

---

### 4. Can left rotation be used for right rotation?

➡️ Yes, using `(n - k)`

---

## 📌 Conclusion

Array rotation is a **core DSA concept** frequently asked in interviews.

* Prefer **Reversal Algorithm** for optimal performance
* Understand all methods for flexibility

---
