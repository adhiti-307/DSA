# 📘 Operators in Java

---

# 🔹 1. What are Operators?

Operators are symbols used to perform operations on variables and values.

```text id="op1"
Example: +, -, *, /, %
```

---

# 🔹 2. Types of Operators

---

## 🔸 2.1 Arithmetic Operators

| Operator | Description    |
| -------- | -------------- |
| +        | Addition       |
| -        | Subtraction    |
| *        | Multiplication |
| /        | Division       |
| %        | Modulus        |

---

### ✅ Example

```java id="op2"
int a = 10, b = 3;

System.out.println(a + b); // 13
System.out.println(a - b); // 7
System.out.println(a * b); // 30
System.out.println(a / b); // 3
System.out.println(a % b); // 1
```

---

# 🔹 3. Unary Operators

---

## 🔸 Increment / Decrement

```java id="op3"
int x = 5;

System.out.println(++x); // 6 (pre)
System.out.println(x++); // 6 (post)
System.out.println(x);   // 7
```

---

## 🔸 Unary Plus / Minus

```java id="op4"
int a = 5;
int b = -a;
```

---

# 🔹 4. Assignment Operators

```java id="op5"
int a = 10;

a += 5;  // 15
a -= 2;  // 13
a *= 2;  // 26
a /= 2;  // 13
```

---

# 🔹 5. Relational Operators

| Operator | Meaning       |
| -------- | ------------- |
| ==       | Equal         |
| !=       | Not equal     |
| >        | Greater       |
| <        | Less          |
| >=       | Greater equal |
| <=       | Less equal    |

---

### ✅ Example

```java id="op6"
int a = 5, b = 10;

System.out.println(a < b); // true
System.out.println(a == b); // false
```

---

# 🔹 6. Logical Operators

| Operator | Meaning |
| -------- | ------- |
| &&       | AND     |
| ||       | OR      |
| !        | NOT     |

---

### ✅ Example

```java id="op7"
boolean a = true, b = false;

System.out.println(a && b); // false
System.out.println(a || b); // true
System.out.println(!a);     // false
```

---

# 🔹 7. Bitwise Operators

| Operator | Meaning |
| -------- | ------- |
| &        | AND     |
| |        | OR      |
| ^        | XOR     |
| ~        | NOT     |

---

### ✅ Example

```java id="op8"
int a = 5, b = 3;

System.out.println(a & b); // 1
System.out.println(a | b); // 7
System.out.println(a ^ b); // 6
```

---

# 🔹 8. Shift Operators

| Operator | Meaning              |
| -------- | -------------------- |
| <<       | Left Shift           |
| >>       | Right Shift          |
| >>>      | Unsigned Right Shift |

---

### ✅ Example

```java id="op9"
int a = 5;

System.out.println(a << 1); // 10
System.out.println(a >> 1); // 2
```

---

# 🔹 9. Ternary Operator

```java id="op10"
int a = 10, b = 20;

int max = (a > b) ? a : b;
```

---

# 🔹 10. Operator Precedence

```text id="op11"
1. ()  
2. Unary (++ -- !)
3. * / %
4. + -
5. Relational
6. Logical AND
7. Logical OR
8. Assignment
```

---

## 🔸 Example

```java id="op12"
int result = 10 + 5 * 2; // 20
```

---

# 🔹 11. Short-Circuit Evaluation

```java id="op13"
if(a != 0 && b/a > 2)
```

👉 Second condition runs only if first is true

---

# 🔹 12. Common Mistakes

```text id="op14"
❌ Using = instead of ==  
❌ Integer division confusion  
❌ Ignoring precedence  
❌ Misusing ++ operator  
```

---

# 🔹 13. Interview Tips

```text id="op15"
✔ Use parentheses for clarity  
✔ Understand precedence  
✔ Be careful with logical operators  
✔ Avoid tricky expressions  
```

---

# 🧠 Quick Revision

```text id="op16"
Arithmetic → + - * /  
Relational → compare  
Logical → conditions  
Bitwise → binary  
```

---

# 🔥 Final Insight

```text id="op17"
Operators define logic flow of your program
```

👉 Master operators → write correct logic faster

---
