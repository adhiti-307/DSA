# 📘 Bitwise Basics in Java

---

# 🔹 1. What is Bitwise Operation?

Bitwise operations work directly on the **binary representation** of numbers.

```text id="bb1"
Each number → sequence of bits (0s and 1s)
```

---

# 🔹 2. Binary Representation

```text id="bb2"
Decimal → Binary

5  = 101  
6  = 110  
```

---

# 🔹 3. Bitwise Operators

| Operator    | Symbol | Meaning             |
| ----------- | ------ | ------------------- |
| AND         | &      | Both bits must be 1 |
| OR          | |      | Any one bit is 1    |
| XOR         | ^      | Different bits      |
| NOT         | ~      | Flip bits           |
| Left Shift  | <<     | Multiply by 2       |
| Right Shift | >>     | Divide by 2         |

---

# 🔹 4. Basic Examples

```text id="bb3"
a = 5  (101)  
b = 3  (011)  

a & b = 001 → 1  
a | b = 111 → 7  
a ^ b = 110 → 6  
```

---

# 🔹 5. AND Operator (&)

```java id="bb4"
if((n & 1) == 0){
    // even number
}
```

👉 Used for:

* Checking even/odd
* Masking bits

---

# 🔹 6. OR Operator (|)

```java id="bb5"
int res = a | b;
```

👉 Sets bit to 1 if any bit is 1

---

# 🔹 7. XOR Operator (^)

```java id="bb6"
int res = a ^ b;
```

👉 Important properties:

```text id="bb7"
a ^ a = 0  
a ^ 0 = a  
```

---

# 🔹 8. NOT Operator (~)

```java id="bb8"
~5 = -6
```

👉 Flips all bits (2’s complement)

---

# 🔹 9. Shift Operators

---

## 🔸 Left Shift (<<)

```java id="bb9"
5 << 1 = 10  
```

👉 Multiply by 2

---

## 🔸 Right Shift (>>)

```java id="bb10"
5 >> 1 = 2  
```

👉 Divide by 2

---

# 🔹 10. Important Bit Tricks

---

## 🔸 Check Even / Odd

```java id="bb11"
(n & 1) == 0 → even  
```

---

## 🔸 Set ith Bit

```java id="bb12"
n | (1 << i)
```

---

## 🔸 Clear ith Bit

```java id="bb13"
n & ~(1 << i)
```

---

## 🔸 Toggle ith Bit

```java id="bb14"
n ^ (1 << i)
```

---

## 🔸 Get ith Bit

```java id="bb15"
(n >> i) & 1
```

---

# 🔹 11. Example Walkthrough

```text id="bb16"
n = 5 → 101  

Set 1st bit:
101 | 010 = 111 (7)
```

---

# 🔹 12. Common Mistakes

```text id="bb17"
❌ Confusing AND & OR  
❌ Wrong bit position  
❌ Ignoring operator precedence  
```

---

# 🔹 13. Interview Tips

```text id="bb18"
✔ Use XOR for unique elements  
✔ Use shifts for fast operations  
✔ Practice bit masking  
✔ Think in binary  
```

---

# 🧠 Quick Revision

```text id="bb19"
& → AND  
| → OR  
^ → XOR  
<< → multiply  
>> → divide  
```

---

# 🔥 Final Insight

```text id="bb20"
Bitwise operations = faster and optimized solutions
```

👉 Use when:

* Performance matters
* Working with subsets / flags

---
