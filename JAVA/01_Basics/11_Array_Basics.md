# 📘 Array Basics in Java

---

# 🔹 1. What is an Array?

An array is a **collection of elements of the same data type** stored in **contiguous memory locations**.

```text id="arr1"
Index-based access → O(1)
```

---

# 🔹 2. Array Representation

```text id="arr2"
Array:   10   20   30   40   50  
Index:    0    1    2    3    4
```

---

# 🔹 3. Declaration & Initialization

---

## 🔸 Declaration

```java id="arr3"
int[] arr;
```

---

## 🔸 Initialization

```java id="arr4"
arr = new int[5];
```

---

## 🔸 Combined

```java id="arr5"
int[] arr = new int[5];
```

---

## 🔸 Direct Initialization

```java id="arr6"
int[] arr = {10, 20, 30, 40, 50};
```

---

# 🔹 4. Accessing Elements

```java id="arr7"
System.out.println(arr[0]);
arr[2] = 100;
```

---

# 🔹 5. Traversing an Array

---

## 🔸 Using for loop

```java id="arr8"
for(int i = 0; i < arr.length; i++){
    System.out.print(arr[i] + " ");
}
```

---

## 🔸 Using for-each loop

```java id="arr9"
for(int x : arr){
    System.out.print(x + " ");
}
```

---

# 🔹 6. Input Array

```java id="arr10"
int n = sc.nextInt();
int[] arr = new int[n];

for(int i = 0; i < n; i++){
    arr[i] = sc.nextInt();
}
```

---

# 🔹 7. Basic Operations

---

## 🔸 Find Maximum

```java id="arr11"
int max = arr[0];

for(int x : arr){
    if(x > max) max = x;
}
```

---

## 🔸 Find Minimum

```java id="arr12"
int min = arr[0];

for(int x : arr){
    if(x < min) min = x;
}
```

---

## 🔸 Sum of Elements

```java id="arr13"
int sum = 0;

for(int x : arr){
    sum += x;
}
```

---

# 🔹 8. Array Length

```java id="arr14"
arr.length
```

---

# 🔹 9. Common Patterns

---

## 🔸 Reverse Array

```java id="arr15"
int left = 0, right = arr.length - 1;

while(left < right){
    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}
```

---

## 🔸 Linear Search

```java id="arr16"
for(int i = 0; i < arr.length; i++){
    if(arr[i] == key){
        return i;
    }
}
return -1;
```

---

# 🔹 10. 2D Array Basics

---

## 🔸 Declaration

```java id="arr17"
int[][] mat = new int[3][3];
```

---

## 🔸 Traversal

```java id="arr18"
for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
        System.out.print(mat[i][j] + " ");
    }
}
```

---

# 🔹 11. Time Complexity

| Operation | Complexity |
| --------- | ---------- |
| Access    | O(1)       |
| Traversal | O(n)       |
| Search    | O(n)       |

---

# 🔹 12. Advantages

```text id="arr19"
✔ Fast access  
✔ Easy traversal  
✔ Memory efficient  
```

---

# 🔹 13. Disadvantages

```text id="arr20"
❌ Fixed size  
❌ Costly insertion/deletion  
```

---

# 🔹 14. Common Mistakes

```text id="arr21"
❌ Index out of bounds  
❌ Not initializing array  
❌ Off-by-one errors  
```

---

# 🔹 15. Interview Tips

```text id="arr22"
✔ Master traversal  
✔ Practice patterns  
✔ Handle edge cases  
✔ Think in indices  
```

---

# 🧠 Quick Revision

```text id="arr23"
Array → contiguous memory  
Index → access  
Loop → traversal  
```

---

# 🔥 Final Insight

```text id="arr24"
Arrays = foundation of DSA
```

👉 Master arrays → everything becomes easier

---
