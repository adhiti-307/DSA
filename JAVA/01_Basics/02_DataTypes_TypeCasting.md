# 📘 Data Types & Type Casting in Java

---

# 🔹 1. What are Data Types?

Data types define:

```text id="dt1"
Type of data a variable can store  
Size of memory allocated  
Range of values  
```

---

# 🔹 2. Types of Data Types

---

## 🔸 2.1 Primitive Data Types

| Type    | Size    | Range                |
| ------- | ------- | -------------------- |
| byte    | 1 byte  | -128 to 127          |
| short   | 2 bytes | -32K to 32K          |
| int     | 4 bytes | ~±2 billion          |
| long    | 8 bytes | very large           |
| float   | 4 bytes | decimal              |
| double  | 8 bytes | more precise decimal |
| char    | 2 bytes | single character     |
| boolean | 1 bit   | true/false           |

---

## 🔸 2.2 Non-Primitive Data Types

```text id="dt2"
String  
Array  
Class  
Object  
```

---

# 🔹 3. Variable Declaration

```java id="dt3"
int a = 10;
double d = 5.5;
char c = 'A';
boolean flag = true;
```

---

# 🔹 4. Type Casting

Type casting is converting one data type into another.

---

# 🔹 5. Types of Type Casting

---

## 🔸 5.1 Implicit Casting (Widening)

👉 Smaller → Larger data type

```java id="dt4"
int a = 10;
double d = a;
```

```text id="dt5"
int → long → float → double
```

---

## 🔸 5.2 Explicit Casting (Narrowing)

👉 Larger → Smaller data type

```java id="dt6"
double d = 10.5;
int a = (int) d;
```

👉 Output:

```text id="dt7"
a = 10
```

---

# 🔹 6. Type Promotion Rules

```text id="dt8"
byte, short, char → converted to int  
int → long → float → double  
```

---

## 🔸 Example

```java id="dt9"
byte a = 10;
byte b = 20;

int c = a + b; // result is int
```

---

# 🔹 7. Casting with Expressions

```java id="dt10"
int a = 10, b = 3;

double result = (double)a / b;
```

👉 Output:

```text id="dt11"
3.333...
```

---

# 🔹 8. Character Type

```java id="dt12"
char c = 'A';

int ascii = c;
```

👉 Output:

```text id="dt13"
65
```

---

# 🔹 9. Overflow & Underflow

```java id="dt14"
int max = Integer.MAX_VALUE;
System.out.println(max + 1);
```

👉 Output:

```text id="dt15"
Negative value (overflow)
```

---

# 🔹 10. Wrapper Classes

Used to convert primitives to objects

```java id="dt16"
Integer x = Integer.valueOf(10);
int y = x;
```

---

# 🔹 11. Parsing Strings to Numbers

```java id="dt17"
int x = Integer.parseInt("123");
double d = Double.parseDouble("10.5");
```

---

# 🔹 12. Common Mistakes

```text id="dt18"
❌ Loss of data in casting  
❌ Integer division mistake  
❌ Overflow issues  
❌ Forgetting type promotion  
```

---

# 🔹 13. Interview Tips

```text id="dt19"
✔ Always check type conversion  
✔ Use casting carefully  
✔ Beware of integer division  
✔ Know type promotion rules  
```

---

# 🧠 Quick Revision

```text id="dt20"
Primitive → int, double, char  
Implicit → automatic  
Explicit → manual  
```

---

# 🔥 Final Insight

```text id="dt21"
Type casting can silently change values
```

👉 Always verify output when casting

---
