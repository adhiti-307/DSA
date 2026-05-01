# 📘 Arrays – Complete Notes

---

# 🔹 1. What is an Array?

An array is a **linear data structure** that stores elements of the same type in **contiguous memory locations**.

---

## 📊 Visualization

```text
Index:   0   1   2   3   4
Value:  10  20  30  40  50
```

---

# 🔹 2. Key Properties

* Fixed size
* Indexed (0-based indexing)
* Fast access → **O(1)**
* Stored in contiguous memory

---

# 🔹 3. Basic Operations

| Operation          | Time Complexity |
| ------------------ | --------------- |
| Access             | O(1)            |
| Traversal          | O(n)            |
| Insertion (end)    | O(1)            |
| Insertion (middle) | O(n)            |
| Deletion           | O(n)            |

---

# 🔹 4. Array Traversal

## ✅ Template

```java
for(int i = 0; i < arr.length; i++){
    System.out.print(arr[i] + " ");
}
```

---

# 🔹 5. Important Patterns in Arrays

---

## 🔸 5.1 Prefix Sum

Used for **range sum queries**

### 📊 Visualization

```text
Array:   1   2   3   4
Prefix:  1   3   6   10
```

### ✅ Formula

```text
prefix[i] = prefix[i-1] + arr[i]
```

### ✅ Code

```java
int[] prefix = new int[n];
prefix[0] = arr[0];

for(int i = 1; i < n; i++){
    prefix[i] = prefix[i-1] + arr[i];
}
```

### 🔥 Range Query

```text
sum(l, r) = prefix[r] - prefix[l-1]
```

---

## 🔸 5.2 Sliding Window

Used for **subarray / substring problems**

### 📊 Visualization
## 🔸 Sliding Window (k = 3)

```text
Array:   2   1   5   1   3   2

[2   1   5] → Sum = 8
    [1   5   1] → Sum = 7
        [5   1   3] → Sum = 9
            [1   3   2] → Sum = 6

Array:   2   1   5   1   3   2

Step 1:  [2   1   5]  1   3   2
Step 2:   2  [1   5   1]  3   2
Step 3:   2   1  [5   1   3]  2
Step 4:   2   1   5  [1   3   2]

🔸 Variable Window (Sum ≤ 7)
Array:   1   2   3   4   5

[1] → Sum = 1
[1   2] → Sum = 3
[1   2   3] → Sum = 6
[1   2   3   4] → Sum = 10 ❌

Shrink →
[2   3   4] → Sum = 9 ❌
[3   4] → Sum = 7 ✅

[3   4   5] → Sum = 12 ❌

Shrink →
[4   5] → Sum = 9 ❌
[5] → Sum = 5

### ✅ Fixed Window

```java
int sum = 0;

for(int i = 0; i < k; i++){
    sum += arr[i];
}

for(int i = k; i < n; i++){
    sum += arr[i];
    sum -= arr[i-k];
}
```

---

### ✅ Variable Window

```java
int left = 0, sum = 0;

for(int right = 0; right < n; right++){
    sum += arr[right];

    while(sum > target){
        sum -= arr[left];
        left++;
    }
}
```

---

## 🔸 5.3 Kadane’s Algorithm (Maximum Subarray Sum)

### 📊 Visualization
Kadane’s Algorithm (Maximum Subarray Sum)

Array:  -2   1  -3   4  -1   2   1  -5   4

Step-by-step:

Start:
curr = -2, max = -2

i=1 → 1
curr = max(1, -2 + 1) = 1
max  = max(-2, 1) = 1

i=2 → -3
curr = max(-3, 1 - 3) = -2
max  = max(1, -2) = 1

i=3 → 4
curr = max(4, -2 + 4) = 4
max  = max(1, 4) = 4

i=4 → -1
curr = max(-1, 4 - 1) = 3
max  = max(4, 3) = 4

i=5 → 2
curr = max(2, 3 + 2) = 5
max  = max(4, 5) = 5

i=6 → 1
curr = max(1, 5 + 1) = 6
max  = max(5, 6) = 6

i=7 → -5
curr = max(-5, 6 - 5) = 1
max  = max(6, 1) = 6

i=8 → 4
curr = max(4, 1 + 4) = 5
max  = max(6, 5) = 6


Final Answer: 6
Subarray: [4  -1  2  1]
---

### ✅ Idea

* Add elements continuously
* Reset sum when it becomes negative

---

### ✅ Code

```java
int maxSum = arr[0];
int curr = arr[0];

for(int i = 1; i < n; i++){
    curr = Math.max(arr[i], curr + arr[i]);
    maxSum = Math.max(maxSum, curr);
}
```

---

## 🔸 5.4 Two Pointer Technique

### 📊 Visualization

Two Pointer Technique (Sorted Array)

Array:   1   2   3   4   6   8   9
Target: 10

left = 0, right = 6

Step 1:
1 + 9 = 10 ✅ (found)


---

Another Example (movement view)

Array:   1   2   3   4   6   8   9
Target: 11

Step 1:
[1               9] → 1+9 = 10 < 11 → move left →

Step 2:
  [2             9] → 2+9 = 11 ✅


---

General Movement Pattern

[ L                 R ]

If sum < target → move L →  
If sum > target → move R ←  
If sum == target → answer found


---

Visual Pointer Movement

Array:   1   2   3   4   6   8   9

Step 1:  L→1               R←9  
Step 2:     L→2            R←9  
Step 3:        L→3         R←9  
Step 4:           L→4      R←9  


---

Quick Summary

Two Pointer:

Start → (L = 0, R = n-1)  
Move inward based on condition  
Reduces O(n²) → O(n)
---

### ✅ Code

```java
int left = 0, right = n - 1;

while(left < right){
    int sum = arr[left] + arr[right];

    if(sum == target) break;
    else if(sum < target) left++;
    else right--;
}
```

---

## 🔸 5.5 Binary Search (on Arrays)

### 📊 Visualization
Binary Search (Sorted Array)

Array:   1   2   3   4   6   8   9
Target: 6

low = 0, high = 6

Step 1:
mid = 3 → arr[3] = 4
4 < 6 → search right
low = 4

Step 2:
mid = 5 → arr[5] = 8
8 > 6 → search left
high = 4

Step 3:
mid = 4 → arr[4] = 6
Found ✅


---

Search Space Reduction

Initial:
[1   2   3   4   6   8   9]

Step 1:
          mid=4
[1   2   3   4]   [6   8   9]

Step 2:
              mid=8
          [6]   [8]

Step 3:
            mid=6 → Found


---

General Pattern

low = 0, high = n-1

while(low <= high):
    mid = low + (high - low)/2

    if arr[mid] == target → found
    if arr[mid] < target → low = mid + 1
    if arr[mid] > target → high = mid - 1


---

Visual Pointer Movement

Array:   1   2   3   4   6   8   9

Step 1:  L→1      M→4        R→9  
Step 2:             L→6   M→8   R→9  
Step 3:             L→6   M→6   R→6  


---

Quick Summary

Binary Search:

Divide search space into halves  
Time Complexity → O(log n)  
Works only on sorted data
---

### ✅ Code

```java
int low = 0, high = n - 1;

while(low <= high){
    int mid = low + (high - low) / 2;

    if(arr[mid] == target) return mid;
    else if(arr[mid] < target) low = mid + 1;
    else high = mid - 1;
}
```

---

# 🔹 6. 2D Arrays (Matrix)

### 📊 Visualization

2D Array (Matrix)

Matrix (3 x 3):

        Col→  0   1   2
Row↓
 0          [1   2   3]
 1          [4   5   6]
 2          [7   8   9]


---

Index Representation

matrix[row][col]

matrix[0][0] = 1  
matrix[1][2] = 6  
matrix[2][1] = 8  


---

Row-wise Traversal

[1   2   3]  
[4   5   6]  
[7   8   9]  


---

Column-wise Traversal

1   4   7  
2   5   8  
3   6   9  


---

Spiral Traversal

  → → →  
 ↑     ↓  
  ← ← ←  
  

Order:
1 → 2 → 3 → 6 → 9 → 8 → 7 → 4 → 5


---

Diagonal Traversal

Primary Diagonal:
1   5   9  

Secondary Diagonal:
3   5   7  


---

Movement Directions

Right  → (0, +1)  
Left   ← (0, -1)  
Down   ↓ (+1, 0)  
Up     ↑ (-1, 0)  


---

Quick Summary

2D Array:

Access → matrix[i][j]  
Row traversal → outer loop (i), inner (j)  
Column traversal → swap loops  
Used in → matrices, grids, graphs
---

### ✅ Traversal

```java
for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
        System.out.print(matrix[i][j] + " ");
    }
}
```

---

# 🔹 7. Important Array Problems

* Two Sum
* Maximum Subarray
* Rotate Array
* Move Zeroes
* Merge Intervals
* Trapping Rain Water

---

# 🔹 8. Common Mistakes

```text
❌ Off-by-one errors  
❌ Not handling empty array  
❌ Ignoring edge cases  
❌ Integer overflow  
```

---

# 🔹 9. Interview Tips

```text
✔ Check constraints first  
✔ Start with brute force  
✔ Optimize using patterns  
✔ Dry run examples  
```

---

# 🧠 Quick Revision

```text
Array → contiguous memory  
Prefix Sum → range queries  
Sliding Window → subarrays  
Kadane → max subarray  
Two Pointer → sorted arrays  
Binary Search → log n  
```

---

# 🔥 Final Insight

```text
Most array problems = pattern recognition
```

👉 Master these:

* Sliding Window
* Prefix Sum
* Two Pointer

You’ll solve **majority of interview questions**

---
