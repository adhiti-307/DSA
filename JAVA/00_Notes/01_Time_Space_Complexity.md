# 📘 Time & Space Complexity

---

## 🔹 1. What is Time Complexity?

Time Complexity measures **how the running time of an algorithm grows with input size (n)**.

👉 It does NOT measure exact time (seconds),
👉 It measures **growth rate**.

---

### 🔸 Example

```java
for(int i = 0; i < n; i++){
    System.out.println(i);
}
```

* Runs **n times**
* Time Complexity = **O(n)**

---

## 🔹 2. What is Space Complexity?

Space Complexity measures **how much extra memory an algorithm uses**.

Includes:

* Variables
* Data structures
* Recursion stack

---

### 🔸 Example

```java
int sum = 0;
```

* Uses constant memory
* Space Complexity = **O(1)**

---

# 🔥 3. Types of Complexity

## ✅ Best Case

Minimum time taken
Example: Searching first element → **O(1)**

## ✅ Average Case

Expected time

## ✅ Worst Case

Maximum time taken
Example: Searching last element → **O(n)**

---

# ⚡ 4. Common Time Complexities

| Complexity | Name         | Example                     |
| ---------- | ------------ | --------------------------- |
| O(1)       | Constant     | Access array element        |
| O(log n)   | Logarithmic  | Binary Search               |
| O(n)       | Linear       | Traversing array            |
| O(n log n) | Linearithmic | Merge Sort                  |
| O(n²)      | Quadratic    | Nested loops                |
| O(2ⁿ)      | Exponential  | Recursion (subset problems) |

---

## 🔹 Growth Order (Best → Worst)

```text
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)
```

---

# 🔍 5. How to Calculate Time Complexity

## 🔸 1. Count loops

```java
for(int i = 0; i < n; i++)   → O(n)
```

---

## 🔸 2. Nested loops

```java
for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
    }
}
```

👉 O(n × n) = **O(n²)**

---

## 🔸 3. Sequential loops

```java
for(int i = 0; i < n; i++){}
for(int i = 0; i < n; i++){}
```

👉 O(n) + O(n) = **O(n)**

---

## 🔸 4. Logarithmic loop

```java
for(int i = 1; i < n; i *= 2)
```

👉 O(log n)

---

## 🔸 5. Recursion

```java
T(n) = T(n-1) + O(1) → O(n)
T(n) = 2T(n/2) + O(n) → O(n log n)
```

---

# 📦 6. Space Complexity Breakdown

## 🔹 1. Input Space

Memory used by input (ignored in most cases)

## 🔹 2. Auxiliary Space

Extra memory used

---

### 🔸 Example

```java
int[] arr = new int[n];
```

👉 Space = **O(n)**

---

### 🔸 Recursion Space

```java
factorial(n)
```

👉 Stack depth = n
👉 Space = **O(n)**

---

# 🔥 7. Important Algorithm Complexities

| Algorithm     | Time Complexity |
| ------------- | --------------- |
| Linear Search | O(n)            |
| Binary Search | O(log n)        |
| Bubble Sort   | O(n²)           |
| Merge Sort    | O(n log n)      |
| Quick Sort    | O(n log n) avg  |
| DFS / BFS     | O(V + E)        |

---

# ⚠️ 8. Important Rules

## ✅ Drop constants

```text
O(2n) → O(n)
```

## ✅ Ignore lower terms

```text
O(n² + n) → O(n²)
```

## ✅ Focus on worst case

---

# 💡 9. Practical Examples

## 🔸 Example 1

```java
for(int i = 0; i < n; i++){
    System.out.println(i);
}
```

👉 O(n)

---

## 🔸 Example 2

```java
for(int i = 0; i < n; i++){
    for(int j = 0; j < i; j++){
    }
}
```

👉 O(n²)

---

## 🔸 Example 3

```java
while(n > 0){
    n = n / 2;
}
```

👉 O(log n)

---

# 🚀 10. Why It Matters

* Helps choose **efficient algorithms**
* Important for **interviews**
* Required for **optimization**

---

# 🧠 Quick Revision

```text
O(1) → constant  
O(log n) → divide by 2  
O(n) → single loop  
O(n²) → nested loop  
O(n log n) → divide + loop  
```

---

# 🔥 Final Tip

Always ask:

```text
“How does this scale when input grows?”
```

That’s the core of complexity analysis.

---
