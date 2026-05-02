# Arrays in Java

## 📌 What is an Array?

An **array** is a fundamental data structure that allows you to store multiple elements of the same data type in a single variable.

- Elements are stored in **contiguous memory locations**
- Each element is accessed using an **index**
- Indexing starts from **0**

In Java:
- Arrays are **objects**
- They can store:
  - Primitive data types (`int`, `char`, etc.)
  - Object references

---

## 📌 Why Arrays are Important?

Arrays are useful when:
- You need to store a **fixed-size collection**
- Efficient **access and manipulation** is required
- Implementing algorithms like searching, sorting, etc.

---

## 📌 Types of Arrays

### 1. One-Dimensional Array
A linear structure storing elements in a single row.

```java
int[] numbers = {1, 2, 3, 4, 5};
```
### 2. Multi-Dimensional Array

Arrays of arrays (used for matrices or tables).

```java
int[][] matrix = {
    {1, 2},
    {3, 4}
};
```

---

## 📌 Basic Operations on Arrays

### 1. Creating Arrays

```java
// Declaration + creation
int[] arr = new int[5];

// Declaration + initialization
int[] arr = {1, 2, 3, 4, 5};
```

---

### 2. Accessing Elements

```java
int[] arr = {10, 20, 30};
System.out.println(arr[0]); // Output: 10
```

---

### 3. Modifying Elements

```java
arr[1] = 25;
```

---

### 4. Traversing (Displaying)

```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

---

## 📌 Complete Example

```java
public class ArrayOperations {
    public static void main(String[] args) {

        int[] numbers = new int[5];

        numbers[0] = 10;
        numbers[1] = 20;
        numbers[2] = 30;
        numbers[3] = 40;
        numbers[4] = 50;

        System.out.println(numbers[0]);
        System.out.println(numbers[3]);

        numbers[2] = 35;

        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
    }
}
```

---

## 📌 Example: Odd & Even Numbers

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner s = new Scanner(System.in);
        int n = s.nextInt();

        int[] a = new int[n];

        for (int i = 0; i < n; i++) {
            a[i] = s.nextInt();
        }

        System.out.print("Odd: ");
        for (int i = 0; i < n; i++) {
            if (a[i] % 2 != 0) {
                System.out.print(a[i] + " ");
            }
        }

        System.out.print("\nEven: ");
        for (int i = 0; i < n; i++) {
            if (a[i] % 2 == 0) {
                System.out.print(a[i] + " ");
            }
        }
    }
}
```

---

## 📌 Advanced Operations

### 1. Find Length

```java
System.out.println(arr.length);
```

---

### 2. Insert Element

```java
int[] original = {10, 20, 30};
int[] newArr = new int[4];

for (int i = 0; i < original.length; i++) {
    newArr[i] = original[i];
}

newArr[3] = 40;
```

---

### 3. Delete Element

```java
int[] original = {10, 20, 30, 40};
int deleteIndex = 1;

int[] newArr = new int[original.length - 1];

for (int i = 0, k = 0; i < original.length; i++) {
    if (i == deleteIndex) continue;
    newArr[k++] = original[i];
}
```

---

### 4. Merge Arrays

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {4, 5, 6};

int[] merged = new int[arr1.length + arr2.length];

System.arraycopy(arr1, 0, merged, 0, arr1.length);
System.arraycopy(arr2, 0, merged, arr1.length, arr2.length);
```

---

## 📌 Key Properties

* Fixed size (cannot be resized)
* Fast access: **O(1)**
* Homogeneous elements
* Stored in contiguous memory

---

## 📌 Limitations

* Size is fixed
* Insertion/Deletion is costly
* No built-in dynamic resizing

👉 Use `ArrayList` for dynamic behavior

---

## 📌 Common Interview Questions

### 1. Can array size be changed?

❌ No

---

### 2. What happens on invalid index?

➡️ Throws `ArrayIndexOutOfBoundsException`

---

### 3. Looping methods:

* `for` loop
* `while` loop
* `for-each` loop

---

