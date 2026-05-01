# 📘 Conditional Statements in Java

---

# 🔹 1. What are Conditionals?

Conditionals are used to **control the flow of execution** based on conditions.

```text id="c1"
If condition is true → execute block  
Else → skip or execute alternative  
```

---

# 🔹 2. if Statement

---

## 🔸 Syntax

```java id="c2"
if(condition){
    // code
}
```

---

## 🔸 Example

```java id="c3"
int a = 10;

if(a > 5){
    System.out.println("Greater");
}
```

---

# 🔹 3. if-else Statement

---

## 🔸 Syntax

```java id="c4"
if(condition){
    // true block
} else {
    // false block
}
```

---

## 🔸 Example

```java id="c5"
int a = 3;

if(a % 2 == 0){
    System.out.println("Even");
} else {
    System.out.println("Odd");
}
```

---

# 🔹 4. if-else-if Ladder

---

## 🔸 Syntax

```java id="c6"
if(condition1){
}
else if(condition2){
}
else{
}
```

---

## 🔸 Example

```java id="c7"
int marks = 75;

if(marks >= 90){
    System.out.println("A");
}
else if(marks >= 70){
    System.out.println("B");
}
else{
    System.out.println("C");
}
```

---

# 🔹 5. Nested if

---

## 🔸 Example

```java id="c8"
int age = 20;
boolean hasID = true;

if(age >= 18){
    if(hasID){
        System.out.println("Allowed");
    }
}
```

---

# 🔹 6. switch Statement

---

## 🔸 Syntax

```java id="c9"
switch(expression){
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}
```

---

## 🔸 Example

```java id="c10"
int day = 2;

switch(day){
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Invalid");
}
```

---

# 🔹 7. Modern Switch (Java 14+)

```java id="c11"
int day = 2;

String result = switch(day){
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    default -> "Invalid";
};
```

---

# 🔹 8. Ternary Operator (Shortcut)

```java id="c12"
int a = 10, b = 20;

int max = (a > b) ? a : b;
```

---

# 🔹 9. Logical Conditions

```java id="c13"
if(a > 5 && b < 10)
if(a > 5 || b < 10)
if(!(a > 5))
```

---

# 🔹 10. Flow Representation

```text id="c14"
Condition → True → Block A  
          → False → Block B  
```

---

# 🔹 11. Common Mistakes

```text id="c15"
❌ Using = instead of ==  
❌ Missing braces {}  
❌ Wrong condition logic  
❌ Forgetting break in switch  
```

---

# 🔹 12. Interview Tips

```text id="c16"
✔ Keep conditions simple  
✔ Use switch for multiple cases  
✔ Avoid deep nesting  
✔ Use ternary for small conditions  
```

---

# 🧠 Quick Revision

```text id="c17"
if → basic condition  
if-else → two choices  
if-else-if → multiple conditions  
switch → multiple cases  
```

---

# 🔥 Final Insight

```text id="c18"
Conditionals control program logic
```

👉 Clear logic = fewer bugs

---
