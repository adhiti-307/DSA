# Factorial Using Recursion in Java

# 📘 Problem Statement

Given a number `N`,
find the factorial of `N` using recursion.

---

# What is Factorial?

Factorial of a number means:

```text
N! = N × (N-1) × (N-2) × ... × 1
```

---

# Examples

## Example 1

```text
5! = 5 × 4 × 3 × 2 × 1 = 120
```

---

## Example 2

```text
3! = 3 × 2 × 1 = 6
```

---

# 🧠 Recursive Thinking

Suppose we want:

```text
5!
```

We can write:

```text
5! = 5 × 4!
```

Similarly:

```text
4! = 4 × 3!
```

Again:

```text
3! = 3 × 2!
```

This creates a recursive relation.

---

# Recursive Relation

```text
factorial(n) = n × factorial(n-1)
```

---

# Base Case

Smallest factorial is:

```text
0! = 1
```

So:

```java
if(n == 0)
    return 1;
```

This stops recursion.

---

# 📌 Recursive Flow

Suppose:

```java
factorial(5)
```

Calls happen like:

```text
factorial(5)
→ 5 × factorial(4)

→ 5 × 4 × factorial(3)

→ 5 × 4 × 3 × factorial(2)

→ 5 × 4 × 3 × 2 × factorial(1)

→ 5 × 4 × 3 × 2 × 1 × factorial(0)

→ 5 × 4 × 3 × 2 × 1 × 1
```

Final Answer:

```text
120
```

---

# 🌳 Recursive Tree

```text
factorial(5)
|
factorial(4)
|
factorial(3)
|
factorial(2)
|
factorial(1)
|
factorial(0)
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
1 → 1 → 2 → 6 → 24 → 120
```

---

# ✅ Java Code

```java
public class FactorialRecursion {

    static int factorial(int n){

        // Base Case
        if(n == 0)
            return 1;

        // Recursive Relation
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {

        int n = 5;

        System.out.println(factorial(n));
    }
}
```

---

# 🧪 Dry Run

Suppose:

```java
factorial(4)
```

---

## Step 1

```text
factorial(4)
= 4 × factorial(3)
```

---

## Step 2

```text
factorial(3)
= 3 × factorial(2)
```

---

## Step 3

```text
factorial(2)
= 2 × factorial(1)
```

---

## Step 4

```text
factorial(1)
= 1 × factorial(0)
```

---

## Step 5

```text
factorial(0)
= 1
```

---

# Returning Answers

```text
factorial(1) = 1

factorial(2) = 2

factorial(3) = 6

factorial(4) = 24
```

---

# 📦 Call Stack Visualization

```text
factorial(4)
factorial(3)
factorial(2)
factorial(1)
factorial(0)
```

After base case:
stack starts removing functions.

---

# ⏱️ Complexity Analysis

## Time Complexity

```text
O(n)
```

Because:
- function runs `n` times.

---

## Space Complexity

```text
O(n)
```

Because:
- recursive calls use stack memory.

---

# ⚠️ Important Note

Without base case:

```java
if(n == 0)
    return 1;
```

recursion never stops and causes:

```text
StackOverflowError
```

---

# 🔥 Key Learning

Every recursive problem needs:

## 1️⃣ Base Case

Stops recursion.

---

## 2️⃣ Recursive Relation

Breaks problem into smaller problem.

---

# 🧠 Main Formula

```text
factorial(n) = n × factorial(n-1)
```

---

# 🚀 Conclusion

Factorial is one of the best beginner recursion problems because it teaches:

- recursive thinking
- base case
- recursive relation
- call stack
- returning answers

It builds the foundation for:
- Dynamic Programming
- Trees
- Backtracking
- Divide & Conquer
