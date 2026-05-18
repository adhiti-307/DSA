# Power Function Using Recursion in Java

# 📘 Problem Statement

Given two integers:

```text
a → base
b → exponent
```

Find:

```text
a^b
```

using recursion.

---

# What is Power?

Power means repeated multiplication.

```text
a^b = a × a × a × ... b times
```

---

# Examples

## Example 1

```text
2^5 = 2 × 2 × 2 × 2 × 2 = 32
```

---

## Example 2

```text
3^4 = 3 × 3 × 3 × 3 = 81
```

---

# 🧠 Recursive Thinking

Suppose we want:

```text
2^5
```

We can write:

```text
2^5 = 2 × 2^4
```

Again:

```text
2^4 = 2 × 2^3
```

Again:

```text
2^3 = 2 × 2^2
```

This creates a recursive relation.

---

# Recursive Relation

```text
power(a,b) = a × power(a,b-1)
```

---

# Base Case

We know:

```text
a^0 = 1
```

So:

```java
if(b == 0)
    return 1;
```

This stops recursion.

---

# 📌 Recursive Flow

Suppose:

```java
power(2,5)
```

Calls happen like:

```text
2 × power(2,4)

2 × 2 × power(2,3)

2 × 2 × 2 × power(2,2)

2 × 2 × 2 × 2 × power(2,1)

2 × 2 × 2 × 2 × 2 × power(2,0)

2 × 2 × 2 × 2 × 2 × 1
```

Final Answer:

```text
32
```

---

# 🌳 Recursive Tree

```text
power(2,5)
|
power(2,4)
|
power(2,3)
|
power(2,2)
|
power(2,1)
|
power(2,0)
```

Then answers return back upward.

---

# 🧠 Going Down & Returning Back

# Going Down

Recursive calls happen:

```text
5 → 4 → 3 → 2 → 1 → 0
```

---

# Returning Back

Answers return:

```text
1 → 2 → 4 → 8 → 16 → 32
```

---

# ✅ Java Code

```java
public class PowerRecursion {

    static int power(int a, int b){

        // Base Case
        if(b == 0)
            return 1;

        // Recursive Relation
        return a * power(a, b - 1);
    }

    public static void main(String[] args) {

        int a = 2;

        int b = 5;

        System.out.println(power(a, b));
    }
}
```

---

# 🧪 Dry Run

Suppose:

```java
power(3,4)
```

---

## Step 1

```text
power(3,4)
= 3 × power(3,3)
```

---

## Step 2

```text
power(3,3)
= 3 × power(3,2)
```

---

## Step 3

```text
power(3,2)
= 3 × power(3,1)
```

---

## Step 4

```text
power(3,1)
= 3 × power(3,0)
```

---

## Step 5

```text
power(3,0)
= 1
```

---

# Returning Answers

```text
power(3,1) = 3

power(3,2) = 9

power(3,3) = 27

power(3,4) = 81
```

---

# 📦 Call Stack Visualization

```text
power(3,4)
power(3,3)
power(3,2)
power(3,1)
power(3,0)
```

After base case:
functions start returning.

---

# ⏱️ Complexity Analysis

## Time Complexity

```text
O(b)
```

Because:
- recursive call runs `b` times.

---

## Space Complexity

```text
O(b)
```

Because:
- recursion stack stores `b` calls.

---

# ⚠️ Important Note

Without base case:

```java
if(b == 0)
    return 1;
```

recursion never stops and causes:

```text
StackOverflowError
```

---

# 🔥 Optimized Power Approach

The previous solution takes:

```text
O(b)
```

But we can optimize using:

```text
Exponentiation by Squaring
```

to:

```text
O(log b)
```

---

# 🧠 Optimized Recursive Idea

If exponent is even:

```text
a^b = (a^(b/2)) × (a^(b/2))
```

If exponent is odd:

```text
a^b = a × (a^(b/2)) × (a^(b/2))
```

---

# ✅ Optimized Recursive Code

```java
public class FastPower {

    static long power(long a, long b){

        // Base Case
        if(b == 0)
            return 1;

        long half = power(a, b / 2);

        // Even Power
        if(b % 2 == 0){

            return half * half;
        }

        // Odd Power
        else{

            return a * half * half;
        }
    }

    public static void main(String[] args) {

        System.out.println(power(2, 10));
    }
}
```

# ✅ Handle Negative Exponent 

```java
import java.util.*;

class Main {

    public static double power(double base, int exp){

        // Base Case
        if(exp == 0){
            return 1;
        }

        // Handle Negative Power Once
        if(exp < 0){
            return 1 / power(base, -exp);
        }

        return base * power(base, exp - 1);
    }

    public static void main(String[] args) {

        System.out.println(power(5, -4));
    }
}
```
---

# Complexity of Optimized Version

| Complexity | Value |
|---|---|
| Time | O(log b) |
| Space | O(log b) |

---

# 📌 Why Optimization Works

Instead of reducing exponent by:

```text
b-1
```

we reduce by:

```text
b/2
```

This drastically reduces recursive calls.

---

# 📊 Comparison

| Approach | Time | Space |
|---|---|---|
| Normal Recursion | O(b) | O(b) |
| Fast Exponentiation | O(log b) | O(log b) |

---

# 🧠 Main Formula

## Basic Recursion

```text
power(a,b) = a × power(a,b-1)
```

---

## Optimized Recursion

```text
power(a,b) = power(a,b/2)^2
```

---

# 🚀 Conclusion

Power recursion is an excellent beginner recursion problem because it teaches:

- recursive relation
- base case
- recursion tree
- call stack
- divide and conquer optimization

It also introduces:

```text
Exponentiation by Squaring
```

which is used heavily in:
- Binary Exponentiation
- Competitive Programming
- Modular Arithmetic
- Matrix Exponentiation
