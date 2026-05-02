# 2D Arrays (Matrix) in Java

## 📌 Introduction

A **2D array (Two-Dimensional Array)** is an array of arrays used to store data in a **tabular format (rows × columns)**.

- Think of it like a **matrix or grid**
- Each element is accessed using **two indices**:
  - Row index
  - Column index

---

## 📌 What is a 2D Array?

A 2D array:
- Stores elements in **rows and columns**
- Is essentially an **array of arrays**
- Follows **row-major order** in memory

---

## 📌 Syntax

```java
dataType[][] arrayName;
````

### Example

```java
int[][] matrix = new int[3][4]; // 3 rows, 4 columns
```

---

## 📌 How 2D Arrays Work

* Each row is a **separate array**
* Access using:

```java
matrix[row][column];
```

### Example

```java
int value = matrix[1][2];
```

---

## 📌 Initialization

### 1. Static Initialization

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

---

### 2. Dynamic Initialization

```java
int[][] matrix = new int[2][3];

matrix[0][0] = 1;
matrix[0][1] = 2;
matrix[0][2] = 3;
```

---

## 📌 Types of 2D Arrays

### 1. Regular 2D Array

All rows have equal columns.

```java
int[][] arr = new int[3][4];
```

---

### 2. Jagged Array (Irregular)

Rows can have different sizes.

```java
int[][] jagged = new int[3][];

jagged[0] = new int[2];
jagged[1] = new int[4];
jagged[2] = new int[1];
```

---

## 📌 Accessing Elements

```java
int value = matrix[1][2];
```

⚠️ Invalid index → `ArrayIndexOutOfBoundsException`

---

## 📌 Modifying Elements

```java
matrix[2][1] = 10;
```

---

## 📌 Traversing a 2D Array

### 1. Using Nested Loops

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

---

### 2. Using For-Each Loop

```java
for (int[] row : matrix) {
    for (int val : row) {
        System.out.print(val + " ");
    }
    System.out.println();
}
```

---

## 📌 Common Operations

### 1. Sum of All Elements

```java
int sum = 0;

for (int[] row : matrix) {
    for (int val : row) {
        sum += val;
    }
}
```

---

### 2. Maximum Element

```java
int max = matrix[0][0];

for (int[] row : matrix) {
    for (int val : row) {
        if (val > max) {
            max = val;
        }
    }
}
```

---

### 3. Transpose of Matrix

```java
int[][] transpose = new int[matrix[0].length][matrix.length];

for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[0].length; j++) {
        transpose[j][i] = matrix[i][j];
    }
}
```

---

## 📌 Complete Example

```java
public class TwoDArrayOperations {
    public static void main(String[] args) {

        int[][] matrix = {
            {5, 8, 2},
            {4, 6, 7},
            {9, 1, 3}
        };

        printMatrix(matrix);

        matrix[1][1] = 10;

        int sum = 0;
        int max = matrix[0][0];

        for (int[] row : matrix) {
            for (int val : row) {
                sum += val;
                if (val > max) max = val;
            }
        }

        System.out.println("Sum: " + sum);
        System.out.println("Max: " + max);

        int[][] transpose = new int[matrix[0].length][matrix.length];

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                transpose[j][i] = matrix[i][j];
            }
        }

        printMatrix(transpose);
    }

    public static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row) {
                System.out.print(val + "\t");
            }
            System.out.println();
        }
    }
}
```

---

## 📌 Advantages

* Represents data in **matrix/grid form**
* Easy to traverse using loops
* Efficient for **fixed-size data**

---

## 📌 Limitations

* Fixed size (not dynamic)
* Complex for very large data
* Less flexible than `ArrayList`

---

## 📌 Important Concepts for DSA

* Matrix traversal
* Spiral traversal
* Diagonal traversal
* Row/Column sum problems
* Matrix rotation
* Prefix sum in 2D

---

## 📌 FAQs

### 1. What is a 2D array?

➡️ An array of arrays storing data in rows and columns

---

### 2. Difference between 1D and 2D array?

| Feature   | 1D Array  | 2D Array    |
| --------- | --------- | ----------- |
| Structure | Linear    | Grid        |
| Indexing  | One index | Two indices |

---

### 3. How to find rows & columns?

```java
int rows = matrix.length;
int cols = matrix[0].length;
```

---

### 4. How to iterate?

* Nested loops
* For-each loop

---

## 📌 Conclusion

2D arrays are essential for:

* Matrix-based problems
* Grid traversal
* Competitive programming

They form the base for many advanced DSA concepts.

---
