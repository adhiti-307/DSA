# 01. Recursion Basics in Java

# 📘 What is Recursion?

Recursion is a programming technique where:

```text
A function calls itself.
```

The function keeps calling itself until a stopping condition is reached.

That stopping condition is called:

```text
Base Case
```

---

# 🧠 Real Life Analogy

Think about standing between two mirrors.

You see:

```text
mirror inside mirror inside mirror...
```

Similarly in recursion:

```text
function → function → function → function...
```

until the base case stops further calls.

---

# 🔥 Structure of a Recursive Function

Every recursive function contains:

## 1️⃣ Base Case

Stops recursion.

Without it:

```text
Infinite recursion occurs.
```

---

## 2️⃣ Recursive Call

Function calls itself on a smaller problem.

---

# Basic Syntax

```java
returnType functionName(parameters){

    // Base Case
    if(condition){
        return value;
    }

    // Recursive Call
    return functionName(smallerInput);
}
```

---

# 📌 Example 1 — Print Numbers from N to 1

## Code

```java
public class RecursionExample {

    static void print(int n){

        // Base Case
        if(n == 0)
            return;

        System.out.println(n);

        // Recursive Call
        print(n - 1);
    }

    public static void main(String[] args) {

        print(5);
    }
}
```

---

# Output

```text
5
4
3
2
1
```

---

# 🧠 Dry Run

```text
print(5)
→ print(4)
→ print(3)
→ print(2)
→ print(1)
→ print(0)
```

At:

```text
n = 0
```

base case stops recursion.

---

# 📌 Important Terminologies

# 1️⃣ Base Case

Condition that stops recursion.

Example:

```java
if(n == 0)
    return;
```

---

# 2️⃣ Recursive Relation

How the problem becomes smaller.

Example:

```java
print(n - 1);
```

---

# 3️⃣ Stack Space

Recursive calls are stored inside:

```text
Call Stack
```

Each function call waits until smaller calls finish.

---

# 📦 Call Stack Visualization

For:

```java
print(3);
```

Stack grows like:

```text
print(3)
print(2)
print(1)
print(0)
```

Then removes calls in reverse order.

---

# 🔄 Recursive Flow

Recursion has TWO phases.

---

# 1️⃣ Going Down Phase

Recursive calls happen.

Example:

```text
5 → 4 → 3 → 2 → 1 → 0
```

---

# 2️⃣ Returning Back Phase

Functions start completing.

Example:

```text
0 → 1 → 2 → 3 → 4 → 5
```

---

# 📌 Example 2 — Print 1 to N

## Code

```java
public class Print1ToN {

    static void print(int n){

        // Base Case
        if(n == 0)
            return;

        // Recursive Call First
        print(n - 1);

        System.out.println(n);
    }

    public static void main(String[] args) {

        print(5);
    }
}
```

---

# Output

```text
1
2
3
4
5
```

---

# 🧠 Important Observation

## Before Recursive Call

Code executes during:

```text
Going Down
```

---

## After Recursive Call

Code executes during:

```text
Returning Back
```

---

# 📌 Example 3 — Factorial

## Problem

Find:

```text
5! = 5 × 4 × 3 × 2 × 1
```

---

# Recursive Thinking

```text
factorial(n)
= n × factorial(n-1)
```

---

# Code

```java
public class Factorial {

    static int factorial(int n){

        // Base Case
        if(n == 0)
            return 1;

        return n * factorial(n - 1);
    }

    public static void main(String[] args) {

        System.out.println(factorial(5));
    }
}
```

---

# Dry Run

```text
factorial(5)
= 5 × factorial(4)
= 5 × 4 × factorial(3)
= 5 × 4 × 3 × factorial(2)
= 5 × 4 × 3 × 2 × factorial(1)
= 5 × 4 × 3 × 2 × 1 × factorial(0)
= 120
```

---

# 📌 Example 4 — Fibonacci

## Fibonacci Series

```text
0 1 1 2 3 5 8 13...
```

Relation:

```text
f(n) = f(n-1) + f(n-2)
```

---

# Code

```java
public class Fibonacci {

    static int fib(int n){

        // Base Cases
        if(n == 0)
            return 0;

        if(n == 1)
            return 1;

        return fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {

        System.out.println(fib(6));
    }
}
```

---

# Recursive Tree

```text
fib(5)
├── fib(4)
│   ├── fib(3)
│   └── fib(2)
└── fib(3)
```

Notice:

```text
fib(3)
```

repeats multiple times.

This leads to:

```text
Dynamic Programming
```

---

# 📌 Types of Recursion

# 1️⃣ Direct Recursion

Function calls itself directly.

```java
fun(){
    fun();
}
```

---

# 2️⃣ Indirect Recursion

Function A calls B,
and B calls A.

```java
funA(){
    funB();
}

funB(){
    funA();
}
```

---

# 3️⃣ Tail Recursion

Recursive call is the LAST operation.

```java
return fun(n-1);
```

Example:

```java
static void print(int n){

    if(n == 0)
        return;

    System.out.println(n);

    print(n-1);
}
```

---

# 4️⃣ Non-Tail Recursion

Work remains after recursive call.

```java
return n + fun(n-1);
```

Example:

```java
static int sum(int n){

    if(n == 0)
        return 0;

    return n + sum(n-1);
}
```

---

# 5️⃣ Tree Recursion

Function makes multiple recursive calls.

Example:

```java
fib(n-1) + fib(n-2)
```

---

# 📌 How to Solve Recursive Problems

Follow these steps.

---

# Step 1️⃣ Identify Smaller Problem

Ask:

```text
How can current problem become smaller?
```

---

# Step 2️⃣ Write Base Case

Smallest valid input.

---

# Step 3️⃣ Trust Recursion

Assume:

```text
recursive function already works.
```

This is VERY important.

---

# Step 4️⃣ Combine Answers

Use smaller answers to build bigger answer.

---

# 📌 Example 5 — Sum of First N Numbers

## Problem

Find:

```text
1 + 2 + 3 + ... + n
```

---

# Recursive Relation

```text
sum(n) = n + sum(n-1)
```

---

# Code

```java
public class SumOfN {

    static int sum(int n){

        // Base Case
        if(n == 0)
            return 0;

        return n + sum(n - 1);
    }

    public static void main(String[] args) {

        System.out.println(sum(5));
    }
}
```

---

# 📌 Example 6 — Power Function

## Problem

Find:

```text
a^b
```

---

# Recursive Relation

```text
power(a,b) = a × power(a,b-1)
```

---

# Code

```java
public class Power {

    static int power(int a, int b){

        // Base Case
        if(b == 0)
            return 1;

        return a * power(a, b - 1);
    }

    public static void main(String[] args) {

        System.out.println(power(2, 5));
    }
}
```

---

# 📌 Recursive Space Complexity

Every recursive call uses stack memory.

If recursion depth is:

```text
n
```

Then stack space becomes:

```text
O(n)
```

---

# ⚠️ Stack Overflow

If recursion becomes too deep:

```text
StackOverflowError
```

occurs.

Example:

```java
void fun(){
    fun();
}
```

This never stops.

---

# 📌 Recursion vs Iteration

| Feature                | Recursion | Iteration |
| ---------------------- | --------- | --------- |
| Uses Stack             | Yes       | No        |
| Easy to Write          | Yes       | Sometimes |
| Memory Efficient       | No        | Yes       |
| Elegant                | Yes       | Less      |
| Risk of Stack Overflow | Yes       | No        |

---

# 📌 When to Use Recursion?

Recursion is useful for:

* Trees
* Graphs
* Backtracking
* Dynamic Programming
* Divide and Conquer
* Binary Search
* Sorting Algorithms

---

# 📌 Important Recursive Problems

# Beginner Level

* Print Numbers
* Factorial
* Fibonacci
* Sum of N Numbers
* Power Function
* Reverse String
* Palindrome Check

---

# Intermediate Level

* Binary Search
* Merge Sort
* Quick Sort
* Tower of Hanoi
* Subsequence Problems
* Permutations
* Combination Sum

---

# Advanced Level

* Backtracking
* DP Memoization
* Tree DP
* Graph DFS
* Divide & Conquer

---

# 📌 Common Mistakes in Recursion

# ❌ Missing Base Case

Leads to:

```text
Infinite recursion
```

---

# ❌ Wrong Recursive Relation

Problem does not reduce properly.

---

# ❌ Stack Overflow

Too many recursive calls.

---

# ❌ Changing Original State Incorrectly

Common in:

* arrays
* strings
* backtracking

---

# 📌 Master Trick for Recursion

Whenever stuck:

Ask:

```text
What is the smallest version of this problem?
```

Then:

```text
Trust recursion for smaller problem.
```

This is the core mindset.

---

# 📌 Recursion + Backtracking Difference

## Recursion

Breaks problem into smaller problems.

---

## Backtracking

Recursion + Undo changes.

Example:

```text
Choose
Explore
Unchoose
```

---

# 📌 Important Interview Questions

* Factorial
* Fibonacci
* Reverse Array
* Reverse String
* Binary Search
* Power Set
* Permutations
* N Queens
* Sudoku Solver
* Rat in Maze

---

# 📌 Time Complexity of Recursive Functions

Depends on:

* number of recursive calls
* work done per call

---

# Examples

| Problem             | Complexity |
| ------------------- | ---------- |
| Factorial           | O(n)       |
| Fibonacci Recursive | O(2^n)     |
| Binary Search       | O(log n)   |
| Merge Sort          | O(n log n) |

---

# 🚀 Final Thoughts

Recursion is one of the MOST IMPORTANT topics in programming.

It builds the foundation for:

* Dynamic Programming
* Trees
* Graphs
* Backtracking
* Divide and Conquer

Mastering recursion improves:

* problem solving
* logical thinking
* coding interviews

---

# 🧠 Golden Rule

```text
1. Identify Base Case
2. Reduce Problem Size
3. Trust Recursive Call
4. Combine Answers
```

If you master these 4 steps,
you can solve most recursive problems.
